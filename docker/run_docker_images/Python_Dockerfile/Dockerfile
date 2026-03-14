# カスタマイズ元のイメージを記載する
FROM python:3.9-slim

# コンテナ内の作業ディレクトリを設定する
WORKDIR /app

# ローカルのapp.pyをコンテナ内にコピー
COPY app.py /app

# Dockerコンテナ内で実行するコマンドを指定する
CMD ["python", "app.py"]