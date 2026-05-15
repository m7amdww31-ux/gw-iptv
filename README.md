# GW IPTV — تطبيق احترافي لمشاهدة IPTV

تطبيق أندرويد كامل لتشغيل خدمات IPTV (بروتوكول Xtream Codes) — يعمل على الهواتف وأجهزة Android TV.

## المميزات

- ✅ **شعار وأيقونة GW** — تصميم احترافي مدمج
- ✅ **تسجيل دخول واحد فقط** — البيانات تُحفظ مشفّرة (AES-256) ولا تحتاج لإعادة الدخول
- ✅ **دعم Xtream Codes و M3U** — اختر الطريقة التي تناسب مزودك
- ✅ **مسلسلات بمواسم وحلقات** — اكتشاف تلقائي من S01E02 / 1x02 / Season 1 Episode 2
- ✅ **مشغّل قوي** — ExoPlayer (HLS, DASH, MP4, MKV, TS, M3U8) مع استئناف وإعادة محاولة
- ✅ **يعمل على الهواتف وشاشات Android TV** — دعم كامل للريموت والتنقل بالأزرار
- ✅ **قوائم احترافية** — Live TV / Movies / Series / Settings مع تصميم Material 3
- ✅ **شاشة إعدادات تعرض الأيام المتبقية** — رقم كبير + شريط تقدم + تاريخ الانتهاء
- ✅ **تنبيه قبل انتهاء الاشتراك** — أحمر ≤7 أيام، برتقالي ≤30 يوم، أخضر >30 يوم
- ✅ **حقوق النشر 2026 ©** — كما طُلب

## كيفية الاستخدام

### الطريقة الأولى: حساب Xtream
1. اختر تبويب **"حساب Xtream"**
2. أدخل: **اسم المستخدم** + **كلمة المرور** + **رابط الخادم**
3. اضغط دخول

### الطريقة الثانية: رابط M3U
1. اختر تبويب **"رابط M3U"**
2. ألصق الرابط، مثال: `http://server.com/get.php?username=X&password=Y&type=m3u`
3. اضغط دخول
4. التطبيق سيقوم بـ:
   - تحميل القائمة وتحليلها
   - فصل القنوات / الأفلام / المسلسلات تلقائياً
   - تنظيم المسلسلات بمواسم وحلقات (يكتشف S01E02، 1x02، إلخ)
   - استخراج بيانات الاشتراك إن كان الرابط من خادم Xtream

> **ملاحظة:** بياناتك تُحفظ مشفّرة، ولن تحتاج لإعادة إدخالها مرة ثانية.

## كيفية البناء (Build)

### الطريقة الأسهل: GitHub Actions (بدون Android Studio) ⭐

1. أنشئ مستودع جديد على GitHub (أو استخدم الحالي `gw-iptv`)
2. **احذف الملفات القديمة** من المستودع (مهم — لا تترك الكود القديم)
3. ارفع كل ملفات هذه النسخة الجديدة
4. روح لـ **Actions** في GitHub
5. ينطلق البناء تلقائياً ويأخذ ٥-٧ دقائق
6. عند الانتهاء، اضغط على الـ run → اسحب لأسفل → **Artifacts** → حمّل **GW-IPTV-debug-apk**

### خطوات الرفع التفصيلية على GitHub

```bash
# 1. فك ضغط GW-IPTV.zip
unzip GW-IPTV.zip
cd GW-IPTV

# 2. إعداد git
git init
git add .
git commit -m "GW IPTV - initial release with M3U + Series support"

# 3. ربط بالمستودع (استبدل YOUR_USERNAME)
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gw-iptv.git

# 4. رفع
git push -u origin main --force
```

> **⚠️ مهم:** الـ `--force` يحذف المحتوى القديم في GitHub ويستبدله بهذه النسخة الجديدة.

### بديل: الرفع من الويب مباشرة
1. روح للمستودع في GitHub
2. **Settings** → **General** → اسحب لأسفل → **Delete this repository** (احذف القديم وأنشئ جديد)
3. أنشئ مستودع جديد فاضي
4. اسحب وأفلت كل الملفات من فولدر GW-IPTV → **Commit changes**
5. الـ Actions تشتغل تلقائياً

### الطريقة المحلية: Android Studio

#### المتطلبات
1. **Android Studio** (Hedgehog أو أحدث)
2. **JDK 17**
3. **Android SDK** (API 34)

#### خطوات البناء

```bash
# 1. افتح Android Studio
# 2. اختر "Open an existing project"
# 3. اختر مجلد GW-IPTV
# 4. انتظر حتى ينتهي Gradle Sync (5-10 دقائق أول مرة)
# 5. اضغط Run ▶ أو Build → Build APK
```

### بناء APK من سطر الأوامر

```bash
cd GW-IPTV
./gradlew assembleDebug
# الـ APK سيكون في: app/build/outputs/apk/debug/app-debug.apk
```

### بناء AAB للنشر على Play Store

```bash
./gradlew bundleRelease
```

## كيفية التثبيت

### على الهاتف
1. انسخ ملف `app-debug.apk` إلى الهاتف
2. فعّل "تثبيت من مصادر غير معروفة" في الإعدادات
3. اضغط على الملف للتثبيت

### على Android TV / Box
1. ثبّت تطبيق "Send Files to TV" أو "Downloader"
2. أرسل الـ APK للتلفزيون
3. ثبّته من خلال مدير الملفات

## كيفية الاستخدام

1. افتح التطبيق — تظهر شاشة الترحيب
2. أدخل بياناتك (تُعطى من مزوّد IPTV):
   - **اسم المستخدم** (Username)
   - **كلمة المرور** (Password)  
   - **رابط الخادم** (مثل `http://example.com:8080`)
3. تأكد من تفعيل "تذكرني" (مفعّل افتراضياً)
4. اضغط "دخول" — لن تحتاج لتسجيل الدخول مرة أخرى!
5. اختر من القائمة الرئيسية: قنوات / أفلام / مسلسلات / إعدادات

## بنية المشروع

```
GW-IPTV/
├── app/
│   ├── build.gradle              ← تبعيات (ExoPlayer, Retrofit, EncryptedSharedPrefs...)
│   └── src/main/
│       ├── AndroidManifest.xml   ← يدعم Phone + Android TV
│       ├── java/com/gw/iptv/
│       │   ├── GWApplication.kt
│       │   ├── data/
│       │   │   ├── local/SessionManager.kt   ← تخزين مشفّر للبيانات
│       │   │   ├── model/Models.kt           ← نماذج Xtream
│       │   │   ├── remote/                   ← Retrofit + ApiClient
│       │   │   └── repository/               ← منطق API
│       │   ├── ui/
│       │   │   ├── SplashActivity.kt         ← يقرر: دخول مباشر أم شاشة تسجيل
│       │   │   ├── login/LoginActivity.kt
│       │   │   ├── main/MainActivity.kt      ← القائمة الرئيسية
│       │   │   ├── channels/                 ← مستعرض القنوات/الأفلام/المسلسلات
│       │   │   ├── player/PlayerActivity.kt  ← مشغل ExoPlayer
│       │   │   └── settings/SettingsActivity.kt ← الأيام المتبقية + تفاصيل
│       │   └── utils/DateUtils.kt
│       └── res/                  ← layouts, drawables, strings (AR)
├── build.gradle
├── settings.gradle
└── gradle.properties
```

## ملاحظات مهمة

### الأمان
- بيانات الدخول محفوظة باستخدام **EncryptedSharedPreferences** بتشفير AES-256-GCM
- لا تُرسل البيانات لأي خادم غير الذي تحدده

### الأيام المتبقية
- يتم حسابها من `exp_date` المُرجع من الـ API
- تظهر بثلاث ألوان حسب الحالة (نشط/تحذير/منتهي)
- التحديث التلقائي عند فتح الشاشة الرئيسية

### التخصيص
- **الشعار**: عدّل `res/drawable/logo_gw.xml`
- **الألوان**: عدّل `res/values/colors.xml`
- **النصوص**: عدّل `res/values/strings.xml`
- **الحقوق**: السطر `copyright_text` في `strings.xml`

## الترخيص

© 2026 GW IPTV — جميع الحقوق محفوظة

---

**تم البناء باستخدام:** Kotlin · Material 3 · ExoPlayer (Media3) · Retrofit · AndroidX Security
