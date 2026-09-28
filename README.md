t-seki の各リポジトリで共有する Renovate の共通プリセット。
各リポジトリの `renovate.json` (または `.github/renovate.json`) に以下を書くだけ:
```json
{
  "extends": ["github>t-seki/renovate-config"]
}
```
パッケージ単位のグループ化や例外は各リポジトリの `packageRules` に書く。
`packageRules` は後に書いたものが勝つので、各リポジトリの `groupName` が共通の
「minor and patch updates」グループを上書きする。
- ベースは `config:best-practices` (GitHub Actions / Docker の digest pin を含む)
- minor/patch: 1 つのグループにまとめ、CI 通過後に自動マージ
- pin/digest: CI 通過後に自動マージ
- major: 自動マージせず手動レビュー
- 週次(月曜 9時前, Asia/Tokyo)にまとめて実行
- PR には `dependencies` ラベルを付ける
- Dependency Dashboard を各リポジトリで有効化
- `homelab-argocd`: Helm chart (Longhorn 等) の更新にマージ前の手動確認が必要なため、共通プリセットを使わず独自設定で運用する
