# Example Voting App - DevOps Projesi

Bu projeyi DevOps becerilerimi geliştirmek için fork ettim ve üzerine eklemeler yaptım.

## Ne Ekledim?

Orijinal projede sadece Docker Compose vardı. Ben şunları ekledim:

- Kubernetes ile deploy ettim (Deployment, Service, Ingress)
- GitHub Actions ile CI/CD pipeline kurdum
- Terraform ile Azure üzerinde AKS cluster oluşturdum

## Uygulamada Ne Var?
5 servisli bir oylama uygulaması:

- **vote** → oy verme sayfası
- **result** → sonuç sayfası  
- **worker** → oyları işleyip veritabanına yazıyor
- **redis** → geçici veri
- **postgres** → kalıcı veri

## Çalıştırmak İçin

```bash
docker compose up -d
```

## Erişim

- Oy ver: http://vote.local
- Sonuçlar: http://result.local

## Kullandığım Teknolojiler

Docker, Kubernetes, GitHub Actions, Terraform, Azure

## Monitoring

Helm ile Prometheus + Grafana kurdum.

- Prometheus → tüm pod'lardan metrik topluyor
- Grafana → CPU, RAM, pod durumlarını dashboard'da gösteriyor

Kurmak için:
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace
```

Grafana'ya erişmek için:
```bash
kubectl port-forward -n monitoring svc/prometheus-stack-grafana 3001:80
```

Kullanıcı adı: admin

<img width="1920" height="992" alt="monitoring" src="https://github.com/user-attachments/assets/5ed81d3a-8a1c-417f-b487-d4859d884919" />
