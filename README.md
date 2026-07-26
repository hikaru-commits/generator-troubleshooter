# GENERATOR TROUBLESHOOTER

船舶のインターンシップ参加者向けに、船舶機関士が行うディーゼル発電機のトラブルシューティングを疑似体験できる教育用Webアプリです。

## 主な機能

- イントロダクションと3段階の難易度
- 5種類のランダムなトラブルケース
- 警報・運転データ比較、21箇所の点検、原因診断
- 安全措置、処置選択、試運転・復旧アニメーション
- 実時間・作業想定時間・スコア・ランク評価
- 段階ヒントと、外部AIへ貼り付けられる相談プロンプト生成
- PC・スマートフォン対応

## 使用技術

HTML5、CSS3、Vanilla JavaScriptのみ。外部ライブラリ、ビルドツール、サーバーサイド処理、データベースは使用していません。

## ファイル構成

```text
generator-troubleshooter/
├── index.html   # アプリの土台
├── style.css    # レスポンシブUI
├── script.js    # ケースデータとゲームロジック
├── README.md
└── .gitignore
```

## ローカルで起動

```bash
cd /Users/hikaru/Documents/generator-troubleshooter
python3 -m http.server 8000
```

ブラウザで `http://localhost:8000` を開きます。`index.html` を直接開いても基本機能は動作します。

## GitHubへ公開

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

GitHub Pagesを使う場合は、リポジトリの Settings → Pages で `main` ブランチのルートを指定します。

## Vercelへ公開

VercelでGitHubリポジトリをImportし、Framework Presetを「Other」、Build Commandを空欄、Output Directoryを `.` としてDeployします。静的ファイルだけなので追加設定は不要です。

## トラブルケースを追加する

`script.js` の `CASES` 配列に既存ケースと同じ構造のオブジェクトを追加します。警報、運転データ、重要点検、点検結果、原因候補、安全措置、処置候補、試運転値、ヒント、学習ポイントを1か所で管理しています。点検候補自体を増やす場合は `INSPECTIONS` に追加してください。

## 重要事項

本アプリは教育用シミュレーションであり、実機の整備手順を代替しません。実際の船舶・発電機では、機器メーカーの取扱説明書、船内手順書、SMS、および責任者の指示に従ってください。
