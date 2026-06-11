# 🎓 คอร์ส: Senior Secure Full Stack (24 สัปดาห์)
> ผู้เรียน: วี | ผู้สอน: Claude | เริ่ม: มิ.ย. 2026

**เอกสารมาตรฐานของคอร์ส** (Claude ต้องยึดทุกครั้งที่สร้างเนื้อหา):
`lesson-standards.md` (โครงบทเรียน 5 ส่วน: แนวคิด dev → why ทีละบรรทัด → ตัวอย่างใช้จริง → Mission เป็นผลงาน → Quiz ความเข้าใจ) · `portfolio-standard.md` (มาตรฐาน repo) · `ai-workflow.md` (กฎ AI)

## วิธีใช้คอร์สนี้
1. แต่ละสัปดาห์มีโฟลเดอร์ `week-XX/` ข้างในมีบทเรียนเรียงเลข อ่านและทำตามลำดับ
2. ทุกบทใช้โครงเดียวกัน: **เป้าหมาย → Mini-lecture → Mission → Quiz → Checkpoint**
3. Mission = คุณเขียนเองทั้งหมด ผมไม่เขียนให้ (ติดเมื่อไหร่ ถามใน chat ผมให้ hint ทีละชั้น)
4. Quiz ทำเสร็จแล้วส่งคำตอบใน chat — ผมตรวจ + อธิบายข้อที่พลาด
5. จบสัปดาห์ → บอกผมใน chat → ผม review งาน + สร้างบทเรียนสัปดาห์ถัดไป (ปรับตามจุดอ่อนที่เจอ)
6. ทุกวันศุกร์: Friday Rebuild 30 นาที (ดู `friday-rebuild.md`)

## แผนที่คอร์ส

### เฟส 1: ปิดช่องว่าง Resume ↔ โค้ดจริง (สัปดาห์ 1-8)
- [ ] **Week 01** — ปิดจบ Frontend: Async/Fetch + Reading List + Deploy ✅ บทเรียนพร้อมแล้ว
- [ ] Week 02 — Kcode Day 1-2: library-system + Express + โครงสร้างโปรเจกต์
- [ ] Week 03 — Kcode Day 3: Express core + **เริ่ม Vitest/Supertest** (ภารกิจเสริม)
- [ ] Week 04 — Kcode Day 3-4: Docker + PostgreSQL + **Zod validation**
- [ ] Week 05 — Kcode Day 4-5: JWT + protect routes + **test ครอบ auth**
- [ ] Week 06 — **TypeScript I**: แปลง backend เป็น TS (strict)
- [ ] Week 07 — **TypeScript II**: generics, utility types + จบการแปลง
- [ ] Week 08 — Kcode Day 6-7: Next.js (TS) + Tailwind + fullstack integration
> ✅ Checkpoint เฟส 1: backend TS + test coverage ≥ 70% — โค้ดไล่ทัน resume

### เฟส 2: Production จริง (สัปดาห์ 9-16)
- [ ] Week 09-10 — Kcode Day 8: ระบบเต็ม (auth pages, protected routes, CRUD, dashboard)
- [ ] Week 11-12 — Docker multi-stage + compose (app+db+redis)
- [ ] Week 13-14 — Kcode Day 9 + GitHub Actions: lint→test→build→deploy
- [ ] Week 15 — Staging/Production + logging (pino) + Sentry
- [ ] Week 16 — โปรเจกต์เสริม: rebuild automation report (GA4/Meta) เป็น TS service
> ✅ Checkpoint เฟส 2: push → deploy อัตโนมัติ

### เฟส 3: Security-First (สัปดาห์ 17-20)
- [ ] Week 17 — OWASP Top 10 ฝั่งป้องกัน + hardening (rate limit, CSP, helmet)
- [ ] Week 18 — OAuth 2.0/OIDC + token storage ที่ถูกต้อง
- [ ] Week 19 — Security ใน CI: npm audit, Semgrep, secret scanning
- [ ] Week 20 — **Pentest โปรเจกต์ตัวเอง** → รายงาน attack→fix ≥ 5 ช่องโหว่
> ✅ Checkpoint เฟส 3: รายงาน pentest portfolio piece

### เฟส 4: System Design + Capstone (สัปดาห์ 21-24)
- [ ] Week 21 — Caching, queue (BullMQ), indexing, N+1, pagination
- [ ] Week 22-23 — Capstone: SecureShare หรือ VulnTracker
- [ ] Week 24 — จบ Capstone + อัปเดต resume/portfolio + mock interview กับผม
> ✅ Checkpoint จบคอร์ส: เล่าโปรเจกต์ใน interview ได้ 30 นาที

### หลังจบคอร์ส (เส้นทางต่อ)
**ภาค 2 ของคอร์สอยู่ที่ `README-week25plus.md`** — โครงเดียวกับภาคนี้: เฟส 5-10 (W25-52) รายสัปดาห์พร้อม checkbox + ภาค 3 Agoda Track (W53-92)
แผนฉบับเล่าเรื่อง/แผนสำรองอยู่ที่ `../plans/POST-COURSE-PLAN.md` · Agoda รายเดือนที่ `../plans/AGODA-PREP-TRACK.md`
> ⚠️ ห้ามเริ่ม Agoda Track ก่อนจบคอร์สนี้ — ฐานไม่แน่นจะเสียเวลาคูณสอง

## กติกาประจำคอร์ส
- **กฎ 20 นาที:** วันที่งาน WordPress กินทั้งวัน แตะโค้ดคอร์สอย่างน้อย 20 นาที
- **จดโน้ต recipe:** เรียนอะไรใหม่ จดใน `notes/` วันนั้น ≤ 15 บรรทัด
- **ห้ามเปิดเฉลยก่อนพยายาม 20 นาที** (struggle คือจุดที่สมองจำ)
- **กฎ AI สองโหมด:** ระหว่างทำ Mission = ปิด AI ทั้งหมด เขียนมือล้วน / นอก Mission ใช้ตามกติกาใน `ai-workflow.md`
- **AI Code Review Drill:** สัปดาห์ละ 30 นาที (โจทย์อยู่ท้ายบทเรียนแต่ละสัปดาห์ เริ่ม Week 2)
- **ทุกชิ้นงานขึ้น Git:** push GitLab/GitHub พร้อม README ที่มี section "AI Usage" ตาม template
