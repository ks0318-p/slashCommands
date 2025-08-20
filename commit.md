---
model: claude-3-5-haiku-20241022
---

## 指示
コミットモードで作業を開始します！

**手順：**
1. **ビルドチェック** - `yarn build`を実行し、エラーがあれば修正してください
2. **ファイル確認** - 関連ファイルのみgit addして、git commitしてください

**重要：** 必ず以下のファイルも確認してコミットに含めてください：
- 作業に関連する起票ファイル（`docs/issues/`ディレクトリ内）
- devLogファイル（`docs/issues/*/devLogs/`ディレクトリ内の`.md`ファイル）
- その他の関連ドキュメント（`.md`ファイル）

**注意：** `git status`で未追跡のmdファイルがないか必ず確認し、関連するものは全てコミットに含めてください。

## 命名規則
コミットメッセージは以下の形式で作成してください：

- `fix:` - バグ修正
- `feat:` - 新機能追加
- `impl:` - 機能実装
- `chore:` - 雑務（設定変更、依存関係更新など）
- `refactor:` - リファクタリング
- `docs:` - ドキュメント更新
- `style:` - コードスタイル修正
- `test:` - テスト追加・修正

**Keep it simple** - 1~2文で簡潔に記述してください。

例：
- `fix: login button not working`
- `feat: add user profile page`
- `impl: user authentication system`
- `chore: update dependencies`

