---
model: claude-3-5-haiku-20241022
---

# /removeDebugLogs - このセッションで追加したdebugログを全て削除

## 概要
このセッションで追加されたdebugログ（console.log、console.debug等）を自動的に検出し、プロジェクト全体から削除するスラッシュコマンドです。本番環境で必要なエラーログやモニタリング用のログは削除対象から除外され、保持されます。

## 使用方法
`/removeDebugLogs`と入力してください。

## 実行内容
1. プロジェクト内の全ファイルをスキャンしてdebugログを検索
2. このセッションで追加されたと思われるdebugログを特定
3. 本番環境で必要なログを判定（以下は削除対象外）：
   - エラーハンドリング用のconsole.error
   - 監視・モニタリング用のログ
   - セキュリティ関連のログ
   - 構造化されたログ（logger.info, logger.errorなど）
4. デバッグ用のログのみを削除（console.log、console.debug、一時的なconsole.info等）
5. 変更されたファイルのリストと削除されたログの数を表示
6. 変更が適用されたことを確認

## 対象となるログ
- `console.log()`
- `console.debug()`
- `console.info()`
- `console.warn()`
- `console.error()`（デバッグ用途の場合のみ）
- その他のデバッグ用ログ文

## 例
実行後の出力例：
```
✅ Debugログの削除が完了しました！

削除されたログ: 15個
変更されたファイル:
- src/components/Header.js (3個)
- src/utils/api.js (7個)
- src/pages/Dashboard.js (5個)
```

## 注意事項
- 本番環境で必要なログ（エラーログ、監視ログ、構造化ログ等）は自動的に検出され、削除対象から除外されます
- プロダクションコードの安全性を確保するため、削除前に必ず対象ログの確認を行います
- バックアップを取ってから実行することを推奨します
- TypeScriptやJavaScriptファイルのみが対象です
- try-catchブロック内のconsole.errorは保持されます