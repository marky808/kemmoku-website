# 見目社会保険労務士事務所 Webサイト 更新マニュアル

このサイトは**Pure HTML/CSS/JavaScript**で作成されており、ビルド不要で動作します。

## 🚀 初回セットアップ（10分）

### 1. GitHubリポジトリ作成

1. GitHub ( https://github.com ) にログイン
2. 「New repository」をクリック
3. リポジトリ名: `kemmoku-sr-website` など
4. 「Public」または「Private」を選択
5. 「Create repository」をクリック

### 2. ファイルをGitHubにアップロード

```bash
# ターミナル/コマンドプロンプトで実行
cd /path/to/kemmoku-sr-website
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/kemmoku-sr-website.git
git push -u origin main
```

### 3. Netlifyにデプロイ

1. Netlify ( https://www.netlify.com/ ) にアクセス
2. 「Sign up」でGitHubアカウントで登録
3. 「Add new site」→「Import an existing project」
4. 「GitHub」を選択
5. 作成したリポジトリを選択
6. 「Deploy site」をクリック

**完了！** URLが自動生成されます（例: `https://random-name-12345.netlify.app`）

### 4. カスタムドメイン設定（オプション）

Netlifyの管理画面で「Domain settings」から独自ドメインを設定できます。

---

## ✏️ 日常的な更新方法

### テキストを変更する

1. VSCodeで `index.html` を開く
2. 変更したい箇所を編集（例: 住所、電話番号、文章など）
3. 保存

```bash
git add index.html
git commit -m "テキスト更新"
git push
```

**30秒後に本番反映！**

---

### 写真を差し替える

#### 方法1: 同じファイル名で上書き（推奨）

```bash
# 新しい写真を同じファイル名で上書き
cp 新しい写真.jpg images/profile_0.png

git add images/profile_0.png
git commit -m "プロフィール写真更新"
git push
```

#### 方法2: 新しいファイル名で追加

1. `images/` フォルダに新しい写真を追加
2. `index.html` で画像パスを変更

```html
<!-- 変更前 -->
<img src="images/profile_0.png" alt="見目悦男">

<!-- 変更後 -->
<img src="images/new-photo.jpg" alt="見目悦男">
```

```bash
git add images/new-photo.jpg index.html
git commit -m "写真追加"
git push
```

---

### 色を変更する

`index.html` の `<style>` 内、`:root` セクションを編集：

```css
:root {
    --primary-color: #3d5a80;    /* メインカラー */
    --secondary-color: #98c1d9;  /* サブカラー */
    --accent-color: #ee6c4d;     /* アクセントカラー */
    /* ... */
}
```

カラーコード参考: https://color.adobe.com/ja/

---

### セクションを追加/削除する

#### セクション追加

1. 既存セクションをコピー
2. `id` を変更（例: `id="new-section"`）
3. ナビゲーションにリンク追加

```html
<!-- ナビゲーションに追加 -->
<li><a href="#new-section">新セクション</a></li>

<!-- セクション本体 -->
<section id="new-section" class="about">
    <div class="container">
        <h2 class="section-title">新しいセクション</h2>
        <p class="section-subtitle">Subtitle</p>
        <!-- コンテンツ -->
    </div>
</section>
```

#### セクション削除

1. 削除したいセクション全体を削除
2. ナビゲーションのリンクも削除

---

## 🗺️ Googleマップの変更

現在のマップは仮のものです。正しい住所に変更する方法：

1. Google Maps ( https://www.google.com/maps ) で住所を検索
2. 「共有」→「地図を埋め込む」をクリック
3. HTMLコードをコピー
4. `index.html` の以下の部分を差し替え

```html
<iframe src="ここに新しいURL" allowfullscreen="" loading="lazy"></iframe>
```

---

## 📧 お問い合わせフォームの設定

**Netlify Formsは自動で有効**になります。追加設定不要！

### 送信テスト

1. サイトにアクセス
2. フォームに入力して送信
3. Netlifyの管理画面「Forms」タブで受信確認

### 通知設定

Netlify管理画面で通知先メールアドレスを設定できます：

1. 「Site settings」→「Forms」→「Form notifications」
2. メールアドレスを追加

---

## 🎨 デザインの微調整

### 余白の調整

```css
section {
    padding: 5rem 2rem;  /* 上下 左右 */
}
```

### フォントサイズの変更

```css
.hero h1 {
    font-size: 3.2rem;  /* ヒーローの見出し */
}

.section-title {
    font-size: 2.2rem;  /* セクションタイトル */
}
```

### ホバー効果の変更

```css
.service-card:hover {
    transform: translateY(-5px);  /* 持ち上がる量 */
}
```

---

## 📱 動作確認

### ローカルでの確認

VSCodeの「Live Server」拡張機能を使用：

1. VSCodeで `index.html` を開く
2. 右クリック →「Open with Live Server」

ブラウザで自動表示されます。

### 本番反映の確認

```bash
git push
```

実行後、30秒〜1分でNetlifyのURLに反映されます。

---

## 🔧 トラブルシューティング

### 画像が表示されない

- ファイル名が正しいか確認（大文字小文字も区別）
- パスが正しいか確認（`images/profile_0.png`）
- Gitに追加されているか確認（`git status`）

### フォームが動かない

- `<form>` タグに `data-netlify="true"` があるか確認
- Netlifyにデプロイされているか確認（ローカルでは動作しません）

### 更新が反映されない

- ブラウザのキャッシュをクリア（Ctrl + Shift + R / Cmd + Shift + R）
- Netlifyのデプロイログを確認

---

## 📞 サポート

質問があれば、このマニュアルを参考にしてください。
それでも解決しない場合は、開発者に連絡してください。

---

## 📝 ファイル構成

```
kemmoku-sr-website/
├── index.html          # メインHTMLファイル（これを編集）
├── images/             # 画像フォルダ
│   ├── profile_0.png   # メインプロフィール写真
│   ├── profile_1.png
│   ├── profile_2.png
│   ├── profile_3.png
│   ├── profile_4.jpeg
│   ├── profile_5.png
│   └── README.md       # 画像の説明
├── netlify.toml        # Netlify設定（触らない）
└── README.md           # このファイル
```

---

**Happy Coding! 🚀**
