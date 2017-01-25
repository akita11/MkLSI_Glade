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
