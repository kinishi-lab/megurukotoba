# めぐることば —答えは循環の中に—

AIジャーナリングのまとめ（Markdown）から「今日の小さな宣言」だけを拾い、
一枚ずつのことばカードにして、月ごとの輪でめぐるアプリ。

## ファイル構成

- `index.html` … アプリ本体。**これ1枚だけで動きます**（ビルド不要）
- `icon-192.png` / `icon-512.png` / `apple-touch-icon.png` / `icon-1024.png` … アプリアイコン
- `manifest.json` … ホーム画面追加用の設定（iOS/Android両対応）
- `src/App.jsx` … 開発用のソース（index.html内のスクリプトと同一内容）
- `README.md` … このファイル

React 18 と Babel を CDN から読み込む方式なので、npm install も build も不要です。

## ローカルで動かす

`index.html` をブラウザで開くだけ。
（Googleフォント・React CDNを使うため、ネット接続は必要です）

## GitHub Pages に公開する手順

1. GitHub（kinishi-lab）で新しいリポジトリを作る（例：`meguru-kotoba`）
2. `index.html` と `README.md` をリポジトリ直下にアップロード
3. リポジトリの **Settings → Pages** を開く
4. Source を **Deploy from a branch**、Branch を **main / (root)** にして Save
5. 数分後、`https://kinishi-lab.github.io/meguru-kotoba/` で公開されます

## データの保存について

- 保存先はブラウザの **localStorage**（キー: `meguru_kotoba_v1`）
- 同じ端末・同じブラウザなら、開き直してもデータは残ります
- 端末をまたぐ引っ越しは、アプリ内「保存」タブの
  バックアップ（コピー&ペースト方式）を使ってください

## Codex / AIコーディングツールに渡す時のメモ

- アプリ本体は `index.html` 内の `<script type="text/babel">` ブロック、
  または同一内容の `src/App.jsx`（こちらを編集して index.html に反映する運用を推奨）
- 単一コンポーネント `App` 構成。主なセクション：
  - `parseEntries()` … Markdownから日付・Day数・状態・宣言・全文を抽出
  - `CardFace` … トレカ比率（63:88）の縦書きカード。半角英数は `toTate()` で全角化
  - ことばの輪 … `WHEEL_R` / `WHEEL_STEP` で円の半径とカード間隔を調整
  - 月の輪 … `months` / `month` state。「★ベストの輪」は全期間の★のみ
  - 保存タブ … バックアップの書き出し/復元（クリップボード方式）と全消し（確認あり）
- デザイン規約：Soft Cocoon パレット（`C` オブジェクト）、Zen Maru Gothic、
  低刺激・余白多め。**AIによる分析コメントは出さない**（思想：決めるのは私）
- 変更時の注意：宣言カードの文言・思想（評価しない/急かさない/選ぶのは本人）を壊さないこと

