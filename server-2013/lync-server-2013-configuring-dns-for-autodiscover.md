﻿---
title: 自動検出の DNS を構成する
TOCTitle: 自動検出の DNS を構成する
ms:assetid: f07a634c-3cf3-4958-8556-84596319ef54
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ945656(v=OCS.15)
ms:contentKeyID: 52056725
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 自動検出の DNS を構成する

 

_**トピックの最終更新日:** 2012-12-12_

Lync クライアントの自動検出をサポートするには、次のドメイン ネーム システム (DNS) レコードを作成する必要があります。

  - 組織のネットワーク内から接続する Lync クライアントをサポートするための内部 DNS レコード

  - インターネットから接続する Lync クライアントをサポートするための外部 (パブリック) DNS レコード

内部 DNS レコードと外部 DNS レコードは SIP ドメインごとに作成する必要があります。

DNS レコードは、サブジェクトの別名 (SAN) で新しい資格情報を作成できるかどうかに基づいて、A (ホスト) レコードまたは CNAME レコードのどちらかになります。lyncdiscover.\<domain name\> SAN で新しい外部 (パブリック) 資格情報をリクエストおよび展開できない場合は、HTTP/TCP ポート 80 を使用する手順を実行します。次の手順では、内部および外部 DNS レコードを作成する方法を説明します。

## DNS CNAME レコードを作成するには

1.  次のように、DNS サーバーにログオンします。
    
      - 内部 DNS レコードを作成するには、Domain Admins グループのメンバーまたは DnsAdmins グループのメンバーとして、ネットワーク内の DNS サーバーにログオンします。
    
      - 外部 DNS レコードを作成するには、パブリック DNS プロバイダーに接続します。

2.  DNS 管理スナップインを開きます。\[**スタート**\] ボタンをクリックし、\[**管理ツール**\]、\[**DNS**\] の順にクリックします。

3.  次のどちらかの操作を行います。
    
      - 内部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する Active Directory ドメイン (例: contoso.local) の \[**前方参照ゾーン**\] を展開します。
        
        > [!NOTE]  
        > このドメインは、Lync Server 2013ディレクター プールおよびフロント エンド プールがインストールされる Active Directory ドメインです。
    
      - 外部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する SIP ドメイン (例: contoso.com) の \[**前方参照ゾーン**\] を展開します。

4.  次のように、ディレクター プールのホスト A レコードが存在することを確認します。
    
      - 内部 DNS レコードの場合、ホスト A レコードはディレクター プールの内部 Web サービス完全修飾ドメイン名 (たとえば、lyncwebdir01.contoso.local) に対して存在する必要があります。
    
      - 外部 DNS レコードの場合、ホスト A レコードは、ディレクター プールの外部 Web サービス FQDN (たとえば、lyncwebextdir.contoso.com) に対して存在する必要があります。

5.  次のように、フロント エンド プールのホスト A レコードが存在することを確認します。
    
      - 内部 DNS レコードの場合、フロント エンド プールの内部 Web サービスの FQDN 用のホスト A レコードが存在します (例: lyncwebpool01.contoso.local)。
    
      - 外部 DNS レコードの場合、フロント エンド プールの外部 Web サービスの FQDN 用のホスト A レコードが存在します (例: lyncwebextpool01.contoso.com)。

6.  内部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する SIP ドメイン (例: contoso.com) の \[**前方参照ゾーン**\] を展開します。
    
    > [!NOTE]
    > 外部 DNS レコードを作成する場合、使用する SIP ドメインの [<strong>前方参照ゾーン</strong>] は手順 3. で既に展開されています。


7.  SIP ドメイン名を右クリックして、\[**新しいエイリアス (CNAME)**\] をクリックします。

8.  \[**エイリアス名**\] に、次のどちらかを入力します。
    
      - 内部 DNS レコードの場合、内部自動検出サービス URL のホスト名として、「lyncdiscoverinternal」と入力します。
    
      - 外部 DNS レコードの場合、自動検出サービスの外部 URL のホスト名として、「lyncdiscover」と入力します。

9.  \[**ターゲット ホスト用の完全修飾ドメイン名 (FQDN)**\] で、次のどちらかの操作を行います。
    
      - 内部 DNS レコードの場合、ディレクター プールの内部 Web サービス FQDN (たとえば、lyncwebdir01.contoso.local) を入力または参照し、\[**OK**\] をクリックします。
    
      - 外部 DNS レコードの場合、ディレクター プールの外部 Web サービス FQDN (たとえば、lyncwebextdir.contoso.com) を入力または参照し、\[**OK**\] をクリックします。
    
    > [!NOTE]
    > ディレクターを使用していない場合、フロント エンド プールの内部および外部 Web サービス FQDN を使用するか、単一サーバーの場合、フロント エンド サーバーまたは Standard Edition サーバーの FQDN を使用します。
    

    > [!IMPORTANT]
    > Lync Server 2013 環境でサポートする各 SIP ドメインの前方参照ゾーンで新しい自動検出 CNAME レコードを作成する必要があります。



## DNS A レコードを作成するには

1.  次のように、DNS サーバーにログオンします。
    
      - 内部 DNS レコードを作成するには、Domain Admins グループのメンバーまたは DnsAdmins グループのメンバーとして、ネットワーク内の DNS サーバーにログオンします。
    
      - 外部 DNS レコードを作成するには、パブリック DNS プロバイダーまたは外部 DNS サーバーに接続します。

2.  DNS 管理スナップインを開きます。\[**スタート**\] ボタンをクリックし、\[**管理ツール**\]、\[**DNS**\] の順にクリックします。

3.  次のどちらかの操作を行います。
    
      - 内部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する Active Directory ドメイン (例: contoso.local) の \[**前方参照ゾーン**\] を展開します。
        
        > [!NOTE]  
        > このドメインは、Lync Server 2013ディレクター プールおよびフロント エンド プールがインストールされる Active Directory ドメインです。
    
      - 外部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する SIP ドメイン (例: contoso.com) の \[**前方参照ゾーン**\] を展開します。

4.  次のように、ディレクター プールのホスト A (IPv6 では AAAA) レコードが存在することを確認します。
    
      - 内部 DNS レコードの場合、ホスト A (IPv6 では AAAA) レコードは、ディレクター プールの内部 Web サービス FQDN (たとえば、lyncwebdir01.contoso.local) に対して存在する必要があります。
    
      - 外部 DNS レコードの場合、ホスト A (IPv6 では AAAA) レコードは、ディレクター プールの外部 Web サービス FQDN (たとえば、lyncwebextdir.contoso.com) に対して存在する必要があります。

5.  次のように、フロント エンド プールのホスト A (IPv6 では AAAA) レコードが存在することを確認します。
    
      - 内部 DNS レコードの場合、フロント エンド プールの内部 Web サービスの FQDN 用のホスト A (IPv6 では AAAA) レコードが存在します (例: lyncwebpool01.contoso.local)。
    
      - 外部 DNS レコードの場合、フロント エンド プールの外部 Web サービスの FQDN 用のホスト A (IPv6 では AAAA) レコードが存在します (例: lyncwebextpool01.contoso.com)。

6.  内部 DNS レコードの場合、DNS サーバーのコンソール ツリーで、使用する SIP ドメイン (例: contoso.com) の \[**前方参照ゾーン**\] を展開します。
    
    > [!NOTE]
    > 外部 DNS レコードを作成する場合、使用する SIP ドメインの [<strong>前方参照ゾーン</strong>] は手順 3. で既に展開されています。


7.  SIP ドメイン名を右クリックして、\[**新しいホスト (A または AAAA)**\] をクリックします。

8.  \[**名前**\] に、ホスト名を次のように入力します。
    
      - 内部 DNS レコードの場合、内部自動検出サービス URL のホスト名として、「lyncdiscoverinternal」と入力します。
    
      - 外部 DNS レコードの場合、自動検出サービスの外部 URL のホスト名として、「lyncdiscover」と入力します。
    
    > [!NOTE]
    > ドメイン名は、レコードが定義されるゾーンから取られるため、A レコードの一部として入力する必要はありません。


9.  \[**IP アドレス**\] に、IP アドレスを次のように入力します。
    
      - 内部 DNS レコードの場合、ディレクターの内部 Web サービス IP アドレスを入力します (または、ロード バランサーを使用している場合、ディレクター ロード バランサーの仮想 IP (VIP) を入力します)。
        
        > [!NOTE]  
        > ディレクターを使用していない場合、フロント エンド サーバーまたは Standard Edition サーバーの IP アドレスを入力するか、ロード バランサーを使用している場合はフロント エンド プール ロード バランサーの VIP を入力します。
    
      - 外部 DNS レコードの場合、リバース プロキシの外部またはパブリック IP アドレスを入力します。

10. \[**ホストの追加**\] をクリックし、\[**OK**\] をクリックします。

11. 追加の A レコードを作成するには、手順 8. ～ 10. を繰り返します。
    

    > [!IMPORTANT]
    > Lync Server 2013 環境でサポートする各 SIP ドメインの前方参照ゾーンで新しい lyncdiscover および lyncdiscoverinternal A レコードを作成する必要があります。



12. A (IPv6 では AAAA) レコードの作成が完了した後で、\[**完了**\] をクリックします。

