## pocketauth

**軽量かつセキュアなOAuth 2.0認証サービス**

`pocketauth`は、Go言語で開発され、Dockerコンテナとして提供される、シンプルで使いやすいOAuth 2.0認証プロバイダです。バックエンドにはMySQLを採用し、高い信頼性と柔軟な設定を提供します。マイクロサービスアーキテクチャや認証を迅速に実装したいプロジェクトに最適です。

-----

## 🚀 特徴

  * **Go言語 (Golang) 製:** 高速で軽量、並行処理に強いバックエンド。
  * **Docker対応:** 依存関係を気にせず、どこでも一貫した環境で実行可能。
  * **MySQL利用:** 信頼性の高いリレーショナルデータベースでユーザー・クライアント情報を管理。
  * **OAuth 2.0実装:** 業界標準の認可フレームワークに準拠。
  * **シンプルな構成:** 最小限の依存関係で、迅速なデプロイと保守が可能。

-----

## 🛠️ 環境構築

`pocketauth`の実行には、**Docker**と**Docker Compose**が必要です。

### 1\. リポジトリのクローン

```bash
git clone https://github.com/mattuu0/pocketauth
cd pocketauth
```

### 2\. 環境変数の設定

プロジェクトルートにある`.env.example`をコピーし、`.env`として認証情報などを設定してください。

```bash
cp .env.example .env
```

**`.env` (抜粋):**

| 変数名 | 説明 | 例 |
| :--- | :--- | :--- |
| `DB_HOST` | MySQLコンテナ名/ホスト名 | `mysql` |
| `DB_USER` | MySQLユーザー名 | `pocketuser` |
| `DB_PASSWORD` | MySQLパスワード | `secure_password` |
| `DB_NAME` | データベース名 | `pocketauth_db` |
| `SERVER_PORT` | Goサーバーのポート | `8080` |
| `JWT_SECRET` | JWT署名に使用するシークレットキー | `very_secret_key_change_me` |

### 3\. 起動

`docker-compose`コマンド一つで、GoアプリケーションとMySQLデータベースが同時に起動します。

```bash
docker-compose up --build -d
```

  * `--build`: 初回起動時やコード変更時にイメージを再ビルドします。
  * `-d`: バックグラウンドでコンテナを実行します。

コンテナが起動したら、`http://localhost:8080` (設定したポート) で認証サービスにアクセスできます。

-----

## 🛑 停止とクリーンアップ

コンテナを停止し、作成されたネットワークとボリュームを削除します。

```bash
docker-compose down
```

> **注意:** データベースのデータも永続化設定をしていない場合は削除されます。
