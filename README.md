# Noor-ut-Tajweed — Android App (Cordova)

Yeh aapki HTML app (Tajweed Interactive) ko ek native-compatible Android
Cordova project mein convert kiya gaya hai. GitHub Actions workflow already
included hai jo APK khud bana degi — aapko apne computer par Android Studio
install karne ki zaroorat nahi.

## APK banane ka tareeqa (GitHub se)

1. Is zip ko extract karein.
2. GitHub par ek **naya empty repository** banayein (public ya private, dono chalega).
3. Extract ki hui files us repo mein push karein:
   ```bash
   cd TajweedApp
   git init
   git add .
   git commit -m "Initial commit - Noor ut Tajweed app"
   git branch -M main
   git remote add origin <aapke-repo-ka-URL>
   git push -u origin main
   ```
4. GitHub par apne repo ke **"Actions"** tab par jaayein.
5. "Build Android APK" workflow khud chalegi (push par). Agar na chale to
   "Run workflow" button se manually trigger kar dein.
6. Build complete hone (2–4 minute) ke baad, us workflow run ko open karein
   aur neeche **"Artifacts"** section mein `noor-ut-tajweed-apk` milega —
   ise download kar lein. Andar `app-debug.apk` hoga.
7. Yeh APK apne Android phone par transfer karke install kar lein ("Unknown
   sources" install allow karna padega, kyunki yeh Play Store se nahi hai).

## Zaroori baatein

- Yeh **debug APK** hai (unsigned, testing ke liye theek hai). Agar Play
  Store par publish karna ho to signed release APK/AAB banana hoga (alag
  process — bata dein to woh workflow bhi bana dun).
- App ke andar Tailwind CSS, Chart.js aur Google Fonts CDN se load hote hain,
  is liye **phone mein internet connection zaroori hai** app chalane ke
  liye. Agar aap chahen to main inhe offline (local files) bhi bana sakta
  hun taake bina internet ke bhi chale.
- Awaaz (pronunciation) wala feature browser ke built-in Text-to-Speech
  (Web Speech API) par depend karta hai — Android WebView mein yeh sab
  devices par consistent tarah se kaam nahi karta.

## Project structure

```
TajweedApp/
├── config.xml              # Cordova app config (package id, permissions)
├── package.json
├── www/
│   └── index.html           # Aapki asal Tajweed app (extracted & cleaned)
└── .github/workflows/
    └── build-apk.yml        # GitHub Actions — APK build karta hai
```

Package/App ID: `com.noor.tajweed` — isko config.xml mein change kar sakte
hain agar apna ID chahiye.
