# blogview-template

blogview と gimonfu を使ったブログ執筆用テンプレート

## 使い方

1. [Use this template](https://github.com/mkizka/blogview-template/generate) からこのリポジトリを複製
2. `yarn`などして依存ライブラリをインストール
3. .gimonfu.json を [gimonfu](https://github.com/yammerjp/gimonfu) のドキュメントに従って設定
4. `yarn pull`などして既存の記事をダウンロード
5. 記事を編集して`yarn push`で投稿

## 新規記事を追加する

例えば Ubuntu 環境であれば、以下のようなシェルスクリプトが使えます。

```sh
#!/bin/sh
NAME=`cat /dev/urandom | tr -dc 'a-f0-9' | fold -w 10 | head -n 1`
echo "---
title: 新規投稿
categories:
  - 雑記
draft: true
---
" > ./entry/"$NAME".md
pnpm push
```

## GitHub Actions から記事を自動投稿する

1. gimonfu.json の内容を`GIMONFU_JSON`という名前で GitHub の Secrets に登録
2. `.github/workflows`以下にある`push.yml.example`を`push.yml`にリネーム
3. `push.yml`をコミットしてプッシュ
