# Week 1 · บทที่ 1: Async/Await ให้เข้าใจถึงแก่น

## 🎯 เป้าหมาย
จบบทนี้คุณต้อง: อธิบายได้ว่าทำไม JS ต้องมี async, เขียน async/await + try/catch ได้โดยไม่เปิด docs และอ่านโค้ด Promise ของคนอื่นออก

---

## 📖 Mini-lecture (10 นาที)

### 1. ทำไมต้องมี Async?
JavaScript มี **thread เดียว** — ถ้ารอแบบ blocking (เช่น รอ API 2 วินาที) ทั้งหน้าเว็บจะค้าง กดอะไรไม่ได้เลย Async คือการ "สั่งงานทิ้งไว้ แล้วไปทำอย่างอื่นก่อน เสร็จแล้วค่อยกลับมา"

### 2. วิวัฒนาการ 3 ยุค (ต้องเล่าได้ใน interview)
```js
// ยุค 1: Callback — ซ้อนลึก ดัก err ทุกชั้น (Callback Hell)
login(user, pass, (err, u) => {
  if (err) return handle(err);
  getProfile(u.id, (err, p) => {
    if (err) return handle(err); // ซ้อนไปเรื่อย ๆ...
  });
});

// ยุค 2: Promise — ต่อคิวแบน ๆ ดัก err จุดเดียว
login(user, pass)
  .then(u => getProfile(u.id))
  .then(p => console.log(p))
  .catch(handle);

// ยุค 3: async/await — เขียนเหมือนโค้ดปกติ (ที่ใช้จริงทุกวันนี้)
const run = async () => {
  try {
    const u = await login(user, pass);
    const p = await getProfile(u.id);
    console.log(p);
  } catch (err) { handle(err); }
};
```

### 3. กฎที่คนพลาดบ่อย
- `await` ใช้ได้เฉพาะในฟังก์ชันที่มี `async`
- ฟังก์ชัน `async` คืนค่าเป็น **Promise เสมอ** (แม้ return ตัวเลขธรรมดา)
- ลืม `await` = ได้ Promise object แทนค่าจริง (บั๊กยอดฮิต — `console.log` แล้วเจอ `Promise {<pending>}`)
- `try/catch` ครอบเฉพาะจุดที่ await — error ที่เกิดนอก try จะหลุด

---

## 🎯 Mission 1.1: เครื่องชงกาแฟ async (20 นาที)
เขียนใน console หรือไฟล์ `practice/coffee.js` (รันด้วย node):

1. สร้างฟังก์ชัน `grindBeans()` คืน Promise — สำเร็จหลัง 1 วิ ได้ค่า `"ผงกาแฟ"`
2. สร้าง `brew(powder)` คืน Promise — สำเร็จหลัง 1.5 วิ ได้ `"เอสเพรสโซ่"` แต่**ถ้า powder ไม่ใช่ "ผงกาแฟ" ให้ reject** ด้วย `"วัตถุดิบผิด!"`
3. เขียนฟังก์ชัน async `makeCoffee()` เรียกทั้งสองตามลำดับ + try/catch + log ทุกขั้น
4. ทดสอบ 2 เคส: เคสปกติ และเคสส่งค่าผิดเข้า brew (ต้องเห็น error จาก catch ไม่ใช่ crash)

**ห้ามเปิดบท 17 ของคอร์สเดิมจนกว่าจะลองเองครบ 20 นาที**

## 🎯 Mission 1.2: อ่านโค้ดแล้วทายผล (10 นาที)
ก่อนรัน — ทายลำดับ output แล้วค่อยรันตรวจ:
```js
console.log("A");
setTimeout(() => console.log("B"), 0);
const f = async () => { console.log("C"); await null; console.log("D"); };
f();
console.log("E");
```
เขียนคำตอบ + เหตุผลของคุณส่งมาใน chat (ข้อนี้คือคำถาม interview จริงของหลายบริษัท)

---

## 📝 Quiz ท้ายบท (ตอบใน chat)
1. ฟังก์ชัน `async` ที่ `return 42` — คนเรียกจะได้อะไร และต้องเอาค่าออกมายังไง
2. โค้ดนี้ผิดตรงไหน: `const data = fetch(url).json();`
3. ถ้ามี await 3 ตัวที่**ไม่ขึ้นต่อกัน** เรียงต่อกัน จะช้ากว่าที่ควรเพราะอะไร และแก้ด้วยอะไร (ใบ้: `Promise.___`)

## ✅ Checkpoint
- [ ] Mission 1.1 รันผ่านทั้ง 2 เคส
- [ ] Mission 1.2 ทายถูก (หรือเข้าใจหลังเฉลย)
- [ ] Quiz ส่งแล้ว
- [ ] จดโน้ต `notes/async-await.md` (≤ 15 บรรทัด)
