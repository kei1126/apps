# 公開手順（GitHub Pages）

App Store Connect の **プライバシーポリシー URL** と **サポート URL** に入れるページ。

## 1. 先に 3 か所だけ書き換える

`REPLACE_WITH_YOUR_EMAIL` を実際の連絡先メールアドレスに置き換えてください。3 ファイルに入っています。

```
index.html
doubt/index.html
doubt/support/index.html
```

公開ページに載るアドレスなので、普段使いのものを出したくなければ、
このアプリ用にフリーメールを 1 つ作るのが無難です。
App Store Connect は連絡が取れるアドレスを求めるので、空欄では出せません。

## 2. リポジトリを作って上げる

GitHub で **public** のリポジトリを 1 つ作ります（例：`apps`）。
private だと GitHub Pages が無料プランでは公開されません。

```bash
cd <このフォルダ>
git init
git add .
git commit -m "Add privacy policy and support pages"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/apps.git
git push -u origin main
```

## 3. Pages を有効にする

リポジトリの **Settings → Pages** で

- Source: `Deploy from a branch`
- Branch: `main` / `/ (root)`

保存してから 1〜2 分で公開されます。

## 4. できあがる URL

```
https://<ユーザー名>.github.io/apps/                     一覧
https://<ユーザー名>.github.io/apps/doubt/               プライバシーポリシー
https://<ユーザー名>.github.io/apps/doubt/support/       サポート
```

App Store Connect にはこう入れます。

| 欄 | URL |
|---|---|
| プライバシーポリシー URL | `https://<ユーザー名>.github.io/apps/doubt/` |
| サポート URL | `https://<ユーザー名>.github.io/apps/doubt/support/` |

**提出前に、その URL をブラウザで実際に開いて確認してください。**
開けない URL を入れると審査で確実に差し戻されます。

## 5. 神経衰弱を足すとき

`doubt/` をまるごとコピーして `shinkeisuijaku/` にし、中身を書き換えて
`index.html` のアプリ一覧にリンクを 1 行足すだけです。

## 中身について

- ページは日本語と英語を縦に並べてあります。App Store Connect はどちらの言語でも同じ URL で構いません
- ダークモードに対応しています（端末の設定に追従）
- アクセス解析も Cookie も入れていません。プライバシーポリシーのページ自体が
  トラッキングしていると、それはそれで矛盾するので
- 広告の記述は Unity LevelPlay（ironSource）前提です。別の広告 SDK に替えたら書き直してください
