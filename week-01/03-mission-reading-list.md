# Week 1 · บทที่ 3: Mission ใหญ่ — "My Reading List" 📚

## 🎯 เป้าหมาย
รวมทุกอย่างของ Frontend เป็นชิ้นงานจริง 1 ชิ้น: Semantic HTML + Bootstrap + Fetch + LocalStorage + Event Handling
นี่คือ **ตัววัดว่าพร้อมเข้า backend หรือยัง** — ทำได้โดยไม่เปิดเฉลย = พร้อม

> สเปคเต็มอยู่ที่ [บท 19 ของคอร์สเดิม](https://021.wwry.net/19-final-workshop.html) — เปิดดูได้เฉพาะ "โจทย์/รูปผลลัพธ์" **ห้ามดูโค้ดตัวอย่าง HTML/JS ของเขา** ให้เขียนเองจากสเปคด้านล่าง

## 📋 สเปค (แบบที่ลูกค้าจริงจะเขียนให้คุณ)
แอปอ่านบทความ: ดึงบทความ 6 ชิ้นจาก `https://jsonplaceholder.typicode.com/posts?_limit=6` แสดงใน main area / กด "บันทึก" เก็บลง sidebar + localStorage / ลบทีละชิ้นหรือล้างทั้งหมดได้ / refresh แล้วรายการที่บันทึกต้องอยู่ครบ

## 🪜 แบ่งเป็น 5 Mission ย่อย (ทำทีละขั้น เทสต์ทุกขั้น)

### Mission 3.1 — โครง HTML (45 นาที)
- Semantic: `<header>` (navbar) / `<main class="col-md-8">` / `<aside class="col-md-4">` / `<footer>`
- Bootstrap 5 ผ่าน CDN, มี `id="articleContainer"`, `id="savedList"`, ปุ่ม `id="btnClear"`
- ✅ เทสต์: เปิดแล้วเห็น layout 2 คอลัมน์บนจอคอม / ซ้อนกันบนมือถือ (ย่อจอดู)

### Mission 3.2 — Fetch + Render (45 นาที)
- ฟังก์ชัน `loadArticles()`: fetch → เช็ค `res.ok` → วนสร้าง card (ใช้ `.map()` + template literal ไม่ใช่ต่อ string ใน loop)
- เนื้อหายาวเกิน 80 ตัวอักษร → `substring(0, 80) + "..."`
- มีสถานะ "กำลังโหลด..." และกรณี error
- ✅ เทสต์: ปิด WiFi แล้ว refresh — ต้องเห็น error message ไม่ใช่หน้าค้าง

### Mission 3.3 — บันทึก (60 นาที)
- ปุ่มบันทึกในแต่ละ card → สร้าง object `{ id, title }` → อ่าน array เดิมจาก localStorage → **เช็คซ้ำก่อน push** → save กลับ → อัปเดต sidebar
- ✅ เทสต์: บันทึกซ้ำชิ้นเดิม ต้องเด้งเตือนและไม่เพิ่มซ้ำ

### Mission 3.4 — โหลด + ลบ (45 นาที)
- `loadSaved()` รันตอนเปิดเว็บ / ปุ่ม X ลบทีละชิ้น (ใช้ `.filter()`) / btnClear ล้างหมด (มี `confirm()`)
- ✅ เทสต์: บันทึก 3 ชิ้น → refresh → ต้องอยู่ครบ 3 → ลบ 1 → refresh → เหลือ 2

### Mission 3.5 — Deploy (30 นาที)
- git init → commit → push ขึ้น GitHub (repo ใหม่ชื่อ `reading-list`)
- เปิด GitHub Pages → ได้ URL จริง
- ✅ เทสต์: เปิด URL จากมือถือ (คนละเครื่อง) ต้องใช้งานได้

## 📏 เกณฑ์ให้คะแนนตอนผม review (บอกล่วงหน้าให้เล็งถูก)
1. ความถูกต้องตามสเปค (40%) — ทุกเทสต์ข้างบนผ่าน
2. คุณภาพโค้ด (30%) — ชื่อตัวแปรสื่อความหมาย, ไม่มีโค้ดตาย, แยกฟังก์ชันชัด
3. Error handling (20%) — res.ok, null จาก localStorage, ปุ่มกดรัว
4. Git hygiene (10%) — commit message สื่อความหมาย ไม่ใช่ "update" 5 รอบ

## ✅ Checkpoint สัปดาห์
- [ ] ทั้ง 5 Mission ผ่านเทสต์ของตัวเอง
- [ ] ส่ง URL (GitHub repo + GitHub Pages) ให้ผม review ใน chat
- [ ] ตอบ Quiz รวมจากบท 1-2 ครบแล้ว
