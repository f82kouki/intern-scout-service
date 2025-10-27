# インターンスカウトサービス

このプロジェクトは、Rails API（バックエンド）とNext.js（フロントエンド）を使用したフルスタックWebアプリケーションです。

## プロジェクト概要

- **バックエンド**: Rails 8.0.3 + PostgreSQL + JWT認証
- **フロントエンド**: Next.js 15.5.4 + TypeScript + Tailwind CSS
- **認証**: Devise + Devise-JWTによるJWT認証
- **API通信**: Axios + React Query

## プロジェクト構造

```
Plex.kadai/
├── backend/          # Rails APIサーバー
│   ├── app/          # Railsアプリケーション
│   ├── config/       # 設定ファイル
│   ├── db/           # データベース関連
│   └── README.md     # バックエンド詳細手順
├── frontend/         # Next.jsアプリケーション
│   ├── src/          # ソースコード
│   ├── public/       # 静的ファイル
│   └── README.md     # フロントエンド詳細手順
└── README.md         # このファイル
```

## ローカル環境構築手順

### 前提条件

以下のソフトウェアがインストールされている必要があります：

- **Ruby**: 3.2.2
- **Node.js**: 18.0.0以上
- **PostgreSQL**: 最新版
- **Git**: 最新版

### 1. リポジトリのクローン

```bash
git clone <repository-url>
cd Plex.kadai
```

### 2. バックエンドのセットアップ

```bash
cd backend

# 依存関係のインストール
bundle install

# PostgreSQLの起動
# macOS: brew services start postgresql
# Linux: sudo systemctl start postgresql
# Windows: PostgreSQLサービスを手動で開始

# データベースの作成とマイグレーション
rails db:create
rails db:migrate

# サーバーの起動（別ターミナルで実行）
rails server
```

バックエンドサーバーは `http://localhost:3000` で起動します。

### 3. フロントエンドのセットアップ

```bash
cd frontend

# 依存関係のインストール
npm install

# 開発サーバーの起動（別ターミナルで実行）
npm run dev
```

フロントエンドアプリケーションは `http://localhost:3000` で起動します。

### 4. 動作確認

1. ブラウザで `http://localhost:3000` にアクセス
2. アプリケーションが正常に表示されることを確認
3. 認証機能（ログイン/登録）をテスト

## 開発環境での実行

### バックエンドのみ

```bash
cd backend
rails server
```

### フロントエンドのみ

```bash
cd frontend
npm run dev
```

### 両方同時実行

2つのターミナルを開いて、それぞれで上記のコマンドを実行してください。

## 環境変数

### バックエンド

- `RAILS_MASTER_KEY`: Railsのマスターキー
- `DATABASE_URL`: PostgreSQLの接続URL

### フロントエンド

- `NEXT_PUBLIC_API_URL`: バックエンドAPIのURL（デフォルト: http://localhost:3000）

## API仕様

### 認証エンドポイント

- `POST /users` - ユーザー登録
- `POST /users/sign_in` - ログイン
- `DELETE /users/sign_out` - ログアウト

### その他のエンドポイント

（実際のAPIエンドポイントに応じて記載してください）

## トラブルシューティング

### よくある問題

1. **ポート競合**
   - バックエンドとフロントエンドが同じポート（3000）を使用している場合
   - バックエンドを `rails server -p 3001` で起動
   - フロントエンドの環境変数 `NEXT_PUBLIC_API_URL` を `http://localhost:3001` に設定

2. **データベース接続エラー**
   - PostgreSQLが起動していることを確認
   - データベースが作成されていることを確認
   - 接続情報を確認

3. **CORSエラー**
   - バックエンドのCORS設定を確認
   - フロントエンドのAPI URL設定を確認

4. **認証エラー**
   - JWTトークンが正しく設定されていることを確認
   - トークンの有効期限を確認

## 本番環境へのデプロイ

### バックエンド

- **Kamal**: `gem "kamal"` が含まれているため、Kamalを使用したデプロイが可能
- **Docker**: 提供されているDockerfileを使用
- **Heroku**: 標準的なRailsデプロイ手順

### フロントエンド

- **Vercel**: Next.jsの推奨デプロイプラットフォーム
- **Netlify**: 静的サイトとしてデプロイ
- **AWS Amplify**: フルスタックデプロイ

## 開発ガイドライン

### コーディング規約

- **バックエンド**: RuboCopによる自動フォーマット
- **フロントエンド**: ESLint + Prettierによる自動フォーマット

### テスト

```bash
# バックエンドテスト
cd backend
rails test

# フロントエンドテスト（設定されている場合）
cd frontend
npm test
```

### Git ワークフロー

1. 機能ブランチを作成
2. 変更をコミット
3. プルリクエストを作成
4. コードレビュー
5. マージ

## 貢献

1. このリポジトリをフォーク
2. 機能ブランチを作成 (`git checkout -b feature/amazing-feature`)
3. 変更をコミット (`git commit -m 'Add some amazing feature'`)
4. ブランチにプッシュ (`git push origin feature/amazing-feature`)
5. プルリクエストを作成

## ライセンス

このプロジェクトのライセンスについては、プロジェクトの要件に応じて設定してください。

## サポート

問題が発生した場合は、以下の手順でサポートを受けてください：

1. このREADMEのトラブルシューティングセクションを確認
2. 各ディレクトリのREADMEファイルを確認
3. 問題を報告する際は、エラーメッセージと環境情報を含めてください

---

**注意**: このプロジェクトは課題提出用のサンプルアプリケーションです。本番環境で使用する場合は、セキュリティ設定やパフォーマンス最適化を適切に行ってください。


