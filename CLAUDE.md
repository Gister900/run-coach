# run-coach — context สำหรับ Claude

แอปผู้ช่วยวิ่งบนลู่ 8 สัปดาห์ (PWA, static, ไฟล์เดียว). เจ้าของ: CJ. ใช้บนมือถือเป็นหลัก.

## หลักการ
- **static ล้วน** — ไม่มี backend, ไม่มี build step. แก้ `index.html` แล้วเปิดได้เลย
- **source of truth คือ `index.html`** — UI, logic, ตารางโปรแกรม 8 สัปดาห์ อยู่ในนี้ทั้งหมด
- **มือถือมาก่อน** — ทดสอบที่ความกว้าง ~390px, ปุ่มแตะง่าย, เต็มจอ
- **offline ต้องไม่พัง** — ถ้าแก้ asset เพิ่ม อย่าลืมเพิ่มใน `ASSETS` ของ `sw.js` และ bump `CACHE` version (`runcoach-vN`)

## โครงโปรแกรม (ใน index.html)
- `DAY_DEFS` = 7 วัน/สัปดาห์: easy, interval, recovery, tempo, easy, long, rest
- builder แต่ละชนิด (`easyDay`/`intervalDay`/...) รับเลขสัปดาห์ 1–8 คืน segment list
- `S(name, sec, speed, incline, zone, opts)` = factory สร้าง 1 ช่วง
- โซนหัวใจ: `ZPCT` (% ของ Max HR), `zoneBpm(z)` คำนวณช่วง bpm

## งานที่มักทำ
- ปรับความเร็ว/ระยะของโปรแกรม → แก้ cfg ใน builder ของวันนั้น
- เพิ่มสัปดาห์/วัน → แก้ `DAY_DEFS` + cfg array (index ตามสัปดาห์)
- เปลี่ยน icon → แก้ `icons/icon.svg` แล้ว `qlmanage -t -s 512 -o . icon.svg` + `sips -z 192 192`

## Deploy
GitHub Pages (repo ส่วนตัว), branch `main`, serve จาก root. push = อัปเดต production.

## ทดสอบ
`python3 -m http.server 8080` แล้วเปิด `http://localhost:8080` (ต้องผ่าน http ให้ SW ทำงาน).
