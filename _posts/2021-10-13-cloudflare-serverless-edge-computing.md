---

layout: post
author: T Kumagai
Title: Cloudflare Serverless Edge Computing
categories: [Cloudflare]

tags: [serverless, edge computing]

---
# クラウドフレアによるサーバレスエッジコンピューティング

- Cloudflare
  - Ryoma Nagata(Solution Engineer)
  - Keio Oyama
  - Erwin van der Koogh(Product Manager)

## Cloudflareの紹介

### ミッション

**We are helping build a better Internet**
* Security
* Performance
* Reliability
* Privacy

![img1](/assets/images/cloudflare2021-10-13-1.png)

### Cloudflareのアーキテクチャ

![img2](/assets/images/cloudflare2021-10-13-2.png)


### 提供プロダクト

![img3](/assets/images/cloudflare2021-10-13-3.png)

今回は赤枠の説明

### 沿革

2009〜

2020/7 日本オフィス開設

---

## Cloudflare WORKERS
Our Vision

A world where there is no distinction between writting ..

### Cloudflare Workers エコシステム

![img4](/assets/images/cloudflare2021-10-13-4.png)

![img5](/assets/images/cloudflare2021-10-13-5.png)


* Cloudflare Workers
* Cron Triggers
* Workers KV(キー・バリューストア)
* Durable Object
* Cache API
* Cloudflare Pages
  * 開発プラットフォーム

### Cloudfare Workers
主要な２つの目的とユースケース

1. 他のCloudflare製品をより強固にする

2. アプリケーションの展開

__sample__

![img6](/assets/images/cloudflare2021-10-13-6.png)


![img7](/assets/images/cloudflare2021-10-13-7.png)


__Workers KV__

自動キャッシング

![img8](/assets/images/cloudflare2021-10-13-8.png)


__Durable Object__

コンセプト

* ユニーク: 全てのIDに対して、世界に１つだけのDurable Objectのインスタンスが存在
* シングル・イベント・ループ: 全てのDurable Objectは、１度に１つのイベントしか実行せず、並行性はなし

* トランザクション・ストレージ: プライベートなKey-Valueストアにアクセス可能

* 近い: 最初にリクエストしたワーカーにできるだけ近い場所で作成

* Websocket対応: 


---

## お知らせ
Cloudflare Developer Summer Charange

![img9](/assets/images/cloudflare2021-10-13-9.png)

----
Fin.