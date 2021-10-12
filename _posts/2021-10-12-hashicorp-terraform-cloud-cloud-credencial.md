---

layout: post
author: T Kumagai
Title: HashiCorp Terraform Cloudでのクラウド認証情報の管理
categories: [HashiCorp]

tags: [Terraform Cloud]

---
# HashiCorp Terraform Cloudでのクラウド認証情報の管理

- HashiCorp Japan 
  - 
  - 
  - 

## Terraform Cloudとは
See 

## クレデンシャル管理の例

* IAM Static User(1 IAM)
* IAM Static User(Multi IAM)
* STS asssume role
* Terraform Cloud Agenet

### Pattern 1 IAM Static User

![img1](/assets/images/terraform-10-12-1.png)

### Pattern 2 IAM Static User - Multi

![img2](/assets/images/terraform-10-12-2.png)


### Pattern 3 STS Credentials

* Vault

![img3](/assets/images/terraform-10-12-3.png)

--- 

![img4](/assets/images/terraform-10-12-4.png)

### Pattern 4 Terraform Cloud Agent and Instance Role

![img5](/assets/images/terraform-10-12-5.png)

----
Fin.