# مِداد — MIDAD releases

Signed installers for **MIDAD**, a private, end‑to‑end encrypted notes app in Arabic and English.
This repository holds release files only — no source code. Each release has:

| File | What it is |
| --- | --- |
| `MIDAD_x.y.z_x64-setup.exe` | Windows installer (per‑user, no administrator rights needed) |
| `MIDAD_x.y.z_x64-setup.exe.sig` | Signature the app checks before installing an update |
| `MIDAD-x.y.z.apk` | Android app, signed with the MIDAD release key (APK Signature Scheme v2 + v3) |
| `SHA256SUMS.txt` | SHA‑256 checksums of the installer and the APK |
| `latest.json` | What the apps read to find updates |

## Install

**Windows** — run the installer. Windows SmartScreen may say “Windows protected your PC”, because
the installer is not signed with a paid code‑signing certificate: choose **More info → Run anyway**.
After that, MIDAD updates itself: it downloads new versions from here and installs them only if
their signature matches the key built into the app.

**Android** — open the APK on the phone and allow installing from this source when asked. MIDAD
checks for updates on launch, downloads the new APK, verifies its SHA‑256 checksum, and hands it to
Android's installer; Android itself refuses any APK not signed with the same key.

## Verify a download (optional)

```powershell
Get-FileHash .\MIDAD-1.0.1.apk -Algorithm SHA256
```

The result must match the line in `SHA256SUMS.txt`. The APK's signing certificate:

```
SHA-256: F2:D0:25:E5:14:CE:69:BE:20:4F:81:27:2C:AD:D5:39:8B:6D:6C:1E:F1:FD:81:9F:C6:1B:3B:4D:88:8E:CD:F1
```

(`apksigner verify --print-certs MIDAD-x.y.z.apk` shows it.)

---

ملفات إصدارات مِداد الموقّعة فقط (دون الشيفرة المصدرية). على Windows قد تظهر رسالة SmartScreen
لأن المثبّت غير موقّع بشهادة تجارية: اختر **مزيد من المعلومات ← التشغيل على أي حال**. بعد ذلك يحدّث
التطبيق نفسه ويتحقّق من توقيع كل تحديث قبل تثبيته. على Android افتح ملف APK واسمح بالتثبيت من هذا
المصدر؛ يتحقّق التطبيق من بصمة SHA‑256 لكل تحديث، ويرفض Android أي نسخة غير موقّعة بالمفتاح نفسه.
