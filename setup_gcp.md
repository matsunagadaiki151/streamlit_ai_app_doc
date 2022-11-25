---
title: "Cloud Vision APIのセットアップ手順"
date: "2022-10-23"
lastmod: "2022-11-25"
---

{% if page.lastmod %}
  {% assign lastmod = page.lastmod %}
{% else %}
  {% assign lastmod = page.date %}
{% endif %}

<span class="date">最終更新日:{{ lastmod }}</span>

ここではPythonからVision APIを呼び出す手順を解説していきます。

### 必要なもの
- Googleアカウント
- クレジットカード

### セットアップ手順
基本的には、Google公式ドキュメント「[クライアント ライブラリを使用して画像内のラベルを検出する](https://cloud.google.com/vision/docs/detect-labels-image-client-libraries?hl=ja)」の手順を踏んでいけば良いです。

ただし、今回はDocker環境で動作させるため、実施手順を少し変更します。(conda環境でやる場合は手順通り実施すれば良いです。)

1. 「[クライアント ライブラリを使用して画像内のラベルを検出する](https://cloud.google.com/vision/docs/detect-labels-image-client-libraries?hl=ja)」の「始める前に」の項目をすべて実施します。この時の要点を以下に軽く記載します。
   - プロジェクトの作成
     - プロジェクト名はわかりやすい名前にする。(今回は、「streamlit-ai-app」)とする。
     - 「組織なし」でOK 
   - サービスアカウントの作成
     - 名前は分かりやすい名前とする。(今回は、「streamlit-ai-app-{好きな文字列}」とする。)
     - JSONファイルのダウンロード先は、本プロジェクト内ではない、ディレクトリに置くと良い。もし、本プロジェクトに置く場合は、`.dockerignore`ファイルを作成する必要がある。
     - ダウンロードしたJSONファイルは絶対に他人には見せない。
   - 環境変数の設定
     - Windowの場合、「環境変数を編集」を使用して設定するとよい。
     - MacやLinuxの場合、export文を実行した後、`source ~/.bashrc`(もしくは`source ~/.zshrc`)を実行する必要がある。

2. (推奨)[Google Cloudの料金アラート設定について](./gcp_cost_monitoring.md)より特定の請求金額に達した場合、Eメールに通知されるような設定を行う。

3.  `src`フォルダに`visionapi_test.py`を作成し、ファイル内に「ラベル検出」の項目に掲載されている、Pythonスクリプトを貼り付ける。
   
   <font color="Red">**11月25日追記**</font>  
   現在、wakeupcat.jpgをダウンロードできないようです。
   そのため、この例では[いらすとやの画像](https://4.bp.blogspot.com/-gX99oMun4bM/U9y_wYoE0EI/AAAAAAAAjiU/DHdcIfImCwQ/s800/pose_ganbarou_man.png)で代用します。

   これに伴い、ソースコードの以下の箇所を修正してください。
   ```
   file_name = os.path.abspath('resources/wakeupcat.jpg')
   file_name = os.path.abspath('resources/pose_ganbarou_man.png')
   ```

4. Dockerfileを以下のように書き換える。  
   
   <font color="Red">**11月25日追記**</font>  
   上記修正に伴い、こちらも修正します。
   
   ```
   FROM python:3.8

   COPY . /opt/app

   WORKDIR /opt/app

   RUN pip install streamlit && \
      pip install --upgrade google-cloud-vision
   RUN mkdir /tmp/keys/ && \
      touch /tmp/keys/key.json

   # RUN mkdir resources/ && wget https://raw.githubusercontent.com/googleapis/python-vision/master/samples/snippets/quickstart/resources/wakeupcat.jpg -P /opt/app/resources

   # 以下に修正
   RUN mkdir resources/ && wget https://4.bp.blogspot.com/-gX99oMun4bM/U9y_wYoE0EI/AAAAAAAAjiU/DHdcIfImCwQ/s800/pose_ganbarou_man.png -P /opt/app/resources/

   ENV GOOGLE_APPLICATION_CREDENTIALS /tmp/keys/key.json

   EXPOSE 8501

   # 一度bashに入りたい場合はこちらを実行
   CMD ["bash"]
   ```

   以下のコマンドで、イメージをビルドする。
   `docker image build -t streamlit_study_img .`
   以下のコマンドでdockerを起動する。起動するとDocker環境下のbashに移動する。
   `docker container run --name streamlit_study_container -it -p 8501:8501 -v $GOOGLE_APPLICATION_CREDENTIALS:/tmp/keys/key.json:ro streamlit_study_img`

5. bash環境下で以下コマンドを実行する。
   `python src/visionapi_test.py`

   実行すると、写真内にある物体の名称がターミナルにプリントされる。

[目次に戻る](./index.md)