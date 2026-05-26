# health-apps

iPhone のホーム画面アイコンとして使う、健康管理用の単一HTMLアプリ集。

- `kit.html` — KIT トレーニング（月・水・土のマシンメニュー、進捗・記録）
- `routine.html` — 健康ルーチン（毎日・毎週・特定日の予定管理）
- `index.html` — 上記2つへのランチャー

GitHub Pages で公開し、Safari の「ホーム画面に追加」で iPhone アプリ化する。

公開URL: https://togotatu-lab.github.io/health-apps/

## ソースの所在

編集は **iCloud Drive** 側のファイルに対して行う。リポジトリ内の `kit.html` / `routine.html` は deploy 時に上書きされるので直接編集しない。

```
~/Library/Mobile Documents/com~apple~CloudDocs/01_健康管理/02_筋トレ・リハビリ/
├── 00_KIT_メニューアプリ.html      → kit.html に同期
├── 01_健康ルーチン.html             → routine.html に同期
└── machine_photos/Mxx.jpg           → machine_photos/ に同期（rsync --delete）
```

## デプロイ手順

iCloud 側で編集したら、ターミナルで:

```
health-apps-deploy
```

実体は `~/.local/bin/health-apps-deploy`（PATH 通り済み）。引数なしで日時メッセージ、引数1つでコミットメッセージ指定可。変更がなければ no-op。push 後 1〜2分で GitHub Pages に反映。

## マシン写真を追加するとき

1. iCloud の `02_筋トレ・リハビリ/machine_photos/` に `Mxx.jpg` を置く（`xx` はマシン番号）
2. `health-apps-deploy` を実行

**GitHub の Web UI から直接 upload しないこと。** ルート直下にアップロードされる事故が起きやすく、`kit.html` は `machine_photos/` 配下のみ参照するため表示されない。deploy スクリプトはこのケースを検出して止める。
