# ベースイメージの設定
FROM python:3.13-slim

# Pythonが.pycファイル（コンパイル済みのPythonコード）を生成するのを防ぐ
ENV PYTHONDONTWRITEBYTECODE=1

# 標準出力をリアルタイムで表示するため
ENV PYTHONUNBUFFERED=1

# 環境変数LANGをja_JP.UTF-8に設定。
# 理由: コンテナ内での文字エンコーディングをUTF-8に設定することで、文字化けなどの問題を防ぐため。
ENV LANG ja_JP.UTF-8

# 環境変数TZをAsia/Tokyoに設定。
# 理由: コンテナ内のデフォルトのタイムゾーンを日本時間に設定するため。
ENV TZ Asia/Tokyo

# run command about creating app directory
RUN mkdir -p /usr/src/app

# copy development.txt to docker
COPY ./django-web/requirements.txt /usr/src/app

# point workdir
WORKDIR /usr/src/app/

# install library listed in development.txt
RUN pip install --upgrade pip --root-user-action=ignore
RUN pip install --no-cache-dir --root-user-action=ignore -r ./requirements.txt

# port number
EXPOSE 8000