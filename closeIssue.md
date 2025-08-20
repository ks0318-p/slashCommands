---
model: claude-3-5-haiku-20241022
---

# /closeIssue - 現在のセッションの関連GitHub issueをクローズ

## 概要
現在のセッションで作業したGitHub issueを、PRがマージされた後にクローズするスラッシュコマンドです。ブランチ名やコミット履歴から関連するissue番号を自動的に検出し、適切なコメントを追加してissueをクローズします。

## 使用方法
`/closeIssue`と入力してください。

## 実行内容

### ステップ1: 関連issue番号の検出
以下の方法で関連するissue番号を検出します：
1. 現在のブランチ名から issue番号を抽出（例：`feature/123-add-feature` → #123）
2. 最近のコミットメッセージから issue番号を検出（例：`fix #123` → #123）
3. PRのタイトルや説明から issue番号を検出

### ステップ2: issue番号の確認
検出されたissue番号をユーザーに確認します：
```
検出されたissue: #123
このissueをクローズしますか？ [Y/n]
```

自動検出できない場合は、ユーザーに入力を求めます：
```
issue番号を入力してください（例：123）：
```

### ステップ3: クローズコメントの作成
デフォルトのクローズコメントを表示し、必要に応じて編集できるようにします：
```
クローズコメント（Enterでデフォルトを使用）：
Fixed in #{PR番号} - {PRタイトル}
```

### ステップ4: issueのクローズ
GitHub CLIを使用してissueをクローズします：
```bash
gh issue close {issue_number} --comment "{comment}"
```

### ステップ5: 完了確認
成功時：
```
✅ Issue #{issue_number} をクローズしました！
📝 コメント: {comment}
🔗 URL: https://github.com/{owner}/{repo}/issues/{issue_number}
```

失敗時：
```
❌ Issue #{issue_number} のクローズに失敗しました
エラー: {error_message}
```

## 例

### 基本的な使用例
```
/closeIssue

検出されたissue: #456
このissueをクローズしますか？ [Y/n] Y

クローズコメント（Enterでデフォルトを使用）：
Fixed in #789 - Add new feature for user authentication

✅ Issue #456 をクローズしました！
```

### 手動でissue番号を指定する例
```
/closeIssue

issue番号を入力してください（例：123）： 234

クローズコメント（Enterでデフォルトを使用）： 
PRがマージされたため、このissueをクローズします。

✅ Issue #234 をクローズしました！
```

## 注意事項
- GitHub CLIがインストールされ、認証済みである必要があります
- 適切な権限（issueをクローズする権限）が必要です
- PRがマージされていることを前提としています