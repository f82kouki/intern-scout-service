# Backend (Rails API)

このプロジェクトはRails 8.0.3を使用したAPIサーバーです。PostgreSQLデータベースを使用し、JWT認証（Devise + Devise-JWT）を実装しています。

## 技術スタック

- **Ruby**: 3.2.2
- **Rails**: 8.0.3
- **データベース**: PostgreSQL
- **認証**: Devise + Devise-JWT
- **CORS**: rack-cors

## ローカル環境構築手順

### 前提条件

以下のソフトウェアがインストールされている必要があります：

- Ruby 3.2.2
- PostgreSQL
- Bundler

### 1. リポジトリのクローン

```bash
git clone <repository-url>
cd backend
```

### 2. 依存関係のインストール

```bash
bundle install
```

### 3. データベースの設定

PostgreSQLが起動していることを確認してください。

```bash
# PostgreSQLの起動（macOS）
brew services start postgresql

# PostgreSQLの起動（Linux）
sudo systemctl start postgresql

# PostgreSQLの起動（Windows）
# PostgreSQLサービスを手動で開始
```

### 4. データベースの作成とマイグレーション

```bash
# データベースの作成
rails db:create

# マイグレーションの実行
rails db:migrate

# シードデータの投入（必要に応じて）
rails db:seed
```

### 5. 環境変数の設定

必要に応じて環境変数を設定してください：

```bash
# .envファイルを作成（推奨）
cp .env.example .env

# または環境変数を直接設定
export RAILS_MASTER_KEY=<your_master_key>
export DATABASE_URL=postgres://username:password@localhost/backend_development
```

### 6. サーバーの起動

```bash
# 開発サーバーの起動
rails server

# または特定のポートで起動
rails server -p 3001
```

サーバーが起動すると、`http://localhost:3000`（または指定したポート）でAPIにアクセスできます。

## API エンドポイント

### 認証関連

- `POST /users` - ユーザー登録
- `POST /users/sign_in` - ログイン
- `DELETE /users/sign_out` - ログアウト

### その他のエンドポイント

（実際のAPIエンドポイントに応じて記載してください）

## 開発時の注意事項

- CORS設定により、フロントエンドからのリクエストが許可されています
- JWT認証を使用しているため、認証が必要なエンドポイントには適切なヘッダーを設定してください
- 開発環境では`config/environments/development.rb`の設定を確認してください

## トラブルシューティング

### よくある問題

1. **PostgreSQL接続エラー**
   - PostgreSQLが起動していることを確認
   - データベースが作成されていることを確認
   - 接続情報（ホスト、ポート、ユーザー名、パスワード）を確認

2. **Gemのインストールエラー**
   - Rubyのバージョンが3.2.2であることを確認
   - `bundle install`を再実行

3. **マイグレーションエラー**
   - データベースが作成されていることを確認
   - `rails db:drop db:create db:migrate`で再作成

## Dockerでの実行

本番環境用のDockerfileが提供されています：

```bash
# Dockerイメージのビルド
docker build -t backend .

# Dockerコンテナの実行
docker run -d -p 80:80 -e RAILS_MASTER_KEY=<value> --name backend backend
```

## テスト

```bash
# テストの実行
rails test

# 特定のテストファイルの実行
rails test test/models/user_test.rb
```
