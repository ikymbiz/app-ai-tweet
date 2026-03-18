
# 🤖 AI Chat & Tweet

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/ja/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/ja/docs/Web/JavaScript)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**AI Chat & Tweet** は、1枚のHTMLファイルで完結する高機能なAIチャット＆X(旧Twitter)連携クライアントです。サーバーやデータベースの構築は一切不要で、ブラウザだけで動作します。

Gemini, GPT-4o, Claude 3などのマルチLLMに対応し、詳細な「ペルソナ設定」や「AIによるツイート自動生成」機能を備えています。チャット履歴やAPIキーはすべてブラウザのローカルDBに安全に保存されます。

---

## ✨ 主な特徴 (Features)

### 💬 マルチLLM対応チャット
- **複数プロバイダ対応**: OpenAI, Google (Gemini), Anthropic に対応（カスタムモデルの追加も可能）。
- **リアルタイムストリーミング**: Web Workerを用いた非同期処理により、UIをブロックせずにAIの回答を滑らかにストリーミング表示します。
- **Markdownレンダリング**: AIの回答に含まれるコードブロックやリストを美しくフォーマット（Marked.js使用）。

### 🎭 高度なペルソナ・役割管理
- **システムプロンプト管理**: 「SNSライター」などの役割（ロール）を自由に作成・切り替え。
- **詳細なプロフィール設定**: 基本情報、思考様式、生活スタイルなど、AIに演じさせる「ペルソナ」を細かく設定可能。
- **🪄 AIプロフィール自動補完**: 一部の情報を入力するだけで、AIが残りのプロフィール項目を想像して自動生成・補完する機能を搭載。

### 🐦 X (Twitter) 連携＆ツイート生成機能
- **AIツイート案生成**: ニュースのURLや今の感情など短いトリガーを入力するだけで、設定したペルソナに基づいた140文字程度のツイート案をAIが作成。
- **自動 / 手動投稿**: AIの回答をそのまま自動ツイートするモードや、生成結果をプレビュー＆編集してから手動投稿する機能を搭載。

### 🗄️ 完全なローカルデータ管理
- **IndexedDB採用**: チャット履歴、プロンプト、各種設定、APIキーはすべて端末のブラウザ内に保存されます（外部サーバーへの送信は各AIプロバイダとTwitterへのAPIリクエストのみ）。
- **履歴管理**: チャット履歴の検索、スレッドごとの保存。
- **インポート / エクスポート**: JSON形式での履歴バックアップ・復元。
- **ファイル保存**: チャット内容をMarkdownまたはJSON形式でローカルファイルとして直接保存（File System Access API利用）。

### 📱 洗練されたUI/UX
- Tailwind CSSによるモバイルファーストなレスポンシブデザイン。
- スライドインメニュー、モーダルダイアログ、トースト通知。
- PWA（Progressive Web App）対応。スマホのホーム画面に追加してネイティブアプリのように利用可能。
- WakeLock APIによる生成中のスリープ（画面消灯）防止。

---

## 🚀 使い方 (Getting Started)

本アプリはビルドプロセスやバックエンドサーバーを必要としません。

1. **ダウンロード**: このリポジトリの `index.html`（または提供されたHTMLファイル）をダウンロードします。
2. **ブラウザで開く**: ダウンロードしたファイルをダブルクリックして、Chrome, Edge, Safariなどのモダンブラウザで開きます。
3. **APIキーの設定**:
   - 画面右上の歯車アイコン（⚙️）をクリックして設定画面を開きます。
   - 利用したいAIプロバイダ（Google, OpenAI, Anthropic）のAPIキーを入力します。（※キーはブラウザ内にのみ保存されます）
4. **チャット開始**:
   - メッセージを入力し、送信ボタンを押してAIとの対話を開始します。

---

## 💡 詳細な使い方

### 👤 ペルソナの作成とAI自動入力
設定画面 > 「プロフィール管理 (ペルソナ)」から追加ボタンを押します。「氏名」や「職業」など思いつく項目だけを入力し、**「🪄 AI自動入力」** ボタンを押すと、設定中のLLMが残りの項目（思考様式や一日のスケジュールなど）を矛盾なく生成して埋めてくれます。

### 📝 AIによるツイート生成
チャット入力欄左のTwitterアイコン（🐦）をクリックして投稿モーダルを開きます。
青い枠内の「AIにツイート案を作成させる」エリアに、「今日のランチが美味しかった」など簡単なメモを入力し、**「🤖 ツイート案を生成」** を押すと、現在のペルソナ設定を反映したバズりやすいツイート案が生成されます。

---

## 🛠️ 技術スタック (Technologies)

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: [Tailwind CSS](https://tailwindcss.com/) (CDN)
- **Icons**: [FontAwesome 6](https://fontawesome.com/)
- **Markdown**: [Marked.js](https://marked.js.org/)
- **Storage**: IndexedDB (Native API)
- **Concurrency**: Web Workers
- **APIs**: OpenAI API, Google Gemini API, Anthropic API, Twitter(X) API v2

---

## ⚠️ 注意事項 (Disclaimer & Notes)

- **APIリクエストの課金について**: 本アプリに入力したAPIキーによるAIプロバイダの利用料金は、ユーザー自身のアカウントに請求されます。APIキーの流出には十分ご注意ください。
- **Twitter(X) APIのCORS制限について**: ブラウザから直接Twitter APIへリクエストを送信すると、通常CORS（Cross-Origin Resource Sharing）エラーが発生します。本コード上のTwitter投稿機能は、フロントエンド検証用のバイパスデモ（エラーを無視して成功とみなす処理）が含まれています。実際に運用する場合は、CORSプロキシサーバーを経由させるか、ブラウザ拡張機能等でCORSを回避する必要があります。
- **データ消失のリスク**: データはブラウザのローカルストレージ（IndexedDB）に保存されます。ブラウザのキャッシュをクリアするとデータが消去される可能性があるため、定期的な「Export」機能によるバックアップを推奨します。

---

## 📄 ライセンス (License)

このプロジェクトは [MIT License](LICENSE) のもとで公開されています。自由に改変・再配布が可能です。
```

### README作成におけるポイント：
1. **視覚的な魅力**: バッジや絵文字を適切に配置し、パッと見の印象を良くしています。
2. **技術的特徴のハイライト**: 単なるチャットUIではなく、「Web Workerによるストリーミング」「IndexedDBによる完全ローカル管理」「PWA対応」など、コードの技術的に優れた部分を強調しました。
3. **独自の機能の説明**: ペルソナ機能における「AI自動補完」や、ツイート画面での「AIツイート案生成」など、このアプリ固有の便利な機能を使い方として分かりやすく記述しています。
4. **誠実な注意事項**: X(Twitter)の投稿において、フロントエンド単体ではCORSエラーになるというWeb技術の前提と、コード内で行われているデモ用の例外処理（`// CORS bypass demo`）について言及し、開発者向けの正確なドキュメントにしています。