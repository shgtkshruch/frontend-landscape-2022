---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Frontend Landscape 2022

<!--
「Frontend Landscape 2022」というタイトルで発表させていただきます。
よろしくお願いします。
-->

---

# Self Introduction

- 城内 栄剛
- 2022 年 8 月入社
- Xuan プロジェクト・フロントエンドエンジニア

<!--
簡単に自己紹介です。

名前は城内と言います。

今年の8月にエス・エム・エスに入社しました。

今は、Xuan プロジェクトでフロントエンドエンジニアとして働いています。
-->

---

# 今日のトピック

<br>

#### 今年のフロントエンドの動きを、以下の 3 つの観点で紹介

<br>

- Browser
- Runtime
- Framework

<!--
今日のトピックです。

今年のフロントエンドの動きを、 ブラウザ、JavaScript ランタイム、フレームワークという3つの観点で超ざっくり振り返ってきます。
-->

---

# IE 11 のサポートが終了 👋

- 2022 年 6 月 15 日に、IE 11 のサポートが終了
- サポート対象のブラウザのベースラインが上がる
- 新しい HTML・CSS・JavaScript の API を使用可能に

<img class="mt-5 mx-auto w-75%" src="/ie11.png" />

<!--
まずブラウザからです。

ブラウザ界隈の大きな動きとしては、 今年の6月に IE 11 のサポートが公式に終了しました。

これによって、サポートするべきブラウザのベースラインが上がって、新しい WEB の API が使いやすい状況が出来つつあります。
-->

---

- モダンブラウザの間では、Interop 2022 を通じてブラウザ間の互換性を担保して新機能を実装
- Interop: 2019 年に始まった、Web ブラウザ(Chrome, Safari, Firefox)の相互運用性を高める取り組み
- 新しい API
  - `<dialog>`
  - `<img loading="lazy">`
  - `@layer`

<img class="w-35% absolute right-15 bottom-10" src="interop-2022.png">

<!--
モダンブラウザの間では、Interop という取り組みを通じて新機能の実装が進みました。
Interop は、Chrome・Safari・Firefox などのブラウザ間の相互運用性を高めつつ、新しい WEB の API を実装していく取り組みです。

使っていきたい機能としては、
モーダルなどサブウィンドウを表示できる `dialog` 要素。
画像が ViewPort に入ってきたときに遅延読み込させることに利用できる `loading` 属性。
CSS に詳細度とは別のカスケードを追加できる `@layer`。
などがあります。

従来は JavaScript でおこなっていた処理や複雑なレイアウトも、HTML や CSS の API を利用して実装できることが増えています。
-->

---

# Runtime

## Node.js

- 2022 年 4 月に v18 がリリース
- experimental で fetch をサポート

<img class="absolute top-19 right-35 w-11%" src="node.png">

<!--
次にランタイムの動きを見ていきます。

サーバーサイドで JavaScript を実行するランタイムとしては、 Node.js が有名だと思いますが、最近では新しいランタイムが登場してきています。

Node.js は、今年の4月にバージョン18がリリースされました。
experimental ではありますが、WEB API の1つである fetch がサポートされました。
これは WEB の API が WEB を超えていく一つのきっかけとして、大きな動きだったなと個人的には思っています。
-->

---

# Runtime

## Node.js

- 2022 年 4 月に v18 がリリース
- experimental で fetch をサポート

## Deno

- Rust で実装された TypeScript が動く JavaScript のランタイム
- 2020 年に v1.0.0 がリリース
- 2022 年 11 月に npm モジュールをサポート

<img class="absolute top-19 right-35 w-11%" src="node.png">
<img class="absolute top-63 right-35 w-11%" src="deno.png">

<!--
Deno は、Rust で実装された JavaScript ランタイムです。
今年の11月には npm のモジュールがサポートされて、Node.js の資産の多くを Deno でも利用することができるようになりました。
-->

---

# Runtime

## Node.js

- 2022 年 4 月に v18 がリリース
- experimental で fetch をサポート

## Deno

- Rust で実装された TypeScript が動く JavaScript のランタイム
- 2020 年に v1.0.0 がリリース
- 2022 年 11 月に npm モジュールをサポート

## Bun

- Zig で実装された、パフォーマンス重視の JavaScript ランタイム
- 2022 年 7 月に v0.1.1 がリリース

<img class="absolute top-19 right-35 w-11%" src="node.png">
<img class="absolute top-63 right-35 w-11%" src="deno.png">
<img class="absolute top-106 right-32 w-13%" src="bun.png">

<!--
また、今年かなり注目されたのは、7月に発表された Bun です。
Zig で実装された JavaScript ランタイムで、Node.js や Deno よりも高速に動作することを押していて、かなり話題になりました。
-->

---

# Edge Runtime

## Cloudflare Workers

- Cloudflare の CDN 上で動作する JavaScript ランタイム
- Cloudflare Workers のコードから利用できるミドルウェア
  - KV: KVS
  - R2: S3 互換のオブジェクトストレージ
  - D1: SQLite

<img class="absolute top-30 right-31 w-25%" src="cloudflare-workers.png">

<!--
サーバーサイドだけでなく、CDN のようなエッジで動くランタイムも出てきています。

Cloudflare Workers は、CDN 上で動作するランタイムです。

Service Worker のようにリクエストに任意の処理を挟むことができるので、CDN 本来のキャッシュの機能をプログラムを介して柔軟に利用できるようになっています。

キーバリューストアや S3 互換のストレージ、今年の5月に発表した SQLite ベースのデータベースなど、様々なミドルウェアをリリースしています。
-->

---

# Edge Runtime

## Cloudflare Workers

- Cloudflare の CDN 上で動作する JavaScript ランタイム
- Cloudflare Workers のコードから利用できるミドルウェア
  - KV: KVS
  - R2: S3 互換のオブジェクトストレージ
  - D1: SQLite

## Edge Runtime

- Vercel の Edge で動作する JavaScript ランタイム
- Next.js の SSR が動く（experimental）
- Vue / Angular など他のフレームワークへの対応も視野に入れている

<img class="absolute top-30 right-31 w-25%" src="cloudflare-workers.png">
<img class="absolute top-80 right-19 w-27%" src="edge-runtime.png">

<!--
Next.js の開発元である Vercel も、Edge で動作するランタイムを今年の6月にリリースしました。
experimental ではありますが、Next.js の SSR が動作するようになっています。
Vue や Angular など他のフレームワークへの対応も視野に入れていて、 将来的には CDN 上で SSR をする未来が来るかもしれません。
-->

---

# WinterCG

- WEB ブラウザ以外の Runtime で、共通して使用できる API の標準化を目指したコミュニティグループ
  - 今年の 5 月に Cloudflare のブログで発表された
- W3C や WhatWG の仕様の尊重しつつ、Runtime 共通の仕様を定義する

<img class="mt-5 mx-auto w-70%" src="winter-cg.png">
<img class="mt-5 mx-auto w-70%" src="winter-cg-company.png">

<!--
こうしてランタイムが増えてくる中で課題になるのが、あるランタイムで実装したコードが他のランタイムでも動くのかということです。

例えば、Node.js のコードが Cloudflare Workers でも動くと便利ですが、現状では Node.js のコアの API を使っているコードだと動かない場合があります。

こうした相互運用性の課題を解決するために、WinterCG というグループが今年の5月に立ち上がりました。

Node.js・Deno・Cloudflare Workers など、様々なランタイム上で利用できる共通の仕様を定義することを目標にしたコミュニティグループです。

新しいランタイムが登場して機能やパフォーマンスの差別化をする一方で、WinterCG のようにランタイムを横断して共通の仕様を作る動きも出てきていて、
差別化と共通化が同時に進んでいるのが、今のランタイム界隈の動きの特徴だと思います。
-->

---

# Framework

- React なら Next.js、Vue.js なら Nuxt.js のように、フレームワーク単位で採用される事例が増えた
  - React / Vue.js を単独のライブラリとして利用する話が少なくなってきた
- Svelte が出てきて以降は、あまり大きな動きがなく落ち着いている印象だったが...
- 今年の夏頃からは、新しい観点に注目したフレームワークが登場してきた
  - Astro
  - Qwik

<!--
最後にフレームワークです。

近年の傾向としては、React なら Next、Vue なら Nuxt のように、フレームワーク単位で採用される事例が増えてきたなと思います。

Svelte が出てきて以降はあまり大きな動きがなく落ち着いていたのですが、今年の夏頃からは新しい観点に注目した Astro や Qwik というフレームワークが登場してきました。
これらのフレームワークがどのような背景から出てきたかを見ると、今のフロントエンドの流れが見えてくるので簡単に紹介します。
-->

---

# 観点

- Pre-rendering
  - 事前にページを生成する仕組み
    - SSR (Server Side Rendering)
    - SSG (Static Site Generation)
    - ISR (Incrimental Static Regeneration)

<!--
フロントエンドでフレームワークを採用する観点の一つとしては、Pre-rendering というものがあります。
パフォーマンスや UX を最適化するために事前にページを生成する仕組みのことで、 SSR / SSG / ISR などいくつかの手法があります。

Next が便利なのは、ページ単位で Pre-rendering の手法を変えられるところで、動的なページは SSR、Static なページは SSG といったようにページの特性に合わせてレンダリング方法を選択できます。
-->

---

# 観点

- Pre-rendering
  - 事前にページを生成する仕組み
    - SSR (Server Side Rendering)
    - SSG (Static Site Generation)
    - ISR (Incrimental Static Regeneration)
- Hydration
  - Pre-rendering した HTML にイベントハンドラを設定して、クライアンド上で Reactive に動くようにすること
  - Hydration が完了しないと、画面に表示されていたとしても操作がでない（不気味の谷）
  - 主要なフレームワークでは、ページ単位で Hydration が行われる

<!--
今年話題になったフレームワークは、Pre-rendering の後に行われる Hydration という処理に注目したものが多かったです。
Hydration は、Pre-rendering した HTML にイベントハンドラを設定して、クライアント上でリアクティブに動くようにする処理のことです。

Hydration が完了しないと、画面に UI が表示されていたとしても操作ができない状態になります。
例えば、ボタンが画面に表示されていても、クリックしたら何も反応しない、という状態が発生することになります。

Next など主要なフレームワークでは、ページ単位で Hydration が行われるので、ページサイズが大きくなると Hydration の処理も重くなるというのが課題になっていました。
-->

---

# 新しい Framework の Hydration 戦略

## Astro

- 2022 年 8 月にリリースされたフレームワーク
- ページのパーツ単位の Hydration（Partial Hydration）
- 画面に表示される要素を優先的に Hydration する

<img class="absolute top-30 right-40 w-10%" src="astro.png">

<!--
この課題を解決する流れの中で、新しいフレームワークが出てきたのが2022年の特徴だと思います。

今年の8月にリリースされた Astro は、ページのパーツ単位で Hydration ができるようになっています。
Hydration する優先順位を設定できるので、ページ上部のパーツから Hydration して、ページ下部のパーツは後から Hydration する、といったことができるようになっています。
-->

---

# 新しい Framework の Hydration 戦略

## Astro

- 2022 年 8 月にリリースされたフレームワーク
- ページのパーツ単位の Hydration（Partial Hydration）
- 画面に表示される要素を優先的に Hydration する

## Qwik

- builder.io が開発しているフレームワーク
- Hydration をしない（Resumable)
- ユーザーが操作を開始してから必要な JavaScript コードを読み込む

<img class="absolute top-30 right-40 w-10%" src="astro.png">
<img class="absolute top-70 right-40 w-10%" src="qwik.jpeg">

<!--
Qwik というフレームワークはもっとラディカルで、Hydration 自体を実行しないという思想で設計されています。
ユーザーが操作を開始してから必要な JavaScript コードを読み込んで、遅延 Hydration をするような方式をとっています。

フロントエンドのフレームワークでは、Next や Nuxt がまだまだ主流ですが、それらのパフォーマンス上の課題を解決するような新しいフレームワークが出てきているのが今年の動きかなと思います。
-->

---

# まとめ

## Browser

- IE 11 が引退して、モダンブラウザが開発のベースラインになった
- ブラウザ新しい WEB API の実装が進んだ

## Runtime

- JavaScript の実行環境が、ブラウザ・サーバーからエッジへと広がりを見せている
- 各ランタイムの間で、機能の差別化と仕様の共通化が同時に起こっている

## Framework

- Next.js / Nuxt.js がまだまだ主流
- 後発のフレームワークは Hydration の課題を解決しにきている
- エッジで動作するフレームワークも登場しており、よりユーザーに近い場所で Pre-rendering 可能に

<!--
まとめです。

ブラウザでは、IE 11 が引退して、モダンブラウザの間では新しい WEB API の実装が進みました。

Runtime では、JavaScript の実行環境が、ブラウザやサーバーからエッジへと広がりつつあります。
各ランタイムの間では、機能の差別化と仕様の共通化が同時に起こっています。

フレームワークでは、Next / Nutx が主流ではありますが、後発のフレームワークは Hydration の課題を解決してパフォーマンスの更なる向上を目指しています。
エッジで動作するフレームワークも登場しており、Pre-rendering する場所もサーバーからエッジに広がる可能性がある。

駆け足ではありましたが、発表は以上になります。
ご清聴いただきありがとうございました。
-->
