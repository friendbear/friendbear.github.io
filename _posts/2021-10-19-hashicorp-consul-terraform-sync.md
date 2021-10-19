---

layout: post
author: T Kumagai
Title: HashiCorp ネットワーク自動化を実現する Consul-Terraform-Sync
categories: [HashiCorp]

tags: [Terraform, Network, Consul]

---
# ネットワーク自動化を実現する Consul-Terraform-Sync

- HashiCorp Japan 
  - 草間一人 san


## DevOpsによってもたらされるもの

### Continuous Integration
* Build
* Test
* Merge

### Continuous Delivery
* リポジトリへの自動リリース

### Continuous Deployment
* 商用環境に自動デプロイ


## エンタープライズ企業におけるネットワークの課題
* リスクが大きい
* 遅いプロセス
* 標準化の欠如

## NetworkInfrastructure Automation

繰り返し行われるアプリケーションデプロイのライフサイクル全体で自動化を実現

![img1](/assets/images/consul-2021-10-19-1.png)

### Terraformのおさらい
* IaC を実現するプロダクト
* コードでインフラを定義し、Terraformを実行することでインフラの構築を自動化できる。
* インフラのコードとして管理することで変更管理が容易になり、再利用性が高まる。人的ミスの削減にもつながる。

**Terraformでネットワーク機器の設定**
もできる

### 従来のサービス間接続

![img2](/assets/images/consul-2021-10-19-2.png)

### Consul Service Catalog

![img3](/assets/images/consul-2021-10-19-3.png)

frontend request > Consul -> response frontend

dns?

* Helth機能

### Network Infrastructure Automation
Consol-Terraform-Sync(CTS)

Consul Terraform-Sync

## Demo: Day1

https://github.com/hashicorp/f5-terraform-consul-sd-webinar/tree/master/terraform

![img4](/assets/images/consul-2021-10-19-4.png)

### AWS 上でのdemo

```sh
$ consol-terraform-sync
```

### Day2

* AWS Autoscale Group 1 -> 3
  * Consol terraform.tfvars auto detect
  * cord diff
  * 

## Consul-Terraform-Syncによる効果

![img5](/assets/images/consul-2021-10-19-5.png)

## 参考資料
* <https://www.consul.io/docs/nia>
* <https://github.com/hashicorp/f5-terraform-consul-sd-webinar>


## Q&A
* Consolの立ち上げ方法
* 