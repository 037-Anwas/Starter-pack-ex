# Workshop: GitHub, Markdown & Git เบื้องต้น

---

## ส่วนที่ 1 — สร้าง Repository บน GitHub

1. ไปที่ https://github.com แล้ว login
2. กด **"+"** มุมขวาบน → **"New repository"**
3. ตั้งชื่อว่า `my-first-repo`
4. เลือก **Public**
5. ติ๊ก **"Add a README file"**
6. กด **"Create repository"**

---

## ส่วนที่ 2 — เขียน README ด้วย Markdown

1. คลิกที่ไฟล์ **README.md**
2. กดไอคอน ✏️ มุมขวาบน
3. ลบข้อความเดิมออก แล้วพิมพ์เนื้อหาด้านล่างนี้

```markdown
# ชื่อของฉัน

## เกี่ยวกับฉัน
- 📍 กรุงเทพฯ ประเทศไทย
- 🌱 กำลังเรียนรู้ Git และ GitHub
- 💬 ถามฉันเกี่ยวกับ ...

## สิ่งที่กำลังเรียน

| หัวข้อ       | สถานะ         |
|-------------|--------------|
| GitHub      | ✅ เรียนแล้ว  |
| Markdown    | ✅ เรียนแล้ว  |
| Git         | 🔄 กำลังเรียน |

## บันทึก

> "Talk is cheap. Show me the code."
> — Linus Torvalds

## สิ่งที่ต้องทำ
- [x] สร้าง GitHub account
- [x] สร้าง repository แรก
- [ ] เรียนรู้ git clone
```

4. กด **"Preview"** เพื่อดูผลลัพธ์
5. เลื่อนลงล่าง ใส่ commit message ว่า `docs: add README content`
6. กด **"Commit changes"**

---

## ส่วนที่ 3 — สร้างไฟล์ใหม่บน GitHub

1. กลับหน้าหลักของ repo
2. กด **"Add file"** → **"Create new file"**
3. ตั้งชื่อไฟล์ว่า `notes.md`
4. พิมพ์เนื้อหาด้านล่าง

```markdown
# บันทึกการเรียน

## Markdown ที่ใช้ได้แล้ว

### ตัวอักษร
**ตัวหนา** และ *ตัวเอียง* และ ~~ขีดทับ~~

### โค้ด
ใช้ backtick สำหรับ `inline code`

และใช้สามอันสำหรับ code block

```bash
git clone URL
```

### รูปภาพ
![GitHub](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

5. commit ด้วย message ว่า `docs: add notes`

---

## ส่วนที่ 4 — ตั้งค่า Git บนเครื่อง

เปิด terminal ขึ้นมา พิมพ์ทีละบรรทัด

```bash
git config --global user.name "ชื่อของคุณ"
git config --global user.email "อีเมลที่ใช้สมัคร GitHub"
```

ตรวจสอบว่าถูกต้อง

```bash
git config --list
```

---

## ส่วนที่ 5 — Clone Repository ลงเครื่อง

1. ไปที่ repo บน GitHub
2. กดปุ่ม **"<> Code"** (สีเขียว)
3. คัดลอก URL ใต้ HTTPS
4. กลับมาที่ terminal พิมพ์

```bash
git clone URL_ที่คัดลอกมา
```

5. เข้าไปในโฟลเดอร์ที่ clone มา

```bash
cd my-first-repo
```

6. ดูว่าไฟล์ที่สร้างบน GitHub อยู่ในเครื่องแล้ว

```bash
ls
```

> สิ่งที่ทำทั้งหมดบนเว็บ GitHub ตอนนี้อยู่ในเครื่องแล้ว ✅

---

## ✅ Checklist

- [ ] สร้าง repo บน GitHub ได้
- [ ] เขียน README ด้วย Markdown บนเว็บได้
- [ ] ใช้ heading, list, table, blockquote, checkbox, code block ได้
- [ ] สร้างไฟล์ใหม่บน GitHub ได้
- [ ] ตั้งค่า git config ได้
- [ ] clone repo ลงเครื่องได้
- [ ] เห็นว่าไฟล์จากเว็บมาอยู่ในเครื่องแล้ว
