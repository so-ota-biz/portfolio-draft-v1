# portfolio-draft-v1

## 重要な注意事項

このリポジトリは、ポートフォリオアプリの方向性を定めるまでの暫定的なものです。
システムの構想がある程度固まった後の、ドキュメント・コード管理は、別のリポジトリに移行して行います。

## 移行後のブランチ運用について

- `main` = 安定開発ブランチ として、`production` を別途置く
- `feature` → `main` で日常的に統合
- 定期的に `main` → `production` をマージしてリリース
- `production` は `hotfix` 直マージ可

※ これは GitLab Flow の環境ブランチ型の簡易版です。

## 移行後のタスク管理について

### 1. タスク管理

- GitHub Issues を 1タスク単位で作成

例: `#12 ログイン画面を実装`

- Issue からブランチを作成 → 実装

```bash
git checkout -b feature/#12-login-page
```

※ ただし、１対多の関係になってもよい

例: `#12 ログイン画面を実装` について、
- `#12-login-page-v2`
- `#12-login-page-v3`

が生まれてもよい

- コミットメッセージに Issue を紐づけ
- 特にそのコミットによって、紐づいている Issue の対応が完了する想定の場合は、以下のようにする

```bash
git commit -m "add: ログイン画面を実装 (closes #12)"
```

→ PR マージ時に Issue が自動で閉じる

- Pull Request (PR) を作成し、レビューして main にマージ

- Project Board をカンバンとして利用

カラム例: `Todo` → `Doing` → `Review` → `Done`
