# Registry Calculator: APK aur EXE kaise banayein

Ye project Registry Calculator (zameen, flat aur lease deed) ko Android APK aur Windows EXE me badalta hai. Sab kuch offline chalta hai.

## Tarika 1: GitHub se (PC par kuch install nahi karna)

1. github.com par free account banayein aur ek naya repository banayein (Private bhi chalega).
2. Is folder ki saari files us repository me upload karein (`.github` folder bhi, ye zaroori hai).
3. Repository me **Actions** tab kholein, **Build APK and EXE** chunein aur **Run workflow** dabayein.
4. Lagbhag 8 se 12 minute baad run complete hoga. Run ke page ke neeche **Artifacts** me do download milenge:
   - `Registry-Calculator-APK`: isme `app-debug.apk` hai. Mobile me copy karke install karein (Unknown sources allow karna padega).
   - `Registry-Calculator-EXE`: isme `Registry-Calculator-Setup-1.0.0.exe` (installer) aur `Registry-Calculator-Portable-1.0.0.exe` (bina install chalne wala) hai.

## Tarika 2: Apne PC par banana

Zaroori: Node.js 20 ya naya. APK ke liye Android Studio aur Java 17 bhi.

EXE (Windows):
```
npm install
npm run build:win
```
EXE `dist` folder me milega. Seedha chalakar dekhne ke liye `npm start`.

APK:
```
npm install
npx cap add android
npx capacitor-assets generate --android
npx cap sync android
cd android
gradlew assembleDebug
```
APK `android/app/build/outputs/apk/debug/app-debug.apk` me milega.

## Calculator me badlav karna

Calculator ka poora code `www/index.html` me hai. Isme badlav karke upar wale steps dobara chalayein (GitHub par file badalkar commit karte hi naya build ban jayega).

## Dhyan dein

- Ye APK "debug" signed hai. Apne mobile par install karne ke liye theek hai. Play Store par daalne ke liye alag release signing key chahiye.
- Windows par pehli baar EXE chalane par SmartScreen "Unknown publisher" dikha sakta hai (EXE par digital signature nahi hai). "More info" aur "Run anyway" dabayein.
- Stamp duty ki dar (5% / 4%) aur baaki dar calculator ke andar badli ja sakti hain. Final rakam se pehle Sub-Registrar se pushti kar lein.
