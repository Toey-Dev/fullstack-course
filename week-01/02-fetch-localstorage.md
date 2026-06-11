# Week 1 · บทที่ 2: Fetch API + LocalStorage (มุมมองคนเคยเป็น Pentester)

## 🎯 เป้าหมาย
ดึงข้อมูลจาก API จริงพร้อมจัดการ loading/error ครบ และรู้ว่าอะไร "ห้าม" เก็บใน localStorage — ข้อหลังนี้คือจุดที่คุณได้เปรียบคนอื่นในตลาด

---

## 📖 Mini-lecture (10 นาที)

### 1. Pattern มาตรฐานที่ใช้ตลอดชีวิต
```js
const loadData = async () => {
  showLoading();                       // 1. UI: กำลังโหลด
  try {
    const res = await fetch(url);      // 2. รอ response
    if (!res.ok) throw new Error(`HTTP ${res.status}`); // 3. เช็คก่อนเสมอ!
    const data = await res.json();     // 4. แกะ JSON
    render(data);                      // 5. UI: สำเร็จ
  } catch (err) {
    showError(err.message);            // 6. UI: ผิดพลาด
  } finally {
    hideLoading();                     // 7. ปิด loading ทุกกรณี
  }
};
```
**จุดที่มือใหม่พลาด:** `fetch` ไม่ throw เมื่อได้ 404/500 — มัน throw เฉพาะ network ล่ม ดังนั้นต้องเช็ค `res.ok` เองเสมอ (บรรทัดที่ 3)

### 2. LocalStorage: กฎ 3 ข้อ
- เก็บได้แค่ string → `JSON.stringify()` เก็บ / `JSON.parse()` อ่าน
- อ่านครั้งแรกอาจเป็น `null` → ใช้ pattern `JSON.parse(localStorage.getItem("key")) ?? []`
- แยกตาม domain — เว็บอื่นอ่านของเราไม่ได้

### 3. 🔐 มุม Security (จุดขายของวี)
localStorage ถูกอ่านได้ด้วย JS ทุกบรรทัดในหน้า → ถ้าโดน **XSS** แม้แต่ script เดียว ข้อมูลทั้งหมดรั่ว
- ❌ ห้ามเก็บ: password, access token อายุยาว, ข้อมูลส่วนตัว
- ✅ เก็บได้: theme, ตะกร้าชั่วคราว, cache ที่ไม่ลับ
- ระบบ auth จริงนิยม: token ใน **HttpOnly cookie** (JS อ่านไม่ได้) — เรื่องนี้จะเจอจริงใน Kcode Day 5 และจะเป็นหัวข้อ debate ที่ผมจะถามคุณตอนนั้น

---

## 🎯 Mission 2.1: Pokedex มินิ (30 นาที)
สร้าง `practice/pokedex.html` (หน้าเดียวจบ):
1. ช่อง input + ปุ่มค้นหา → fetch `https://pokeapi.co/api/v2/pokemon/{ชื่อ}`
2. เจอ → แสดงชื่อ + รูป (`data.sprites.front_default`) + น้ำหนัก
3. ไม่เจอ (404) → ข้อความสีแดง "ไม่พบโปเกมอน" (ทดสอบ: พิมพ์ชื่อมั่ว)
4. ระหว่างโหลด → แสดง "กำลังค้นหา..." และ**ปุ่มต้องกดซ้ำไม่ได้** (disabled)

ข้อ 4 คือสิ่งที่คอร์สเดิมไม่สอนแต่งานจริงต้องมี (กันผู้ใช้กดรัว = ยิง API ซ้ำ)

## 🎯 Mission 2.2: เพิ่มระบบ Favorites (20 นาที)
ต่อจาก 2.1: ปุ่ม "เก็บเข้ากระเป๋า" → push ชื่อลง array ใน localStorage (กันชื่อซ้ำ) → แสดงรายการใต้หน้า → โหลดอัตโนมัติตอนเปิดเว็บ → ปุ่มล้างทั้งหมด (มี confirm)

---

## 📝 Quiz ท้ายบท (ตอบใน chat)
1. ทำไม `fetch` ที่ได้ 500 ถึงไม่เข้า catch ถ้าไม่เช็ค `res.ok` — แล้ว network ล่มต่างกันยังไง
2. ในมุม pentester: อธิบายการโจมตี 1 รูปแบบที่ทำให้ token ใน localStorage รั่ว และ HttpOnly cookie ป้องกันได้เพราะอะไร
3. `JSON.parse(localStorage.getItem("x")) ?? []` — `??` ทำหน้าที่อะไร ต่างจาก `||` ยังไง

## ✅ Checkpoint
- [ ] Pokedex ครบ 4 ข้อ (รวม disabled ตอนโหลด)
- [ ] Favorites รอด refresh
- [ ] Quiz ส่งแล้ว + โน้ต `notes/fetch-localstorage.md`
