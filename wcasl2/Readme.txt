
 CASL?U and COMET?U Simulator for Windows WCASL-?U ver1.08

                                                               渡辺 博芳

１．概要
  WCASL-?Uは，CASL?UとCOMET?Uのシミュレータです．Windows系のOSで動作します．
Windows XP, Windows 2000, Windows NT ver4.0 と Windows 98 上での動作は確認しました．
  以下の2つのシミュレーションモードがあるのが特徴です．
   ・CASL?Uプログラミング習得のためのモード
   ・CPUとしてのCOMET?Uの動作を理解するためのモード
  旧CASL用のシミュレータWCASLは，帝京大学理工学部情報科学科の演習で5年間使用した
実績があり，WCASL-?Uも同演習で1年間使用しました．その間，不具合に対処するとともに，
教育的配慮を高めてきました．
  インターネットに接続できる環境であれば，本文書を読むよりも，以下のURLを見て頂く
方がわかりやすいと思います．
  http://www.ics.teikyo-u.ac.jp/wcasl2/ 

  WCASL-?Uでは，WCASL(旧版)が持っていた機能の他に，以下のような機能を設けました．
  ・複数のCASLソースファイルをリンクして1つの実行プログラムにすることが
  できます．メイクファイルにCASLソースファイルを登録することで行います．
  ・シミュレーションにおいて，レジスタの値を設定できるようにしました．
  メニューの[プロジェクト]から行います．
  ・CASLシミュレーションにおいて，レジスタの値の10進表示は，符号付整数と
  符号無整数の切り替えが可能です．メニューの[表示]から行います．

２．ソースプログラムの作成
  CASLプログラムは，一般のテキストエディタで作成する方法とWCASL-?Uで作成する方法
があります．いずれの方法の場合も以下の点に注意してください．

  ・１つの命令を１行で記述します．
  ・ラベルは行の最初にブランクやタブを置かずに書きます．
    (行の第1文字がブランクやタブの場合，ラベルとみなしません．)
  ・ラベルが無い場合，命令コードを行の最初から書かずにブランクかタブをおきます．
  ・ラベル，命令コード，オペランドの間は１つ以上のブランクまたはタブをおきます．
  ・セミコロン;のあとはコメントになります．
  ・コメント以外のプログラムの部分は大文字で記述します．
  ・ファイル名の拡張子を.casとします．
  ・プログラムの途中に空の行があるとエラーになります．


３．コマンド
3.1 ファイル
  フォーカスされているウィンドウによって異なりますが，ファイルを選択すると，CASL2
プログラムの新規作成，CASL2プログラムを開く，閉じる，メイクファイルの新規作成，メ
イクファイルを開く，上書き保存，名前を付けて保存，印刷，印刷のプレビュー，プリンタ
の設定，WCASLの終了などの項目を持つサブメニューが表示されます．
  ここで開いたり，保存したりするのはCASLプログラム(ファイル名*.cas)です．

3.2 編集
  編集は，CASLプログラム編集ウィンドウだけで選択できます．ここではアンドゥ，切
り取り，コピー，貼り付けなどの項目を持つサブメニューが表示されます．マウスで領
域を指定して，これらのコマンドを用いると，カットアンドペーストが行なえます．

3.3 表示
  ツールバー，ステータスバーを持つサブメニューが表示されます．マウスでクリック
することにより，表示するか否かを選択できます．チェックされているときはそれぞれ
のバーが表示されます．

3.4プロジェクト(プログラムの編集ウィンドウ)
  プロジェクトのサブメニューはシミュレータの状態によって異なります．プログラム
編集ウィンドウでは，アセンブル，アセンブルモード，CASLシミュレート，COMETシミュ
レートの4つのメニューがあります．

(1)アセンブル
  アセンブルを実行すると，アセンブラアウトプットウィンドウが開いて，アセンブル
の結果を表示します．エラーがある場合には，エラーがある行に error> という印が
付きますので，プログラム編集ウィンドウに戻って，プログラムを修正してください．
アセンブルエラーが無い場合には，シミュレートが行えます．
  CASLプログラム編集ウィンドウでアセンブルを実行すると，そのCASLプログラムから
実行形式を生成し，CPUのメモリにロードします．
  メイクファイル編集ウィンドウでアセンブルを実行すると，メイクファイルに登録さ
れているCASLファイル全てをアセンブル，リンクして実行形式を生成し，CPUのメモリに
ロードします．

(2)ロードモード
  ロードモードとして，プログラムをロードする先頭アドレスの指定とロード時に メ
モリレジスタを0で初期化するか，-1で初期化するか，初期化しないかを選べます．デ
フォルトでは，"-1で初期化する"になっています．
C言語などでは，コンパイルなどで変数を初期化しませんので，最初にどんな値が入って
いるかわかりません．BASICなどでは，変数は最初に0で初期化されることになっています．
通常，アセンブリ言語は前者です．演習で使用した経験から，最初から0が入っていない
状態である方が教育的と考え，-1で初期化するをデフォールトにしてます．

(3)CASLシミュレート
  アセンブルして，エラーが無ければ続いてCASLシミュレートウィンドウを開きます．
エラーがある場合には，アセンブラアウトプットウィンドウにエラーが表示されます．

(4)COMETシミュレート
 アセンブルして，エラーが無ければ続いてCOMETシミュレートウィンドウを開きます．
エラーがある場合には，アセンブラアウトプットウィンドウにエラーが表示されます．

3.5プロジェクト(アセンブラアウトプットウィンドウ)
  アセンブラアウトプットウィンドウでは，CASLシミュレートとCOMETシミュレートの
2つの項目があります．エラーがなければ，それぞれのシミュレータが起動されます．
エラーがある場合は，項目を選択しても，動作しません．

3.6プロジェクト(CASLシミュレートウィンドウ)
  コマンドの説明をする前に，表示されている情報について説明します．
  まず，左上に各レジスタの値が表示されています．青は16進数，水色は10進数，茶色
と紫は2進数の値を表しています．ただし，FRについては2進数のみで表示されます．
その下には，プログラム中のデータ領域のラベルのアドレスとそこに格納されている値が
16進数と10進数でで示されています．データの数が多い場合は，スクロールバーが現れ
ますので，それを使ってスクロールさせることができます．
  右上にはプログラムが表示されます．まず，アドレスが緑色で，次に機械語コードが
水色で，そして，ソースリストが緑色で示されます．実行した命令は赤色になります．
プログラムが15行よりも長い場合は，スクロールバーでスクロールさせることが可能です．
  右下には小さいディスプレイを用意しました．OUTによって，文字列をここに表示する
ことができます．
  左下はスタックエリアの内容です．アドレスとその内容が16進数で表示されます．
ここも表示のメニューからコマンドを選択してスクロールが可能です．

  CASLシミュレートウィンドウでは，リロード，ロードモード，STEPの設定，STEPの実行，
 時間の設定，時間実行，時間実行停止，レジスタ値の設定があります．  

(1)リロード
  実行形式のプログラムをロードし直します．

(2)ロードモード
  3.4で述べたロードモードと同じです．

(3)STEPの設定
  1ステップで実行する単位を指定します．命令ごとの1ステップ実行，最後まで実行，
指定したアドレスまで実行の3つの中から選択できます．選択するにはダブルクリック
してください．指定したアドレスまで実行は，そのアドレスの前の命令までを実行し
ます．このとき，そのアドレスの命令が赤くなりますが，まだ，実行はされていません．
これを使って，ブレークポイントを指定できます．つまり，長いプログラムで，ある程
度までプログラムを進めて，命令ごとに切換えて1ステップずつ確認することができます．

(4)STEPの実行
  (3)で指定されたステップを実行します．これは，ENTERキーを押しても同じです．

(5)1STEP戻る
　1ステップ前の状態に戻ります．これは，BackSpaceキーを押しても同じです．
　ただし，ロード後，レジスタ値を変更した場合は正しく動作しません．

(6)時間の設定
  時間実行で，インターバル時間をおいて，自動的に次のステップを実行することがで
きます．その時間を設定します．

(7)時間実行
  (6)で設定した間隔でステップを自動的に実行します．

(8)時間実行停止
  時間実行を停止します．CTL-Qでも止めることができます．

(9)レジスタ値の設定
  レジスタとそこに設定する値を入力して，レジスタの値を設定します．
(10)入出力装置の設定
  INの入力装置とOUTの出力装置を設定します．入力装置はキーボードか，ファイル，
出力装置はディスプレイか，ファイルを選択できます．

3.7プロジェクト(COMETシミュレートウィンドウ)
  左側にCPUを構成するレジスタやバスが表示され，右側にはメモリの内容が表示され
ます．また，下にディスプレイがあります．個々の実行でデータの移動や値の変化が伴
う箇所は赤色になります．
  COMETシミュレートウィンドウでは，CASLモードと同じように，ロードモード，リロード，
STEPの設定，STEPの実行，1STEP戻る，時間の設定，時間実行，時間実行の停止，レジスタ値
の設定があります．異なるのは，STEPの設定として，最小の単位，フェーズごとが追加されて
いることです．COMETモードではより詳細なデータの流れをトレースすることができます．


4.COMETシミュレートウィンドウ
  COMETシミュレートウィンドウでは一つ一つの命令の実行過程，すなわち，命令取り
出しサイクル，命令解読サイクル，アドレス生成サイクル，命令実行サイクルを詳細に
トレースします．このウィンドウではレジスタやメモリを配置した図が表示されます．
まず，以下のレジスタやユニットがそれぞれどこにあるか，それらの関係を確認して
おきましょう．
    PR  プログラムレジスタ
        次に実行される命令のアドレスを保存．
    IR  命令レジスタ
        解読，実行する命令を保存．
    GR  汎用レジスタ
        
    FR  フラグレジスタ
        演算後のフラグの状態を保持．
    MAR  メモリアドレスレジスタ
        メモリを読み書きする際に，アクセスするアドレスを指定するレジスタ．
    MDR  メモリデータレジスタ
        メモリを読む場合，メモリの内容が転送されます．反対にメモリに書き込む
        場合，このレジスタの内容が書き込まれます．メモリの読み書きの制御は
        コントロールユニットが行います．
    EADR 有効アドレス
        実際には，このようなレジスタはありません．有効アドレスの内容がわかる
        ように窓を設けたと考えてください．
    adr-adder  アドレス加算器
        命令のアドレス部とインデックスレジスタの内容から有効アドレスを求める
        加算器です．
    ALU    演算装置
        算術，論理，シフト，比較などの演算を行います．

  メモリの右側には，ソースコードを表示します．また，SVC命令以外の命令は一通り
トレース可能です．IN, OUT から展開されるSVC 1 と SVC  2は実行はされますが，
命令実行サイクルの詳細な様子はトレースされません．

５．おわりに
  WCASL-?Uはフリーソフトです．アーカイブの内容を変更しなければ，配布は自由です．
著作権は渡辺博芳にあります．また，WCASLによって障害または損害が発生しても著作者
は一切責任を負いません．
  WCASL-?Uに関するご意見・お問合せは，以下のメールアドレスまでお願いします．
    wcasl@ics.teikyo-u.ac.jp

 WCASL-?Uホーム  http://www.ics.teikyo-u.ac.jp/wcasl2/ 

謝辞
  WCASL，及びWCASL-?Uについて多くの貴重なコメントを頂きました武井惠雄先生，
荒井正之先生，高井久美子さんに感謝いたします．また，公開以来，何人かの方々に
不具合などの報告をいただきました．どうもありがとうございます．