Glade用ひびきの設計関連ファイル(2017/1/24:akita11)

スタセル作成時の指針
StdCellライブラリを開き、既存のスタセル(inv1.gexなど)に対して、以下の修正・追加を行っていく。
・名称の変更(末尾の_v2.gexを取る。inv1_v2.gex -> inv1 など)
・layoutでの信号名ラベル文字列の変更（入力はIA, IB, ...とIから始まる。出力はゲートはO、フリップフロップはQとQB）
・回路図(schematics)の作成（信号名はlayoutにあわせる。nMOS/pMOSはStdCellライブラリ内のnch/pchを、電源はbacisライブラリ内のVDD/GNDを使用する）
・シンボル(symbol)の作成（以下の点に留意: inv1のsymbolを参考に）
  - グリッドは1um単位として、少なくともネット（赤い四角）はグリッドに乗せる（可能な範囲ですべての図形も）
  - ネット名はlayout, schematicsにあわせる
  - 全体の大きさは、inv1のものを目安に（極端に大きくor小さくならないように）
  - 全体の中心がほぼ原点に来るように配置する
  - cellName, instName、Textを作成時に"Label Use"をdevice label/inst labelを選び、sizeを1.0に
  - 外枠をboundaryの長方形で囲う

スタンダードセルの使い方
1. File->New Libでライブラリを作成。このとき、Technologyでhibikino.tchを指定する（ここでレイヤ定義などが設定される）
2. File->Import->Import GDS2で、stdcell_v2.gdsを指定する。このとき読み込むライブラリを、1.で作成したライブラリに設定する。またはFile->Open Libraryで、ここにある StdCell_v2を指定する。
3. スタセルがこのライブラリに読み込まれるので、これを使って新しい回路(Cellview)をつくる

DRCファイルの使い方
Verify->DRC->Run DRC (Shift+D)で、"hibikino-drc.py" を指定してDRCをかける。
エラーがあればVerify->DRC->View DRC Errorsで確認できる

回路抽出の使い方
Verify->Extract->RunLVEで、"hibikino-ext.py"を指定すると、そのセルに対してextractedというビューができる。右下の"Net Browser"に、ネット名が現れ、どれかを選択すると、そのネットに対応するオブジェクトがハイライトされる。なおレイアウトで、ML1/ML2/POLに同じレイヤで書いた文字列（文字列の制御点が対象図形の中にあること）が、そのネットのネット名になる。ネットリストファイルの出力は、File->Export->Export CDLで、（ほぼ）spice形式で出力できる。

回路図入力
・MOSはStdCell_v2内のセルnch/pchを使う。
・入出力は、Create->Pinでピンとして、名称をつけて作成。
・VDD/GND等は、basicライブラリ中のvdd/gndを使う。または入出力と同じくピンとして作成する。
・これらの端子（赤い四角）をWireで結ぶ。
なおWireは最初はネット名がついていないが、Check Cellviewするとネット名がつく。
つながっているはずなのにつながっていない（浮いている）、というエラーが出ることがあるが、再度Check Cellviewすると治ることもある（謎挙動）。
端点でwireの2回目をクリックすると、wire配線が終わるので、それでつながっているかは判断できる（端点上でクリックしないとwire配線が続く）。
File->Export→Export CDLで（ほぼ）spice形式のネットリストを出力できる。

LVSのかけ方
1.レイアウト("layout")を開き、↑の手順で回路抽出。"extracted"ビューが生成される。
2."extracted"ビューを開き、そこからVerify->LVS->Run LVSでLVSを実行。画面の右側で↑で回路図からexportしたネットリスト(CDL形式)を指定する。
3.LVSが実施される。なおMOSトランジスタのサイズの不一致は検出されない模様（詳細未確認）。

PCell
Pcell(parameterized cell)とは、MOSトランジスタなどの要素部品を、その形状パラメータ（ゲート長など）を指定して、自動的にレイアウトを作成する機能。
(1)nMOS/pMOS用
1.nmos_master.pyとpmos_master.pyをどこかに置き、環境変数PYTHONPATHを、そのディレクトリに設定する（ない場合は作成、既にある場合は追加）。またはこれらをGladeのディレクトリ(・・・/glade_win64/など)に置く。
2.New->CellでCellを作成するとき、"CellView is a Pcell"をチェックし、"Pcell script"に、これらの*.pyを指定し、OKすると、nmos_masterまたはnmos_masterのlayoutが作成される。これらのサイズは標準値で作成される。（このセルをsuper masterと呼ぶ）
3.使いたいセル(layout)で、インスタンス作成(i)で、CellNameでh_nmosまたはh_pmosを選び、 そのとき"Instance Property"タブで、l（ゲート長）、w（ゲート幅）、m（フィンガー数）、poly_con（ゲートにコンタクトを打つか）を指定してインスタンスを作成すると、そのパラメータの寸法のMOSトランジスタが置かれる。（うまく作成されない場合があるようだが、いったん作成後、インスタンスのプロパティからこれらのパラメータを修正すれば、それに応じたサイズのMOSトランジスタになる）

(2)コンタクト・VIA用
以下のものがある。いずれも横・縦に並べるコンタクトorVIAの個数をnx,nyで指定する。
・polycon_master.py : POL-ML1+コンタクト(CNP)
・ncon_master.py : nACT-ML1+コンタクト(CNA)
・pcon_master.py : pACT-ML1+コンタクト(CNA)
・ml1via_master.py : ML1-ML2+VIA

Glade操作メモ
DisplayOption->MiscellaneousのAlways pop up option dialogをはずすと、Moveなどのたびにオプション画面が表示されない（F3で適宜表示できる）
