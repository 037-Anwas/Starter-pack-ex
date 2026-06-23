# Workshop: GitHub & Git เบื้องต้น

---

## ส่วนที่ 1 — สร้าง Repository บน GitHub

1. ไปที่ https://github.com แล้ว login
2. กดปุ่ม **"+"** มุมขวาบน → เลือก **"New repository"**
3. ตั้งชื่อ repository ว่า `my-first-repo`
4. เลือก **Public**
5. ติ๊ก **"Add a README file"**
6. กด **"Create repository"**

---

## ส่วนที่ 2 — แก้ไข README ด้วย Markdown บน GitHub

1. คลิกที่ไฟล์ **README.md**
2. กดไอคอน ✏️ (Edit) มุมขวาบนของไฟล์
3. ลบข้อความเดิมทิ้งทั้งหมด แล้วพิมพ์เนื้อหาด้านล่างนี้ลงไป

```markdown
# ชื่อโปรเจกต์ของฉัน

## เกี่ยวกับโปรเจกต์นี้
โปรเจกต์แรกของฉันบน GitHub สร้างขึ้นเพื่อฝึกใช้ Git และ Markdown

## สิ่งที่ฉันกำลังเรียนอยู่
- Git และ GitHub
- Terminal เบื้องต้น
- Markdown

## ตารางแผนการเรียน

| สัปดาห์ | หัวข้อ        | สถานะ  |
|---------|--------------|--------|
| 1       | Git & GitHub | ✅ เรียนแล้ว |
| 2       | HTML & CSS   | 🔄 กำลังเรียน |
| 3       | JavaScript   | ⏳ ยังไม่ถึง |

## คำพูดที่ชอบ

> "Talk is cheap. Show me the code."
> — Linus Torvalds ผู้สร้าง Git

## ติดต่อฉัน
- GitHub: [ใส่ชื่อ GitHub ของคุณ](https://github.com/ใส่ชื่อ-GitHub)
```

4. กด **"Preview"** เพื่อดูผลลัพธ์ก่อน commit
5. เลื่อนลงมาด้านล่าง ช่อง **"Commit changes"** พิมพ์ข้อความว่า `docs: add README content`
6. กด **"Commit changes"**

---

## ส่วนที่ 3 — ฝึก Markdown เพิ่มเติม

สร้างไฟล์ใหม่บน GitHub โดย

1. กลับไปหน้าหลักของ repo
2. กด **"Add file"** → **"Create new file"**
3. ตั้งชื่อไฟล์ว่า `notes.md`
4. พิมพ์เนื้อหาด้านล่างลงไป แล้วลองแก้ให้เป็นของตัวเองด้วย

```markdown
# บันทึกการเรียน Git

## คำสั่งที่จำได้แล้ว

### ดูสถานะ
`git status`

### บันทึกการเปลี่ยนแปลง
```bash
git add .
git commit -m "ข้อความ"
git push
```

## สิ่งที่ยังสับสน
- [ ] ยังไม่เข้าใจเรื่อง branch
- [ ] สับสนระหว่าง pull กับ clone
- [x] เข้าใจ add และ commit แล้ว

## รูปตัวอย่าง (ลองใส่รูปจาก URL)
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)
```

5. commit ไฟล์นี้ด้วย message ว่า `docs: add learning notes`

---

## ส่วนที่ 4 — ทำ Git บนเครื่อง

### 4.1 ตั้งค่าครั้งแรก

เปิด terminal ขึ้นมา แล้วพิมพ์ทีละบรรทัด

```bash
git config --global user.name "ชื่อของคุณ"
git config --global user.email "อีเมลที่ใช้สมัคร GitHub"
```

ตรวจสอบว่าตั้งค่าถูกต้อง

```bash
git config --list
```

---

### 4.2 สร้างโฟลเดอร์และไฟล์

```bash
mkdir my-local-project
cd my-local-project
mkdir src
touch README.md
touch src/index.html
```

---

### 4.3 เริ่มต้น Git

```bash
git init
git status
```

> สังเกตว่า `git status` จะแสดงไฟล์สีแดง หมายความว่า Git เห็นไฟล์แต่ยังไม่ได้ track

---

### 4.4 บันทึกครั้งแรก

```bash
git add .
git status
```

> ตอนนี้ไฟล์จะเปลี่ยนเป็นสีเขียว หมายความว่าพร้อม commit แล้ว

```bash
git commit -m "feat: initial project setup"
git log --oneline
```

---

### 4.5 เชื่อมกับ GitHub แล้ว Push

1. ไปที่ GitHub สร้าง repo ใหม่อีกอัน ชื่อ `my-local-project`
2. **อย่าติ๊ก** "Add a README file" (เพราะเรามีอยู่แล้ว)
3. กด "Create repository"
4. GitHub จะแสดง URL ให้ คัดลอกมา แล้วพิมพ์คำสั่งด้านล่าง

```bash
git remote add origin https://github.com/ชื่อของคุณ/my-local-project.git
git push -u origin main
```

5. ไปเปิด GitHub ดูว่าไฟล์ขึ้นไปแล้ว ✅

---

### 4.6 แก้ไขและ Push อีกครั้ง

เปิดไฟล์ `README.md` แก้ไขอะไรก็ได้ จากนั้น

```bash
git status
git add .
git commit -m "docs: update README"
git push
```

ไปดูบน GitHub ว่าไฟล์อัปเดตแล้ว

---

## สรุป Flow ที่ต้องจำ

```
git add .  →  git commit -m "..."  →  git push
```

---

## ✅ Checklist

- [ ] สร้าง repo บน GitHub ได้
- [ ] เขียน README ด้วย Markdown บน GitHub ได้
- [ ] ใช้ heading, list, table, blockquote, code block ได้
- [ ] รัน `git config` ตั้งชื่อและอีเมลได้
- [ ] รัน `git init` สร้าง repo ในเครื่องได้
- [ ] รัน `git add`, `git commit`, `git push` ได้
- [ ] เห็นไฟล์ขึ้นบน GitHub ได้
