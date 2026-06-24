# 🦅 Altay Mühendislik Dergisi Platformu

![Status](https://img.shields.io/badge/Status-Geliştirme_Aşamasında-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
![Tech](https://img.shields.io/badge/Architecture-React_%7C_Node.js_%7C_PostgreSQL-red?style=for-the-badge)

Altay Mühendislik Dergisi, savunma sanayii, havacılık, yapay zeka ve yüksek teknoloji odaklı akademik ve sektörel makaleleri barındıran, modern siber/askeri tasarım diline (Siyah-Kırmızı konsepti) sahip dinamik bir e-dergi ve web uygulaması platformudur. 

Bu repo, platformun **Frontend (React)** ve **Backend (Node.js)** kaynak kodlarını, veritabanı mimarisini ve otomasyon entegrasyonlarını içermektedir.

---

## 🚀 Öne Çıkan Özellikler

* **Modern E-Dergi (Flipbook) Deneyimi:** Canva üzerinde tasarlanan profesyonel PDF sayılarının, tarayıcı üzerinden sesli ve sayfa çevirme efektli dijital dergi formatında (`react-pageflip` altyapısı ile) interaktif okunabilmesi.
* **Yazar & Yönetim Paneli:** Yazarların ve adminlerin JWT (JSON Web Token) korumalı paneller üzerinden sisteme güvenli giriş yapabilmesi, makale taslakları oluşturabilmesi.
* **Yapay Zeka Destekli Yorum Analizi:** Okuyuculardan gelen yorumların doğrudan yayına alınmadan önce **n8n workflow otomasyonu** aracılığıyla AI API'lerine gönderilmesi; spam, hakaret ve duygu analizi süzgecinden geçirilerek admin onayına sunulması.
* **OWASP Standartlarında Güvenlik:** Gelen tüm dinamik girdilerin ( inputs) backend tarafında filtrelenerek (Sanitization) SQL Injection ve XSS açıklarına karşı tam koruma altına alınması.

---

## 🛠️ Kullanılan Teknolojiler (Tech-Stack)

* **Ön Yüz (Frontend):** React.js, CSS (Montserrat & Inter tipografisi)
* **Arka Yüz (Backend):** Node.js, Express.js
* **Otomasyon (Workflow):** n8n Automation Engine & AI API
* **Veritabanı (Database):** PostgreSQL
* **Sunucu / Dağıtım (Deployment):** Güzel Hosting (Linux Server - Node.js & PostgreSQL enabled) ile SSL/HTTPS koruması.

---

## 📂 Proje Klasör Yapısı

```text
altay-muhendislik-dergisi/
├── backend/          # Node.js & Express API, Veritabanı Modelleri ve Güvenlik Filtreleri
├── frontend/         # React Uygulaması, Bileşenler (Components) ve E-Dergi Modülü
├── n8n/              # Yapay Zeka Yorum Analizi Workflow Şemaları (JSON)
└── README.md         # Proje Tanım Dokümanı
