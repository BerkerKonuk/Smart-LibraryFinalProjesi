# SmartLibrary2 - ORM Tabanlı Akıllı Kütüphane Sistemi

Bu proje, **Nesneye Dayalı Programlama-II** dersi final ödevidir. Kütüphane yönetim süreçlerini dijitalleştirmek amacıyla geliştirilmiş, Java tabanlı ve Hibernate ORM mimarisini kullanan bir otomasyon sistemidir. Proje, **OOP** prensipleri ve **Veri Kalıcılığı** (Persistence) standartlarına tam uygun olarak tasarlanmıştır.

## 👤 Öğrenci Bilgileri

* **Ad Soyad:** [ADINI SOYADINI BURAYA YAZ]
* **Öğrenci No:** [NUMARANI BURAYA YAZ]
* **Ders Sorumlusu:** Emrah SARIÇİÇEK
* **GitHub Repository:** [GITHUB LINKINI BURAYA YAPIŞTIR]

---

## 🎯 Projenin Amacı

SmartLibrary2, geleneksel veritabanı kodlaması (JDBC) yerine modern **ORM (Object Relational Mapping)** tekniklerini kullanarak veritabanı işlemlerini nesne tabanlı bir yaklaşımla yönetmeyi hedefler. Proje, CRUD (Ekleme, Okuma, Güncelleme, Silme) işlemlerini **DAO** (Data Access Object) tasarım deseni ile gerçekleştirir.

**Sistemin Temel Yetenekleri:**
* Kitap ve Öğrenci kayıtlarının yönetimi.
* Ödünç verme ve iade alma süreçlerinin takibi.
* Otomatik veritabanı ve tablo oluşturma (Hibernate `hbm2ddl`).
* One-To-Many ve One-To-One ilişki yapıları.
* Kullanıcı dostu konsol menüsü.

---

## 🛠 Kullanılan Teknolojiler

Bu projenin geliştirilmesinde aşağıdaki teknoloji ve kütüphaneler kullanılmıştır:

* **Dil:** Java (JDK 1.8 ve üzeri uyumlu)
* **ORM:** Hibernate 5.6.15.Final
* **Veritabanı:** SQLite (`library.db`)
* **Build Tool:** Maven
* **Loglama:** Hibernate Logları (Konsol temizliği için optimize edilmiştir)

---

## 🗄️ Veritabanı Yapısı ve İlişkiler

Proje, ilişkisel veritabanı modeline uygun olarak 3 ana Entity sınıfından oluşur:

1.  **Book (Kitap):**
    * Özellikler: `id`, `title`, `author`, `year`, `status` (ENUM: AVAILABLE/BORROWED).
    * İlişki: Ödünç durumunda Loan tablosu ile ilişkilidir.

2.  **Student (Öğrenci):**
    * Özellikler: `id`, `name`, `department`.
    * İlişki: `OneToMany` -> Bir öğrenci birden fazla kitap ödünç alabilir.

3.  **Loan (Ödünç İşlemi):**
    * Özellikler: `id`, `borrowDate`, `returnDate`.
    * İlişkiler:
        * `ManyToOne` -> Hangi öğrenci aldı?
        * `OneToOne` -> Hangi kitap alındı?

---

## 📂 Proje Mimarisi

Proje, modülerlik ve temiz kod prensiplerine göre paketlenmiştir:

* `src/entity`: Veritabanı tablolarını temsil eden sınıflar.
* `src/dao`: Veritabanı erişim ve CRUD işlemlerini yapan sınıflar.
* `src/util`: Hibernate bağlantı ayarlarını yöneten `HibernateUtil` sınıfı.
* `src/app`: Uygulamanın ana giriş noktası (`Main`) ve menü yönetimi.

---

## 🚀 Kurulum ve Çalıştırma

1.  Projeyi bilgisayarınıza indirin veya klonlayın.
2.  `pom.xml` dosyasındaki bağımlılıkların yüklenmesini bekleyin (Maven Reload).
3.  `src/app/Main.java` sınıfını çalıştırın.
4.  Uygulama ilk açıldığında `library.db` veritabanı ve gerekli tablolar otomatik olarak oluşturulacaktır.

---

## 📋 Menü Kullanımı

Uygulama başlatıldığında aşağıdaki işlemler yapılabilir:

* **[1] Kitap Ekle:** Kütüphaneye yeni kitap ekler (Varsayılan: MÜSAİT).
* **[2] Kitapları Listele:** Tüm kitapları durumlarıyla (MÜSAİT/ÖDÜNÇTE) listeler.
* **[3] Öğrenci Ekle:** Yeni öğrenci kaydı oluşturur.
* **[4] Öğrencileri Listele:** Kayıtlı öğrencileri listeler.
* **[5] Kitap Ödünç Ver:** Müsait bir kitabı öğrenciye zimmetler. Kitap durumu 'ÖDÜNÇTE' olur.
* **[6] Ödünç Listesi:** Kimin hangi kitabı ne zaman aldığını listeler.
* **[7] İade Al:** Kitabın iade tarihini işler ve kitabı tekrar 'MÜSAİT' durumuna getirir.

---
