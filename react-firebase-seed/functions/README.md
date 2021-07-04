# seed start

```bash
$node lib/commands/dbseed.js [ドキュメント名] seeds/[tsvファイル名]
```

## example

```bash
$node lib/commands/dbseed.js publishers seeds/publishers.tsv
```

## 注意
vscodeでfunctionディレクトリを起点に開いてください。

## ドキュメント削除

「Firestore はコレクション＞ドキュメント＞コレクション＞ドキュメント＞…と親子階層を持てるよ うになってるんだけど、普通に親ドキュメントを削除しただけでは、その子コレクション（サブコレ クション）は残ってしまうのね。親子まとめて削除するためには -r,--recursive オプションを指定 してあげる。あと Firestore 内の全てのコレクションとドキュメントをまとめて削除したいときは --all-collections を指定。

## vscode 色設定

(URL)[https://zenn.dev/hkawasaki/articles/baca58035c9e7c]

## クローラー設定

コミックスの新刊情報を取得して、適切な形でデータベースに格納する作業が発生する。
それをやる関数を作成

Nodeでは外部サイトのクリーリングをする場合はPuppeteerが主流

## Puppeteerとは

Puppeteerは、Headless Chromeを操作できるNode.jsのライブラリです。Chrome DevToolsチームがメンテナンスを行なっており、スクレイピングやフロントテストに活用できます。ここでは、Puppeteerの基本的な使い方を確認します。

ヘッドレスブラウザとは？
GUIを持たないブラウザ

※PuppeteerをインストールするとChromiumを同時にダウンロードされる。

```bash
$yarn add puppeteer lodash node-fetch date-fns date-fns-timezone
$typesync
```

## 次やること

puppeteerをインストールするのにnode 10.18以上が必要10.17。このプロジェクト
