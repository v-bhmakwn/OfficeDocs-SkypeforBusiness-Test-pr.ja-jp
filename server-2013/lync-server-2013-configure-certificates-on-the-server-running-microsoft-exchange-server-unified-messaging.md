﻿---
title: Microsoft Exchange Server ユニファイド メッセージングを実行しているサーバーでの証明書の構成
TOCTitle: Microsoft Exchange Server ユニファイド メッセージングを実行しているサーバーでの証明書の構成
ms:assetid: 74c883b4-cef6-41a9-b2eb-7212be32fea4
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398564(v=OCS.15)
ms:contentKeyID: 48272531
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Exchange Server ユニファイド メッセージングを実行しているサーバーでの証明書の構成

 

_**トピックの最終更新日:** 2016-12-08_

「計画」のドキュメントの「[Lync Server 2013 での Exchange ユニファイド メッセージング統合の計画](lync-server-2013-planning-for-exchange-unified-messaging-integration.md)」の手順どおりに Exchange ユニファイド メッセージング (UM) を展開してあり、Exchange UM の機能を組織内のエンタープライズ VoIP ユーザーに提供する場合は、以下の手順を使用して、Exchange UM を実行するサーバーで証明書を構成します。


> [!IMPORTANT]
> 内部証明書については、Lync Server 2013 を実行しているサーバーと Microsoft Exchange を実行しているサーバーの両方に、相互に信頼された、信頼されたルート機関の証明書が存在する必要があります。各サーバーの信頼されたルート機関の証明書ストアに証明機関 (CA) のルート証明書が登録されている限り、それぞれの証明機関は同じものであっても別のものであっても構いません。



Lync Server 2013 に接続するためには、Exchange Server がサーバー証明書を使用して構成されている必要があります。

1.  Exchange Server の CA 証明書をダウンロードします。

2.  Exchange Server の CA 証明書をインストールします。

3.  CA が、Exchange Server の信頼されたルート証明機関一覧にあることを確認します。

4.  Exchange Server の証明書要求を作成し、証明書をインストールします。

5.  Exchange Server の証明書を割り当てます。

## CA 証明書をダウンロードするには

1.  Exchange UM を実行するサーバーで、\[**スタート**\]、\[**ファイル名を指定して実行**\] の順にクリックして、「**http://\<発行を行う CA サーバーの名前\>/certsrv**」と入力し、\[**OK**\] をクリックします。

2.  \[**タスクの選択**\] の \[**CA 証明書、証明書チェーン、または CRL のダウンロード**\] をクリックします。

3.  \[**CA 証明書、証明書チェーン、または CRL のダウンロード**\] で \[**Base 64 へのエンコード方式**\] をクリックし、\[**CA 証明書のダウンロード**\] をクリックします。
    
    > [!NOTE]
    > このステップで Distinguished Encoding Rules (DER) エンコードを指定することもできます。DER エンコードを選択する場合は、この手順の次のステップと「<strong>CA 証明書をインストールするには</strong>」のステップ 10 のファイル タイプが .cer ではなく, .p7b になります。


4.  \[**ファイルのダウンロード**\] ダイアログ ボックスで \[**保存**\] をクリックし、ファイルをサーバー上のハード ディスクに保存します。(このファイルの拡張子は、前のステップで選択したエンコードに応じて, .cer または .p7b となります。)

## CA 証明書をインストールするには

1.  Exchange UM を実行するサーバーで、\[**スタート**\]、\[**ファイル名を指定して実行**\] の順にクリックして、\[**名前**\] ボックスに「**mmc**」と入力し、\[**OK**\] をクリックして、Microsoft 管理コンソール (MMC) を開きます。

2.  \[**ファイル**\] メニューの \[**スナップインの追加と削除**\] をクリックし、\[**追加**\] をクリックします。

3.  \[**スタンドアロン スナップインの追加**\] ボックスで、\[**証明書**\] をクリックし、\[**追加**\] をクリックします。

4.  \[**証明書スナップイン**\] ダイアログ ボックスの \[**コンピューター アカウント**\] をクリックし、\[**次へ**\] をクリックします。

5.  \[**コンピューターの選択**\] ダイアログ ボックスで、\[**ローカル コンピューター: (このコンソールを実行しているコンピューター)**\] チェック ボックスがオンになっていることを確認して、\[**完了**\] をクリックします。

6.  \[**閉じる**\] をクリックし、\[**OK**\] をクリックします。

7.  コンソール ツリーで、\[**証明書 (ローカル コンピューター)**\] を展開し、\[**信頼されたルート証明機関**\] を展開して \[**証明書**\] をクリックします。

8.  \[**証明書**\] を右クリックし、\[**すべてのタスク**\] をクリックして \[**インポート**\] をクリックします。

9.  \[**次へ**\] をクリックします。

10. \[**参照**\] をクリックしてファイルを特定し、\[**次へ**\] をクリックします。(このファイルの拡張子は、「**CA 証明書をダウンロードするには**」のステップ 3 で選択したエンコードに応じて, .cer または .p7b となります。)

11. \[**証明書をすべて次のストアに配置する\]** をクリックします。

12. \[**参照**\] をクリックし、\[**信頼されたルート証明機関**\] をクリックします。

13. \[**次へ**\] をクリックし、設定を確認して、\[**完了**\] をクリックします。

## CA が信頼されたルート証明機関の一覧にあることを確認するには

1.  Exchange UM を実行するサーバーの MMC で、\[**証明書 (ローカル コンピューター)**\] を展開し、\[**信頼されたルート証明機関**\] を展開して \[**証明書**\] をクリックします。

2.  詳細ウィンドウで、CA が、信頼されたルート証明機関の一覧にあることを確認します。

## Lync Server に Exchange Server 2013 UM を構成するには

1.  詳細については、Exchange Server のドキュメント ([http://go.microsoft.com/fwlink/?linkid=265372\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=265372%26clcid=0x411)) の「Integrate Exchange 2013 UM with Lync Server」を参照してください。

## 証明書要求を作成して、証明書を Exchange Server 2007 (SP1) にインストールするには

1.  Exchange UM を実行するサーバーで、\[**スタート**\]、\[**ファイル名を指定して実行**\] の順にクリックして、「**http://\<***発行を行う CA サーバーの名前***\>/certsrv**」と入力し、\[**OK**\] をクリックします。

2.  \[**タスクの選択**\] で \[**証明書の要求**\] をクリックします。

3.  \[**証明書の要求**\] で \[**証明書の要求の詳細設定**\] をクリックします。

4.  \[**証明書の要求の詳細設定**\] で \[**この CA への要求を作成し送信する**\] をクリックします。

5.  \[**証明書の要求の詳細設定**\] で、サーバー認証用に構成された \[**Web サーバー**\] 証明書テンプレートまたは別のサーバー証明書テンプレートを選択します。

6.  \[**オフライン テンプレート用の識別情報**\] の \[**名前**\] ボックスに、Exchange Server の完全修飾ドメイン名 (FQDN) を入力します。
    
    > [!NOTE]
    > 通信を可能にするには、Exchange Server の FQDN を入力する必要があります。


7.  \[**キーのオプション**\] で \[**ローカル コンピューターの証明書ストアに証明書を格納する**\] チェック ボックスをオンにします。

8.  Web ページの下部にある \[**送信**\] をクリックします。

9.  確認のダイアログ ボックスで、\[**はい**\] をクリックします。

10. \[証明書は発行されました\] ページの \[**証明書は発行されました**\] で \[**この証明書のインストール**\] をクリックします。

11. 確認のダイアログ ボックスで、\[**はい**\] をクリックします。

12. "新しい証明書は正しくインストールされました" というメッセージが表示されることを確認します。

## Exchange Server 2010 で証明書を作成するには

1.  Exchange UM を実行するサーバーに、適切なユーザー権限でログオンします。詳細については、「クライアント アクセス許可」([http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x411)) を参照してください。

2.  証明書を作成するには、以下の手順を参照してください。
    
    1.  「新しい Exchange 証明書の作成」([http://go.microsoft.com/fwlink/?linkid=195494\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=195494%26clcid=0x411))
    
    2.  「Exchange 証明書のインポート」([http://go.microsoft.com/fwlink/?linkid=195496\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=195496%26clcid=0x411))
    
    > [!NOTE]
    > 通信を可能にするには、証明書の [<strong>サブジェクト名</strong>] に、Exchange Server の FQDN を入力する必要があります。


## Exchange Server 2007 (SP1) に証明書を割り当てるには

1.  Exchange UM を実行するサーバーで MMC を開きます。

2.  コンソール ツリーで \[**個人**\] を展開し、\[**証明書**\] をクリックします。

3.  詳細ウィンドウに個人の証明書が表示されていることを確認します。

4.  証明書をダブルクリックして詳細を読み、証明書が有効であることを確認します。
    
    > [!NOTE]
    > 証明書に有効と表示されるまでに数分かかることがあります。


5.  Microsoft Exchange ユニファイド メッセージング サービスを再開します。
    
    > [!NOTE]
    > Exchange Server 2007 SP1 ユニファイド メッセージングを実行しているサーバーで、正しい証明書が自動的に取得されます。


6.  イベント ビューアを開き、イベント ID 1112 を探します。このイベントは、Exchange Server 2007 SP1 ユニファイド メッセージングを実行しているサーバーが取得した証明書を示します。

## Exchange Server 2010 に証明書を割り当てるには

1.  Exchange UM を実行するサーバーに、適切なユーザー権限でログオンします。詳細については、「クライアント アクセス許可」([http://go.microsoft.com/fwlink/?linkid=195499\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=195499%26clcid=0x411)) を参照してください。

2.  証明書を割り当てる手順については、「サービスの証明書への割り当て」([http://go.microsoft.com/fwlink/?linkid=195497\&clcid=0x411](http://go.microsoft.com/fwlink/?linkid=195497%26clcid=0x411)) を参照してください。

