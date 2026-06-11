# 📦 มาตรฐาน Repo ระดับ Portfolio
> ทุกชิ้นงานในคอร์สที่ push ขึ้น GitLab/GitHub ต้องผ่าน checklist นี้ — เพื่อให้ "ทุก repo คือผลงานสมัครงานได้ทันที"

## โครงสร้างขั้นต่ำของทุก repo
```
my-project/
├── README.md          ← หน้าตาของผลงาน (สำคัญที่สุด)
├── .gitignore         ← ห้ามมี node_modules, .env, ไฟล์ขยะ
├── src/ หรือไฟล์งาน
└── (ถ้ามี) .env.example  ← ตัวอย่าง config โดยไม่มีค่าจริง
```

## README Template (ใช้ทุก repo)
```markdown
# ชื่อโปรเจกต์
ประโยคเดียวว่าทำอะไร + [🔗 Live Demo](url)

## Features
- ลิสต์สั้น ๆ 3-6 ข้อ ที่ทำได้จริง

## Tech Stack
HTML/CSS · JavaScript (ES6) · Bootstrap 5 · ... (ตามจริง)

## What I Learned
- 2-4 ข้อ เขียนแบบเฉพาะเจาะจง เช่น "การเช็ค res.ok เพราะ fetch ไม่ throw เมื่อได้ 404"
  (section นี้ทำให้ repo ฝึกหัดกลายเป็นหลักฐานการเติบโต — recruiter ชอบมาก)

## Setup
วิธีรัน 2-5 บรรทัด (clone → install → run)

## AI Usage
ตาม template ใน ai-workflow.md — โปร่งใสเสมอ
```

## มาตรฐาน Git
- **Commit message:** `ประเภท: สิ่งที่ทำ` เช่น `feat: add localstorage persistence`, `fix: handle 404 from api`, `refactor: extract render function`
  - ประเภทหลัก: `feat` / `fix` / `refactor` / `docs` / `test` / `chore`
  - ❌ ห้าม: "update", "แก้บัค", "aaa", commit ก้อนยักษ์ทีเดียวจบ
- **Commit เป็นจังหวะ:** จบ 1 mission ย่อย = 1 commit (เล่าเรื่องการสร้างงานได้จาก history)
- **Branch:** โปรเจกต์เล็กใช้ main ได้ / ตั้งแต่เฟส 2 จะเริ่มใช้ feature branch + merge ให้เหมือนทำงานทีม

## มาตรฐานโค้ด (เริ่มบังคับตั้งแต่ Week 1)
- ชื่อตัวแปร/ฟังก์ชันเป็นภาษาอังกฤษ สื่อความหมาย (`savedArticles` ไม่ใช่ `data2`)
- ไม่มีโค้ดตาย: comment ทดลอง, `console.log` debug, ตัวแปรไม่ได้ใช้ — ลบก่อน commit เสมอ (บทเรียนจาก Project2)
- สะกดถูก: `FirstCard` ไม่ใช่ `FristCard` — เปิด Code Spell Checker ช่วย
- ฟังก์ชันละหน้าที่เดียว ตั้งชื่อเป็นกริยา: `loadArticles`, `renderSaved`, `removeArticle`

## เช็คก่อน push ทุกครั้ง (30 วินาที)
- [ ] README ครบตาม template + ลิงก์ demo ใช้ได้
- [ ] ไม่มี secret/รหัสผ่าน/token ในโค้ด (สแกนด้วยตาทุกไฟล์ — นิสัย pentester)
- [ ] ไม่มีโค้ดตาย / console.log ขยะ
- [ ] เปิดจากเครื่อง/มือถืออื่นแล้วใช้งานได้จริง
