# start up

```bash
$cd react-firebase-seed
$yarn start
```

## node version

・Cloud Function(サーバーレス)の関数実行環境を使用するために
まだ最新12系に対応していないため10系で対応する　。

```bash
$nodenv install 12.13.1
$nodenv install 10.17.0
```

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
