﻿---
title: 'Lync Server 2013: ユーザー モデルを使用した処理能力の計画'
TOCTitle: ユーザー モデルを使用した処理能力の計画
ms:assetid: 902ab23e-94d6-482a-9d6e-c0b28dc3e03d
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg615015(v=OCS.15)
ms:contentKeyID: 49887051
ms.date: 07/20/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ユーザー モデルを使用した Lync Server 2013 の処理能力の計画

 

_**トピックの最終更新日:** 2016-12-08_

このセクションでは、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」に説明されている使用法に従って、そのサイトに存在するユーザー数に対して、1 つのサイトに何台のサーバーが必要かについてのガイダンスを提供します。

## テスト済みのハードウェア プラットフォーム

このセクションで説明しているパフォーマンスの結果と展開の推奨事項はすべて、次の表に示すハードウェアを実行しているサーバーで実施したパフォーマンス テストに基づいています。同様のハードウェアを使用することをお勧めします。パフォーマンスが劣るハードウェアを使用する場合は、機能上の問題が発生したり、パフォーマンスが低下したりする可能性があります。これらのハードウェアの推奨事項のレベルは、以前のバージョンの Lync Server の推奨事項よりも高くなっています。

### パフォーマンス テストで使用するハードウェア

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ハードウェア コンポーネント</th>
<th>推奨値</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64 ビット デュアル プロセッサ、6 コア、2.26 GHz 以上</p>
<p>Intel Itanium プロセッサは、 Lync Server のサーバーの役割用としてはサポートされていません。</p></td>
</tr>
<tr class="even">
<td><p>メモリ</p></td>
<td><p>32 ギガバイト (GB)</p></td>
</tr>
<tr class="odd">
<td><p>ディスク</p></td>
<td><ul>
<li><p>10,000 RPM のハード ディスク ドライブで 72 GB 以上の空きディスク領域があるものを 8 台以上。</p>
<p>ディスクのうち 2 台で RAID 1 を使用し、6 台で RAID 10 を使用する必要があります。</p>
<p>- または -</p></li>
<li><p>10,000 RPM の機械的ディスク ドライブ 8 台と同等のパフォーマンスを持つソリッド ステート ドライブ (SSD)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>ネットワーク</p></td>
<td><ul>
<li><p>1 Gbps 以上のデュアルポート ネットワーク アダプター 1 つ (2 つを推奨。その場合は 1 つの MAC アドレスと 1 つの IP アドレスのチーミングが必要)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## 結果の概要

次の表は、これらの推奨事項を要約したものです。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>サーバーの役割</th>
<th>サポートされる最大ユーザー数</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>12 台の フロント エンド サーバーと 1 台の バック エンド サーバーまたはミラー化された バック エンド サーバーのペアを含む フロント エンド プール</p></td>
<td><p>エンドポイントの合計 152,000 に対し、同時にログインする 80,000 の一意ユーザー、および非モバイル インスタンスを表す 50% の複数の MPOP (Multiple Point of Presence)、モビリティが有効な 40% のユーザー。</p></td>
</tr>
<tr class="even">
<td><p>音声ビデオ会議</p></td>
<td><p>フロント エンド プールが提供する音声ビデオ会議サービスは、プールの会議をサポートします。サポートされる最大会議規模は 250 ユーザーで、このように大きな会議は一度に 1 つだけ開催されると想定されます。</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>また、大きな会議をホストするための 2 台の フロント エンド サーバーを含む個別の フロント エンド プールを展開することによって、250 ～ 1000 ユーザーの大きな会議をサポートできます。詳細については、「<a href="lync-server-2013-supporting-large-meetings.md">Lync Server 2013 を使用した大規模会議のサポート</a>」を参照してください。</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p>1 台の エッジ サーバー</p></td>
<td><p>12,000 同時リモート ユーザー</p></td>
</tr>
<tr class="even">
<td><p>1 台のディレクター</p></td>
<td><p>12,000 同時リモート ユーザー</p></td>
</tr>
<tr class="odd">
<td><p>監視およびアーカイブ</p></td>
<td><p>Lync Server 2013 では、監視とアーカイブのフロントエンド サービスは、独立したサーバーの役割ではなく各 フロント エンド サーバーで実行されるようになりました。</p>
<p>監視とアーカイブにはそれぞれ専用のデータベース ストアが必要です。 Exchange 2013 も実行する場合は、専用の SQL データベースではなく Exchange にアーカイブ データを保持できます。</p></td>
</tr>
<tr class="even">
<td><p>1 台の仲介サーバー</p></td>
<td><p>フロント エンド サーバーと併置されている 仲介サーバーは、プール内のすべての フロント エンド サーバーで実行されます。このサーバーは、プール内のユーザーに十分な処理能力を提供する必要があります。スタンドアロンの 仲介サーバーについては、この後の「仲介サーバー」を参照してください。</p></td>
</tr>
<tr class="odd">
<td><p>1 台の Standard Edition サーバー</p></td>
<td><p>Standard Edition サーバーを使用してユーザーをホストする場合は常に 2 台のサーバーを使用し、「<a href="lync-server-2013-planning-for-high-availability-and-disaster-recovery.md">Lync Server 2013 での高可用性および障害復旧の計画</a>」に示す推奨事項に従って 2 台をペアにすることを強くお勧めします。ペアの中の各サーバーは、最大 2,500 ユーザーをホストすることができ、フェールオーバー シナリオでは、1 台のサーバーに障害が発生した場合は残りの 1 台で 5,000 ユーザーをサポートできます。</p>
<p>展開に大量のオーディオまたは動画トラフィックがある場合、サーバーあたりのユーザー数が 2,500 名を超えるとサーバー パフォーマンスが低下することがあります。この場合、Standard Edition サーバーを追加するか、Lync ServerEnterprise Edition に移行することを検討する必要があります。</p></td>
</tr>
</tbody>
</table>


## フロント エンド サーバー

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>拡大されたプールは、このサーバーの役割ではサポートされていません。</td>
</tr>
</tbody>
</table>


プール内のすべてのサーバーでハイパースレッディングが有効であり、「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」で説明されている推奨事項をサーバー ハードウェアが満たしている場合、 フロント エンド プールでは、プールに所属する 6,660 ユーザーごとに 1 台の フロント エンド サーバーが必要です。プール内のすべてのサーバーでハイパースレッディングが有効な場合、1 つの フロント エンド プールの最大ユーザー数は 80,000 です。サイトに 80,000 を超えるユーザーが存在する場合、複数の フロント エンド プールを展開できます。

フロント エンド プール内のユーザー数を考慮する際は、この フロント エンド プールに関連付けられているブランチ オフィスの存続可能ブランチ アプライアンスおよび存続可能ブランチ サーバーに所属するユーザーを含めます。

アクティブなサーバーが使用できなくなると、その接続はプール内にある他のサーバーに自動的に転送されます。たとえば、30,000 ユーザーと 5 台の フロント エンド サーバーが存在する場合、1 台のサーバーが使用できなくなると、6,000 ユーザーの接続を他の 4 台のサーバーに転送する必要があります。残りの 4 台のサーバーはそれぞれ、推奨最大数を超える 7,500 ユーザーをサポートすることになります。

また、30,000 ユーザー用に 6 台の フロント エンド サーバーが存在する場合、1 台のサーバーが使用できなくなると、残りの 5 台のサーバーに合計 5,000 ユーザーが移動されます。これらの 5 台のサーバーはそれぞれ、推奨数の範囲内の 6,000 ユーザーをホストすることになります。

1 フロント エンド プール内の最大ユーザー数は 80,000 です。1 プール内の最大 フロント エンド サーバー数は 12 です。

80,000 ユーザーが存在する フロント エンド プールの場合、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」に従った一般的な展開においては、12 台の フロント エンド サーバーで十分なパフォーマンスを得ることができます。障害復旧のフェールオーバーをサポートするように設計された展開では、ペアになった 2 つの フロント エンド プールのそれぞれにおいて、最大 40,000 ユーザーをホストできると想定しています。一方のプールをもう一方にフェールオーバーする必要がある場合に備えて、各プールには、両方のプール内のユーザーに対応できる十分な数の フロント エンド サーバーが用意されています。

特定の フロント エンド プールによって十分なパフォーマンスを確保できるユーザー数は、これらのユーザー数とは以下の理由で異なる場合があります。

  - フロント エンド サーバーのハードウェアが、「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」の推奨事項を満たしていません。

  - ユーザー モデルよりもかなり多い会議トラフィックの場合など、組織の使用法がユーザー モデルのそれと著しく異なります。


> [!IMPORTANT]
> Lync Server 2013 では、プレゼンス データベースが フロント エンド サーバーでホストされるようになりました。 Lync Server 2010 では、これらのデータベースが バック エンド サーバーでホストされていました。つまり、 フロント エンド サーバーがホストするユーザー数に関係なく、このセクションの前半および「<A href="lync-server-2013-server-hardware-platforms.md">Lync Server 2013　用のサーバー ハードウェア プラットフォーム</A>」で示している推奨事項によって、 フロント エンド サーバーのディスクのパフォーマンスと容量が影響を受けることはありません。



次の表は、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」で定義された、ユーザー モデルを考慮した IM およびプレゼンスの平均帯域幅を示します。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ユーザー単位の平均帯域幅</th>
<th>6,660 ユーザーが存在する フロント エンド サーバーごとの帯域幅要件</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.3 Kpbs</p></td>
<td><p>13 Mbps</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>フロント エンド サーバーで、併置された音声ビデオ会議および 仲介サーバーの機能のメディア パフォーマンスを改善するには、フロント エンド サーバーのネットワーク アダプターの Receive-Side Scaling (RSS) を有効にする必要があります。RSS により、着信パケットをサーバーの複数のプロセッサによって並行して処理することが可能になります。詳細については、「Windows Server 2008 での Receive-Side Scaling 拡張機能」( <a href="http://go.microsoft.com/fwlink/?linkid=268731" class="uri">http://go.microsoft.com/fwlink/?linkid=268731</a>) を参照してください。RSS を有効にする方法の詳細については、ネットワーク アダプターのドキュメントを参照してください。</td>
</tr>
</tbody>
</table>


## 最大会議数

プール内のユーザーのうちの 5% がいつでも会議中である可能性があるというユーザー モデルを考慮すると、プール内のユーザー数が 80,000 の場合は、一度に約 4,000 ユーザーが会議中である可能性があります。これらの会議は、混合メディア (たとえば、IM のみ、音声付き IM、音声ビデオ) であり、参加者数もさまざまであると考えられます。許可される実際の会議数に対して厳しい制限はありません。実際の利用状況が実際のパフォーマンスを決定します。たとえば、組織内の混合モードの会議数がユーザー モデルで想定された数よりも多い場合は、このドキュメントで推奨値よりも多くの フロント エンド サーバーまたは音声ビデオ会議サーバーを展開することが必要になる可能性があります。ユーザー モデルの想定内容の詳細については、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」を参照してください。

ユーザーもホストする Lync Server 2013 の通常の フロント エンド プールがホストする、サポートされる最大会議規模は、参加者 250 名です。250 ユーザーが参加する会議が行われている場合、プールは同時に他の会議もサポートします (同時に行われる会議にプール ユーザーのうちの 5% が参加している場合など)。たとえば、12 台の フロント エンド サーバーおよび 80,000 ユーザーが存在するプールでは、250 名のユーザーが参加する会議が行われている場合に、 Lync Server は 3,750 名の他のユーザーがより小さい会議に参加するのをサポートします。

フロント エンド プールまたは Standard Edition サーバーに所属するユーザー数にかかわらず、 Lync Server は、250 名のユーザーが参加する会議をホストする同じプールまたはサーバーにおいて、最小で 125 名の他のユーザーがより小さい会議に参加するのをサポートします。

250 ～ 1,000 名のユーザーが参加する会議を有効にするために、それらの会議のみをホストする個別の フロント エンド プールを設定できます。この フロント エンド プールはユーザーをホストしません。詳細については、「[Lync Server 2013 を使用した大規模会議のサポート](lync-server-2013-supporting-large-meetings.md)」を参照してください。

組織内の混合モードの会議数がユーザー モデルで想定された数よりも多い場合は、このドキュメントで推奨値よりも多くの フロント エンド サーバー (最大 12 FE) を展開することが必要になる可能性があります。ユーザー モデルの想定内容の詳細については、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」を参照してください。

## エッジ サーバー

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>拡大されたプールは、このサーバーの役割ではサポートされていません。</td>
</tr>
</tbody>
</table>


サイトに同時にアクセスする 12,000 リモート ユーザーごとに 1 台の エッジ サーバーを展開する必要があります。高可用性を実現するために 2 台以上の エッジ サーバーを用意することをお勧めします。これらの推奨事項は、 エッジ サーバー用のハードウェアが「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」で説明されている推奨事項を満たしていることを前提としています。

エッジ サーバーのユーザー数を考慮する際は、このサイトの フロント エンド プールに関連付けられているブランチ オフィスの存続可能ブランチ アプライアンスおよび存続可能ブランチ サーバーに所属するユーザーを含めます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>エッジ サーバーの音声ビデオ会議エッジ サービスのパフォーマンスを改善するには、エッジ サーバーのネットワーク アダプターの Receive-Side Scaling (RSS) を有効にする必要があります。RSS により、着信パケットをサーバーの複数のプロセッサによって並行して処理することが可能になります。詳細については、「Windows Server 2008 での Receive-Side Scaling 拡張機能」( <a href="http://go.microsoft.com/fwlink/?linkid=268731" class="uri">http://go.microsoft.com/fwlink/?linkid=268731</a>) を参照してください。RSS を有効にする方法の詳細については、ネットワーク アダプターのドキュメントを参照してください。</td>
</tr>
</tbody>
</table>


## ディレクター

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>拡大されたプールは、このサーバーの役割ではサポートされていません。</td>
</tr>
</tbody>
</table>


ディレクター サーバーの役割を展開する場合は、サイトに同時にアクセスする 12,000 リモート ユーザーごとに 1 台の ディレクターを展開することをお勧めします。高可用性を実現するために 2 台以上の ディレクターを用意することをお勧めします。これらの推奨事項は、 エッジ サーバー用のハードウェアが「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」で説明されている推奨事項を満たしていることを前提としています。

ディレクターのユーザー数を考慮する際は、このサイトの フロント エンド プールに関連付けられているブランチ オフィスの存続可能ブランチ アプライアンスおよび存続可能ブランチ サーバーに所属するユーザーを含めます。

## 仲介サーバー

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>拡大されたプールは、このサーバーの役割ではサポートされていません。</td>
</tr>
</tbody>
</table>


仲介サーバーと フロント エンド サーバーを併置する場合、 仲介サーバーは、プール内のすべての フロント エンド サーバーで実行されます。このサーバーは、プール内のユーザーに十分な処理能力を提供する必要があります。

スタンドアロンの 仲介サーバー プールを展開する場合、何台の 仲介サーバーを展開するかは、 仲介サーバーに使用されるハードウェア、存在する VoIP ユーザーの数、それぞれの 仲介サーバー プールが管理するゲートウェイ ピアの数、それらのゲートウェイを通過する最繁時トラフィック、 仲介サーバーをバイパスするメディアを使用した通話の割合などの、多くの要素から決まります。

次の表は、仲介サーバーが処理できる同時通話数に関するガイドラインを提供しています。このガイドラインは、仲介サーバー用のハードウェアが「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」で説明されている推奨事項を満たしていることを前提としています。仲介サーバーのスケーラビリティの詳細については、「[Lync Server 2013 の音声の利用状況とトラフィックの予測](lync-server-2013-estimating-voice-usage-and-traffic.md)」および「[Lync Server 2013 の仲介サーバーの展開ガイドライン](lync-server-2013-deployment-guidelines-for-mediation-server.md)」を参照してください。

以降の表はすべて、「[Lync Server 2013 のユーザー モデル](lync-server-2013-user-models.md)」にまとめられている使用法を前提としています。

### スタンドアロン 仲介サーバーの処理能力: 内部ユーザーが 70%、外部ユーザーが 30%、バイパスではない通話の処理能力 ( 仲介サーバーによって実行されるメディアのコード変換)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>サーバー ハードウェア</th>
<th>最大通話数</th>
<th>T1 回線の最大数</th>
<th>E1 回線の最大数</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>デュアル プロセッサ、6 コア、2.26 GHz ハイパースレッディング CPU ( <strong>ハイパースレッディング無効</strong>)、32 GB メモリ、デュアルポート ネットワーク アダプター カード 1 つ</p></td>
<td><p>1100</p></td>
<td><p>46</p></td>
<td><p>35</p></td>
</tr>
<tr class="even">
<td><p>デュアル プロセッサ、6 コア、2.26 GHz ハイパースレッディング CPU、32 GB メモリ、デュアルポート ネットワーク アダプター カード 1 つ</p></td>
<td><p>1500</p></td>
<td><p>63</p></td>
<td><p>47</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>パフォーマンス テストにはメモリが 32 GB のサーバーを使用しましたが、スタンドアロンの 仲介サーバーではメモリが 16 GB のサーバーがサポートされており、その条件のサーバーでもこの表に示されるパフォーマンスを十分実現できます。</td>
</tr>
</tbody>
</table>


### 仲介サーバーの処理能力: ( フロント エンド サーバーと併置されている 仲介サーバー) 内部ユーザーが 70%、外部ユーザーが 30%、バイパスではない通話の処理能力 ( 仲介サーバーによって実行されるメディアのコード変換)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>サーバー ハードウェア</th>
<th>最大通話数</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>デュアル プロセッサ、6 コア、2.26 GHz ハイパースレッディング CPU、32 GB メモリ、1 GB ネットワーク アダプター カード × 2</p></td>
<td><p>150</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>この数は、スタンドアロンの 仲介サーバーの場合の数よりも少なくなっています。 フロント エンド サーバーでは、音声通話に必要なコード変換に加えて、そのサーバーに所属する 6,600 ユーザーが使用するその他の機能を処理する必要があるためです。</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>仲介サーバーのパフォーマンスを改善するには、仲介サーバーのネットワーク アダプターの Receive-Side Scaling (RSS) を有効にする必要があります。RSS により、着信パケットをサーバーの複数のプロセッサによって並行して処理することが可能になります。詳細については、「Windows Server 2008 での Receive-Side Scaling 拡張機能」( <a href="http://go.microsoft.com/fwlink/?linkid=268731" class="uri">http://go.microsoft.com/fwlink/?linkid=268731</a>) を参照してください。RSS を有効にする方法の詳細については、ネットワーク アダプターのドキュメントを参照してください。</td>
</tr>
</tbody>
</table>


## バック エンド サーバー

Lync Server 2013 では、プレゼンス データベースが バック エンド サーバーではなく フロント エンド サーバーに配置されます。これにより、 Lync Server 2013 における各 バック エンド サーバーの要件が大幅に簡素化され、 フロント エンド サーバーのハードウェア要件と同等になりました。 Lync Server 2010 では、25 台のディスクを搭載した高度なサーバーを バック エンド サーバーとして使用する必要がありました。しかし、 バック エンド サーバーのワークロードについては、このセクションの前半および「[Lync Server 2013　用のサーバー ハードウェア プラットフォーム](lync-server-2013-server-hardware-platforms.md)」で示しているハードウェアの推奨事項を満たしている必要があります。

バック エンド サーバーの高可用性を提供するために、サーバー ミラーリングを展開することをお勧めします。詳細については、「[Lync Server 2013 のバックエンド サーバーの高可用性](lync-server-2013-back-end-server-high-availability.md)」を参照してください。

## 監視およびアーカイブ

Lync Server 2013 では、監視またはアーカイブを展開すると、これらのサービスのフロントエンド機能が独立したサーバーの役割ではなく フロント エンド サーバーで実行されます。監視とアーカイブではそれぞれ、バックエンド ストアから切り離された専用のデータベース ストアを使用します。また、 Exchange 2013 を展開済みの場合は、専用の SQL ストアではなく Exchange にインスタント メッセージのアーカイブ データを保存できます。

次の表は、監視およびアーカイブのデータに必要な、ユーザーごとの 1 日あたりのデータベース記憶域 (概算) を示します。


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>CDR (監視)</strong></p></td>
<td><p><strong>QoE (監視)</strong></p></td>
<td><p><strong>アーカイブ</strong></p></td>
</tr>
<tr class="even">
<td><p>ユーザーごとに 1 日に必要なディスク容量</p></td>
<td><p>49 KB</p></td>
<td><p>28 KB</p></td>
<td><p>57 KB</p></td>
</tr>
</tbody>
</table>


Microsoft では、パフォーマンス テストの際に、次の表に示すハードウェアを監視およびアーカイブ用のデータベース サーバーとして使用しました。このテストでは、それぞれに 80,000 ユーザーが存在する 2 つの フロント エンド プールのデータを収集しました。

### 監視およびアーカイブのパフォーマンス テストで使用したハードウェア

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ハードウェア コンポーネント</th>
<th>推奨値</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>64 ビット デュアル プロセッサ、6 コア、2.26 GHz 以上</p></td>
</tr>
<tr class="even">
<td><p>メモリ</p></td>
<td><p>48 ギガバイト (GB)</p></td>
</tr>
<tr class="odd">
<td><p>ディスク</p></td>
<td><p>次の構成を持つ 10,000 RPM のハード ディスク ドライブ × 25 (各ディスクのサイズは 300 GB)</p>
<h3 id="section-3"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>ドライブ</strong></p></td>
<td><p><strong>RAID 構成</strong></p></td>
<td><p><strong>ディスク数</strong></p></td>
</tr>
<tr class="even">
<td><p>CDR、QoE、およびアーカイブ データベースのデータ ファイル (単一のドライブ上)</p></td>
<td><p>1 + 0</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>CDR データベースのログ ファイル</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>QoE データベースのログ ファイル</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>アーカイブ データベースのログ ファイル</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>ネットワーク</p></td>
<td><ul>
<li><p>1 Gbps 以上のデュアルポート ネットワーク アダプター 1 つ (2 つを推奨。その場合は 1 つの MAC アドレスと 1 つの IP アドレスのチーミングが必要)</p></li>
</ul></td>
</tr>
</tbody>
</table>


## このセクション中

  - [Lync Server 2013 の音声の利用状況とトラフィックの予測](lync-server-2013-estimating-voice-usage-and-traffic.md)

  - [Lync Server 2013 の仲介サーバーの展開ガイドライン](lync-server-2013-deployment-guidelines-for-mediation-server.md)
