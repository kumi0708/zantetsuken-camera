# 斬鉄剣カメラ

FF6風エフェクトのWebカメラアプリです。シャッターを押すとオーディンが現れ、斬鉄剣で人物を両断します。


## デモ

GitHub Pages で公開している場合はこちら → `https://ユーザー名.github.io/zantetsuken-camera/`

---

## 使い方

1. ブラウザで `index.html` を開く（またはGitHub PagesのURL）
2. カメラへのアクセスを**許可**する
3. **「斬鉄剣を研いでいる…」**が消えるまで待つ
4. シャッターボタンを押す
5. 人物が写っていればオーディンが斬ってくれます

---

## 注意事項

### ⚠️ 初回はダウンロードに時間がかかります

起動時にAI人物検出モデル（TensorFlow.js BodyPix）を自動ダウンロードします。  
回線速度にもよりますが、**初回は10〜30秒ほどかかる**場合があります。  
画面下部の「斬鉄剣を研いでいる…」が消えてからシャッターを押してください。  
2回目以降はブラウザキャッシュが効くため速く起動します。

### 🌐 インターネット接続が必要です

以下のリソースを外部CDNから読み込んでいます。**オフラインでは動作しません。**

- TensorFlow.js（AIエンジン）
- BodyPix モデルデータ（人物検出AI）
- DotGothic16（Google Fonts）

### 📷 カメラ許可が必要です

ブラウザからカメラへのアクセス許可を求められます。許可しないと起動しません。  
撮影した映像はすべてブラウザ内で処理されます。外部サーバーには送信されません。

### 🔒 HTTPSまたはlocalhostで開く必要があります

カメラAPIはセキュアな接続でのみ動作します。

- ✅ GitHub Pages（`https://`）
- ✅ ローカルの開発サーバー（`localhost`）
- ❌ ファイルを直接ダブルクリック（`file://`）→ カメラが使えません

ローカルで試す場合は以下のいずれかを使ってください。

```bash
# Python 3
python -m http.server 8000

# Node.js (npx)
npx serve .
```

その後 `http://localhost:8000` をブラウザで開きます。

---

## 動作確認ブラウザ

| ブラウザ | 対応 |
|---|---|
| Chrome / Edge（最新版） | ✅ |
| Safari（iOS / macOS） | ✅ |
| Firefox | ✅ |

---

## ファイル構成

```
zantetuken/
├── index.html    # アプリ本体
├── a-odin.gif    # オーディンスプライト
├── zan.gif       # 参考アニメーション
├── moji.png      # ウィンドウデザイン参考
└── README.md
```

---

## 技術スタック

- HTML / CSS / JavaScript（フレームワークなし）
- [TensorFlow.js](https://www.tensorflow.org/js) + [BodyPix](https://github.com/tensorflow/tfjs-models/tree/master/body-pix) — 人物セグメンテーション
- [DotGothic16](https://fonts.google.com/specimen/DotGothic16) — ドット風フォント
