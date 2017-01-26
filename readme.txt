Glade用ひびきの設計関連ファイル(2017/1/24:akita11)

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

Glade操作メモ
DisplayOption->MiscellaneousのAlways pop up option dialogをはずすと、Moveなどのたびにオプション画面が表示されない（F3で適宜表示できる）

