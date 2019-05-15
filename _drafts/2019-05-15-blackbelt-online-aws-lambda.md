---
layout: post
title: AWS Blackbelt online AWS Lambda 1,2,3
author: friendbear
category: [lambda]
tags: [aws, ]

---

Speecher: @Keisuke69

## Lamda 2 (60m)

* ENI
  * VPCアクセス

* 上限 1アカウント単位 (1000)
* 関数毎に上限設定

* 同時実行数
  * スロットリングボタンで０にすることができる（全て止められる）

* 環境変数
  * AWS Key Management Service(AWS KMS)で自動的に暗号化して保存して必要に応じて複合化される。

* バージョニング
  * Arnが一意に発行される
* 環境変数や中身も全てスナップショットとして保存され一切変更不可となる

Alias: Prod = version no の張り替え
Routing-config でトラヒックの転送される割合を決められる
カナリアデプロイ

* Lambda Layar
refs: <https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/access-control-resource-based.html>


## Lambda 3 (60m)

X-Rayで可視化できる。
コールドスタート、ワームスタート
* コンピューティングリソースを増やすとコールドスタートを早くできる
  * memory設定＝パフォーマンス設定
* パッケージサイズを小さくする
  * 不要なコードを減らす（zipの展開に時間がかかる)
* 依存関係を減らす
* コード最適化ツールを使って減らす手もある
  * ProGuard(Java)
  * UglifyJS(Node.js)

* VPCは必要でない限り利用しない

### 関数コード
* コードの最適化
* Fatでモノシリックな関数にならないようにする
  * オーケストレーションしない(関数のネスト)
  * ステート管理、エラーハンドリングなど
  * => Step Functionを利用する

* デプロイパッケージの依存関係をコントロールする
* ハンドラとコアロジックは分離させる

```python
app = Todo() // コアロジック

def lambda_handler(event, context):
    hander()

```

* コンテナ再利用を有効活用する
  * DBクライアントの初期化はハンドラの外側で行う。
    * グローバルスコープはコールドスタートでしか実行されない
    * コンテナが維持されている間は利用可能

* レジリエンシーの向上
  * エラーハンドリング
  * AWS Lambdaのリトライポリシーを理解すること
    * 同期はリトライなし
    * 非同期は2回リトライされる
    * ストリームは期限が切れるまでリトライが繰り返される
  * Dead Letter Queueを活用する
    * 関数ごとに設定する
* 複雑な依存関係を避ける
* 組み込まれたSDKは利用しない
  * AWS Lambdaのサービス側で定期的に更新される
  * 組み込みSDKはデプロイパッケージとしてパッケージする
* 非同期実行を活用する

* 冪等性を確保する
  * 最低１回実行することであり１回しか実行されないことではない

>  イベントIDをDynamoDBに保管し、処理実行前にチェックする
>  処理前後でバケットを分け、処理後に消す

* Think Parallel

* Javaの場合POJOではなくバイトストリームにする
* ハードコーディングしない
  * コードと設定/データを分離する
    * 関数へのパラメータは環境変数を利用する
    * 書き込み先のS3バケットの名前など
    * ステージ(Prod, Dev, Testなど)ごとの切り替えなども容易になる
  * 認証系は特に
* AWS Systems Manager - Parameter Storeを活用する

* AWS Secrets Manager
  DBの認証情報、パスワード、サードパーティーのAPIキーなどをシークレットを一元的に保存・制御可能

* ストリーム型のイベントソースを利用する上でのプラクティス
  * Kinesis/DynamoDB Streamなど
  * 成功＋ログ出力はDLQへ失敗したレコードの情報を送る

* DynamoDBを利用するにあたって
  * サーバーレスアプリケーション向きのDB設計ベストプラクティス
    refs: slideshare.com/AmazonWebService/ ...

* RDBMSへの反映は非同期にする
  * Streams -> AWS Lambdaをり湯して非同期にRDBMSへ反映
  * Kinesis Data StreamsやSQSとAWS Lambdaを利用して非同期に反映
  * Amazon API Gatewayとの組み合わせの場合、サービスプロキシで構成してLambda関数を非同期呼び出し
  * VPCレイテンシの問題も緩和される

* Aurora Serverless Data API
  * コネクション管理不要
  * APIコールに認証情報を渡す

### アプリケーションの管理
1. AWS Lambda console
1. IDE plugin
1. AWS Cloud9
1. Text editor + α
1. サードパーティ

### CloudFormation
* SAM

Lambda関数のテスト
---
* ユニットテストはローカル
* インテグレーションや受け入れは実際のサービスで
  * SAMを使う

* AWS SAM CLIを利用したローカル開発
`sam init`コマンドによるアプリの雛形生成
 <https://github.com/awslabs/aws-sam-cli>

* CI/CDパイプライン
```
Source -> Build -> Beta -> Prod
GitHub -> AWS CodeBuild -> SAM -> Code Deploy
```





