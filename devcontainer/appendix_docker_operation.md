### docker compose起動方法
1. WSL2のカレントディレクトリをDJANGO_APP_DEVELOP_SRCに移動する
2. 以下コマンドを実行する
   docker compose up -d
3. 以下コマンドを実行し、2コンテナ(django_docker、django_db)が起動していることを確認する
   docker container ls -a

### docker compose停止方法
1. 以下コマンドを実行する
   docker compose stop

### docker compose削除方法
1. 以下コマンドを実行する
   docker compose down

***
### docker image build方法
1. WSL2のカレントディレクトリをdevelopmentに移動する
2. 以下コマンドを実行する
   docker build -t イメージ名 .
3. 以下コマンドを実行し、表示されたイメージ一覧に指定したイメージ名が表示されることを確認する
   docker image ls

### docker imageを用いたコンテナ起動
1. 以下コマンドを実行し、表示されたイメージ一覧からコンテナ化したいイメージ名(REPOSITORY) or IMAGE IDを確認する
   docker image ls
2. 以下コマンドを実行し、コンテナを起動する
   docker run --name コンテナ名 -dit イメージ名 -p ホストポート番号：コンテナポート番号
3. 以下コマンドを実行し、コンテナが起動していることを確認する(指定したコンテナ名が表示されていること、STATUSがUpであること)
   docker container ls

### 起動中のdocker container内へ接続する
1. 以下コマンドを実行し、接続する起動中コンテナ名 or CONTAINER IDを確認する
   docker container ls
2. 以下コマンドを実行し、コンテナ内へ接続する
   docker exec -it コンテナ名 /bin/bash


***
## 適宜必要なコマンド
### コンテナ個別削除
1. 以下コマンドを実行し、削除するコンテナ名 or CONTAINER IDを確認する
   docker container ls
2. 削除するコンテナが起動中(STATUSがUp)の場合、以下コマンドを実行し停止する
   docker stop コンテナ名
3. 以下コマンドを実行し、削除するコンテナが停止していること(STATUSがExisted)を確認する
   docker container ls -a
4. 以下コマンドを実行する
   docker rm コンテナ名
5. 以下コマンドを実行し、コンテナが削除されていることを確認する
   docker container ls -a

### コンテナ一括削除
1. 以下コマンドを実行する
   docker rm $(docker ps -aq)
   ※-fを指定すると起動中コンテナも強制的に削除

### イメージ個別削除
1. 以下コマンドを実行し、削除するイメージ名 or IMAGE IDを確認する
   docker image ls
2. 以下コマンドを実行する
   docker image rm イメージ名
3. 以下コマンドを実行し、イメージが削除されていることを確認する
   docker image ls
### イメージ一括削除
1. 以下コマンドを実行する
   docker image rm $(docker image ls -q)
   ※-fを指定すると起動中コンテナも強制的に削除