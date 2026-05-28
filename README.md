# Weekly Presentation Trainer

英語スピーキング練習のための個人用Webアプリケーション。週次プレゼンテーションのスクリプト確認・リスニング・重要フレーズ復習を一つの画面で完結できる。

**アクセスURL：** https://708Nishi.github.io/Private-English-presentation-trainer/

---

## 概要

呼吸器内科・臨床微生物学を専門とする研究者が、週次で行う1〜2分程度の英語プレゼンテーション練習を効率化するために開発した個人用ツール。

### 主な機能

- **スクリプト表示**：重要フレーズが自動ハイライト表示される
- **リスニング**：OpenAI TTS（tts-1-hd）による高品質な音声読み上げ
- **音声キャッシュ**：生成した音声をブラウザに保存し、2回目以降は即座に再生
- **繰り返し再生**：🔁ボタンで自動ループ再生
- **フラッシュカード**：抽出されたキーフレーズを表裏でめくりながら復習
- **List view**：フレーズ一覧と日本語解説・例文を一覧表示
- **データ同期**：GitHub Gistを介してPC・スマートフォン間でデータを共有

---

## 技術構成

| 項目 | 内容 |
|---|---|
| ホスティング | GitHub Pages（無料プラン） |
| データ保存 | GitHub Gist（スクリプト・フレーズJSON） |
| フレーズ抽出 | Anthropic API（claude-haiku-4-5） |
| 音声生成 | OpenAI API（tts-1-hd） |
| 音声キャッシュ | ブラウザ localStorage（base64） |
| フロントエンド | HTML / CSS / Vanilla JS（単一ファイル） |

---

## セットアップ

### 必要なもの

- GitHubアカウント
- Anthropic APIキー（[console.anthropic.com](https://console.anthropic.com/settings/keys)）
- OpenAI APIキー（[platform.openai.com](https://platform.openai.com/api-keys)）
- GitHub Personal Access Token（scopeは`gist`のみ、有効期限90日推奨）
- GitHub Gist（`pt_data.json` という名前のファイルを含むSecret Gist）

### 初期設定手順

1. このリポジトリをPublicで作成する
2. `index.html` をリポジトリにアップロードする
3. Settings → Pages → Branch を `main` に設定して Save する
4. アプリのURLにアクセスする
5. 「⚙ APIキーを設定」から以下を入力して保存する
   - Anthropic API Key
   - OpenAI API Key
   - GitHub Personal Access Token

> **注意**：APIキーはブラウザの`localStorage`にのみ保存され、外部には送信されない。PC・スマートフォンそれぞれで初回のみ設定が必要。

---

## 使い方

### PC（週1回・スクリプト更新時）

1. アプリにアクセスする
2. 「✏️ 更新」から入力画面を開く
3. 英語スクリプトを貼り付ける（目安：280〜320語）
4. 「✨ 抽出して保存」をクリックする
5. Claude APIがキーフレーズを自動抽出し、GitHub Gistに保存する

### スマートフォン（毎日の練習）

1. アプリのURLにアクセスする（ホーム画面に追加推奨）
2. 「保存済みスクリプトあり」バナーの「読み込む」をタップする
3. ▶ Play でスクリプトを聴く（🔁で繰り返し再生）
4. ハイライトされたフレーズをタップするとフラッシュカードにジャンプする
5. フラッシュカードをタップして裏返し、意味・例文を確認する

---

## ファイル構成

```
/
├── index.html    # アプリ本体（HTML / CSS / JS 単一ファイル）
└── README.md     # このファイル
```

---

## API利用コスト目安

| サービス | 用途 | 目安 |
|---|---|---|
| Anthropic API | フレーズ抽出（週1回） | 月$0.01未満 |
| OpenAI API | 音声生成（初回のみ、以降キャッシュ） | 月$0.03〜$0.10程度 |

---

## 更新履歴

| 日付 | 内容 |
|---|---|
| 2026-05 | 初版リリース |
| 2026-05 | OpenAI TTS対応・音声キャッシュ追加 |
| 2026-05 | 繰り返し再生ボタン追加 |
| 2026-05 | スクリプト内フレーズハイライト追加 |
| 2026-05 | PC・スマートフォン対応レスポンシブUI |
