# Frontend (Next.js)

このプロジェクトはNext.js 15.5.4を使用したReactアプリケーションです。TypeScript、Tailwind CSS、React Queryを使用して構築されています。

## 技術スタック

- **Next.js**: 15.5.4
- **React**: 19.1.0
- **TypeScript**: 5.x
- **Tailwind CSS**: 3.4.0
- **React Query**: 5.90.2
- **Axios**: 1.12.2

## ローカル環境構築手順

### 前提条件

以下のソフトウェアがインストールされている必要があります：

- Node.js (18.0.0以上推奨)
- npm または yarn

### 1. リポジトリのクローン

```bash
git clone <repository-url>
cd frontend
```

### 2. 依存関係のインストール

```bash
# npmを使用する場合
npm install

# yarnを使用する場合
yarn install

# pnpmを使用する場合
pnpm install
```

### 3. 環境変数の設定

必要に応じて環境変数を設定してください：

```bash
# .env.localファイルを作成
cp .env.example .env.local

# または環境変数を直接設定
export NEXT_PUBLIC_API_URL=http://localhost:3000
export NEXT_PUBLIC_APP_NAME=YourAppName
```

### 4. 開発サーバーの起動

```bash
# npmを使用する場合
npm run dev

# yarnを使用する場合
yarn dev

# pnpmを使用する場合
pnpm dev
```

開発サーバーが起動すると、`http://localhost:3000`でアプリケーションにアクセスできます。

## 利用可能なスクリプト

- `npm run dev` - 開発サーバーの起動
- `npm run build` - 本番用ビルドの作成
- `npm run start` - 本番サーバーの起動
- `npm run lint` - ESLintによるコードチェック

## プロジェクト構造

```
src/
├── app/                 # Next.js App Router
├── components/          # 再利用可能なコンポーネント
├── lib/                 # ユーティリティ関数
├── hooks/               # カスタムフック
├── types/               # TypeScript型定義
└── styles/              # スタイルファイル
```

## 主要な機能

- **認証**: JWT認証によるユーザー認証
- **API通信**: Axiosを使用したREST API通信
- **状態管理**: React Queryによるサーバー状態管理
- **スタイリング**: Tailwind CSSによるレスポンシブデザイン
- **型安全性**: TypeScriptによる型チェック

## バックエンドとの連携

このフロントエンドは、`backend`ディレクトリのRails APIサーバーと連携するように設計されています。

### API設定

- デフォルトのAPIベースURL: `http://localhost:3000`
- 認証: JWTトークンを使用
- CORS: バックエンドでCORS設定が有効

### 認証フロー

1. ユーザー登録/ログイン
2. JWTトークンの取得
3. トークンをローカルストレージに保存
4. APIリクエスト時にトークンをヘッダーに含める

## 開発時の注意事項

- TypeScriptの型チェックが有効になっています
- ESLintによるコード品質チェックが設定されています
- Tailwind CSSのクラス名は自動補完されます
- ホットリロードが有効になっています

## トラブルシューティング

### よくある問題

1. **依存関係のインストールエラー**
   - Node.jsのバージョンが18.0.0以上であることを確認
   - `node_modules`を削除して再インストール
   - `npm cache clean --force`でキャッシュをクリア

2. **API接続エラー**
   - バックエンドサーバーが起動していることを確認
   - CORS設定を確認
   - 環境変数`NEXT_PUBLIC_API_URL`を確認

3. **ビルドエラー**
   - TypeScriptの型エラーを確認
   - ESLintエラーを確認
   - `npm run lint`でコードチェック

4. **スタイルが適用されない**
   - Tailwind CSSの設定を確認
   - クラス名のスペルを確認
   - `tailwind.config.js`の設定を確認

## 本番環境へのデプロイ

### Vercel（推奨）

```bash
# Vercel CLIのインストール
npm i -g vercel

# デプロイ
vercel
```

### その他のプラットフォーム

- **Netlify**: `npm run build`でビルド後、`out`ディレクトリをデプロイ
- **AWS Amplify**: 自動ビルド設定
- **Docker**: Dockerfileを作成してコンテナ化

## パフォーマンス最適化

- Next.jsの自動最適化機能を活用
- 画像最適化（`next/image`）
- コード分割（動的インポート）
- 静的生成（`getStaticProps`）

## テスト

```bash
# テストの実行（テストが設定されている場合）
npm test

# テストの監視モード
npm run test:watch
```