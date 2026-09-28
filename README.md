# renovate-config

t-seki の各リポジトリで共有する Renovate の共通プリセット。

## 使い方

各リポジトリの `renovate.json` (または `.github/renovate.json`) に以下を書くだけ:

```json
{
  "extends": ["github>t-seki/renovate-config"]
}
```

## 方針

- minor/patch: CI 通過後に自動マージ
- major: 自動マージせず手動レビュー
- 週次(月曜 9時前)にまとめて実行
- Dependency Dashboard を各リポジトリで有効化
