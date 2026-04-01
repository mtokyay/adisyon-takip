# Adisyon Takip Sistemi — Adım Adım Kurulum

## Gerekenler
- Bilgisayar ve internet bağlantısı
- Tarayıcı (Chrome önerilir)
- Yaklaşık **15 dakika**

---

## ADIM 1 — GitHub Hesabı Aç ve Depo Oluştur

1. **github.com** adresine gidin → **Sign up** (ücretsiz)
2. Hesap oluşturduktan sonra giriş yapın
3. Sağ üstteki **+** butonuna tıklayın → **New repository**
4. Ayarlar:
   - Repository name: `adisyon-takip`
   - Public seçin (zorunlu değil, Private da olur)
   - **Create repository** tıklayın
5. Açılan sayfada **"uploading an existing file"** bağlantısına tıklayın
6. **`index.html`** dosyasını sürükleyip bırakın
7. **Commit changes** tıklayın

---

## ADIM 2 — Supabase'de Ücretsiz Veritabanı Oluştur

1. **supabase.com** adresine gidin → **Start your project** (ücretsiz)
2. GitHub ile giriş yapın (kolay olur)
3. **New project** tıklayın:
   - Organization: kendi adınız
   - Project name: `adisyon-takip`
   - Database Password: güçlü bir şifre yazın (kaydedin!)
   - Region: **West EU** veya **EU Central** seçin
   - **Create new project** tıklayın
4. Proje oluşturulurken bekleyin (~2 dakika)

---

## ADIM 3 — Veritabanı Tablolarını Kur

1. Sol menüden **SQL Editor** tıklayın
2. **New query** tıklayın
3. `supabase-kurulum.sql` dosyasını bir metin editöründe açın
4. İçeriğin **tamamını** kopyalayın (Ctrl+A → Ctrl+C)
5. SQL Editor'e yapıştırın (Ctrl+V)
6. **Run** butonuna tıklayın (yeşil düğme)
7. Alt kısımda `Success` yazısını görmelisiniz ✅

---

## ADIM 4 — Supabase Bağlantı Bilgilerini Al

1. Sol menüden **Settings** → **API** tıklayın
2. Şu iki bilgiyi kopyalayıp bir yere kaydedin:

```
Project URL:  https://xxxxxxxxxxxx.supabase.co
              (bu sizin URL'niz olacak)

anon public:  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
              (çok uzun bir satır)
```

> ⚠️ **anon public** key'i kullanın, **service_role** key'i KULLANMAYIN!

---

## ADIM 5 — Netlify'a Bağlan ve Yayına Al

1. **netlify.com** adresine gidin → **Sign up** (ücretsiz)
2. **GitHub ile giriş yapın**
3. **Add new site** → **Import an existing project** tıklayın
4. **GitHub** seçin → `adisyon-takip` reposunu seçin
5. Ayarlar olduğu gibi bırakın → **Deploy site** tıklayın
6. Birkaç saniye sonra siteniz yayında! 🎉
   - Adres şöyle görünür: `https://amazing-lokanta-123.netlify.app`

> 💡 Dilerseniz Netlify'dan özel domain de ekleyebilirsiniz.

---

## ADIM 6 — İlk Kez Açma ve Bağlantı Ayarı

1. Netlify'ın verdiği adresi açın (her cihazdan açılır)
2. **Supabase Bağlantısı** ekranı çıkar — **bir kez** doldurmanız yeterli:
   - **Project URL**: Adım 4'ten kopyaladığınız URL
   - **Anon / Public Key**: Adım 4'ten kopyaladığınız uzun key
3. **Bağlan** tıklayın
4. Giriş ekranı açılır:
   - Kullanıcı adı: `admin`
   - Şifre: `admin123`
5. İçeri girin! 🎉

> ⚠️ **İlk yapacağınız şey:** Kullanıcılar menüsünden admin şifresini değiştirin!

---

## ADIM 7 — Kullanıma Hazırlık

### Garson Ekle
1. Sol menü → **Kullanıcılar** → **Yeni Kullanıcı**
2. Ad, kullanıcı adı, şifre girin, Rol: **Garson** seçin

### Adisyon Serisi Oluştur
1. Sol menü → **Seri Oluştur**
2. Kaç koçan basacaksanız sayıyı girin (örn: 5)
3. **Oluştur** tıklayın
4. Her seri için **Etiket Yazdır** butonuna tıklayın
5. A4 kağıda yazdırın → 32×57mm etikete kesin ve adisyonlara yapıştırın

### Garson Ataması Yap
1. Sol menü → **Atamalar**
2. Seri seçin → Garson seçin → **Ata**

---

## Günlük Kullanım

| Kim | Ne yapıyor |
|-----|-----------|
| **Kasa (admin/yönetici)** | Adisyon Okut → barkod okutucuyu tutar |
| **Garson (telefon)** | Adisyonlarım → kendi serilerini görür |
| **Yönetici** | Geçmiş → kimin ne kadar okuttuğunu görür |

### Telefon Kamerası ile Okutma
1. **Adisyon Okut** sayfasını açın
2. **Kamerayı Aç** tıklayın → izin verin
3. QR kodu kameraya gösterin → otomatik okur ✅

---

## Güncelleme (Yeni Özellik Eklenirse)
1. GitHub'da `index.html` dosyasını güncelleyin
2. Netlify **otomatik olarak** yeni sürümü yayına alır

---

## Sorun Giderme

| Sorun | Çözüm |
|-------|-------|
| "Bağlantı hatası" | Supabase URL ve key'i kontrol edin |
| "Barkod bulunamadı" | SQL kurulumunu tekrar çalıştırın |
| Kamera açılmıyor | Tarayıcıya kamera izni verin (HTTPS zorunlu) |
| Şifremi unuttum | Supabase SQL Editor'den: `SELECT fn_create_user('yeni-admin','yeni-sifre','Ad','admin')` |

---

*Tüm veriler Supabase'de güvenle saklanır. Uygulama tamamen ücretsizdir.*
