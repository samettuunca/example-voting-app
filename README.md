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


<img width="1920" height="992" alt="monitoring" src="https://github.com/user-attachments/assets/5ed81d3a-8a1c-417f-b487-d4859d884919" />
