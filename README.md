
**AI Chat & Tweet** は、複数の最先端LLM（Gemini, GPT-4o, Claude 3）をひとつの画面で切り替えながら利用でき、AIの生成した回答を直接 Twitter (X) に投稿できる、ブラウザ完結型のシングルページアプリケーション（SPA）です。

## ✨ 主な機能 (Features)

* 💬 **マルチLLM対応**
  * OpenAI, Google, Anthropic の API を直接サポート。
  * 独自のエンドポイントを持つ「カスタムモデル」の追加も可能。
* 🐦 **シームレスな Twitter (X) 連携**
  * AIの回答を引用し、文字数（280文字）を確認しながら手動ツイート。
  * 「AIの生成完了時に自動投稿」するオートモード搭載。
* 🎭 **プロンプト（役割）管理**
  * 「SNSライター」「翻訳家」などのシステムプロンプトを事前に登録し、ワンタップで切り替え。
* 🔒 **プライバシー・ローカルファースト**
  * APIキーやチャット履歴はすべてブラウザの **IndexedDB にローカル保存** されます。作者や第三者のサーバーには一切データが送信されません。
* 💾 **高度なファイル管理**
  * チャット履歴の JSON エクスポート / インポート。
  * *File System Access API* を利用した、Markdown または JSON 形式でのローカルファイル保存。
* ⚡ **モダンで快適な UX**
  * Web Worker を活用した非同期のストリーミング描画。
  * Tailwind CSS を用いたモバイルファーストのレスポンシブデザイン。
  * 生成中の画面スリープを防ぐ WakeLock API 対応。

## 🛠 技術スタック (Tech Stack)

このアプリケーションは、ビルドツールやバックエンドを必要としない **単一のHTMLファイル** で構成されています。

* **Frontend**: HTML5, Vanilla JavaScript
* **Styling**: Tailwind CSS (CDN)
* **Markdown**: Marked.js (CDN)
* **Icons**: FontAwesome (CDN)
* **Storage**: IndexedDB (Native API)

## 🚀 使い方 (Getting Started)

### 1. 起動
特別なインストールやビルドは不要です。
ダウンロードした `index.html` をブラウザで直接開くか、ローカルサーバー経由で起動してください。

```bash
# Node.jsがインストールされている場合（npxを使用）
npx serve .
```

### 2. 初期設定（APIキーの登録）
1. 画面右上の **「⚙️（設定）」** アイコンをクリックして設定パネルを開きます。
2. 「APIキー設定」の項目に、利用したいプロバイダ（Google, OpenAI, Anthropic）の API Key を入力します。
   * *※入力内容は自動的に端末内に暗号化されず保存されます。共有PCでの利用にはご注意ください。*
3. 利用したい「使用モデル」と「役割」を選択します。

### 3. Twitter (X) 連携の設定
1. 設定パネルの「X (Twitter) 連携」から「追加」ボタンを押します。
2. 表示名と、Twitter API v2 の **User Access Token (Bearer Token)** を入力して保存します。
3. チャット入力欄の横にある 🐦（Twitterアイコン）をクリックすると、現在の回答内容を引用したツイート作成画面が開きます。

## ⚠️ 注意事項と制約 (Limitations)

* **CORSの制約について（Twitter API）**
  * 本アプリケーションはフロントエンドから直接 Twitter API (`api.twitter.com`) に対して POST リクエストを送信するアーキテクチャになっています。
  * ブラウザの仕様上、直接通信すると **CORSエラー** が発生します。実運用環境でTwitter投稿を正常に機能させる場合は、CORSヘッダーを付与するバックエンドのプロキシサーバーを経由するように `fetch` の URL を改修する必要があります。
  * *(※現在のコードでは、CORSエラー発生時もUIの挙動を確認できるよう、デモ用のフォールバック処理が組み込まれています)*
* **ブラウザの互換性**
  * 「ローカルファイルに保存」機能は `showSaveFilePicker` をサポートするモダンブラウザ（Chrome, Edge等）でのみ動作します。FirefoxやSafariでは機能しない場合があります。

## 📝 カスタマイズ (Customization)

コード内の以下の変数を編集することで、デフォルトのモデルやシステムプロンプトを変更できます。

```javascript
// デフォルトのモデルリスト
const defaultModels = [
    { id: 'gemini-2.5-flash', name: 'Gemini 2.5 Flash', provider: 'google' },
    { id: 'gpt-4o', name: 'GPT-4o', provider: 'openai' },
    // ...
];

// デフォルトの役割リスト
const defaultRoles = [
    { id: 'default', name: 'デフォルト', prompt: 'あなたは優秀なAIアシスタントです...' },
    { id: 'sns_writer', name: 'SNSライター', prompt: 'あなたはバズるSNS投稿を作成するプロのライターです...' }
];
```

## 📄 ライセンス (License)

このプロジェクトは [MIT ライセンス](https://opensource.org/licenses/MIT) のもとで公開されています。自由に改変、再配布、商用利用が可能です。
```

### このREADMEのポイント
1. **バッジと絵文字**を活用し、リポジトリの顔として見栄えを良くしています。
2. **ローカル完結型**であるというセキュリティ面での大きなメリットを強調しています。
3. コードを分析して判明した**Twitter APIのCORS問題**について「注意事項」として正直かつ技術的に明確に記載し、開発者がつまづかないように配慮しています。
4. 単一ファイル構成である手軽さをアピールし、セットアップの手間がゼロであることを伝えています。