# health-apps

iPhone のホーム画面アイコンとして使う、健康管理用の単一HTMLアプリ集。

- `kit.html` — KIT トレーニング（月・水・土のマシンメニュー、進捗・記録）
- `routine.html` — 健康ルーチン（毎日・毎週・特定日の予定管理）
- `index.html` — 上記2つへのランチャー

GitHub Pages で公開し、Safari の「ホーム画面に追加」で iPhone アプリ化する。

## 更新フロー

iCloud Drive で .html を編集 → `bin/health-apps-deploy` を実行して反映。
