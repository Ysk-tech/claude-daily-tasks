# claude-daily-tasks

Claude のスケジュールタスクで毎朝自動実行している、3つのデイリータスクの指示文（プロンプト）と設定をまとめたリポジトリです。

実行そのものは Claude（Proプラン）のスケジュールタスクで行っているため、追加費用はかかりません。このリポジトリは、プロンプトのバージョン管理とバックアップのために使います。

## タスク一覧

| タスク | 内容 | 実行時刻 | 届け方 |
|---|---|---|---|
| [AI Daily Digest](tasks/ai-daily-digest.md) | AI関連の新モデル・新機能、主要人物の発信、スキル化できそうなネタ、注目のYouTube動画を日本語でまとめる | 毎日 7:45 JST | メール＋プッシュ通知 |
| [ローカル課題アプリ案](tasks/local-issue-app-ideas.md) | 地域のニュースから小さいけれど刺さる困りごとを見つけ、それを解決するアプリ案を3〜5件出す | 毎日 7:45 JST | メール＋プッシュ通知 |
| [ホットニュース＆金融デイリー](tasks/hot-news-finance-daily.md) | 国内外のホットニュース、政治・国際（各立場の見方付き）、マーケット概況、金融ニュース（初心者向け解説＋投資の視点）、注目予定、今日の用語 | 毎日 7:45 JST | メール＋プッシュ通知 |

## 仕組み

- **情報収集**：Claude の Web検索（WebSearch / WebFetch）を使う。有料APIは使わない。
- **重複防止**：各タスクは Claude の Docs にある「履歴ドキュメント」を最初に読み、過去に取り上げた項目を除外する。実行の最後にその日の分を追記し、14日より古い分は削除する。
  - AI Daily Digest 掲載履歴：https://claude.ai/artifact/Hn579KX5x7HMEgjDegEAuq
  - ローカル課題×アプリ案 履歴：https://claude.ai/artifact/XGkzK9xi1GEaxZqYGeybMJ
  - ホットニュース＆金融デイリー 掲載履歴：https://claude.ai/artifact/NeFLq5FjTVMCLbyy77SPit
- **期間**：前日（JST）の情報が中心。足りないときだけ直近7日以内で補う。

## プロンプトを変更するとき

1. `tasks/` のファイルを編集してコミットする。
2. Claude のチャットで「AI Daily Digest のプロンプトを tasks/ai-daily-digest.md の内容に更新して」のように頼み、スケジュールタスク側にも反映する。

※ GitHub のファイルを変えただけでは、実行中のタスクには反映されません（Claude 側に保存されたプロンプトで動いているため）。

## ファイル構成

```
README.md
tasks/
  ai-daily-digest.md        # AI Daily Digest のプロンプトと設定
  local-issue-app-ideas.md  # ローカル課題アプリ案のプロンプトと設定
  hot-news-finance-daily.md # ホットニュース＆金融デイリーのプロンプトと設定
```
