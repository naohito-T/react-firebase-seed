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
