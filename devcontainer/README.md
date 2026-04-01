開発・動作確認用の環境構築

■ DB環境の構築
DBはdocker-compose.yml内に定義されている。
後述するDjango開発コンテナを起動することでDBコンテナも起動する。
そのため、DB環境のみ明示的に起動することはない。

※DB情報
ポート：5432
ユーザー：test_user
パスワード：rootroot
DB名：django_application

============================================

■ Django開発コンテナ

■ 前提
  Djangoの開発（ソースコードの編集・Djangoアプリ起動など）はDockerコンテナ内で実行する。
  Docker内でVSCodeを起動し編集を行う。
  必要な拡張機能はコンテナ内に自動でインストールされる。

■ 起動方法
1. 自身のVSCode(ローカル環境)に以下の拡張機能をインストールする。
   ・WSL
   ・Dev Containers
   ・Docker

2. VSCodeの左下の「><」を選択し、「WSLへの接続」を選択する。
  VSCodeが再度開き、VSCodeの左下が「WSL: Ubuntu」になっていることを確認する。

3. VSCodeで「django_app_develop_src」を開く。

※初回起動時のみ以下の4. 5. を実施する。
4. VSCode上で「Ctrl + Shift + p」を押下し、「Dev Containers: Settings」を選択する。

5. 「Dev › Containers: Execute In WSL」にチェックをつける。

6. 検索画面に「Dev Containers: Reopen in Container」を選択する。

7. django-webコンテナ内でVSCodeを開いた状態になる。

■ スーパーユーザー作成
以下コマンドを実行しスーパーユーザーを作成する。
python manage.py createsuperuser

username: admin
メールアドレス: test@example.com
password: rootroot

■Webサーバー起動
1. VSCodeの「実行とデバック」を開く。

2. 「実行とデバック」のリストから「runserver」を選択する

3. 「デバックの開始」(再生ボタン)を選択する

4. サーバーが起動する。
※ローカルPCから接続する場合は以下URLを用いて接続する
http://localhost:8001