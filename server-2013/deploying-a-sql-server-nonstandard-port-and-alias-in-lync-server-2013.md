﻿---
title: Lync Server 2013 で SQL Server の非標準ポートおよびエイリアスを展開する
TOCTitle: Lync Server 2013 で SQL Server の非標準ポートおよびエイリアスを展開する
ms:assetid: 2da92c1f-250e-407a-8651-fb2aec76aeb0
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn776290(v=OCS.15)
ms:contentKeyID: 62634461
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 で SQL Server の非標準ポートおよびエイリアスを展開する

 

_**トピックの最終更新日:** 2016-12-08_

Microsoft Lync Server 2013 では、SQL Server の非標準ポートおよびエイリアスの使用をサポートしています。SQL Server の非標準ポートおよびエイリアスを使用すると、セキュリティが向上し、Lync 展開のより柔軟な環境を作成できます。これらの手順は、Lync Server 2013 環境を適切にセキュリティで保護するための 1 つの手順にすぎません。Lync Server 2013 実装の攻撃対象を少なくするには、追加の手順を実行する必要があります。

次の記事では、Lync Server 2013 で SQL Server の非標準ポートおよびエイリアスを設定するために必要な手順について説明します。

## Lync Server 2013 に SQL Server の非標準ポートおよびエイリアスを展開する

Lync Server 2013トポロジ ビルダーでは、Lync Server 2013 を構成するときに実際の SQL Server FQDN の代わりに SQL Server エイリアスを完全修飾ドメイン名 (FQDN) として使用できます。これにより、実際の SQL Server FQDN を悪意のある攻撃者から隠すことができます。また、非標準のポートを使用すると、次の図に示すように、標準ポート 1433 でデータベースへの攻撃を試みるあらゆる攻撃者から実際のポートを隠すことができます。

![ハッカーには、攻撃するポート番号がわかりません。](images/Dn776290.2f3923e0-2bdc-416b-a66b-bf56599eb14e(OCS.15).jpg "ハッカーには、攻撃するポート番号がわかりません。")

Lync Server 2013 で SQL Server との通信に使用されているポートを攻撃者が特定するには、すべてのポートをスキャンしてポート情報を取得する必要があります。攻撃者によるポート スキャンが行われると、セキュリティがその命令を検出して停止できる可能性が高くなります。非標準ポートを使用してセキュリティを強化できるだけでなく、SQL Server エイリアスを使用して柔軟に展開できます。これで、SQL Server 名の変更が必要な場合に構成の変更を減らすことができます。

>[!NOTE]
> SQL Server には、2 つのフォールト トレランスの方法があります (フェールオーバー クラスターと ミラーリング)。SQL Server の両方のフォールト トレランスの方法は、Lync Server 2013 で SQL Server の非標準ポートおよびエイリアスを使用してサポートされます。


トポロジ ビルダー内から SQL Server データベース接続を構成するときや、Install-CsDatabase コマンドレットを使用するときは、SQL Server の非標準ポート番号を明示的に定義して SQL インスタンスに関連付けることができません。非標準ポートを設定するには、SQL Server および Windows Server ユーティリティを使用する必要があります。

Lync Server 2013 で使用する SQL Server の非標準ポートおよびエイリアスを設定するには、4 つの主要な手順を実行する必要があります。これらの手順を次に示します。

  - Lync Server 2013 に最新の更新プログラムが適用されていることを確認する。

  - SQL Server の非標準ポートおよびエイリアスを設定する。

  - トポロジ ビルダーを使用して、SQL Server のエイリアスを含む Lync Server 2013 を構成する。

  - トポロジを公開して、データベースを検証する。

## Lync Server 2013 に最新の更新プログラムが適用されていることを確認する

Lync Server 2013 を常に最新状態に保つことが重要です。最新の更新プログラムの有無を調べたり、更新プログラムの適用方法を確認したりするには、「[Lync Server 2013 の更新](http://support.microsoft.com/kb/2809243)」を参照してください。

## SQL Server の非標準ポートおよびエイリアスを設定する

SQL Server の非標準ポートとエイリアスを Lync Server 2013 のトポロジ ビルダーから参照するには、事前にデータベース インスタンスにそれらを設定する必要があります。SQL Server の非標準ポートとエイリアスを設定するには、3 つの主要な手順を実行する必要があります。これらの手順を次に示します。

  - 既定の TCP/IP プロトコル値を変更する。

  - SQL Server エイリアスを作成および構成する。

  - ドメイン ネーム システム (DNS) の正規名 (CNAME) リソース レコードを作成する。

**既定の TCP/IP プロトコル値を変更する**

1.  次の図に示すように、\[**スタート**\] を選択し、\[**SQL Server 構成マネージャー**\] を選択します。
    
    ![SQL Server Management Studio アイコン](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "SQL Server Management Studio アイコン")

2.  ナビゲーション ウィンドウで、**SQL Server インスタンス**を選択して展開します。\[**SQL Server ネットワークの構成**\] を選択して展開し、次の図に示すように、\[**\<インスタンス名\> のプロトコル**\] を選択します。
    
    ![TCP/IP プロパティへの移動。](images/Dn776290.3d7a964c-f17e-47fd-8f0c-535453da7fad(OCS.15).jpg "TCP/IP プロパティへの移動。")

3.  右側のウィンドウで、\[**TCP/IP**\] を右クリックして、\[**プロパティ**\] を選択します。\[TCP/IP のプロパティ\] ダイアログ ボックスが表示されます。

4.  \[**IP アドレス**\] タブを選択します。\[IP アドレス\] タブには、サーバー上のすべてのアクティブな IP アドレスが表示されます。これらの IP アドレスは、次の図に示すように、IP1、IP2 という形式で IPAll まで表示されます。
    
    ![TCP/IP プロパティを開く。](images/Dn776290.ed2fd70d-1836-4ebf-80fe-09191d96585e(OCS.15).jpg "TCP/IP プロパティを開く。")

5.  すべての IP アドレスについて、\[**TCP 動的ポート**\] ボックスの値を消去します。このフィールドに値 0 が含まれる場合、SQL Server が動的ポートでリッスンしていることを示します。これらのフィールドが消去されていて、0 が含まれていないことを確認します。

6.  次の図に示すように、Lync Server がデータベースに接続するために使用する IP アドレスに対して、\[**有効**\] が \[**はい**\] に設定されていることを確認します。
    
    ![適切な IP に \[Yes\] を設定して有効にする。](images/Dn776290.7f818b91-0793-4594-8932-90447270fad9(OCS.15).jpg "適切な IP に [Yes] を設定して有効にする。")

7.  次の図に示すように、ダイアログの下部の \[**IPAll**\] セクションの \[**TCP ポート**\] ボックスに、目的のポートを入力します。この例ではポート 50062 を使用していますが、49152 ～ 65535 の任意のポートを使用できます。これらは、動的に割り当てられてプライベートに使用されるポートです。これにより、Lync Server 2013 展開で使用されている他のポートとの競合を回避できます。
    
    ![IPAll セクションでポートを設定する。](images/Dn776290.b5af53e2-7961-4664-b586-3ca8f3a17f06(OCS.15).jpg "IPAll セクションでポートを設定する。")

8.  \[**OK**\] を選択して \[TCP/IP のプロパティ\] ダイアログを閉じます。

9.  SQL Server インスタンスを再起動するために、SQL Server 構成マネージャーの左側のウィンドウで \[**SQL Server のサービス**\] を選択します。次に、次の図に示すように、右側のウィンドウで \[**SQL Server \<インスタンス名\>**\] を右クリックして、\[**再起動**\] を選択します。
    
    ![インスタンス用の SQL Server サービスをリセットする。](images/Dn776290.a965c8cf-f769-4b52-bb38-c48a438cf491(OCS.15).jpg "インスタンス用の SQL Server サービスをリセットする。")


> [!IMPORTANT]
> 新しい SQL Server ポートに対応するようにファイアウォール設定が更新されていることを確認します。



**SQL Server エイリアスを作成および構成する**

1.  次の図に示すように、\[**スタート**\] を選択し、\[**SQL Server 構成マネージャー**\] を選択します。
    
    ![SQL Server Management Studio アイコン](images/Dn776290.6e811f27-cea9-4437-b44c-55bff013150f(OCS.15).png "SQL Server Management Studio アイコン")

2.  左側のウィンドウで、**SQL Server インスタンス**を選択して展開します。次の図に示すように、\[**SQL Native Client \<バージョン\> の構成**\] を選択して展開し、\[**エイリアス**\] を選択します。
    
    ![SQL Server Configuration Manager のエイリアス。](images/Dn776290.95341826-55d7-425f-ae19-d47d6668c5d8(OCS.15).jpg "SQL Server Configuration Manager のエイリアス。")

3.  \[**エイリアス**\] を右クリックして、\[**新しいエイリアス**\] を選択します。

4.  次の図に示すように、**エイリアス名**、**ポート番号**、**プロトコル**、**サーバー**を入力します。
    
    ![新しいエイリアスの作成](images/Dn776290.03653588-aecf-4fdd-b58a-95f5b372d478(OCS.15).jpg "新しいエイリアスの作成")
    

    > [!TIP]
    > 前の手順で使用したのと同じ非標準ポートを入力してください (これが、SQL Server がリッスンするポートになります)。構成したエイリアスによって不適切な SQL Server FQDN またはインスタンスに接続される場合は、関連付けられているネットワーク プロトコルをいったん無効にしてから再び有効にしてください。これにより、キャッシュされた接続情報がクリアされ、クライアントが適切に接続できるようになります。



**DNS CNAME リソース レコードを作成する**

1.  DNS を管理しているコンピューターにサインインします。

2.  次の図に示すように、\[**スタート**\] を選択し、\[**サーバー マネージャー**\] を選択します。
    
    ![サーバー マネージャーを開く](images/Dn776290.3e4bd8ad-2a65-4a05-af40-c8dd3583bc8f(OCS.15).jpg "サーバー マネージャーを開く")

3.  次の図に示すように、\[**ツール**\] ボックスの一覧の \[**DNS**\] を選択します。
    
    ![サーバー マネージャーから DNS を開く。](images/Dn776290.415e1da1-7c9a-4a4e-a896-ca34a76aaeff(OCS.15).jpg "サーバー マネージャーから DNS を開く。")

4.  左側のウィンドウで、サーバー名ノード、\[前方参照ゾーン\] ノードの順に展開し、目的のドメインを選択します。

5.  次の図に示すように、ドメインを右クリックして、\[**新しいエイリアス (CNAME)**\] を選択します。
    
    ![新しいエイリアス CNAME を作成するためのオプションの選択](images/Dn776290.abe66cca-b53c-427a-9094-1a59dc6840ca(OCS.15).jpg "新しいエイリアス CNAME を作成するためのオプションの選択")

6.  次の図に示すように、**エイリアス名**と **SQL Server の FQDN** を入力します。
    
    ![新しいエイリアス CNAME ダイアログへの入力。](images/Dn776290.dd0ebd2d-3407-4459-8bd9-2b389a7bc440(OCS.15).jpg "新しいエイリアス CNAME ダイアログへの入力。")

7.  \[**OK**\] を選択して CNAME を保存した後、これを DNS マネージャーで表示します。

## データベース接続を検証する

接続が正常に機能しているかどうかを調べる方法はたくさんあります。ここでは、エイリアスを使用して SQL Server データベースが指定されたポートでリッスンしていることを確認します。**netstat** コマンドと **telnet** コマンドを使用すると、これを簡単に確認できます。

>[!NOTE]
> Telnet クライアントは Windows Server に付属する機能ですが、自分でインストールする必要があります。Windows Server 機能をインストールするには、サーバー マネージャーを開き、[管理] メニューの [役割と機能の追加] を選択します。


**netstat と telnet を使用してデータベース接続を検証する**

1.  \[**スタート**\] を選択し、「**cmd**」と入力してコマンド プロンプトを開きます。

2.  次の図に示すように、「**netstat -a -f**」と入力して、SQL Server が適切なポートで動作していることを確認します。
    
    ![netstat を使用したポートの確認。](images/Dn776290.4ff3a1b2-c5eb-4496-8be7-374c351fa027(OCS.15).jpg "netstat を使用したポートの確認。")

3.  「**telnet \<エイリアス名\> \<ポート番号\>**」と入力して、SQL Server インスタンスへの接続を確認します。接続が正常な場合は、telnet 接続が成功し、エラーは表示されません。これは、SQL Server インスタンスが適切なエイリアスを使用して適切なポートでリッスンしていることを示します。SQL Server データベースへの接続に問題がある場合は、接続できないことを示すエラーが telnet から返されます。データベース サーバーでのデータベース接続の確認が終わったら、(ネットワーク経由で) Lync Server から同じ操作を行って、アクセスをブロックしているファイアウォールがないことを確認します。

## 終わりに

SQL Server エイリアスを構成したら、これを使用してトポロジ ビルダー ツールで Lync Server 2013 トポロジを作成できます。トポロジの詳細については、「[Lync Server 2013 でのトポロジの定義と構成](lync-server-2013-defining-and-configuring-the-topology.md)」を参照してください。

## 関連項目

#### 概念

[Microsoft Lync Server 2013](microsoft-lync-server-2013.md)  

#### その他のリソース

[Lync Server 2013 のセキュリティの計画](lync-server-2013-planning-for-security.md)  
[Lync Server 2013 でのトポロジの定義と構成](lync-server-2013-defining-and-configuring-the-topology.md)  
[Lync Server 2013 の展開](lync-server-2013-deploying-lync-server.md)
