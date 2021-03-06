﻿---
title: 'Lync Server 2013: FAQ: Skype 接続用の Lync Server のプロビジョニング'
TOCTitle: 'FAQ: Skype 接続用の Lync Server のプロビジョニング'
ms:assetid: 4d1b2bfc-780b-4b8c-afd5-11c2e59203b5
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn440172(v=OCS.15)
ms:contentKeyID: 59602757
ms.date: 12/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# FAQ: Skype 接続用の Lync Server 2013 のプロビジョニング

 

_**トピックの最終更新日:** 2016-12-27_

**Q: Microsoft Lync と Skype の間ではどの機能がサポートされていますか。**

**A:** 現在、Skype は Microsoft 製品ファミリの一部であるため、Skype を利用する何億人というユーザーには、統合通信のシナリオを拡張する新しい可能性が広がっています。この組み合わせでは、Lync の豊富な機能と Skype のカバー範囲により、Lync のお客様は、サプライヤー、カスタマー、およびパートナーとの接続と共同作業が実現できます。

  - インスタント メッセージと音声/ビデオ通話 - Lync ユーザーと Skype ユーザーの間で、音声/ビデオ通話とインスタント メッセージングのフェデレーションが実現されます。

  - プレゼンスの共有 - フェデレーション連絡先の間でプレゼンス情報を交換できます。

  - シンプルな管理 - 設定と制御で、組織のポリシーと基準に従ってフェデレーション通信を構成できます。

**Q: Lync 展開と Skype を接続するにはどのような条件が必要ですか。**

**A:** 次のいずれか一方を所有している場合、Skype 接続のライセンスがあります。

  - Skype に接続する組織内のユーザー/デバイス用の Lync Server (2010 または 2013) と Lync Server Standard Client Access Licenses (2010 または 2013 の "CAL")。

  - (スタンドアロン ライセンス、または Office 365 スイートの一部である) Lync Online。ただし、このサービス (pic.lync.com) は、Lync Server およびハイブリッドの Lync Server と Lync Online 展開のプロビジョニング専用です。Lync Online PIC のプロビジョニングは、Lync Online コントロール パネル (LOCP) で行います。

**Q: Lync のエンド ユーザーが Skype の連絡先に接続するにはどのような操作が必要ですか。**

**A:** 組織の Lync 管理者によりドメインがアクティブにされ、機能が有効にされた後、Lync のユーザーは Skype の連絡先を Lync クライアント内の連絡先リストに追加できます。

**Q: Skype のエンド ユーザーが Lync の連絡先に接続するにはどのような操作が必要ですか。**

**A:** Lync のユーザーへの接続が必要なすべての Skype のユーザーは、Skype ID と関連付けられている Microsoft アカウントを用意し、その Microsoft アカウントを使用してサインインする必要があります。この操作は Skype クライアント内で実施できます。

**Q: Windows Live とのフェデレーションはまだ使用できますか。**

**A:** 2012 年 10 月より、マイクロソフトは Windows Live Messenger (WLM) のユーザーを Skype に移行する支援を開始しましたが、これは最終的には WLM の提供中止を目的としています。Lync は WLM が市場に存在する限りは WLM とのフェデレーションを引き続きサポートしますが、追加の Windows Live ドメインのアクティブ化は許可されていません。WLM ユーザーの移行は、Microsoft アカウント (WLM と同じ資格情報) を使用したサインインが可能である、Mac および Windows 版の Skype 6.0 (2012 年 10 月 25 日リリース) により実現されます。Skype にサインインするだけで、WLM のバディ リストは自動的に Skype に入力されます。またユーザーは、固定電話と携帯電話への通話、画面の共有、グループ ビデオ通話などの Skype の拡張通信機能と、幅広いデバイスのサポートを利用できます。さらに、WLM ユーザーのフェデレーション関係にある Lync の連絡先は残りのバディ リストと共に Skype への移行に従い、またこれらの連絡先に関する Skype と Lync の間の IM はすぐに使用できるようになります。Lync のお客様には、このサービスの継続を有効にするために必要な操作はありません。

**Q: Yahoo\! または AOL とのフェデレーションはまだ使用できますか。**

**A:** Lync および Office Communications Server のお客様用の、Yahoo\! および AOL とのフェデレーションは両方とも終了予定です。Microsoft がこれらの各サービスを提供できるのは、Yahoo\! と AOL からのサポートを条件とするものでしたが、これらの基盤となる契約の終了が近づいてきました。Yahoo\! と AOL のサービスは、2014 年 6 月まで継続されます。

  - Yahoo\!: サービスは 2014 年 6 月まで継続され、お客様は引き続き Microsoft Lync パブリック IM 接続のユーザー サブスクリプション ライセンス ("PIC USL") によるライセンスが必要です。2012 年 9 月 1 日の時点で、PIC USL を新規または更新契約で購入できなくなりました。この日の前に購入されたライセンスをお持ちのお客様は、サービス終了日またはライセンス有効期限のうち、早い方の日付まで Yahoo\! とのフェデレーションを引き続きご利用いただけます。有効期限が 2014 年 7 月 1 日以降の PIC ライセンスをお持ちのお客様には、2014 年 7 月 1 日以降の期間に相当するお支払額を返金いたします。

  - AOL: 2014 年 6 月 30 日をもって、Lync の IM 接続 ("PIC") サービスは終了いたします。サービス終了時のお客様のサービス中断を避けるため、追加ドメインの提供はすでに終了しています。2014 年 6 月 30 日までの期間、お客様は特別な手続きなしに引き続き AIM でフェデレーションによる通信をサポートしていただけます。7 月 1 日以降 (またはそれまでの間、追加ドメインをご希望のお客様には)、AOL から代替サービスが直接提供されます。AOL の新規サービスの詳細については、 <http://aimenterprise.aol.com/pic.php> (英語) を参照してください。 

**Q: Lync を購入する前に Skype の接続を試用することはできますか。**

**A:** Skype の接続は試用では提供されていません。試用の代わりに、適格なライセンスを所有する Lync のお客様には、サービスにサインアップしてテストすることをお勧めします。

**Q: プロビジョニングにはどのような情報が必要ですか。**

**A:** 条件を満たすライセンスの下でプロビジョニング要求を送信するには、次の情報が必要です。

  - マイクロソフト契約番号:
    
      - Microsoft ボリューム ライセンス サポート: Microsoft ボリューム ライセンス契約番号
    
      - Microsoft Partner Network: ヘッドクォーター パートナー ID
    
      - サービス ブロバイダーのライセンス契約: 初期登録番号
    
      - 高ボリューム サービス: 製品登録番号

  - アクセス エッジ サービスの完全修飾ドメイン名 (FQDN)。
    
      - 少なくとも 1 つのアクセス エッジ サービスの FQDN が必要です。
    
      - 組織でアクセス エッジ サービスを実行しているサーバーが複数存在する場合、追加のアクセス エッジ サービスごとに FQDN を指定します。重要: 以前にアクセス エッジ サービスの FQDN を指定していて、それを変更する必要がある場合、変更のプロビジョニングが完了するまで数日かかる可能性があり、また結果としてサービスが中断する可能性があります。サービスの中断を防ぐには、アクセス エッジ サービスの以前に指定した FQDN を維持することをお勧めします。

  - セッション開始プロトコル (SIP) ドメイン。これは、ユーザーがインスタント メッセージングに現在使用している SIP URI のドメイン サフィックスです。組織で複数の SIP ドメインを使用している場合は、インスタント メッセージングに使用する各ドメインのドメイン サフィックスを指定します。たとえば、user1@contoso.com には SIP ドメインの contoso.com を指定し、user1@example.fabrikam.com には SIP ドメインとして example.fabrikam.com を指定します。
    
    > [!NOTE]
    > SIP ドメインのドメイン サフィックスのみを指定します。SIP ドメインの FQDN (アクセス エッジ サービスの FQDN を含む) は指定しないでください。


  - 連絡先情報。指定する各 SIP ドメインの管理者のメール アドレスを指定します。

**Q: 分割ドメインのシナリオで Lync と Skype の接続を有効にするにはどうすればよいですか。**

**A:** Lync Online 2013 と Lync Server 社内分割ドメインのシナリオ (ユーザーは両方ともオンラインで、社内では同じ SIP ドメインを使用) を使用している場合は、次の順序で以下の 2 つの手順を実行して、Lync と Skype の接続を有効にします。

1.  「PIC プロビジョニング ガイド」で説明されているように、社内の Lync と Skype の接続を設定します。

2.  マイクロソフトによりドメインがプロビジョニングされたという確認を参照するまで待ちます。

3.  確認を参照した後、Lync 管理センターを使用して "外部通信" を有効にします。詳細については、[http://office.microsoft.com/ja-jp/support/configure-external-communications-HA102817865.aspx?CTT=5\&origin=HA102817356](http://office.microsoft.com/ja-jp/support/configure-external-communications-ha102817865.aspx?ctt=5%26origin=ha102817356) を参照してください。

この順序は重要です。Lync Online での通信を有効にする前に、社内の接続を設定する必要があります。順序が逆であると、 <https://pic.lync.com> で社内用に入力された情報が有効になりません。このドメインとの外部通信用に Lync Online を既に設定した場合は、その通信を無効にして 24 時間待機してから再開します。まず、 <https://pic.lync.com> で社内の情報を入力し、Lync Online の外部通信を有効にします。

**Q: Skype 接続用に複数のアクセス エッジ サービスの FQDN をプロビジョニングできますか。**

**A:** プロビジョニング要求ごとに 10 個までのアクセス エッジ サービスの FQDN をプロビジョニングできます。

**Q: プロビジョニングを要求する組織に関してマイクロソフトの担当者が確認した Microsoft アカウントのメール アドレスの一覧を入手できますか。**

**A:** いいえ。これらのアドレスは個人を識別できる情報と見なされ、共有されません。

**Q: Windows Live でサポートされるドメイン以外のドメインが含まれる ID が付属する Windows Live Messenger 連絡先を追加するにはどうすればよいですか。**

**A:** ドメインが Windows Live 以外のドメインであるアカウントまたは ID が付属する Windows Live Messenger ユーザーを追加する場合は、\<ユーザー名\>(\<ドメイン名\>)@msn.com の形式でアドレスを入力します。\<ドメイン名\> はユーザーのメール アドレスのドメイン名です。たとえば、ted@contoso.com を追加する場合は、ted(contoso.com)@msn.com という形式を使用します。Windows Live により管理されるドメインの一覧については、http://support.microsoft.com/?kbid=897567 の「Live Communications Server Service Pack 1 をインストールした後にパブリック インスタント メッセージングで発生する可能性がある既知の問題」の「サポートされるドメイン」セクションを参照してください。

**Q: プロビジョニング処理にはどの程度の時間がかかりますか。**

**A:** プロビジョニングは最長で 30 日かかる可能性があります。

**Q: プロビジョニングの完了はどのようにすればわかりますか。**

**A:** プロビジョニングが完了した時点で、マイクロソフトはメール通知を送信します。

**Q: 送信した構成または連絡先の詳細情報を更新するにはどうすればよいですか。**

**A:** プロビジョニングが完了する前に、プロビジョニングの要求に使用した同じ Web サイトで情報を更新できます。契約番号を入力し、\[Update service\] (サービスの更新) をクリックします。

