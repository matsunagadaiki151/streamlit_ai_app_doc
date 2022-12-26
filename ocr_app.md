---
title: "(WIP)Streamlitで文字検出アプリを作る"
date: "2022-12-25"
lastmod: "2022-12-25"
---

{% if page.lastmod %}
  {% assign lastmod = page.lastmod %}
{% else %}
  {% assign lastmod = page.date %}
{% endif %}

<span class="date">最終更新日:{{ lastmod }}</span>
※この記事は執筆中です。

Vision AIをとstreamlitを組み合わせて、簡単な文字認識アプリを作っていきます。

### 完成画面

### 手順
1. Dockerfileの設定
コンテナ起動時にstreamlitが起動し、ローカルホストからアプリを実行できるようにします。具体的には、以下のように編集しなおします。

2. ソースコードの作成
`app.py`の中身を以下のように変更します。

3. Dockerコンテナの起動
まず、``でDockerをビルドした後、以下のコマンドで、コンテナを起動します。

### 完成!!
完成品と同じ画面になるはずです。自分の持っている文字付きの画像をアップロードしてうまく動くか確かめて見ましょう。

### 挙動がおかしい場合は
- ソースコードを見直してください。特に、Pythonはインデントが合っていないとエラーが発生するため、注意してください。
- streamlitのバージョンを確認してください。


[目次に戻る](./index.md)