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


erDiagram
    users {
        int id PK
        string name
        string email UNIQUE
        string password_hash
        user_role role
        boolean is_premium
        text biography
        string avatar_url
    }

    dergi_sayilari {
        int id PK
        int sayi_no UNIQUE
        string baslik
        string pdf_url
        string kapak_gorsel_url
        text kareografi_metni
        date yayin_tarihi
    }

    makaleler {
        int id PK
        int yazar_id FK
        string baslik
        text icerik
        string kapak_gorsel_url
        string durum
    }

    yorumlar {
        int id PK
        int makale_id FK
        int kullanici_id FK
        int ust_yorum_id FK
        text icerik
        string durum
    }

    indirme_izinleri {
        int id PK
        int kullanici_id FK
        int dergi_id FK
        boolean is_permitted
    }

    fiziki_dergi_talepleri {
        int id PK
        string konum_adi
        string yetkili_adi
        string email
        string telefon
        text adres
        int talep_edilen_adet
        string durum
    }

    slider_yonetimi {
        int id PK
        string gorsel_url
        string ana_slogan
        string alt_yazi
        string buton_yazisi
        string buton_url
        int sira_no
        boolean is_active
    }

    dinamik_sayfalar {
        int id PK
        string slug UNIQUE
        string baslik
        text icerik
    }

    podcastler {
        int id PK
        string baslik
        text aciklama
        string ses_dosyasi_url
        date yayin_tarihi
    }

    eposta_bulteni {
        int id PK
        string email UNIQUE
        boolean is_active
    }

    %% İLİŞKİLER VE BAĞLANTILAR (FOREIGN KEYS)
    users ||--o{ makaleler : "yazar_id (Yazarın yazıları)"
    users ||--o{ yorumlar : "kullanici_id (Okurun yorumları)"
    users ||--o{ indirme_izinleri : "kullanici_id (Kullanıcı izni)"
    
    makaleler ||--o{ yorumlar : "makale_id (Yazıya gelen yorumlar)"
    dergi_sayilari ||--o{ indirme_izinleri : "dergi_id (Dergiye ait izinler)"
    
    yorumlar ||--o{ yorumlar : "ust_yorum_id (Yazarın yoruma cevabı)"
