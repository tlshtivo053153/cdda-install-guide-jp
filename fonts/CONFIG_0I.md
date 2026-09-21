# フォント設定(0.I-1以後)

## ゲームオプション
`[タイトル画面]->[設定]->[オプション]->[表示]` からフォントのサイズなどを変更できる。
フォントの設定を反映するためには、ゲームの再起動が必要なので注意。

### フォント/表示調整
`True` にするとアンチエイリアスという処理によって、文字のギザギザをなめらかにする。
フォントのサイズを大きくする場合は `True` にすると良い。

### フォント/横幅, 縦幅, サイズ
通常のフォント設定。

### マップフォント/横幅, 縦幅, サイズ
戦闘アニメーションのテキストで用いるフォント設定。

### 全体マップフォント/横幅, 縦幅, サイズ
全体マップのフォント設定。

### 文字切れが発生する場合
導入したフォントによっては文字切れが発生して見にくくなる。

![string example](https://raw.githubusercontent.com/tlshtivo053153/cdda-install-guide-jp/images/stringExample.png)

文字切れが発生している場合は、フォントの横幅や縦幅の値を大きくする。
フォントの横幅・縦幅を適切な値に設定したら、サイズを見やすい大きさに変更する。
横幅・縦幅・サイズの比があまり変わらないように変更するときれいになる。
例えば、元々の値が 8,19,16 の場合は 10,24,20 や 12,29,24 などとする。

## `config/fonts.json`
フォントの設定ファイルは `config/fonts.json` にある。
存在しない場合は、ゲーム起動時に自動生成される。
以下が、デフォルトの設定である。

```json
{
  "//": "See docs/user-guides/FONT_OPTIONS.md for an explanation of this file.",
  "typeface": [ { "path": "data/font/Terminus.ttf", "hinting": "Bitmap" }, { "path": "data/font/unifont.ttf", "hinting": "Default" } ],
  "gui_typeface": [ { "path": "data/font/Terminus.ttf", "hinting": "Bitmap" }, { "path": "data/font/unifont.ttf", "hinting": "Default" } ],
  "map_typeface": [ { "path": "data/font/Terminus.ttf", "hinting": "Bitmap" }, { "path": "data/font/unifont.ttf", "hinting": "Default" } ],
  "overmap_typeface": [ { "path": "data/font/Terminus.ttf", "hinting": "Bitmap" }, { "path": "data/font/unifont.ttf", "hinting": "Default" } ]
}
```

コメントに書いてあるドキュメントのパスは間違っていて、`docs/` ではなく、`doc/` なので注意。

* `"typeface"` は通常のテキストのフォント設定
* `"gui_typeface"` はImGuiのテキストのフォント設定
* `"map_typeface"` は戦闘アニメーションのテキストのフォント設定
* `"overmap_typeface"` は全体マップのフォント設定

* `Terminus.ttf` はアルファベット文字などのフォントファイル
* `unifont.ttf` は日本語や全角記号を含んだフォントファイル

各設定の `[]` で囲まれたフォントの優先順位は、先に書いてあるものが高い。
具体例を挙げて説明する。
文字 `a` をゲーム内で表示するときは、先に書いてある `"Terminus.ttf"` を使用する。
一方、文字 `あ` を表示するときは、`"Terminus.ttf"` に文字 `あ` がないので
`"unifont.ttf"` を使用する。

フォントのパスはどこでも良い。
`font/フォント.ttf` などと配置するとわかりやすいと思う。

hinting については、doc/user-guides/FONT_OPTIONS.md を参照。

### 1種類のフォントで置き換える方法
`font/日本語.ttf` で置き換える。

```json
{
  "typeface": [ { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "gui_typeface": [ { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "map_typeface": [ { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "overmap_typeface": [ { "path": "font/日本語.ttf", "hinting": "Default" } ]
}
```

次の記述も同等。

```json
{
  "typeface": [ { "path": "font/日本語.ttf" } ],
  "gui_typeface": [ { "path": "font/日本語.ttf" } ],
  "map_typeface": [ { "path": "font/日本語.ttf" } ],
  "overmap_typeface": [ { "path": "font/日本語.ttf" } ]
}
```

この記述も同等。

```json
{
  "typeface": "font/日本語.ttf",
  "gui_typeface": "font/日本語.ttf",
  "map_typeface": "font/日本語.ttf",
  "overmap_typeface": "font/日本語.ttf"
}
```

### 2種類のフォントで置き換える方法
`font/アルファベット.ttf`, `font/日本語.ttf` にあるフォントで置き換える。

```json
{
  "typeface": [ { "path": "font/アルファベット.ttf", "hinting": "Default" }, { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "gui_typeface": [ { "path": "font/アルファベット.ttf", "hinting": "Default" }, { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "map_typeface": [ { "path": "font/アルファベット.ttf", "hinting": "Default" }, { "path": "font/日本語.ttf", "hinting": "Default" } ],
  "overmap_typeface": [ { "path": "font/アルファベット.ttf", "hinting": "Default" }, { "path": "font/日本語.ttf", "hinting": "Default" } ]
}
```

次の記述も同等。

```json
{
  "typeface": [ { "path": "font/アルファベット.ttf" }, { "path": "font/日本語.ttf" } ],
  "gui_typeface": [ { "path": "font/アルファベット.ttf" }, { "path": "font/日本語.ttf" } ],
  "map_typeface": [ { "path": "font/アルファベット.ttf" }, { "path": "font/日本語.ttf" } ],
  "overmap_typeface": [ { "path": "font/アルファベット.ttf" }, { "path": "font/日本語.ttf" } ]
}
```

### 3種類のフォントで置き換える方法
`font/日本語1.ttf`, `font/日本語2.ttf`, `font/日本語3.ttf`
にあるフォントで置き換える。

```json
{
  "typeface": [ { "path": "font/日本語1.ttf", "hinting": "Default" }, { "path": "font/日本語2.ttf", "hinting": "Default" }, { "path": "font/日本語3.ttf", "hinting": "Default" } ],
  "gui_typeface": [ { "path": "font/日本語1.ttf", "hinting": "Default" }, { "path": "font/日本語2.ttf", "hinting": "Default" }, { "path": "font/日本語3.ttf", "hinting": "Default" } ],
  "map_typeface": [ { "path": "font/日本語1.ttf", "hinting": "Default" }, { "path": "font/日本語2.ttf", "hinting": "Default" }, { "path": "font/日本語3.ttf", "hinting": "Default" } ],
  "overmap_typeface": [ { "path": "font/日本語1.ttf", "hinting": "Default" }, { "path": "font/日本語2.ttf", "hinting": "Default" }, { "path": "font/日本語3.ttf", "hinting": "Default" } ]
}
```

次の記述も同等。

```json
{
  "typeface": [ { "path": "font/日本語1.ttf" }, { "path": "font/日本語2.ttf" }, { "path": "font/日本語3.ttf" } ],
  "gui_typeface": [ { "path": "font/日本語1.ttf" }, { "path": "font/日本語2.ttf" }, { "path": "font/日本語3.ttf" } ],
  "map_typeface": [ { "path": "font/日本語1.ttf" }, { "path": "font/日本語2.ttf" }, { "path": "font/日本語3.ttf" } ],
  "overmap_typeface": [ { "path": "font/日本語1.ttf" }, { "path": "font/日本語2.ttf" }, { "path": "font/日本語3.ttf" } ]
}
```

## フォントの探し方
自分でフォントを探す場合は、
「フォント フリー」「フォント ゲーム」「フォント プログラミング」
などのワードで検索すると良い。
フリーフォントでも、商用利用できないものもあるので、
確認しておく。

* 半角のバックスラッシュに対応しているものだと見栄えがいい
* 等幅フォントを選ぶ
    * 等幅フォント(Monospaced font)は、フォント名に mono や m と書いてあるものが多い
    * 可変幅フォント(Proportional font)を使うとアルファベットの部分が乱れる。使わない方が良い

### 日本語フォント例

* [Ricty Diminished](https://github.com/edihbrandon/RictyDiminished)
    * プログラミング向けフォント
    * 全角スペースが可視化
* [Mgen+](https://jikasei.me/font/mgenplus/)
    * JIS第1〜4水準すべてを含む
* [HackGen](https://github.com/yuru7/HackGen)
* [PlemolJP](https://github.com/yuru7/PlemolJP)
* [UDEVGothic](https://github.com/yuru7/udev-gothic)

#### 上記のRicty Diminished と Mgen+ を使った例
フォントを `font/RictyDiminished-Bold.ttf`, `font/mgenplus-1m-bold.ttf`
に配置した設定ファイルの例。
プログラミング向けフォントの `Ricty Diminished` は、対応していない漢字
があるかもしれない。
そのため、対応している漢字の多い `Mgen+` と併用する。

```json
{
  "typeface": [ { "path": "font/RictyDiminished-Bold.ttf", "hinting": "Default" }, { "path": "font/mgenplus-1m-bold.ttf", "hinting": "Default" } ],
  "gui_typeface": [ { "path": "font/RictyDiminished-Bold.ttf", "hinting": "Default" }, { "path": "font/mgenplus-1m-bold.ttf", "hinting": "Default" } ],
  "map_typeface": [ { "path": "font/RictyDiminished-Bold.ttf", "hinting": "Default" }, { "path": "font/mgenplus-1m-bold.ttf", "hinting": "Default" } ],
  "overmap_typeface": [ { "path": "font/RictyDiminished-Bold.ttf", "hinting": "Default" }, { "path": "font/mgenplus-1m-bold.ttf", "hinting": "Default" } ]
}
```

次の記述も同等。

```json
{
  "typeface": [ { "path": "font/RictyDiminished-Bold.ttf" }, { "path": "font/mgenplus-1m-bold.ttf" } ],
  "gui_typeface": [ { "path": "font/RictyDiminished-Bold.ttf" }, { "path": "font/mgenplus-1m-bold.ttf" } ],
  "map_typeface": [ { "path": "font/RictyDiminished-Bold.ttf" }, { "path": "font/mgenplus-1m-bold.ttf" } ],
  "overmap_typeface": [ { "path": "font/RictyDiminished-Bold.ttf" }, { "path": "font/mgenplus-1m-bold.ttf" } ]
}
```
