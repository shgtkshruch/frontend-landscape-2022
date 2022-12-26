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

# Frontend Lanscape 2022

<!--
2022年にあったフロントエンドの動きの中で、個人的に注目したもの、今後のフロントエンドの動向に影響しそうなものをピックアップして発表します。
よろしくお願いします。
-->

---

# Self Introduction

- 城内 栄剛
- 2022 年 8 月入社
- Xuan プロジェクト・フロントエンドエンジニア

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
簡単に自己紹介です。
名前は城内と言います。
2022年の8月にエス・エム・エスに入社しました。
Xuan プロジェクトでフロントエンドエンジニアとして働いています。
-->

---

# 今日のトピック

- 今年のフロントエンドの動きを、以下の 3 つの観点で紹介

<br>

- Browser
- Runtime
- Framework

<!--
今日のトピックです。
今年のフロントエンドの動きを、以下の3つの観点で紹介します。
ブラウザ、JavaScript ランタイム、フロントエンドのフレームワークという各トピックごとに、今年どんな動きがあったかをサクッと見ていきたいと思います。
-->

---

# IE 11 のサポートが終了 👋

- 2022 年 6 月 15 日に、IE 11 のサポートが終了
- サポート対象のブラウザのベースラインが上がる
- 新しい HTML・CSS・JavaScript の API を使用可能に

<img class="mt-5 mx-auto w-75%" src="/ie11.png" />

<!--
2022年6月15日に、IE 11 のサポートが終了しました。

これでサポートするべきブラウザのベースラインが上がって、新しい仕様が使いやすい状況が出来つつあります。
-->

---

# モダンブラウザの動き

- モダンブラウザの間では、Interop 2022 を通じて互換性を担保して新機能を実装
- Interop: 2019 年に始まった、Web ブラウザ(Chrome, Safari, Firefox)の相互運用性を高める取り組み
- 今年実装された API
  - `<dialog>`
  - `<img loading="lazy">`
  - `@layer`

<img class="w-35% absolute right-15 bottom-10" src="interop-2022.png">

<!--
モダンブラウザの間では、Interop 2022 を通じてブラウザ間の互換性を担保した形で新機能の実装が進みました。
Interop は、2017年から始まっている Chrome・Safari・Firefox などの WEB ブラウザの開発者が取り組んでいるブラウザ間の相互運用性を高める取り組みです。

今年実装されたものとしては、
モーダルなどサブウィンドウを表示できる`dialog`要素。
画像が ViewPort に入ってきたときに遅延読み込みされる`loading`属性。
CSS にレイヤを追加できる`@layer`。
などがありました。

従来は JavaScript でおこなっていた処理も、HTML や CSS の API を利用して実装できるようになってきています。
アプリケーションを作る際に必要となる UI やパフォーマンスの最適化に関する表現力が増えてきているなと思います。
-->

---

# Runtime

## Node.js

- 2022 年 4 月に v18 がリリース
- experimental で fetch をサポート

## Deno

- Rust で実装された TypeScript が動く JavaScript のランタイム
- 2020 年に v1.0.0 がリリース
- 今年は npm モジュールをサポート

## Bun

- Zig で実装された、パフォーマンス重視の JavaScript ランタイム
- 2022 年 7 月に v0.1.1 がリリース

<img class="absolute top-19 right-35 w-11%" src="node.png">
<img class="absolute top-63 right-35 w-11%" src="deno.png">
<img class="absolute top-106 right-32 w-13%" src="bun.png">

<!--
主にサーバーサイドで JavaScript を実行するランタイム。
Node.js が一番有名だと思いますが、それとは違った新しいランタイムが登場してきています。
ここ数年の傾向ではありますが、今年も JavaScript のランタイムが盛り上がった年だと思います。

Node.js は今年の4月にバージョン18がリリースされました。
experimental ではありますが、WEB API の1つである fetch がサポートされました。
これは WEB の API が WEB を超えていく一つのきっかけとして、大きな動きだったなと個人的には思っています。

Deno は、Rust で実装された JavaScript ランタイムで、Node.js の作者のライアン・ダールが中心となって開発をしています。
2022年にバージョン1.0がリリースされてから、今年も活発に開発が進められていました。
大きなものとしては、npm のモジュールのサポートが入りました。
これまでは、Node.js 向けに作られた npm モジュールは Deno では動かなかったのですが、npm をサポートしたことで Node.js の資産の多くを Deno でも利用することができるようになりました。

また、今年ホットだったのは、2022年7月に発表された Bun です。
Zig で実装された JavaScript ランタイムで、Node.js や Deno よりも高速に動作することを押しています。

既存のものが進化したり、バージョン1が出たり、新しいランタイムが登場したり、なかなか盛り上がっているなと思っています。
これだけランタイムが増えてくると、JavaScript が分断されていくのでは？と一瞬思うのですが、それをカバーする動きも出てきています。
それについてはこの後のスライドでご紹介します。
-->

---

# Edge Runtime

## Cloudflare Workers

- Cloudflare の CDN 上で動作する JavaScript ランタイム
- Cloudflare Workersのコードからシームレスに利用できるミドルウェア
  - KV: KVS
  - R2: S3 互換のオブジェクトストレージ
  - D1: SQLite

## Edge Runtime

- Vercel の Edge で動作する JavaScript ランタイム
- Next.js だけでなく Vue / Anguler など他のフレームワークへの対応も視野に入れている

<!--
サーバーサイドだけでなく、CDN のようなエッジで動くランタイムも出てきています。

Cloudflare Workers は、Cloudflare の CDN 上で動作する JavaSceript ランタイムです。
Service Worker のようにリクエストに任意の処理を挟むことができるので、リソースを加工してレスポンスを返したり、そのままオリジンに流したりリダイレクトするなど、CDN 本来のキャッシュの機能をプログラムを介して柔軟に利用できるようになっています。

他にも キーバリューストアや S3 互換のストレージ、今年の5月に発表した SQLite ベースのデータベースなど、Cloudflare Workers から利用できる様々なミドルウェアをリリースしています。

Next.js の開発元である Vercel も Edge で動作する JavaScript ランタイム、名前もそのままの「Edge Runtime」を今年の6月にリリースしました。
experimental ではありますが、Next.js の SSR が動作するようになっています。
Next.js だけでなく、Vue や Anguler など他のフレームワークへの対応も視野に入れているようです。
将来的には CDN 上で SSR をする未来が来るかもしれません。
-->

---

# WinterCG

- WEB ブラウザ以外の Runtime で、共通して使用できる API の標準化を目指したコミュニティグループ
  - 今年の 5 月に Cloudflare のブログで発表された
- W3C や WhatWG の仕様の尊重しつつ、Runtime 共通の仕様を定義する

<img class="mt-5 mx-auto w-70%" src="winter-cg.png">
<img class="mt-5 mx-auto w-70%" src="winter-cg-company.png">

<!--
ランタイムが増えてくる中で気になるのが、あるランタイムで実装した JavaScript が他のランタイムでも動くのかということです。

例えば、Node.js の npm モジュールを実装したコードが Cloudflare Workers 上でも動作すると移植する時に便利です。

しかし現状では、サーバーで動作する Node.js や Deno、サーバレス環境で動く Cloudflare Workers では、それぞれ動作する環境が異なることから、共通した機能に対してそれぞれ独自の実装をしており、npm モジュールはそのままでは Cloudflare Workers では動作しません。

こうした相互運用性の課題を解決するために、WinterCG というグループが今年の5月に立ち上がりました。

Node.js／Deno／Bun／Cloudflare Workersなどのランタイムエンジン上で共通の仕様を定義することを目標にしたコミュニティグループです。

将来的には、あるランタイム間の相互運用性を向上させて、あるランタイムで実装したコードが別の環境でも動作する状態を目指しています。
-->

---

# Framework

- React なら Next.js、Vue.js なら Nuxt.js のように、フレームワーク単位で採用される事例が増えた
  - React / Vue.js をライブラリとして利用する話がなくなってきた
- Svelte が出てきて以降は、あまり大きな動きがなく落ち着いている印象だったが...
- 今年の夏頃からは、新しい観点に注目したフレームワークが登場してきた
  - Astro
  - Qwik

---

# 観点

- Pre-rendering
  - どこで HTML を生成するか
  - ブラウザ
    - SPA
  - サーバー
    - SSR / SSG / ISG
- Hydration
  - Pre-rendering した HTML にイベントハンドラを設定して、クライアンド上で Reactive に動くようにすること
  - Hydration が完了しないと、画面に表示されていたとしても操作がでない（不気味の谷）
  - 主要なフレームワークでは、ページ単位で Hydration が行われる

---

# 各 Framework の Hydration 方式

## Next.js

- ページ単位の Hydration
- ページやバンドルサイズが大きくなると Hydration の処理が重くなる

## Astro

- 2022 年 8 月にリリースされたフレームワーク
- ページの部分単位の Hydration（Partial Hydration）
- 画面に表示される要素を優先的に Hydration する

## Qwik

- builder.io が開発しているフレームワーク
- Hydration をしない（Resumable)
- ユーザーが操作を開始してから必要な JavaScript コードを読み込む

<img class="absolute top-22 right-33 w-16%" src="nextjs.png">
<img class="absolute top-60 right-40 w-10%" src="astro.png">
<img class="absolute top-100 right-40 w-10%" src="qwik.jpeg">

---

# まとめ

- JavaScript の実行環境が、ブラウザ・サーバーからエッジへと広がりを見せている
- ブラウザ・サーバー・エッジの各レイヤで、機能の差別化と仕様の共通化が同時に起こっている
- パフォーマンスはフロントエンドにおいて重要な観点であり続ける
  - ページに必要なリソースをどれだけ早く返すか（ネットワーク）
  - ページがロードされてからどれだけ早く操作できるか（レンダリング）
