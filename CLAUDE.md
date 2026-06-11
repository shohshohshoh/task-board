# CLAUDE.md

## プロジェクト概要

タスクボードアプリケーション。
管理ディレクトリ: `c:\Users\shoh0\Claude\task-board`

## Git 運用ルール

**コードを変更するたびに、必ずコミットして GitHub にプッシュすること。**

### 手順

1. 変更をステージング (特定ファイルを名前で指定する):
   ```
   git add <変更したファイル>
   ```

2. コミット (変更内容を明確に記述):
   ```
   git commit -m "変更の概要"
   ```

3. GitHub へプッシュ:
   ```
   git push origin <ブランチ名>
   ```

### コミットメッセージ規則

- `feat:` 新機能追加
- `fix:` バグ修正
- `refactor:` リファクタリング
- `docs:` ドキュメント変更
- `test:` テスト追加・修正
- `chore:` ビルド・設定変更

末尾に必ず以下を付与:
```
Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
```

### ブランチ戦略

- `main` — 安定版、常にデプロイ可能な状態を維持
- 機能開発はブランチを切り、PR 経由でマージ

### 注意事項

- `.env` などの機密ファイルはコミットしない (`git add .` は使わない)
- 直接 `main` ブランチへのプッシュは避け、PR を使う
- `--force` プッシュは原則禁止 (`main`/`master` への force push は厳禁)
- 破壊的な git 操作 (reset --hard 等) は必ずユーザーに確認を取ること

## デプロイ先

- **本番 URL**: https://shohshohshoh.github.io/task-board/
- **デプロイ方法**: `main` へ push すると GitHub Actions が自動ビルド＆デプロイ
- **ワークフロー**: [.github/workflows/deploy.yml](.github/workflows/deploy.yml)

## 技術スタック

| 用途 | ライブラリ／ツール |
|---|---|
| UI フレームワーク | React 18 |
| ビルドツール | Vite 5 |
| 言語 | JavaScript (JSX) |
| スタイリング | CSS Modules (`.css` ファイル直書き) |
| 状態管理 | React `useState` / `useEffect` (外部ライブラリなし) |
| 永続化 | `localStorage` |
| パッケージマネージャ | npm |

## コンポーネント命名規約

- **ファイル名**: PascalCase（例: `TaskItem.jsx`、`TaskList.jsx`）
- **コンポーネント関数名**: ファイル名と同じ PascalCase
- **CSS ファイル名**: コンポーネントと同名（例: `TaskItem.css`）
- **props**: camelCase（例: `onToggle`、`onDelete`）
- **イベントハンドラ**: `handle` プレフィックス（例: `handleKeyDown`、`handleSubmit`）
- **コールバック props**: `on` プレフィックス（例: `onToggle`、`onDelete`）
- **状態変数**: camelCase、意味が明確な名前（例: `tasks`、`input`）

## コーディング規則

- コメントは原則書かない (コード自体が自己説明的であること)
- 不要な抽象化・将来のための設計はしない
- セキュリティ上の脆弱性 (XSS, SQLインジェクション等) を避ける

## 開発環境

- Platform: Windows 11, PowerShell
- PowerShell 構文を使用 (`$env:VAR`、行継続はバッククォート)
