# 💕 Glamour Bərdə Shopping — Tam Quraşdırma Təlimatı v2.0

## ✅ Saytda Olan Hər Şey

- 🖼 Cloudinary şəkil yükləmə (Admin paneldən, avtomatik bazaya düşür)
- 🔐 Firebase Auth — e-poçt + Google girişi
- 🔑 Şifrəni unutdum — e-poçta sıfırlama linki
- 💳 Stripe kart ödənişi — pul birbaşa sizin hesaba
- 🧾 Çek sistemi — unikal kod, müştəri adı, məhsul, ölçü, məbləğ
- ⭐ Rəy silmə — yazan özü, ya admin silə bilər
- ⚙️ Admin panel — tam idarəetmə
- 📱 Tam responsiv — telefon/planşet/komputer
- 🏷 11 kateqoriya — Donlar, Ətəklər, Koftalar, Ayaqqabı, Çanta, İçgeyim, Aksesuar, Ətir, Kombin, Uşaq, Paltar altlığı (ev aksesuarı yoxdur)

---

## 🌐 GitHub-a Yükləmə

1. github.com → hesab açın (pulsuz)
2. "New repository" → Ad: glamour-berde → Public → Create
3. "uploading an existing file" → index.html sürüklə-burax → Commit
4. Settings → Pages → Branch: main → Save
5. Saytınız: https://ADINIZ.github.io/glamour-berde

---

## 🔥 Firebase Quraşdırma

1. console.firebase.google.com → "Add project" → glamour-berde
2. </> (Web) → Register → Konfiqurasiya kodunu kopyalayın
3. index.html → CFG.firebase → yapışdırın
4. Authentication → Email/Password + Google → Enable
5. Firestore → Create database → Test mode → europe-west

Firestore Security Rules:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth.uid == userId;
    }
    match /products/{pid} {
      allow read: if true;
      allow write: if request.auth.token.email == 'admin@glamour.az';
    }
    match /orders/{oid} {
      allow create: if request.auth != null;
      allow read, write: if request.auth.token.email == 'admin@glamour.az'
                         || resource.data.customerId == request.auth.uid;
    }
  }
}
```

---

## ☁️ Cloudinary Quraşdırma

1. cloudinary.com → Pulsuz hesab açın
2. Dashboard → Cloud Name-i kopyalayın
3. Settings → Upload → Add upload preset
   - Preset name: glamour-berde-upload
   - Signing Mode: Unsigned (VACİBDİR!)
   - Folder: products
4. index.html → CFG.cloudinary → daxil edin

---

## 💳 Stripe Quraşdırma

1. stripe.com → Hesab açın + bank məlumatlarını daxil edin
2. Developers → API keys → Publishable key kopyalayın
3. index.html → CFG.stripe.publishableKey → yapışdırın
4. Ödəniş ediləndə pul Stripe → Sizin bank hesabınıza gəlir

---

## 🔑 Admin Girişi

```
E-poçt: admin@glamour.az
Şifrə:  admin123
```

---

## ✏️ Dəyişdiriləcək Yerlər (index.html)

- Telefon: "050-462-00-27" axtarın, dəyişin
- WhatsApp: "994517415706" axtarın, dəyişin  
- Ünvan: "Üzeyir Hacıbəyli" axtarın, dəyişin
- Admin email: CFG.adminEmail
- Rənglər: :root { --rose: #c8556a; --gold: #c9a96e; }

💕 Glamour Bərdə Shopping 2025
