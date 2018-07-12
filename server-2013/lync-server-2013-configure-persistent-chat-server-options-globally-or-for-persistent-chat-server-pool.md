﻿---
title: 'Lync Server 2013: 常設チャット サーバーのオプションをグローバルに、または常設チャット サーバー プール用に構成する'
TOCTitle: 常設チャット サーバーのオプションをグローバルに、または常設チャット サーバー プール用に構成する
ms:assetid: 1e8d5245-cd58-4aad-9a1c-35b24189bc40
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204731(v=OCS.15)
ms:contentKeyID: 48271465
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 で常設チャット サーバーのオプションをグローバルに、または常設チャット サーバー プール用に構成する

 

_**トピックの最終更新日:** 2012-10-06_

Lync Server 2013 コントロール パネルで、\[**常設チャット**\] ページの \[**常設チャットの構成**\] セクションを使用すると、常設チャットの設定をグローバルに構成してすべての 常設チャット サーバー プールに適用したり、設定を特定の 常設チャット サーバー プール用に構成したりできます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>常設チャット サーバーを構成して使用するには、まず、トポロジ ビルダーを使用して 常設チャット サーバー サポートをトポロジに追加してから、そのトポロジを公開する必要があります。詳細については、「展開」のドキュメントの「<a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013 での展開への常設チャットサーバーの追加</a>」を参照してください。</td>
</tr>
</tbody>
</table>


## 常設チャットのオプションをグローバルに構成するには

1.  CsPersistentChatAdministrator または CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  \[**スタート**\] メニューから \[ Lync Server コントロール パネル\] を選択するか、ブラウザー ウィンドウを開いて管理 URL を入力します。Lync Server コントロール パネルの起動に使用できるさまざまな方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。
    

    > [!IMPORTANT]
    > Windows PowerShell コマンドレットを使用することもできます。詳細については、「展開」のドキュメントの「<A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Windows PowerShell コマンドレットを使用した常設チャット サーバーの構成</A>」を参照してください。



3.  左側のナビゲーション バーで \[**常設チャット**\] をクリックし、\[**常設チャットの構成**\] をクリックします。

4.  \[**常設チャットの構成**\] ページで、\[**新規**\] をクリックし、\[**サイト構成**\] をクリックします。
    

    > [!IMPORTANT]
    > このオプションは、サイトに展開されたすべての 常設チャット サーバー プールに構成を適用する場合に選択します。特定の 常設チャット サーバー プールに構成を適用する場合は、[<STRONG>プール構成</STRONG>] をクリックします。



5.  \[**サイトの選択**\] で、常設チャット サーバー サイト構成用に構成するサイトを選択します。

6.  \[**新規 常設チャットの構成**\] で、次の操作を行います。
    
      - \[**名前**\] で、新しい構成設定の名前を指定します。既定では、サイト名が既に存在します。
    
      - \[**Default chat history**\] で、最初の要求時にチャット ルームごとに処理されるチャット メッセージ数を定義します。既定値は 30 で、これはグローバルな既定値です。管理者はカテゴリごとにチャット履歴を無効にできます。
        

        > [!IMPORTANT]
        > 常設チャット サーバーは、これらのメッセージをメモリ内にキャッシュするので、この値を増やすとキャッシュされるメッセージの数も増加します。履歴コンテンツには、検索を使用していつでもアクセスできます。既定値は、チャット ルームに接続したときに最初に表示されるメッセージの最大数を規定しているにすぎません。

    
      - \[**最大ファイル サイズ (KB)**\] で、各チャット履歴の最大ファイル サイズを選択します。既定値は 20 MB (20,000 KB) です。これは、システム内のチャット ルーム (対応する \[**分類**\] 設定でファイルのアップロードが有効化されているチャット ルーム) にアップロードできるファイルの最大サイズです。
        

        > [!IMPORTANT]
        > カスタム アプリケーション、あるいは Office Communications Server 2007 R2グループ チャット サーバーまたは Lync Server 2010、グループ チャットを使用する以前の グループ チャット クライアントはチャット ルームにファイルを投稿できるため、この設定がサーバーに対して適用されます。Lync 2013 クライアントにはファイル アップロード/ダウンロード機能がないため、純粋な Lync 2013 展開または Lync 2013 クライアントの場合は 常設チャット サーバー チャット ルームにファイルを投稿することはできません。

    
      - \[**参加者の更新制限**\] で、参加者の更新の制限値を選択します。常設チャット サーバーは、接続しているユーザーの数がこの値に達するまで、すべての参加者に名簿情報 (チャット ルームに接続しているユーザー) を送信します。既定値は 75 です。この制限値は特定のチャット ルームの参加者の最大数を示し、この値を超えると、常設チャット サーバーでは、チャット ルームに現在誰がいるかに関する名簿の更新を、接続しているクライアントに送信することを停止します。
    
      - (オプション) \[**ルームの管理 URL**\] で、ルーム管理 URL を選択します。これは Web ベースのカスタム チャット ルーム管理用の URL です。チャット ルームの管理をカスタマイズする必要がなく、既定の設定をそのまま使用する場合は、このオプションを空白のままにします。URL を設定すると、その URL は内部と外部の両方のチャット ルーム管理 URL として適用されます。
        
        チャット ルームの作成をカスタマイズして、特定のビジネス ワークフローを含める場合は、常設チャット サーバー ソフトウェア開発キット (SDK) を使用してカスタムのチャット ルーム管理ソリューションを構築し、それをホストして、その URL をここに配置します。ユーザーがチャット ルームを表示または作成するときにカスタム チャット ルーム管理ソリューションを使用するよう、この URL がクライアントに伝えられます。

7.  \[**確定**\] をクリックします。

## 常設チャットのオプションを特定の 常設チャット サーバー プール用に構成するには

1.  CsPersistentChatAdministrator または CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  \[**スタート**\] メニューから \[ Lync Server コントロール パネル\] を選択するか、ブラウザー ウィンドウを開いて管理 URL を入力します。Lync Server コントロール パネルの起動に使用できるさまざまな方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。
    

    > [!IMPORTANT]
    > Windows PowerShell コマンドレットを使用することもできます。詳細については、「展開」のドキュメントの「<A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Windows PowerShell コマンドレットを使用した常設チャット サーバーの構成</A>」を参照してください。



3.  左側のナビゲーション バーで \[**常設チャット**\] をクリックし、\[**常設チャットの構成**\] をクリックします。

4.  \[**常設チャットの構成**\] ページで、\[**新規**\] をクリックし、\[**プール構成**\] をクリックします。

5.  \[**サービスの選択**\] で、構成する 常設チャット サーバー プールに関連付けられたサービスを選択します。

6.  \[**新規 常設チャットの構成**\] で、次の操作を行います。
    
      - \[**名前**\] で、新しい構成設定の名前を指定します。既定では、サイト プール名が既に存在します。
    
      - \[**Default chat history**\] で、最初の要求時にチャット ルームごとに処理されるチャット メッセージ数を定義します。既定値は 30 で、これはグローバルな既定値です。管理者はカテゴリごとにチャット履歴を無効にできます。
        

        > [!IMPORTANT]
        > 常設チャット サーバーは、これらのメッセージをメモリ内にキャッシュするので、この値を増やすとキャッシュされるメッセージの数も増加します。履歴コンテンツには、検索を使用していつでもアクセスできます。既定値は、チャット ルームに接続したときに最初に表示されるメッセージの最大数を規定しているにすぎません。

    
      - \[**最大ファイル サイズ (KB)**\] で、各チャット履歴の最大ファイル サイズを選択します。既定値は 20 MB (20,000 KB) です。これは、システム内のチャット ルーム (対応する \[**分類**\] 設定でファイルのアップロードが有効化されているチャット ルーム) にアップロードできるファイルの最大サイズです。
        

        > [!IMPORTANT]
        > カスタム アプリケーションまたは以前の グループ チャット クライアント (Office Communications Server 2007 R2グループ チャット サーバーまたは Lync Server 2010、グループ チャット) はチャット ルームにファイルを投稿できるため、この設定がサーバーに対して適用されます。Lync 2013 クライアントにはファイル アップロード/ダウンロード機能がないため、純粋な Lync 2013 展開または Lync 2013 クライアントの場合は 常設チャット サーバー チャット ルームにファイルを投稿することはできません。

    
      - \[**参加者の更新制限**\] で、参加者の更新の制限値を選択します。常設チャット サーバーは、接続しているユーザーの数がこの値に達するまで、すべての参加者に名簿情報 (チャット ルームに接続しているユーザー) を送信します。既定値は 75 です。この制限値は特定のチャット ルームの参加者の最大数を示し、この値を超えると、常設チャット サーバーでは、チャット ルームに現在誰がいるかに関する名簿の更新を、接続しているクライアントに送信することを停止します。
    
      - \[**ルームの管理 URL**\] で、ルーム管理 URL を選択します。これは Web ベースのチャット ルーム管理用の URL です。チャット ルームの管理をカスタマイズする必要がなく、既定の設定をそのまま使用する場合は、このオプションを空白のままにします。
        
        チャット ルームの作成をカスタマイズして、特定のビジネス ワークフローを含める場合は、常設チャット サーバー ソフトウェア開発キット (SDK) を使用してカスタムのチャット ルーム管理ソリューションを構築し、それをホストして、その URL をここに配置します。ユーザーがチャット ルームを表示または作成するときにカスタム チャット ルーム管理ソリューションを使用するよう、この URL がクライアントに伝えられます。

7.  \[**確定**\] をクリックします。
