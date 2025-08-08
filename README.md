# 🚀 K3s WordPress Deploy

Bu proje, 1 master ve 2 worker node'dan oluşan bir K3s (lightweight Kubernetes) kümesi üzerinde WordPress uygulamasının Helm Chart ile kurulumu ve CI/CD sürecinin otomasyonu amacıyla hazırlanmıştır.

---

## 🔧 Kullanılan Teknolojiler

- 🐳 **K3s** - Lightweight Kubernetes dağıtımı
- 🐘 **Helm** - Kubernetes için paket yöneticisi
- 📦 **Bitnami WordPress Chart** - Hazır WordPress Helm Chart
- ⚙️ **GitHub Actions** - CI/CD pipeline
- 🔍 **Lens** - Kubernetes UI dashboard (kubeconfig ile bağlanıldı)
- 💻 **Virtual Machines** - Ubuntu 22.04 (1 master, 2 worker)

---

## 📁 Proje Yapısı

k3s-wordpress-deploy/
├── .github/
│ └── workflows/
│ └── deploy.yaml # CI/CD pipeline (Helm deploy)
├── wordpress-deploy/
│ └── values.yaml # WordPress Helm chart için özelleştirilmiş değerler
└── README.md # Proje açıklaması

## ⚙️ Kurulum Adımları

### 1. K3s Kurulumu

```bash
curl -sfL https://get.k3s.io | sh -

curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash


### 2. Helm VE Wordpress Kurulumu

helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update

helm upgrade --install wordpress bitnami/wordpress \
  -f wordpress-deploy/values.yaml

