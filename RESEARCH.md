# ค้นคว้า: ลู่วิ่ง Kingsmith MX16+ & แนวทาง run-coach (2026-06-07)

> สรุปเพื่อยืนยันทิศทาง design ของ run-coach (manual coaching) — ไม่ต้องเปลี่ยน

## ลู่ Kingsmith MX16+ โดยย่อ
- **แอปทางการ:** KS Fit (iOS+Android, package `com.kingsmith.xiaojin`) — คุมความเร็ว, 11 โปรแกรม, ตั้งเป้า (เวลา/ระยะ/ก้าว/แคล), ดูสถิติ, NFC sync
- **รีวิว ~1.9 ดาว:** BT หลุดบ่อย, บังคับล็อกอิน+GPS, ต้องเปิดแอปค้าง, UI รก, **ไม่มีภาษาไทย**
- **สเปคคุม:** ความเร็ว 1–16 กม./ชม. · **ไม่มีความชัน / ไม่มี auto-incline** (พื้นราบล้วน)
- **เชื่อมต่อ:** BLE + NFC · FTMS น่าจะรองรับระดับซีรีส์ (third-party QZ/qdomyos-zwift เชื่อม Zwift/Strava ได้) · KS Fit → Apple Health/Strava sync ไม่ชัด

## ผลต่อ run-coach
**เสริมไม่ซ้ำ** — จุดแข็ง run-coach ที่ KS Fit ไม่มี: โซนหัวใจ (HR zone) · หลักสูตร 8 สัปดาห์ไล่ระดับ · UX ที่ดีกว่า

**Auto-control ลู่ผ่านเว็บ = ทำไม่ได้บน iPhone (ทางตัน):**
- Web Bluetooth ไม่มีบน iOS Safari/WebKit ทุกเวอร์ชัน (รวม iOS 18) → Chrome/Edge บน iPhone ก็ไม่ได้ (บังคับใช้ WebKit)
- ทางอ้อมต้องโหลดเบราว์เซอร์พิเศษ (Bluefy/WebBLE) = พัง UX ไม่ควรทำเป็น flow หลัก
- MX16+ ไม่มี incline เหลือคุมแค่ความเร็ว + การเร่งลู่อัตโนมัติมีความเสี่ยงความปลอดภัย

**→ คงโมเดล manual (ผู้ใช้กดปรับลู่เอง) ถูกต้องแล้ว.** ถ้าจะเพิ่มความฉลาดในอนาคต: ดึง HR จาก Apple HealthKit (ต้องเป็น native app/wrapper ไม่ใช่เว็บล้วน) หรือให้กรอกเอง; auto-control จริงจังต้องเป็น iOS native (Core Bluetooth) + ลู่ที่มี incline ถึงจะคุ้ม

## แหล่งอ้างอิงหลัก
- Kingsmith MX16+ official · KS Fit (App/Play Store + รีวิว)
- 3G Cardio — FTMS speed control limits · QZ qdomyos-zwift (GitHub)
- WebKit Web Bluetooth bug #101034 · iOS Core Bluetooth guide
