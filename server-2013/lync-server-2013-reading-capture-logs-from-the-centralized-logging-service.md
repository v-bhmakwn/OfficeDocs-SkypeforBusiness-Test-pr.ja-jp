﻿---
title: 集中ログサービスからキャプチャしたログの閲覧
TOCTitle: 集中ログサービスからキャプチャしたログの閲覧
ms:assetid: c86ccf61-d86f-4ebd-b8d1-984a1b73005d
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ721879(v=OCS.15)
ms:contentKeyID: 49887144
ms.date: 12/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 集中ログサービスからキャプチャしたログの閲覧

 

_**トピックの最終更新日:** 2016-12-28_

検索を実行し、報告された問題の追跡に使用できるファイルを入手することで、集中ログ サービス の真のメリットを実感できます。このファイルを読む方法はさまざまです。出力ファイルは標準のテキスト形式であり、メモ帳を使用するか、テキスト ファイルを開いて読むことができるその他の任意のプログラムを使用することができます。ファイルのサイズが比較的大きく、問題がより複雑である場合、集中ログ サービス からのログ出力の読み込みと解析を行えるように設計された Snooper.exe などのツールを使用できます。Snooper は、個別のダウンロードとして入手可能な Lync Server 2013 デバッグ ツールに含まれています。Lync Server 2013 デバッグ ツールをインストールしたら、Windows エクスプローラーのコマンドライン ビューを開くか、Lync Server 管理シェル を開いてディレクトリ (既定の場所) C:\\Program Files\\Microsoft Lync Server 2013\\Debugging Tools に移動します。コマンドラインまたは Lync Server 管理シェル を使用する場合は、Snooper.exe をダブルクリックするか、Snooper.exe と入力してから Enter キーを押します。


> [!IMPORTANT]
> このトピックの目的は、トラブルシューティングの手法を詳細に説明したり議論したりすることではありません。トラブルシューティングとそれに関連するプロセスは、複雑な問題です。トラブルシューティングの基本およびトラブルシューティング固有のワークロードの詳細については、「Microsoft Lync Server 2010 リソース キットブック」(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=211003%26clcid=0x411">http://go.microsoft.com/fwlink/?linkid=211003&amp;clcid=0x411</A>) を参照してください。プロセスと手順は、Lync Server 2013 にも適用されます。



Lync Server 2013 では、いくつかの新機能を含む更新されたバージョンの Snooper が導入されています。次のスクリーン ショットは、Office Communications Server 2007 のバージョンの Snooper を示します。

![Office Communications 2007 バージョンの Snooper](images/JJ721879.129503a8-8edd-4bb0-a68f-c43f9a548b93(OCS.15).jpg "Office Communications 2007 バージョンの Snooper")

次のスクリーン ショットは、Lync Server 2013 デバッグ ツールに含まれる新しいバージョンの Snooper を示します。

![Lync Server 2013 バージョンの Snooper](images/JJ721879.131495dd-8220-4ae4-af37-0ac5c318fd45(OCS.15).jpg "Lync Server 2013 バージョンの Snooper")

次のスクリーン ショットは、よく使用する機能を含むツールバーを示します。

![Snooper 2013 のツール バー](images/JJ721879.989249c5-a33e-4251-b8b4-411019cc12b2(OCS.15).jpg "Snooper 2013 のツール バー")

また、価値を高める最新の機能として、フロー チャート (通話フロー) 図ビューがあります。\[**メッセージ**\] タブでメッセージ フローを選択して \[**通話フロー**\] ボタンをクリックします。メッセージを読み進めると、通話フロー図が新しいデータで更新されます。

![Snooper 2013 の通話フロー図](images/JJ721879.bb8be45d-a842-48fe-86f8-380207d70bab(OCS.15).jpg "Snooper 2013 の通話フロー図")

図のビューにマウスを合わせると、メッセージに関する詳細、フローおよびメッセージの内容、サーバーの要素が表示されます。通話フローのいずれかの矢印をクリックすると、メッセージ ビューでメッセージが表示されます。

![通話フロー図のメッセージの詳細](images/JJ721879.1147d720-38a9-4bda-8361-78f27ecde3d1(OCS.15).jpg "通話フロー図のメッセージの詳細")

## Snooper でログ ファイルを開くには

1.  Snooper を使用してログ ファイルを開くためには、ログ ファイルへの読み取りアクセス権が必要です。Snooper を使用してログ ファイルにアクセスするためには、役割ベースのアクセス制御 (RBAC) のセキュリティ グループである CsAdministrator または CsServerAdministrator のメンバーであるか、これらの 2 グループのいずれかを含むカスタムの RBAC の役割のメンバーである必要があります。

2.  Lync Server デバッグ ツール (LyncDebugTools.msi) のインストール後に、Windows エクスプローラーまたはコマンド ラインを使用して、Snooper.exe が存在するディレクトリに移動します。既定では、デバッグ ツールは C:\\Program Files\\Microsoft Lync Server 2013\\Debugging Tools にあります。Snooper.exe をダブルクリックするか、実行します。

3.  Snooper を開いたら、\[**ファイル**\] を右クリックして \[**OpenFile**\] をクリックします。ログ ファイルを探し、\[**開く**\] ダイアログ ボックスでファイルを選択して \[**開く**\] をクリックします。

4.  ログ ファイルの**トレース** メッセージは、\[**トレース**\] タブに表示されます。収集されたトレースのメッセージの内容を表示するには、\[**メッセージ**\] タブをクリックします。

## 通話フロー図を表示するには

1.  Snooper を使用してログ ファイルを開くためには、ログ ファイルへの読み取りアクセス権が必要です。Snooper を使用してログ ファイルにアクセスするためには、役割ベースのアクセス制御 (RBAC) のセキュリティ グループである CsAdministrator または CsServerAdministrator のメンバーであるか、これらの 2 グループのいずれかを含むカスタムの RBAC の役割のメンバーである必要があります。

2.  ログ ファイルを開いて \[**メッセージ**\] タブをクリックし、メッセージ ビューで会話を選択するか、\[**トレース**\] タブでトレース コンポーネントを選択します。

3.  \[**通話フロー**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>通話フローに含まれていないメッセージまたはトレースをクリックした場合、図は表示されず、Snooper の最下部に &quot;This message is not eligible for callfow&quot; (このメッセージは通話フローの対象ではありません) というステータス メッセージが表示されます。別のメッセージまたはトレースを選択すると、そのメッセージまたはトレースが通話フローに含まれている場合は通話フローが表示されます。</td>
    </tr>
    </tbody>
    </table>


4.  メッセージ間またはトレース線を移動して、通話フロー図が更新されるか変化して、新しい図が表示されるかどうかに注目してください。

5.  要素にマウスをポイントすると、通話メッセージ、エンドポイント、その他のコンポーネントに関する情報を表示されます。
