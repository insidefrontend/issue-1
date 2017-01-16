# セッションスピーカー名前

小山田 晃浩 (@yomotsu)

## プロフィール画像

![](https://www.gravatar.com/avatar/3d8d92b9ff9e708e3e4c247d5ab787ba.png?s=256)

## SNSs、ブログ等

- [Twitter](https://twitter.com/yomotsu)
- [GitHub](https://github.com/yomotsu)
- [Blog](http://yomotsu.net/blog/)

## 所属

[株式会社ピクセルグリッド](https://www.pxgrid.com/)

## セッションタイトル

WebGL/WebVR for FrontEnd Engineer

## セッション概要(100文字程度)

TBA

## アウトライン

こういうの作ってます
-> 3Dフィギュアビューアとか

## ネイティブアプリのような表現【イントロダクション】

いまのWebではHTML/CSSでできなかったアプリみたいなことができる
↓
WebGLで動いているよ
↓
WebGLというと難しい？
OpenGLから派生した、Webの人には馴染みのない技術？
↓
でもいまはさまざまなJSライブラリがある

- three
- babylon
- play canvas
- blend web

APIがあるから、その上にライブラリが作られて
低レベルAPIをWebらしく、馴染み深い形式にしている

音にしても画像にしても、ローレベルAPIがあることが重要だよね

↓
必要なのは、JSの知識 + 基本的な数学、3D用語（どれもすぐ慣れるよ）
↓
threeは抽象化されているのでいい、ドキュメントもおおい。コミュニティも大きい

わからなかったらStackoberflowがある

簡単な例

でもこういうのはもう空きましたよね。
もう少し実践的なお話が本題です

## Webにおける3Dアプリでの問題点と解決例【メインで伝えたいこと】

- ローポリ化しよう(Webはローカルファイルではない、JSONをエディタで開くとこんな感じだよ)
- CPUとGPUは物理的に離れていることを意識しよう
  - JSで毎回メッシュを更新してアップロード vs Shaderで頂点を操作demo
-ドローコールを意識しよう
  - ドローコールを見てみよう
  - 端末種は不特定多数、ドローコール数の違いdemoを見てみよう
  - ドローコールをまとめるには？
- zip圧縮してみよう
  - リスエストが一つになって回線に優しい
  - ロード進行度の管理も楽
  - モデルデータはzipですごく圧縮できる 10MB → 3MB）
  - その他圧縮: http://compress-or-die.com/obj

#まとめ
WebGLはWebフロントエンドの技術。
よりよく使うための道具は、あなたのJS経験の中にもあるはず。
なぜなら、JSのAPIだから。JSのこーどだから

たとえば、Vueを使った例


## WebGLとWebVR
- 本物VR
- 簡易VR

## 関連技術もあるよ
- SIMD
- ASM.js
- WebAssembly
