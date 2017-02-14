# セッションスピーカー名前
原 一成 (@herablog)

## プロフィール画像
![herablogプロフィール画像 FF7のシドのイラストから引用](https://pbs.twimg.com/profile_images/2300848944/ato0j2c85jxqfb5mxt8m_400x400.jpeg)

## SNSs、ブログ等

- [Twitter](https://twitter.com/herablog)
- [Ownd](https://herablog.amebaownd.com/)

## 所属

[株式会社サイバーエージェント](https://www.cyberagent.co.jp/)

## セッションタイトル

アメブロ2016: 実録、アメブロフロントリニューアル275日

## セッション概要(100文字程度)

アメブロは2016年9月にシステムリニューアルをしました。使用した技術は[ブログ記事](https://developers.cyberagent.co.jp/blog/archives/636/)に記載していますので本セッションでは、その進め方やパフォーマンスチューニングをどのようにしていったかについてお伝えします。

## アウトライン
- アメブロ2016？
  - アメブロのモバイル面をリニューアルしたプロジェクト
  - Isomorphicで速度改善をして成果があった
  - 成果
  - 採用技術はこんな感じ
  - 詳しくはブログや記事を
- 今日は主に速度改善をしたフローをご紹介
  - 275日は単純に日にちを足しただけ
- コンセプト (当時のメモから振り返る)
  - できるだけ普通(その時点で一番有名)のツールを使う
    - 情報が多い
    - 色んなひとが触れる
  - フロントエンドサーバー化
    - node
    - 表示に関わるところは誰でもさっと変えられるようにする
    - できるだけHTMLで返し、js, cssの容量減らす
    - 将来のhttps, HTTP/2に向けた設計
   - 設計を変えつつ運営していくことを当たり前にする
  - JS
    - React
    - Flux
    - ES6, 7
    - ESLint
    - 型はどうしようかなあ
  - CSS
    - PostCSS
    - BEM
    - stylelint
    - Style Guide (結果的にはこのメンテが大変そうなのでWeb管理になった)
  - HTML
    - モダンなMETA
    - アクセシビリティ
    - AMP仕様決まってたらやってみるか
  - Build
    - gulp
    - package.json中心
  - Store
    - DBは持たないが、軽いキャッシュ欲しい
  - CI
    - 検討する
  - モニタリング
    - kibana？
    - パフォーマンスを簡単にモニタリングできるようにする
  - Docker? オンプレで上手くいくの？
- まず調査 SpeedCurve (当時のissueから)
  - Blocking Resorces 多い
  - JSの非同期化
  - HTML容量多い
  - statキャッシュの最適化
  - Webfontの統合
  - いらない読み込みの削除
  - 画像のCSS化
- 基本設計ぎめ
  - SSR, LazyLoad
  - SPAはあとから追加した
  - モダンなワークフロー
    - Git, Lint, CI, deployment
    - コケるテスト
- ひたすら実装
  - まずは、しっかりと作り込む
  - 作っては壊すを繰り返す
  - リリース前からリリース練習をする
  - いい感じになってきた
  - 負荷試験
    - 過去のアクセスログを元に検証
    - NewRelic
  - 事件!! (最初の結果はよくなかった)
    - レスポンスの遅さ, CPU利用率の高さ
    - アメブロのアクセスの多さ
    - コンポーネントの増加
- ひたすらチューニング
  - Docker, Linux設定
  - Rancher, HAProxy設定
    - 1host1LB化
  - Optimization killers
    - メモリリーク
    - setTimeout
    - react defaultProps
    - try catch
    - renderToString
  - キャッシュ
    - on-memory and cache servers
    - Redis vs Memcached
    - APIデータと生成したHTML自体をキャッシュ
    - データ更新には内部APIを用意
 - 2ヶ月延びてプレッシャーをかけられる
- なんとかリリース
  - 結果としてPremature optimization is the root of all evil
  - チューニング自体が目的にならないことはよかった
- お疲れ様でした
