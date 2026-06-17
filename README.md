# ⚔️ Modern Taş-Kağıt-Makas Oyunu

Modern Taş Kağıt Makas, klasik el oyunu mekaniklerini gelişmiş bir web mimarisiyle yeniden yorumlayarak oyuncuların anlık reaksiyon sürelerini milisaniye (ms) hassasiyetinde ölçen, analiz eden ve veri tabanında saklayan **Tek Sayfa Tabanlı (SPA)** bir performans analiz platformudur.

---

## 📸 Proje Ekran Görüntüleri (UI / UX)

### 1. Kullanıcı Giriş Paneli
*Cam efektiyle (Glassmorphism) tasarlanmış, sayfa yenilenmeden asenkron doğrulama yapan giriş ekranı.*
<img width="1911" height="950" alt="Screenshot 2026-06-17 181715" src="https://github.com/user-attachments/assets/a9554a4f-1543-436d-9a93-f22f933c9eb0" />


### 2. Dinamik Oyun Modu Seçimi
*Kullanıcının 1v1 veya CPU modları arasında asenkron geçiş yaptığı yönetim paneli.*
<img width="1913" height="940" alt="Screenshot 2026-06-17 181754" src="https://github.com/user-attachments/assets/76f2d439-350a-4f2a-9ee0-dc04e764aed1" />


### 3. Hamle Gizleme Mekanizması
*Oyuncular hamlelerini seçtiği an buton kodları DOM'dan tamamen silinir ve yerini güvenli seçim onayına (`✓`) bırakır.*
<img width="1916" height="942" alt="Screenshot 2026-06-17 181945" src="https://github.com/user-attachments/assets/28b08866-9c1d-4cc4-8e1a-83064f3242b2" />


### 4. Dinamik Atmosfer Motoru (Alev & Buz Arenaları)
*Seçilen temaya göre arka plan, buton tasarımları ve sistem analiz metinleri dinamik olarak güncellenir.*

| 🔥 Alev Arenası | ❄️ Buz Arenası |
|:---:|:---:|
<img width="1909" height="945" alt="Screenshot 2026-06-17 181838" src="https://github.com/user-attachments/assets/42b61d97-8453-4d51-af6f-f96a3752f401" />

<img width="1906" height="945" alt="Screenshot 2026-06-17 181858" src="https://github.com/user-attachments/assets/4585c56b-42c7-467a-b7eb-50b7cb68e1e2" />


### 5. Süre Aşımı ve Hükmen Sonuçlandırma Sistemi
*15 saniyelik kritik süre dolduğunda oyunculara ceza puanı (15000ms) atanır ve sistem kilitlenmeden raunt sonuçlandırılır.*
<img width="1910" height="941" alt="Screenshot 2026-06-17 181914" src="https://github.com/user-attachments/assets/eb18fe10-f161-4701-971d-703186f0bb9c" />


---

## 🛠️ Kurulum ve Çalıştırma Adımları

### 1. Gereksinimler
* Bilgisayarınızda **XAMPP**  veya **MampServer** gibi bir yerel PHP/MySQL sunucu paketinin kurulu olması gerekir.

### 2. Projenin İndirilmesi ve VS Code ile Açılması
1. GitHub sayfasındaki yeşil **"Code"** butonuna tıklayın ve **"Download ZIP"** seçeneğini seçerek projeyi indirin.
2. İndirdiğiniz ZIP dosyasını klasöre çıkartın.
3. Çıkarttığınız proje klasörünü yerel sunucunuzun kök dizinine taşıyın:
   * **XAMPP için:** `C:\xampp\htdocs\` klasörünün içine yerleştirin.
4. **VS Code** (Visual Studio Code) programını açın; `File -> Open Folder` adımlarını takip ederek `htdocs` içine attığınız proje klasörünü seçip açın.

### 3. Veritabanının (MySQL) Hazırlanması
1. Tarayıcınızı açarak `http://localhost/phpmyadmin` adresine gidin.
2. Üst menüden **"Yeni" (New)** seçeneğine tıklayarak `tsmart_db` adında yeni bir veritabanı oluşturun.
3. Oluşturduğunuz veritabanının içine girip üstteki **"SQL"** sekmesine tıklayın ve aşağıdaki tablo yapısını çalıştırın:
   ```sql
   CREATE TABLE IF NOT EXISTS scores (
       id INT AUTO_INCREMENT PRIMARY KEY,
       game_mode VARCHAR(20),
       battlefield VARCHAR(30),
       total_rounds INT,
       p1_score INT,
       p2_score INT,
       p1_avg_speed_ms INT,
       p2_avg_speed_ms INT,
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   
