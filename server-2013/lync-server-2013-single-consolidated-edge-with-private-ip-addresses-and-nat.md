﻿---
title: 'Lync Server 2013: プライベート IP アドレスと NAT を用いた単一統合エッジ'
TOCTitle: プライベート IP アドレスと NAT を用いた単一統合エッジ
ms:assetid: e1e5189e-f17d-45e9-b177-e0e6f97f8951
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg399001(v=OCS.15)
ms:contentKeyID: 48273843
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 におけるプライベート IP アドレスと NAT を用いた単一統合エッジ

 

_**トピックの最終更新日:** 2016-12-08_

組織がサポートを必要とするアクセス エッジ サービスのクライアント接続が 15,000 未満、有効 Lync Server Web 会議サービスのクライアント接続が 1,000 未満、および音声ビデオ エッジの同時セッションが 500 未満であり、エッジ サーバーの高可用性が重要でない場合には、このトポロジを活用することで、ハードウェア コストを削減し、展開を簡単化できます。高い処理能力や高可用性を必要とする場合には、拡張統合エッジ サーバー トポロジを展開する必要があります。詳細については、次のいずれかを参照してください。

  - [Lync Server 2013 における拡張統合エッジ、NAT によるプライベート IP アドレスを使用した DNS 負荷分散](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Lync Server 2013 での拡張統合エッジ、パブリック IP アドレスによる DNS 負荷分散](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Lync Server 2013 のハードウェア ロード バランサーによる拡張統合エッジ](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md)

この図では、内部ネットワークで エッジ サーバーと フロント エンド プールまたはサーバーとの間に展開されるオプションのサーバー役割である ディレクターは示されていません。ディレクターのトポロジの詳細については、「[Lync Server 2013 のディレクターに必要なコンポーネント](lync-server-2013-components-required-for-the-director.md)」を参照してください。この図は、単一のリバース プロキシを表しています。

> [!NOTE]
> 以下の図には、方向と IP アドレス指定の例が示されていますが、正しい受信トラフィックと送信トラフィックを使用した実際の通信フローを表すことを目的としていません。図は、可能なトラフィックを大まかに表しています。着信 (リッスン ポートへの) および発信 (宛先サーバーまたはクライアントへの) に関連するトラフィック フローの詳細は、各シナリオのポートの概要図に示されています。たとえば、実際には TCP 443 は着信 (エッジ プロキシまたはリバース プロキシへの) のみで、プロトコル (TCP) の観点から見た場合のみ双方向のフローになります。たとえば、実際には TCP 443 は着信 (エッジ プロキシまたはリバース プロキシへの) のみで、プロトコル (TCP) の観点から見た場合のみ双方向のフローになります。さらに、図は、ネットワーク アドレス変換 (NAT) が発生したとき (着信で宛先アドレスが変更され、発信で発信元アドレスが変更されます) に変化するトラフィックの特性を示しています。外部および内部ファイアウォールとサーバー インターフェイスの例は参照のみを目的としたものです。最後に、必要に応じて、既定のゲートウェイとルート関係の例が示されています。図では、 <em>.com</em> DNS ゾーンを使用してリバース プロキシおよび エッジ サーバーの外部 DNS ゾーンを表し、 <em>.net</em> DNS ゾーンを使用して内部 DNS ゾーンを表していることに注意してください。


Microsoft Lync Server 2013 では、IPv6 アドレス指定が新しくサポートされるようになりました。IPv4 アドレス指定と同じように、IPv6 アドレスを、割り当てられた IPv6 アドレス スペースの一部になるように割り当てる必要があります。このトピックのアドレスは、例としてのみ使用されています。展開で機能する IPv6 アドレスを取得して正しいスコープを指定し、内部および外部アドレスと相互運用する必要があります。 Windows Server は、段階的な IPv6 運用と *デュアル スタック* と呼ばれる IPv4 から IPv6 への通信にとって重要な機能を提供します。デュアル スタックは、IPv4 および IPv6 用の別個のネットワーク スタックです。デュアル スタックを使用すると、IPv4 および IPv6 用のアドレスを同時に割り当て、要件に基づいて、サーバーが他のホストやクライアントと通信できるようになります。

IPv6 アドレス指定で使用する通常のアドレス タイプは、IPv6 グローバル アドレス (パブリック IPv4 アドレスに類似しています)、一意の IPv6 ローカル アドレス (プライベート IPv4 アドレスに類似しています)、および IPv6 リンクローカル アドレス (IPv4 用 Windows Server の自動プライベート IP アドレスに類似しています) です。

IPv6 から IPv4 に変換 (一般に NAT64 と呼ばれます) したり、IPv6 から IPv6 に変換 (一般に NAT66 と呼ばれます) したりするネットワーク アドレス変換 (NAT) テクノロジが存在します。NAT テクノロジが存在するため、 Lync Serverエッジ サーバー用に示された 5 つのシナリオは引き続き有効です。


> [!WARNING]
> IPv6 は複雑なトピックであり、ネットワーク チームおよびインターネット プロバイダーと共同で注意深く計画し、Windows サーバー レベルおよび Lync Server 2013 レベルに割り当てるアドレスが意図したとおりに動作することを保証する必要があります。IPv6 アドレス指定および計画に関するその他のリソースについては、このトピックの最後にあるリンクを参照してください。



**単一統合エッジ トポロジ**

![単一統合エッジ、トポロジ](images/Gg399001.d9b889c1-587c-4732-9b68-841186ccff78(OCS.15).jpg "単一統合エッジ、トポロジ")


> [!IMPORTANT]
> 通話受付管理 (CAC) を使用している場合は、IPv4 アドレスを エッジ サーバー内部インターフェイスに引き続き割り当てる必要があります。CAC は IPv4 アドレスを使用しており、動作可能な IPv4 アドレスが存在する必要があります。



## このセクション中

  - [証明書の概要 - Lync Server 2013 内の NAT を使用したプライベート IP アドレスを持つ単一統合エッジ](lync-server-2013-certificate-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

  - [ポートの概要 - Lync Server 2013 の NAT を使用したプライベート IP アドレスを含む単一統合エッジ](lync-server-2013-port-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

  - [DNS の概要 - Lync Server 2013 の単一統合エッジ (NAT によるプライベート IP アドレスを使用)](lync-server-2013-dns-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

## 関連項目

#### その他のリソース

[IP Version 6 アドレス指定アーキテクチャ](http://tools.ietf.org/html/rfc4291)  
[IPv6 グローバル ユニキャスト アドレス形式](http://tools.ietf.org/html/rfc3587)  
[一意のローカル IPv6 ユニキャスト アドレス](http://tools.ietf.org/html/rfc4193)

