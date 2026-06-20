# ポケモンタイピングゲーム 仕様書

## 1. 概要

8歳の子供向けに、ローマ字入力とタイピングを同時に学べるポケモンテーマのゲーム。
画面に表示されたポケモンの名前をローマ字でキーボード入力し、正解すると「ゲット」できる。

- **対象**: 8歳・タイピング初心者・ローマ字未習得
- **動作環境**: HTML/CSS/JavaScript（単一ファイル推奨）、iPad + Bluetoothキーボード + ブラウザ
- **開発環境**: Cursor

---

## 2. 基本フロー

1. ポケモンの画像が表示される
2. ローマ字のヒントが画面に表示される（最初は常時フル表示）
3. 子供がキーボードでローマ字を入力する
4. 1文字ずつ入力するたびに、その文字が緑色などでハイライトされる
5. 全部正解したら「ゲット演出」→ 図鑑/進捗に反映
6. 次のポケモンへ進む

---

## 3. ゲームモード（2種類）

### モード①: 図鑑コンプリートモード
- 最初は **1体だけ** 登場。順番または自由に選んで練習
- 各ポケモンを**50回入力**したら「マスター」として図鑑に記録
- **マスターするたびに、新しいポケモンが1体ずつ登場**（リスト順）
- 未登場のポケモンは図鑑で 🔒 表示（シルエット / ???）
- 進捗バー（例: ピカチュウ 32/50）を表示
- 全ポケモンをマスターで図鑑コンプリート！
- **31体目以降の追加キャラ**は今後検討（解放リストに追加する想定）

### モード②: ステージクリアモード
- **解放済み**のポケモンからランダムに**10体**を連続で入力
- タイマーまたは入力数でスコア化（任意: 速度や正確さでスター評価）
- 10体終わったら「ステージクリア！」演出
- 何度でもリトライ可能（毎回ランダムな10体）

---

## 4. 入力・ヒント仕様

- **ヒント表示**: 常にローマ字フル表示（今回は非表示モードは実装しない）
- **入力判定**: 1文字ずつ判定し、正しい文字を入力するごとに色を変える（例: グレー→緑）
- **ミス入力時**: 軽い視覚フィードバック（赤くフラッシュ等）。次の文字に進めず、正しいキーを押すまで待つ
- **大文字小文字**: 区別しない（すべて小文字として判定）
- **促音・長音など特殊表記の統一ルール**:
  - 日本語の長音記号 **「ー」** には、同じ位置に **`-`（ハイフン）** を置く（例: イーブイ → I-BUI、ミュウツー → MYUUTSU-）
  - 「ー」がない長い母音は **母音を重ねる**（例: ピカチュウ → PIKACHUU、ミュウ → MYUU）
  - 促音（っ）は次の子音を重ねる（例: ポッポ → POPPO）
  - 小さい仮名（ァィゥェォ等）は **`X` + 母音** で表す（例: ディ → DEXI、シィ → SHIXI）
  - 語末の「ん」は **`NN`** で表す（例: カビゴン → KABIGONN、ロコン → ROKONN）
  - 語中の「ん」（次の文字が子音・母音で続く場合）は **`N`** 1文字（例: マンキー → MANKI-、ゼニガメ → ZENIGAME）
  - 「ー」＋語末の「ん」が続く場合は **`-` + `NN`**（例: コクーン → KOKU-NN）

---

## 5. ポケモン収録リスト（30体・第1世代中心）

キーボードの様々なキーをバランスよく練習できるよう選定。

| # | 図鑑No | 名前（日本語） | ローマ字 | PokeAPI画像URL |
|---|---|---|---|---|
| 1 | 1 | フシギダネ | HUSHIGIDANE | sprites/pokemon/1.png |
| 2 | 4 | ヒトカゲ | HITOKAGE | sprites/pokemon/4.png |
| 3 | 7 | ゼニガメ | ZENIGAME | sprites/pokemon/7.png |
| 4 | 10 | キャタピー | KYATAPI- | sprites/pokemon/10.png |
| 5 | 11 | コクーン | KOKU-NN | sprites/pokemon/11.png |
| 6 | 13 | ビードル | BI-DORU | sprites/pokemon/13.png |
| 7 | 16 | ポッポ | POPPO | sprites/pokemon/16.png |
| 8 | 19 | コラッタ | KORATTA | sprites/pokemon/19.png |
| 9 | 21 | オニスズメ | ONISUZUME | sprites/pokemon/21.png |
| 10 | 23 | アーボ | A-BO | sprites/pokemon/23.png |
| 11 | 25 | ピカチュウ | PIKACHUU | sprites/pokemon/25.png |
| 12 | 27 | サンド | SANDO | sprites/pokemon/27.png |
| 13 | 35 | ピッピ | PIPPI | sprites/pokemon/35.png |
| 14 | 37 | ロコン | ROKONN | sprites/pokemon/37.png |
| 15 | 39 | プリン | PURINN | sprites/pokemon/39.png |
| 16 | 41 | ズバット | ZUBATTO | sprites/pokemon/41.png |
| 17 | 52 | ニャース | NYA-SU | sprites/pokemon/52.png |
| 18 | 54 | コダック | KODAKKU | sprites/pokemon/54.png |
| 19 | 56 | マンキー | MANKI- | sprites/pokemon/56.png |
| 20 | 58 | ガーディ | GA-DEXI | sprites/pokemon/58.png |
| 21 | 63 | ケーシィ | KE-SHIXI | sprites/pokemon/63.png |
| 22 | 66 | ワンリキー | WANRIKI- | sprites/pokemon/66.png |
| 23 | 74 | イシツブテ | ISHITSUBUTE | sprites/pokemon/74.png |
| 24 | 129 | コイキング | KOIKINGU | sprites/pokemon/129.png |
| 25 | 131 | ラプラス | RAPURASU | sprites/pokemon/131.png |
| 26 | 133 | イーブイ | I-BUI | sprites/pokemon/133.png |
| 27 | 143 | カビゴン | KABIGONN | sprites/pokemon/143.png |
| 28 | 147 | ミニリュウ | MINIRYUU | sprites/pokemon/147.png |
| 29 | 150 | ミュウツー | MYUUTSU- | sprites/pokemon/150.png |
| 30 | 151 | ミュウ | MYUU | sprites/pokemon/151.png |

画像URLは以下のベースに番号を足して使用:
`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/{図鑑No}.png`

※ お子さんと相談して、好きなポケモンに入れ替え・追加してOK（図鑑Noさえ分かれば画像はそのまま使える）。

---

## 6. 画面構成（案）

### トップ画面
- 「図鑑コンプリートモード」「ステージクリアモード」の2つのボタン

### 図鑑コンプリートモード画面
- ポケモン選択（図鑑一覧から選ぶ、または順番に出題）
- メイン画面: ポケモン画像＋ローマ字ヒント＋入力中の文字列表示＋進捗（n/50）

### ステージクリアモード画面
- 現在何匹目か（例: 3/10）表示
- ポケモン画像＋ローマ字ヒント＋入力表示
- クリア後にリザルト画面（タイム、ミス数など任意）

---

## 7. データ構造（実装イメージ）

```javascript
const pokemonList = [
  { dexNo: 1, name: "フシギダネ", romaji: "HUSHIGIDANE" },
  { dexNo: 4, name: "ヒトカゲ", romaji: "HITOKAGE" },
  { dexNo: 133, name: "イーブイ", romaji: "I-BUI" },
  { dexNo: 143, name: "カビゴン", romaji: "KABIGONN" },
  // ... 以下30体
];

// 図鑑コンプ進捗の保存イメージ（React state や localStorage相当）
const progress = {
  1: { count: 0, mastered: false },
  4: { count: 0, mastered: false },
  // ...
};

// 解放済みポケモン（localStorage）
const unlocked = [1]; // 最初は1体のみ。マスターごとに1体追加
```

画像URL生成関数:
```javascript
function getSpriteUrl(dexNo) {
  return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${dexNo}.png`;
}
```

---

## 8. 技術仕様

- **形式**: 単一HTMLファイル（CSS/JS同梱）でCursor上で開発・iPad Safariで動作確認
- **画像取得**: PokeAPIのスプライト画像をURL直接参照（ネット接続必要）
- **状態管理**: シンプルなJavaScript変数 or localStorageで進捗保存（再訪問時も継続できると良い）
- **入力デバイス想定**: Bluetoothキーボード（物理キー入力をkeydownイベントで取得。`-` キーも入力可能）
- **レスポンシブ**: iPad画面サイズ（横向き想定）に最適化

---

## 9. 今後の拡張アイデア（今回は実装しない・メモ）

- ヒントを徐々に隠す難易度調整
- タイピング速度のグラフ表示
- 効果音・BGM
- 自作イラストへの差し替え
- 第2世代以降のポケモン追加
