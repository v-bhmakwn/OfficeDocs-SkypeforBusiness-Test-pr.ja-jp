﻿---
title: 'Lync Server 2013: ホスト SIP フェデレーション プロバイダーの作成または編集'
TOCTitle: ホスト SIP フェデレーション プロバイダーの作成または編集
ms:assetid: 0dd6dcb6-a88d-46b8-9c96-b35967309bcd
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ552445(v=OCS.15)
ms:contentKeyID: 49115197
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのホスト SIP フェデレーション プロバイダーの作成または編集

 

_**トピックの最終更新日:** 2012-10-19_

ホストされるプロバイダーのインスタント メッセージング (IM) 接続では、組織内のユーザーは IM を使用して、Microsoft Office 365 や Lync Online などのホストされるプロバイダーが提供する IM サービスのユーザーと通信できます。

各ホストされるプロバイダーは、プロバイダーのエッジ サーバーの完全修飾ドメイン名と、既定の確認レベルである \[**連絡先リストのユーザーのうち、このプロバイダーを使うユーザーとの通信のみを許可する**\] によって構成されます。

ホストされるプロバイダーを作成または編集するには、次の手順を使用します。

## ホストされるプロバイダーを作成または編集するには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで、\[**フェデレーションと外部アクセス**\] をクリックし、\[**SIP フェデレーション プロバイダー**\] をクリックします。

4.  新しいホストされるプロバイダーを作成するには、\[**新規**\] をクリックし、\[**ホストされるプロバイダー**\] をクリックします。

5.  ホストされるプロバイダーの一覧に示されるプロバイダーを編集する必要がある場合は、編集するプロバイダーを選択し、\[**編集**\]、\[**編集の表示**\] の順にクリックします。

6.  \[**編集 SIP フェデレーション プロバイダー**\] ページでは、次の設定を入力または編集できます。
    
      - \[**このプロバイダーとの通信を有効にする**\]   この設定を選択すると、このプロバイダーのユーザーと通信できます。
    
      - \[**プロバイダー名:**\]  必須プロパティです。プロバイダーの名前を入力します。この名前は、SIP フェデレーション プロバイダーの一覧に反映されます。
    
      - \[**アクセス エッジ サービス (FQDN)**\]   必須プロパティ。構成するホストされるプロバイダーのアクセス エッジ サービスの完全修飾ドメイン名を入力します。この情報は、ホストされるプロバイダーによって提供される必要があります。また、この情報は、ホストされるプロバイダーのアクセス エッジ サービスの FQDN が変更された場合に限り、それに応じて変更する必要があります。
    
      - \[**Default verification level:**\]   既定の設定である \[**Allow users to communicate with people on their Contacts list who use this provider**\] を使用すると、連絡先リストに含まれる承認済みの連絡先に通信が制限されます。
        
        \[**このプロバイダーを使うすべてのユーザーとの通信を許可する**\] を選択すると、連絡先に対する制限が削除されます。この設定は、ホストされるプロバイダーのネットワークからの通信を制限しません。

7.  設定の構成が完了したら、\[**コミット**\] をクリックして保存するか、\[**キャンセル**\] をクリックして変更を破棄します。

## 関連項目

#### タスク

[Lync Server 2013 でのパブリック ユーザー アクセスを制御するポリシーの構成](lync-server-2013-configure-policies-to-control-public-user-access.md)  
[Lync Server 2013 でのフェデレーションおよびパブリック IM 接続の有効化または無効化](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

