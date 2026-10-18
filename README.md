# Kakei Note

予算と実績・貯金目標・月別比較ができる家計簿アプリ。入力内容はお使いのブラウザにだけ保存されます。

## 構成

| ファイル | 役割 |
| --- | --- |
| `index.html` | アプリ本体（CSS・JavaScript・アイコンを含む1ファイル） |
| `sw.js` | オフラインで開くための Service Worker |
| `404.html` | 存在しないURLを開いたときに、トップへ戻す |
| `.nojekyll` | GitHub Pages の Jekyll 処理をオフにする |

## GitHub Pages で公開する手順

1. GitHub で新しいリポジトリを作る（例：`kakei-note`）。
2. このフォルダの中身（`.nojekyll` を含む全ファイル）を、リポジトリの直下にアップロードする。
3. リポジトリの **Settings → Pages** を開く。
4. **Build and deployment** の Source を **Deploy from a branch** にし、Branch を `main`、フォルダを `/ (root)` にして **Save**。
5. 1〜2分ほどで `https://<ユーザー名>.github.io/kakei-note/` に公開される。

## 公開後に確認すること

- **ログイン機能（Firebase）を使う場合**：Firebase コンソールの **Authentication → Settings → 承認済みドメイン** に `<ユーザー名>.github.io` を追加する。追加しないと、公開先でログインできません。
- **Firebase の設定値**：`index.html` 内の `FIREBASE_CONFIG` は公開されます。Web 用の設定値は公開前提のものですが、Firestore のセキュリティルールで、本人のデータだけ読み書きできるようにしておいてください。
- **更新したとき**：`index.html` を差し替えてコミットするだけです。`sw.js` はネットワーク優先なので、通常は次に開いたときに新しい版になります。
- **データの保存先**：ブラウザの保存領域（localStorage）です。ブラウザやURLが変わると、データは引き継がれません。公開URLを変える前に、アプリ内のバックアップを取ってください。
