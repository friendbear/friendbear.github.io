---

layout: post
author: T Kumagai
Title: Vaultに格納したシークレットをKubernetesから活用する方法
categories: [HashiCorp]

tags: [Vault, Kubernetes]

---
# Vaultに格納したシークレットをKubernetesから活用する方法

- HashiCorp Japan

  - time 30min

## 概要

Vault CSIドライバーを活用して、コンテナ内のアプリケーションにシークレットを渡す方法を解説します。

### キー製品

* Vault

---

## 概要

![1](/assets/images/vault-2022-03-08-1.png)
![1](/assets/images/vault-2022-03-08-3.png)
![1](/assets/images/vault-2022-03-08-4.png)

### Kubernetes Auth Method

![1](/assets/images/vault-2022-03-08-2.png)
![1](/assets/images/vault-2022-03-08-5.png)
![1](/assets/images/vault-2022-03-08-6.png)


![1](/assets/images/vault-2022-03-08-7.png)
![1](/assets/images/vault-2022-03-08-8.png)
![1](/assets/images/vault-2022-03-08-9.png)

### Vault  Agent Injector

![1](/assets/images/vault-2022-03-08-10.png)
![1](/assets/images/vault-2022-03-08-11.png)
![1](/assets/images/vault-2022-03-08-12.png)
![1](/assets/images/vault-2022-03-08-13.png)
![1](/assets/images/vault-2022-03-08-14.png)
![1](/assets/images/vault-2022-03-08-15.png)



---

### Vault CSI Provider

![1](/assets/images/vault-2022-03-08-16.png)

![1](/assets/images/vault-2022-03-08-17.png)

![1](/assets/images/vault-2022-03-08-18.png)

![1](/assets/images/vault-2022-03-08-19.png)
![1](/assets/images/vault-2022-03-08-20.png)

![1](/assets/images/vault-2022-03-08-20.png)

---

## Sidecar or CSI?

![1](/assets/images/vault-2022-03-08-21.png)


