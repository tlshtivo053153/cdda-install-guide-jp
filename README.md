# CDDA インストールガイド
この文書は Cataclysm:DDA のインストールガイドである。

## 必要スペック

* OS
    * Windows, Mac, Linux, Android
* メモリ
    * 空き容量4GB
* ストレージ
    * 4GB
* CPU
    * シングルスレッド性能の高いものがよい

### メモリ
メモリは約2GB消費するので空き容量4GBあれば不足しないはず。

### ストレージ
このゲームの世界は無限に広がるので、世界の大きさに比例して
ストレージも消費する。
セーブデータのサイズは、ゲーム開始直後なら数MBだが
やり込んだデータならGB単位のサイズにもなる。

### CPU
このゲームはマルチスレッドに対応していないため、
シングルスレッド性能が高いCPUだと快適に遊べる。
CPUの性能が高いと、ゲームの1ターンの処理が早く終わる。
長時間の待機や、アイテムのクラフト、睡眠などで、数千、数万ターン
かかる場合などに影響する。
また、NPCやモンスターが多くいる場所では、CPUの負荷が大きくなる。

## インストール
このゲームには、安定版(Stable)と開発版(Experimental)がある。
安定版は、バグが少ないが開発版より古い。
開発版は、最新の機能があるがバグが多い。

Curses版とTiles版の2種類あるが、
Cursesはコマンドライン環境の文字ベースのバージョンで、
Tilesはグラフィックのあるバージョンである。
よほどのことがなければTilesを推奨する。

### ゲーム本体

* [安定版0.G](stable/0.G/INSTALL.md)
* [開発版](experimental/INSTALL.md)

### タイルセット
ゲーム本体にも多くのタイルセットが同梱されているが、
外部のタイルセットも導入できる。

* [MSX++UnDeadPeopleEdition](tilesets/UDP.md)

### サウンドパック
サウンドパック同梱済みのバージョンもあるが、
満足できないなら外部のサウンドパックもある。

* [Otopack-Mods-Updates](soundpack/OTOPACK-MODS-UPDATES.md)

## オプション
ゲームオプションの変更は `[タイトル画面]->[設定]->[オプション]` から行う。
必要最低限の変更をする。

オプションには `全般`, `インターフェース`, `表示`, `世界生成`, `デバッグ`
の5種類があり、`Tab` キー、`Shift-Tab` キー、で切り替えることができる。

### 全般

#### サウンドパック選択
外部のサウンドパックを導入した場合、ここから選択できる。
反映には再起動が必要。

* 初期設定: `基本`

### インターフェース

#### 温度単位
`摂氏` に変更。

* 初期設定: `華氏`
* 選択肢: `華氏`, `摂氏`, `ケルビン`

#### 速度単位
`km/h` に変更。

* 初期設定: `mph`
* 選択肢: `mph`, `km/h`, `タイル/ターン`

#### 重量単位
`kg` に変更。

* 初期設定: `lbs`
* 選択肢: `lbs`, `kg`

#### 距離単位
`メートル法` に変更。

* 初期設定: `ヤードポンド法`
* 選択肢: `メートル法`, `ヤードポンド法`

### 表示

#### タイルセット選択
外部のタイルセットを導入した場合、ここから選択できる。

* 初期設定: UltiCa
* 選択肢: ASCIITiles, AltiCa, BrownLikeBears, Chibi_Ultica,
Cuteclysm, Hollow Moon, Larwick Overmap, MSXotto+, NeoDays, RetroDays,
SmashButton iso, SurveyorsMap, Ultica_iso, UltiCa

#### 全体マップタイル表示
`True` に変更すると、全体マップをタイル表示できる。
タイルセットの種類は `全体マップタイルセット選択` から変更する。

* 初期設定: `False`
* 選択肢: `False`, `True`

### 世界生成
これは、世界生成を行うときのデフォルト設定である。
このオプションを変更しても生成済みの世界には影響はないため注意。
生成済みの世界設定を変更したい場合は、変更したい世界でゲームを開始して
`Esc` からメインメニューを開き、`オプション->現在の世界` で変更できる。
ただし、オプションの変更によってエラーが発生する可能性がある。

#### 大変動開始日
`0` が春の1日目になり `-1` で開始日ランダムになる。

`季節の長さ` を変更した場合に `大変動開始日` も変更しないと
ゲームの開始季節が変わることがある。
例えば、`季節の長さ` が `30`, `大変動開始日` が `60` だと
秋の1日目にゲームが始まる。
`季節の長さ` が `30` のときに春スタートにしたい場合は、
`大変動開始日` を `20` などと変更する。

* 初期設定: `60`
* 値範囲:
    * 最小: `-1`
    * 最大: `999`

#### 季節の長さ
1季節の長さを変更できる。
おそらく、1季節が91日というデフォルトの設定は、
現実世界の1年(365日)に近づけるためだと思う。
長すぎるので、`14` から `60` の間ぐらいに変更をするといい。

* 初期設定: `91`
* 値範囲:
    * 最小: `14`
    * 最大: `127`

## フォント設定
フォントの設定ファイルは `config/fonts.json` にある｡
外部フォントも利用可能。

* [フォント設定](fonts/CONFIG.md)

## 外部リンク

* [Cataclysm:DDA 日本語Wiki](https://w.atwiki.jp/cataclyj/)
* [Hitchhiker's Guide to the Cataclysm](https://nornagon.github.io/cdda-guide/)
* [公式Webページ(英語)](https://cataclysmdda.org/)
* [フォーラム(英語)](https://discourse.cataclysmdda.org/)
* [英語wiki](http://cddawiki.chezzo.com/cdda_wiki/index.php/Main_Page)
* [Githubリポジトリ](https://github.com/CleverRaven/Cataclysm-DDA)
* [英語公式Discord](https://discord.gg/jFEc7Yp)
