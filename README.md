# 環境構築手順
## アプリケーションの用意
このリポジトリをクローン
```
https://github.com/nakashima63/backend.git
```

## リポジトリのディレクトリに移動
```
cd /path/to/backend
```

## 依存パッケージのインストール
```
composer install
```
```
npm install
```

## シェルエイリアスの設定
### シェル設定ファイルに追加
```
# 設定ファイルを開く（Zsh を使用している場合は~/.zshrc）
vi ~/.bashrc

# ファイルの末尾に下記エイリアス行を追加して保存
alias sail='sh $([ -f sail ] && echo sail || echo vendor/bin/sail)'

# 設定の再読み込み（Zsh を使用している場合は~/.zshrc）
source ~/.bashrc
```

### sailコマンドが実行できることを確認
```
# app_keyを生成
sail artisan key:generate

# コンテナを起動
sail up -d

# マイグレーション実行
sail artisan migrate
```

## ブラウザでアクセスできることを確認
http://localhost

## テストの用意
### テスト用のDBの用意
```
# envファイルを複製
cp -p .env .env.testing
```

### .env.testingを修正
```
DB_DATABASE=testing
```

### テスト実行
```
# DB接続を含まないテスト
php artisan test

# DB接続を含むテスト
sail artisan test
```
