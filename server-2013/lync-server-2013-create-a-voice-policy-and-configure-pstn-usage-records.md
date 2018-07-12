﻿---
title: Lync Server 2013 での音声ポリシーの作成と PSTN 使用法レコードの構成
TOCTitle: Lync Server 2013 での音声ポリシーの作成と PSTN 使用法レコードの構成
ms:assetid: e6ff27e0-e2d1-4445-840f-08f738200c20
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg399027(v=OCS.15)
ms:contentKeyID: 48273894
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での音声ポリシーの作成と PSTN 使用法レコードの構成

 

_**トピックの最終更新日:** 2012-11-01_

新しい音声ポリシーを作成するには、次の手順を実行します。 音声ポリシーを編集する場合の手順については、「[Lync Server 2013 での音声ポリシーの変更と PSTN 使用法レコードの構成](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)」を参照してください。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>各音声ポリシーには、少なくとも 1 つの公衆交換電話網 (PSTN) 使用法レコードが関連付けられている必要があります。エンタープライズ VoIP 展開の使用可能な PSTN 使用法レコードすべての一覧とそれぞれのプロパティを表示するには、「<a href="lync-server-2013-view-pstn-usage-records.md">Lync Server 2013 での PSTN 使用法レコードの表示</a>」を参照してください。</td>
</tr>
</tbody>
</table>


## 音声ポリシーを作成するには

1.  RTCUniversalServerAdmins グループのメンバーとして、あるいは CsVoiceAdministrator、CsServerAdministrator、または CsAdministrator の役割のメンバーとしてコンピューターにログオンします。詳細については、「[Lync Server 2013 でのセットアップのアクセス許可の委任](lync-server-2013-delegate-setup-permissions.md)」を参照してください。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**音声ルーティング**\] をクリックし、\[**音声ポリシー**\] をクリックします。

4.  \[**音声ポリシー**\] ページで \[**新規**\] をクリックし、新しいポリシーのスコープを選択します。
    
      - \[**サイト ポリシー**\] は、ユーザー ポリシーに割り当てられているユーザーまたはグループを除いて、サイト全体に適用されます。 ポリシー スコープとしてサイトを選択する場合は、\[**サイトの選択**\] ダイアログ ボックスでサイトを選択します。 サイトで音声ポリシーが既に作成されている場合、そのサイトは \[**サイトの選択**\] ダイアログ ボックスに表示されません。
    
      - \[**ユーザー ポリシー**\] は、指定したユーザーまたはグループに適用できます。

5.  音声ポリシーのスコープがユーザーの場合は、そのポリシーのわかりやすい名前を \[**名前**\] フィールドに入力します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>音声ポリシー スコープがサイトの場合は、[<strong>新しい音声ポリシー</strong>] の [<strong>名前</strong>] フィールドにサイト名が事前に入力されており、変更することはできません。</td>
    </tr>
    </tbody>
    </table>


6.  (オプション) その音声ポリシーについての追加説明を入力します。

7.  次のチェック ボックスをオンまたはオフにして、この音声ポリシーの各 \[**通話機能**\] を有効または無効にします。
    
      - **ボイス メール エスケープ**は、同時呼び出しが構成されている場合に、電話が電源オフ、電池切れ、または圏外になっているときに、通話がユーザーの携帯電話のボイス メール システムにすぐにルーティングされることを防ぎます。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>この機能は、Lync Server 管理シェルを通じてのみ構成できます。</td>
        </tr>
        </tbody>
        </table>
    
      - **着信転送**を使用すると、着信を他の電話機またはクライアント デバイスに転送できます。Lync Server 2013 には、着信転送に関する構成オプションが極めて幅広く用意されています。たとえば、着信が外部で PSTN に転送されることを組織が許可しない方針の場合、管理者は特殊な音声ポリシーを適用して、この制限を展開することができます。既定では有効です。
    
      - **委任** では、代わりに通話を送受信する他のユーザーを指定できます。Lync Server 2013 では、代理人は同時呼び出しを構成できます。同時呼び出しを使用すると、マネージャーに対して着信があった場合に、代理人によって設定されたターゲット ユーザー全員が同時に呼び出されます。この機能を使用すると、代理人はマネージャーに対する直接の着信により柔軟に対応できます。既定では有効です。
    
      - \[**通話の転送**\] では、他のユーザーに通話を転送できます。 既定では有効です。
    
      - \[**コール パーク**\] では、通話を保留 (パーク) し、別の電話機やクライアントで受けることができます。 既定では無効です。
    
      - **同時呼び出し**では、追加の電話機 (携帯電話など) や他のエンドポイント デバイスで、着信の呼び出し音を鳴らすことができます。Lync Server 2013 には、同時呼び出しに関する構成オプションが極めて幅広く用意されています。既定では有効です。
    
      - \[**チーム呼び出し**\] では、定義したチームのユーザーがチームの他のメンバーの呼び出しに応答できます。 既定では有効です。
    
      - **PSTN 再ルート**では、WAN が混雑していたり利用できない場合に、このポリシーを割り当てられているユーザーが他のエンタープライズ ユーザーに掛けた通話を、公衆交換電話網 (PSTN) で再ルートできます。既定では有効です。
    
      - \[**帯域幅ポリシーの上書き**\] により管理者は、特定のユーザーに関する通話受付管理ポリシーによる決定を上書きできます。 既定では無効です。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>ポリシーが上書きされるのはユーザーに着信する通話のみです。ユーザーが発信する通話は上書きされません。セッションの確立後、使用帯域幅は正確に記録されます。この設定は慎重に使用し、適切な通話受付管理の決定に対しては使用しないでください。</td>
        </tr>
        </tbody>
        </table>
    
      - **悪意のある呼び出しのトレース**では、ユーザーがクライアントの UI を使用して、悪意のある呼び出し (爆弾脅迫など) を報告できます。報告されると、通話詳細記録 (CDR) 内のその呼び出しにフラグが付けられます。既定では無効です。

8.  この音声ポリシーの PSTN 使用法レコードの関連付けと構成を行うには、次のいずれかを実行します。
    
      - エンタープライズ VoIP 展開で利用できるすべての PSTN 使用法レコードの一覧から、1 つ以上のレコードを選択するには、\[**選択**\] をクリックします。この音声ポリシーに関連付けるレコードを選択状態にし、\[**OK**\] をクリックします。
    
      - PSTN 使用法レコードをこの音声ポリシーから削除するには、レコードを選択状態にして \[**削除**\] をクリックします。
    
      - 新しい PSTN 使用法レコードを定義してこの音声ポリシーに関連付けるには、次の操作を実行します。
        
        1.  \[**新規**\] をクリックします。
        
        2.  \[**名前**\] フィールドに、レコードを説明する一意の名前を入力します。 たとえば、Redmond で勤務しているフルタイム従業員用に **Redmond** という名前の PSTN 使用法レコードを作成し、パートタイム従業員用に **RedmondTemps** という別の名前の PSTN 使用法レコードを作成する場合があります。
            
            <table>
            <thead>
            <tr class="header">
            <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
            </tr>
            </thead>
            <tbody>
            <tr class="odd">
            <td>PSTN 使用法レコードの名前は、エンタープライズ VoIP 展開内で一意である必要があります。 レコードの保存後、[<strong>名前</strong>] フィールドを編集することはできません。</td>
            </tr>
            </tbody>
            </table>
        
        3.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
            
              - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から、1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
            
              - PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
            
              - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
            
              - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
        
        4.  \[**OK**\] をクリックします。
    
      - この音声ポリシーに既に関連付けられている PSTN 使用法レコードを編集するには、次の操作を実行します。
        
        1.  編集する PSTN 使用法レコードを選択状態にし、\[**詳細の表示**\] をクリックします。
        
        2.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
            
              - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から、1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
            
              - この PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
            
              - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
            
              - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
        
        3.  \[ **OK** \] をクリックします。

9.  最適なパフォーマンスを得るために、PSTN 使用法レコードを並べ替えます。 一覧内でのレコードの位置を変更するには、レコードの名前を選択状態にして、上矢印または下矢印をクリックします。
    

    > [!IMPORTANT]
    > 音声ポリシー内の一覧における PSTN 使用法レコードの順序は重要です。Lync Server は、上から下の順に一覧内をスキャンします。 この一覧は、使用頻度の高い順番に並べておくことを推奨します。たとえば、 "レドモンド市内"、"レドモンド長距離"、"レドモンド国際"、"レドモンド バックアップ" の順に並べます。



10. この音声ポリシーの着信転送および同時呼び出しの PSTN 使用法レコードの関連付けと構成を行うには、次のいずれかを実行します。
    
      - この音声ポリシーのように着信転送および同時呼び出しに対して同じ PSTN 使用法レコードを使用するには、ドロップダウン メニューから \[**呼び出し PSTN 使用法を使用したルーティング**\] オプションを選択します。
    
      - 内部 Lync ユーザーのみに着信転送および同時呼び出しを許可するには、ドロップダウン メニューから \[**内部 Lync ユーザーのみへのルーティン**\] オプションを選択します。着信は、外部 PSTN 番号に転送されません。
    
      - この音声ポリシーでの使用とは異なり、着信転送および同時呼び出しに対して異なる PSTN 使用法レコードを指定するには、ドロップダウン メニューから \[**カスタムの PSTN 使用法を使用したルーティング**\] オプションを選択します。このオプションでは、既存の PSTN 使用法レコードを選択するか、または着信転送および同時呼び出し用の特別な新しい PSTN 使用法レコードを作成するコントロールが表示されます。
        
          - 着信転送および同時呼び出しの PSTN 使用法レコードの一覧から、1 つ以上のレコードを選択するには、\[**選択**\] をクリックします。この着信転送および同時呼び出しポリシーに関連付けるレコードを選択状態にし、\[**OK**\] をクリックします。
        
          - PSTN 使用法レコードをこの着信転送および同時呼び出しポリシーから削除するには、レコードを選択状態にして \[**削除**\] をクリックします。
        
          - 新しい PSTN 使用法レコードを定義してこの着信転送および同時呼び出しポリシーに関連付けるには、次の操作を実行します。
            
            1.  \[**新規**\] をクリックします。
            
            2.  \[**名前**\] フィールドに、レコードを説明する一意の名前を入力します。
                
                <table>
                <thead>
                <tr class="header">
                <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
                </tr>
                </thead>
                <tbody>
                <tr class="odd">
                <td>PSTN 使用法レコードの名前は、エンタープライズ VoIP 展開内で一意である必要があります。 レコードの保存後、 [<strong>名前]</strong> フィールドを編集することはできません。</td>
                </tr>
                </tbody>
                </table>
            
            3.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
                
                  - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から、1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
                
                  - PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
                
                  - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
                
                  - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
            
            4.  \[**OK**\] をクリックします。
        
          - この音声ポリシーに既に関連付けられている PSTN 使用法レコードを編集するには、次の操作を実行します。
            
            1.  編集する PSTN 使用法レコードを選択状態にし、\[**詳細の表示**\] をクリックします。
            
            2.  次のいずれかの方法を使用して、この PSTN 使用法レコードのルートの関連付けと構成を行います。
                
                  - エンタープライズ VoIP 展開で利用できるすべてのルートの一覧から、1 つ以上のルートを選択するには、\[**選択**\] をクリックし、この PSTN 使用法レコードに関連付けるルートを選択状態にして、\[**OK**\] をクリックします。
                
                  - この PSTN 使用法レコードからルートを削除するには、ルートを選択状態にして \[**削除**\] をクリックします。
                
                  - 新しいルートを定義してこの PSTN 使用法レコードに関連付けるには、\[**新規**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)」を参照してください。
                
                  - この PSTN 使用法レコードに既に関連付けられているルートを編集するには、ルートを選択状態にして \[**詳細の表示**\] をクリックします。詳細については、「[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)」を参照してください。
            
            3.  \[**OK**\] をクリックします。

11. (オプション) 音声ポリシーをテストする番号を入力して、\[**実行**\] をクリックします。 テスト結果は、\[**テストする変換後の番号**\] の下に表示されます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>まだテストに成功していない音声ポリシーを保存して、後で再構成することができます。詳細については、「<a href="lync-server-2013-test-voice-routing.md">Lync Server 2013 での音声ルーティングのテスト</a>」を参照してください。</td>
    </tr>
    </tbody>
    </table>


12. \[ **OK** \] をクリックします。

13. \[**音声ポリシー**\] ページで \[**確定**\] をクリックし、\[**すべて確定**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>音声ポリシーを作成または変更したときは常に、[<strong>すべて確定</strong>] コマンドを実行して、構成の変更を公開する必要があります。詳細については、「操作」のドキュメントの「<a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Lync Server 2013 での音声ルーティング構成に対する保留中の変更の公開</a>」を参照してください。</td>
    </tr>
    </tbody>
    </table>


14. (オプション) ボイスメール エスケープは、着信がユーザーの携帯電話のボイス メールによって即座に応答されたことを検出し、携帯電話のボイス メールへの通話を切断します。これにより、ユーザーの他のエンドポイントで着信の呼び出しが続けられるので、ユーザーは着信に応答できるようになります。ボイス メール ポリシーの構成方法に関する詳細については、「[Lync Server 2013 でのボイス メール エスケープの構成](lync-server-2013-configuring-voice-mail-escape.md)」を参照してください。

## 関連項目

#### タスク

[Lync Server 2013 での音声ポリシーの変更と PSTN 使用法レコードの構成](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Lync Server 2013 での PSTN 使用法レコードの表示](lync-server-2013-view-pstn-usage-records.md)  
[Lync Server 2013 でのボイス ルートの作成](lync-server-2013-create-a-voice-route.md)  
[Lync Server 2013 でのボイス ルートの変更](lync-server-2013-modify-a-voice-route.md)  
[Lync Server 2013 での音声ルーティング構成に対する保留中の変更の公開](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  
[Lync Server 2013 でのボイス メール エスケープの構成](lync-server-2013-configuring-voice-mail-escape.md)  

#### その他のリソース

[Lync Server 2013 での音声ルーティングのテスト](lync-server-2013-test-voice-routing.md)
