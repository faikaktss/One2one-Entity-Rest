# 🔗 Spring One2One REST API

Merhaba!  
Bu proje, **Spring Boot** ve **Spring Data JPA** ile geliştirilmiş; öğrenci, müşteri ve adres varlıkları arasında **bire bir (one-to-one)** ilişkiyi kurumsal seviyede yöneten, modern ve katmanlı bir RESTful API örneğidir.  
DTO, katmanlı mimari, validasyon ve gelişmiş hata yönetimi ile temiz kod ve veri güvenliğini ön planda tutar.

---

## 🚀 Özellikler

- 🔄 **One-to-One (1-1) Entity İlişkisi:**  
  Student, Customer ve Address entity’leri arasında bire bir ilişki örnekleri.
- 📦 **DTO Kullanımı:**  
  Tüm veri giriş-çıkış işlemlerinde DTO’lar ile güvenli ve sade veri transferi.
- 💾 **Spring Data JPA ile CRUD:**  
  Entity’ler için otomatik repository ve veritabanı işlemleri.
- 🧩 **Katmanlı Mimari:**  
  Controller, Service, Repository, DTO, Entity ve Exception katmanları ile sürdürülebilir yapı.
- ✅ **Validasyon ve Hata Yönetimi:**  
  Alan doğrulama (@Valid, @NotNull, @Email, @Size…) ve merkezi exception handler.
- 🛡️ **Temiz Kod ve Açıklamalar:**  
  Kodda bol açıklama, anlaşılır mimari ve kolay geliştirme imkanı.

---

## 🏗️ Proje Mimarisi

```
src/main/java/com/faik/
├── Controller/
│   ├── Impl/
│   │   ├── StudentControllerImpl.java      # Student API implementasyonu
│   │   ├── CustomerControllerImpl.java     # Customer API implementasyonu
│   │   └── AddressControllerImpl.java      # Address API implementasyonu
│   ├── IStudentController.java
│   ├── ICustomerController.java
│   └── IAddressController.java
│
├── Services/
│   ├── Impl/
│   │   ├── StudentServiceImpl.java
│   │   ├── CustomerService.java
│   │   └── AddressServiceImpl.java
│   ├── IStudentService.java
│   ├── ICustomerService.java
│   └── IAddressService.java
│
├── Repository/
│   ├── StudentRepository.java
│   ├── CustomerRepository.java
│   └── AddressRepository.java
│
├── Entites/
│   ├── Student.java                        # Student entity
│   ├── Customer.java                       # Customer entity (1-1 Address)
│   └── Address.java                        # Address entity (1-1 Customer)
│
├── dto/
│   ├── DtoStudent.java
│   ├── DtoStudentIU.java
│   ├── DtoCustomer.java
│   └── DtoAddress.java
│
├── exception/
│   ├── ApiError.java                       # Hata response modeli
│   └── GlobalExecptionHandler.java         # Merkezi hata yönetimi
│
└── Starter/
    └── Application.java                    # Uygulama başlatıcı
```

---

## 🔗 One-to-One İlişkisi Nedir?

- **Customer** ve **Address** entity’leri arasında bire bir ilişki vardır:  
  Her müşteri için bir adres, her adres için bir müşteri kaydı tutulur.  
  - `@OneToOne`, `@JoinColumn`, `mappedBy` ile iki yönlü ilişki kurgulanır.
- DTO katmanı ile bu ilişkiler sade ve kontrollü şekilde dışarı açılır.

---

## 🛣️ API Endpointleri

### Student API (`/rest/api/student`)
| Metot | Endpoint                        | Açıklama                        |
|-------|---------------------------------|---------------------------------|
| POST  | `/save`                         | Yeni öğrenci ekler              |
| GET   | `/list`                         | Tüm öğrencileri listeler        |
| GET   | `/list/{id}`                    | Belirli öğrenciyi getirir       |
| PUT   | `/update/{id}`                  | Öğrenci günceller               |
| GET   | `/delete/{id}`                  | Öğrenci siler                   |

### Customer API (`/rest/api/customer`)
| Metot | Endpoint            | Açıklama                |
|-------|---------------------|-------------------------|
| GET   | `/list/{id}`        | ID ile müşteri getirir  |

### Address API (`/rest/api/address`)
| Metot | Endpoint            | Açıklama                |
|-------|---------------------|-------------------------|
| GET   | `/list/{id}`        | ID ile adres getirir    |

---

## 🧩 Katmanların Görevleri

- **Controller:** API endpointlerinin tanımlandığı katman. DTO ile veri alışverişi sağlar, validasyonları yönetir.
- **Service:** İş mantığının ve veri işleme operasyonlarının gerçekleştiği katman.
- **Repository:** JPA ile CRUD işlemlerini kolaylaştıran arayüzler.
- **Entity:** Veritabanı tablolarını yansıtan, ilişkiyi kuran model sınıfları.
- **DTO:** Dış dünyaya açılan sade ve güvenli veri transfer nesneleri.
- **Exception:** Hataları merkezi olarak yönetip, kullanıcıya anlamlı mesajlar döner.

---

## 🛡️ Validasyon ve Hata Yönetimi

- DTO'larda annotasyonlarla (@NotEmpty, @Email, @Size, vs.) alan doğrulama.
- GlobalExecptionHandler ile validasyon ve diğer hataları özelleştirilmiş biçimde dönen merkezi yönetim.
- Hatalar, API yanıtında; id, zaman bilgisi ve detaylı hata mesajlarıyla döner.

---

## ⚙️ Projeyi Çalıştırmak İçin

1. Repoyu klonla:
   ```bash
   git clone https://github.com/faikaktss/spring-one2one-rest-api.git
   ```
2. `application.properties`’te veritabanı bağlantı ayarlarını yapılandır.
3. Projeyi başlat:
   ```bash
   ./mvnw spring-boot:run
   ```
4. API endpointlerini Postman veya benzeri araçlarla test edebilirsin.

---

## 💡 Notlar

- Kodlar, hem yeni başlayanlar hem ileri seviye geliştiriciler için açıklamalı ve özelleştirilebilir yapıdadır.
- Proje, kurumsal projelerdeki best practice’leri yansıtmak amacıyla titizlikle hazırlanmıştır.
- Her türlü katkıya, öneriye ve soruya açığım!

---

## 👨‍💻 Geliştirici

Faik Aktaş  
[GitHub Profilim](https://github.com/faikaktss)

---
