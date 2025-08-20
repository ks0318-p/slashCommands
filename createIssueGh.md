## 指示
GitHub Issue を自動作成するコマンドです。

## 動作
説明文を基に、以下の要素を自動生成してGitHub Issueを作成してください：

1. **タイトル生成**：説明文から適切な絵文字付きタイトルを生成
2. **ラベル判定**：キーワードから適切なラベルを自動判定
3. **確認後作成**：内容を確認してからIssueを作成

## 判定ルール

### Issue タイプ判定
- バグ関連 (`bug`, `error`, `broken`, `fix`, `issue`, `problem`, `fail`) → 🐛 Fix: + bug ラベル
- 新機能 (`feature`, `add`, `new`, `implement`, `create`) → ✨ Feature: + enhancement ラベル  
- 改善 (`improve`, `enhance`, `optimize`, `update`, `refactor`) → ⚡ Improvement: + enhancement ラベル
- ドキュメント (`doc`, `documentation`, `readme`, `guide`) → 📚 Docs: + documentation ラベル
- テスト (`test`, `testing`, `spec`, `coverage`) → 🧪 Test: + testing ラベル
- セキュリティ (`security`, `vulnerability`, `auth`, `permission`) → 🔒 Security: + security ラベル
- パフォーマンス (`performance`, `slow`, `speed`, `optimize`) → 🚀 Performance: + performance ラベル
- その他 → 📝 Task: + task ラベル

### 優先度判定
- 高優先度 (`urgent`, `critical`, `asap`, `important`, `high priority`) → high-priority ラベル追加
- 低優先度 (`low priority`, `minor`, `nice to have`, `sometime`) → low-priority ラベル追加

## 実行方法
1. 説明文を解析
2. タイトルとラベルを生成
3. 内容を表示して確認
4. 承認後に `gh issue create` コマンドでIssue作成

必ず確認ダイアログを表示してから実行してください。