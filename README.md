# start up

次やること。puppeteerをインストールする 10.18以上でfunction/配下
## node version

nodeのversionは固定している。
package.jsonでyarnを固定および.npmrcでnpmでも固定。

```bash
$node -v
v12.13.1
```

```bash
$cd react-firebase-seed
$yarn start
```
## node version

・Cloud Function(サーバーレス)の関数実行環境を使用するために
・まだ最新12系に対応していないため10系で対応する。

```bash
$nodenv install 12.13.1
$nodenv install 10.17.0
```

node.jsのライブラリ運用手順
[URL](https://dev.classmethod.jp/articles/strategies-node-project/)

node version固定
[URL](https://qiita.com/suin/items/994458418c737cc9c3e8)

## 手順

## create-react-app

・create-react-appでTypeScript対応のを作る

```bash
$npx create-react-app react-firebase-seed --typescript // tsconfigなどが作成されないためNG
$npx create-react-app react-firebase-seed  --template typescript // tsconfig作成される
```

## tsconfig.json修正

以下を追加
incremental オプションを有効にすると再コンパイルがぐっと早くなる。
CRAでは開発環境サーバはホットリロードが有効になっているが、その時間が短縮されるため設定しておくとよい。

```json
"baseUrl": "src",
"incremental": true
"exclude": ["node_modules", "build", "script", "functions"]
```

## Lint Prettier設定

書籍 booth typescript firebase参照
こちらも参照
[URL](https://zenn.dev/yhay81/articles/def73cf8a02864)

```bash
$yarn add -D stylelint prettier

$yarn add -D eslint-plugin-react eslint-plugin-react-hooks eslint-plugin-import eslint-plugin-jest

$yarn add -D @typescript-eslint/parser @typescript-eslint/eslint-plugin

$yarn add -D stylelint-config-prettier stylelint-config-standard stylelint-order

$yarn add -D stylelint-config-styled-components stylelint-processor-styled-components

$yarn add -D prettier-stylelint

$touch .eslintrc.js

$touch .eslintignore

$touch stylelint.config.js

$vi .gitignore

```

## typesync install

・package.jsonの中身を調べて、必要なTypeScriptの型ファイルがなければ自動でdevDependenciesに追加してくれる

```bash
$npm install -g typesync
typesync後yarnを実行すれば自動で実行してくれる
$typesync
$yarn


```

## husky lint-staged setup
lint-stagedとhuskyを使い、git commitのタイミングでeslintによるチェックを実施し、エラーだったらコミットさせない設定をする。
husky@4 versio4でないと動かないためhusky ver4を導入

```bash
$yarn add -D husky@4 lint-staged

```

以下を追加

```json
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "src/**/*.{js,jsx,ts,tsx}": [
      "eslint --fix './src/**/*.{js,jsx,ts,tsx}'",
      "prettier --write ."
    ],
    "src/**/*.{css,jsx,tsx}": [
      "stylelint --fix",
      "prettier --write ."
    ],
    "function/src/**/*.{js,ts}": [
      "cd function/ && eslint --fix",
      "prettier --write ."
    ]
```

## sort-package.json

・package.jsonのsortをしてくれるpackageをinstall

```bash
$yarn add -D sort-package-json
```

## firebase setup

```bash
$npm install -g firebase-tools

$exec $SHELL -l

$firebase login

ブラウザ上で作成したfirebaseアプリを元に初期化をしていく。
cloud Firestoreも作成しておくこと。
asia-northeast1 東京
asia-northeast2 大阪

firebase initで選択したもの
$firebase init
 ◉ Firestore: Configure security rules and indexes files for Firestore
 ◉ Functions: Configure a Cloud Functions directory and its files
❯◉ Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys

? Please select an option:
❯ Use an existing project 選択
  Create a new project
  Add Firebase to an existing Google Cloud Platform project
  Don't set up a default project


```

## firebase build

```bash
$yarn build

$firebase deploy --only hosting
```

## firebase Hostingへのデプロイ

デプロイは今すぐ行うことも、後で行うこともできます。今すぐデプロイするには、ターミナル ウィンドウを開き、ウェブアプリのルート ディレクトリに移動するか、ルート ディレクトリを作成します。

Google へのログイン

```bash
$firebase login
```

プロジェクトの開始
このコマンドはアプリのルート ディレクトリから実行してください:

```bash
$firebase init
```

準備ができたらウェブアプリをデプロイ
静的ファイル（HTML、CSS、JS など）をアプリのデプロイ ディレクトリ（デフォルトは「public」）に配置します。続いて、アプリのルート ディレクトリで次のコマンドを実行します:

```bash
$firebase deploy
```

デプロイ後、アプリを magazin-app-demo.web.app で表示します。


## firebase cloud functionディレクトリセットアップ

```bash
$nodenv local 10.17.0

package.jsonを10にする

$yarn install

```

tsconfig設定変更

## test環境構築

```bash
$yarn add -D jest ts-jest @types/jest
```

## lint setup

```bash
$yarn add -D eslint prettier
$yarn add -D eslint-plugin-import eslint-plugin-jest eslint-plugin-prefer-arrow eslint-plugin-prettier eslint-config-prettier eslint-config-airbnb-base
$yarn add -D @typescript-eslint/parser @typescript-eslint/eslint-plugin
$typesync
$yarn
```

## firestore seed setup

seedスクリプトはFirebaseのAdmin SDKを使うため、その認証のために秘密鍵が必要になる。

Nodeでコマンドラインインターフェースを実現してくれるライブラリでCommander.jsが一番メジャー

```bash
$yarn add firebase commander csv-parse

$yarn add -D @types/node
```
