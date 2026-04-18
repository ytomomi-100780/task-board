# task-board

タスク管理ボードアプリのプロジェクトです。

## プロジェクト概要

- **プロジェクト名**: task-board
- **目的**: タスクの作成・管理・追跡を行うボードアプリケーション

## 技術スタック

- **フレームワーク**: React 18
- **ビルドツール**: Vite 5
- **言語**: JavaScript (JSX)
- **スタイル**: CSS（コンポーネントごとに `App.css` で管理）
- **状態管理**: React `useState`（外部ライブラリなし）
- **永続化**: `localStorage`
- **デプロイ**: GitHub Pages（GitHub Actions による自動デプロイ）

## デプロイ先

https://ytomomi-100780.github.io/task-board/

`main` ブランチへのプッシュで自動ビルド・デプロイされる。

## コンポーネント命名規約

| 種別 | 規約 | 例 |
|---|---|---|
| コンポーネントファイル | PascalCase + `.jsx` | `TaskItem.jsx` |
| コンポーネント関数 | PascalCase | `function TaskItem()` |
| CSS クラス名 | kebab-case | `.task-list`, `.input-row` |
| イベントハンドラ | `handle` + 動詞 | `handleKeyDown`, `handleSubmit` |
| state 変数 | camelCase | `tasks`, `input` |
| state セッタ経由の保存関数 | `save` + 名詞 | `saveTasks` |

## ディレクトリ構成

```
task-board/
├── src/
│   ├── App.jsx       # メインコンポーネント
│   ├── App.css       # スタイル
│   ├── main.jsx      # エントリーポイント
│   └── index.css     # グローバルスタイル
├── public/
├── index.html
├── vite.config.js
└── package.json
```

## 開発コマンド

```bash
npm install      # 依存関係インストール
npm run dev      # 開発サーバー起動 (http://localhost:5173)
npm run build    # 本番ビルド
npm run preview  # ビルド結果のプレビュー
```

---

## Git 運用ルール

### 基本方針

- **コードを変更するたびに GitHub へプッシュする**
- すべての変更はコミット → プッシュのサイクルで即座に反映する

### コミット手順

1. 変更内容を確認する
   ```bash
   git status
   git diff
   ```

2. 関連ファイルをステージングする（`git add .` は避け、ファイルを個別に指定する）
   ```bash
   git add <変更ファイル>
   ```

3. 意味のあるコミットメッセージを付けてコミットする
   ```bash
   git commit -m "変更内容の要約"
   ```

4. **必ず GitHub へプッシュする**
   ```bash
   git push origin <ブランチ名>
   ```

### コミットメッセージ規則

| プレフィックス | 用途 |
|---|---|
| `feat:` | 新機能追加 |
| `fix:` | バグ修正 |
| `refactor:` | リファクタリング |
| `style:` | スタイル・フォーマット変更 |
| `docs:` | ドキュメント更新 |
| `chore:` | 設定・ツール変更 |

例: `feat: タスク追加フォームを実装`

### ブランチ戦略

- `main` — 本番相当のブランチ。直接コミット禁止（初期設定を除く）
- `develop` — 開発用メインブランチ
- `feature/<機能名>` — 機能開発用ブランチ

### 注意事項

- `.env` などの機密情報を含むファイルは **絶対にコミットしない**
- `node_modules/` 等の生成物は `.gitignore` で除外する
- force push (`git push --force`) は原則禁止
