# 🌬️ AI Relay Protocol (息継ぎプロトコル)
> **個人開発・実務運用の現場で使っている「AIエージェントの息継ぎ（セッション中継ぎ）」の定義ファイル置き場です。**  
> Claude Code, Cursor, Windsurf, Codex, Antigravity 等で自由にご活用ください。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Author](https://img.shields.io/badge/Author-036%20Factory-7DCA7E.svg)](https://036blog.com)

---

## 📌 はじめに（このリポジトリについて）

AIエージェント（Claude Code, Cursor, Codex等）と長時間の作業を行う中で、**「会話が長引いてAIが指示を忘れる問題（コンテキスト過熱）」** と **「新規チャットを開いたときの記憶喪失問題」** を解消するために、私（036 Factory）が自身のプロジェクトで実際に使っている運用ルールを置いています。

積極的な配布を目的としたものではなく、あくまで**個人の実務用置き場（公開メモ）**ですが、同じ悩みを持つ方の参考になれば幸いです。自由にお使いください。

---

## 🚀 使い方（プロジェクト設定への追加）

お使いのAIエージェントの指示ファイル（`CLAUDE.md`, `.cursorrules`, `AGENTS.md` 等）に以下をそのまま貼り付けてお使いください。

```markdown
# Autonomous Relay & Safety Protocol (自律息継ぎ＆クォータ防衛プロトコル)

## 1. 自律的な「息継ぎ（ブレーキ）」提案の義務化
以下のいずれかを検知した際、AIは作業を無理に継続せず、直ちにユーザーへ「息継ぎ（中継ぎメモ生成と新セッション移行）」を自律提案すること：
- 1つの大きなタスクや機能実装が完了・着地したとき
- 会話ターン数が長くなり（目安15〜20往復以上）、コンテキストの肥大化・アテンション低下が懸念されるとき
- 重いファイル修正やエラーリカバリーが連続したとき

## 2. 息継ぎの自動実行（セッション終了時）
提案が承認された際、またはユーザーから「一休み」「中継ぎメモ」の指示を受けた際は、直ちに `HANDOFF_RELAY_NOTE.md` をプロジェクトルートに生成・上書き保存すること。
- 完了した決定事項・最新ステータス
- 変更されたファイル一覧
- 次のセッションで直ちに着手すべき課題

## 3. 0フレーム再開（セッション開始時）
新規セッション開始時、自律的に `HANDOFF_RELAY_NOTE.md` を読み込み、直前の文脈・決定事項を復元してから思考を開始すること。
```

---

## 📝 生成される中継ぎメモの例（`HANDOFF_RELAY_NOTE.md`）

```markdown
# 📌 Project Handoff Relay Note (中継ぎメモ)
更新日時: YYYY-MM-DD HH:MM

## 1. 今回の完了事項と着地点
- [確定仕様]: (例: 〇〇機能の実装完了)
- [変更ファイル]: `path/to/file.py`
- [動作確認]: ✅ テスト通過

## 2. 次のセッションで即座に着手すること
1. (例: 次の機能の追加)

## 3. 留意事項・制約（引き継ぎ用）
- (例: 破壊的変更に注意)
```

---

## 🛠️ 同梱の実務スキル集（Practical Skills Catalog）

本リポジトリの `skills/` フォルダには、036 Factory の実務現場で日常的に使用している**汎用的なプロンプトスキル（構造化指示書）**を同梱しています。各自のプロジェクトの `skills/` またはルールにコピーしてお使いいただけます。

* **[🛡️ Logic Auditor Skill](skills/logic-auditor-skill/SKILL.md)**: 
  AIが生成した文章・コードから誇大表現（100%、絶対等）を排除し、事実と前提条件を厳格に自己監査する冷徹査読プロトコル。
* **[🎬 Subtitle Formatter Skill](skills/subtitle-formatter-skill/SKILL.md)**: 
  YouTube/Shorts/リール用に、台本を1行18文字以内・句読点排除・1カット2行制限でリズミカルに整えるテロップ最適化プロトコル。
* **[🤖 AIO Writer Skill](skills/aio-writer-skill/SKILL.md)**: 
  SearchGPT, Perplexity, Gemini 等のAI検索エンジンに最も引用・要約されやすい「結論ファースト＋構造化データ」を生成する執筆プロトコル。

---

## ⚠️ 免責事項（Disclaimer / As-Is）
* 本リポジトリの内容は、作者（036 Factory）の実務環境に合わせて最適化された個人用ノウハウです。
* **MITライセンス（現状有姿・無保証）** に基づき公開しています。各自のプロジェクトに合わせて自由に変更・利用いただけますが、本プロトコルの利用によって生じた一切の損害やトラブル等について、作者は責任を負いかねますのであらかじめご了承ください。

---
Produced with ☕ by [036 Factory](https://036blog.com)
