# 🛠️ Git & GitHub Workshop

> คู่มือฝึกปฏิบัติ Git, GitHub และ Terminal เบื้องต้น  
> สำหรับผู้เริ่มต้นที่ยังไม่เคยใช้ Git มาก่อน

---

## 📋 สารบัญ

- [สิ่งที่ต้องเตรียมก่อน Workshop](#-สิ่งที่ต้องเตรียมก่อน-workshop)
- [Session 1 — Terminal เบื้องต้น](#-session-1--terminal-เบื้องต้น)
- [Session 2 — Git พื้นฐาน](#-session-2--git-พื้นฐาน)
- [Session 3 — GitHub & Remote Repository](#-session-3--github--remote-repository)
- [Session 4 — Workflow จริงและปัญหาที่พบบ่อย](#-session-4--workflow-จริงและปัญหาที่พบบ่อย)
- [Cheat Sheet สรุปคำสั่ง](#-cheat-sheet-สรุปคำสั่ง)

---

## ✅ สิ่งที่ต้องเตรียมก่อน Workshop

1. **ติดตั้ง Git**
   - macOS: `brew install git` หรือดาวน์โหลดจาก https://git-scm.com
   - Windows: ดาวน์โหลด Git for Windows จาก https://git-scm.com
   - Linux: `sudo apt install git`

2. **ตรวจสอบว่า Git ติดตั้งแล้ว**
   ```bash
   git --version
   ```

3. **สร้างบัญชี GitHub** ที่ https://github.com (ถ้ายังไม่มี)

---

## 💻 Session 1 — Terminal เบื้องต้น

> เวลา: ~45 นาที  
> เป้าหมาย: นำทางใน terminal ได้คล่องก่อนแตะ Git

### คำสั่งพื้นฐานที่ต้องรู้

```bash
# ดูว่าอยู่ที่ไหนใน filesystem
pwd

# แสดงไฟล์และโฟลเดอร์
ls
ls -la        # แสดงทุกไฟล์รวมถึงไฟล์ที่ซ่อนอยู่

# เข้าโฟลเดอร์
cd ชื่อโฟลเดอร์

# ออกมา 1 ระดับ
cd ..

# กลับไปที่ home directory
cd ~

# สร้างโฟลเดอร์ใหม่
mkdir ชื่อโฟลเดอร์

# สร้างไฟล์เปล่า
touch ชื่อไฟล์.txt

# อ่านเนื้อหาในไฟล์
cat ชื่อไฟล์.txt

# ล้างหน้าจอ terminal
clear
```

### 🏋️ แบบฝึกหัดที่ 1 — สร้างโครงสร้างโฟลเดอร์ผ่าน Terminal

ให้สร้างโครงสร้างนี้โดยใช้ terminal เท่านั้น (ห้ามใช้ GUI)

```
myproject/
├── src/
│   └── index.html
└── README.md
```

คำสั่งที่ใช้:

```bash
mkdir myproject
cd myproject
mkdir src
touch src/index.html
touch README.md
ls -la
```

ตรวจสอบผลลัพธ์:

```bash
ls src/
# ควรเห็น: index.html
```

---

## 🌱 Session 2 — Git พื้นฐาน

> เวลา: ~60 นาที  
> เป้าหมาย: เข้าใจ 3 โซนของ Git และใช้ add/commit ได้

### แนวคิด 3 โซนของ Git

```
┌──────────────────┐    git add     ┌──────────────────┐    git commit    ┌──────────────────┐
│  Working         │ ────────────►  │  Staging Area    │ ───────────────► │  Local           │
│  Directory       │                │  (Index)         │                  │  Repository      │
│  (แก้ไขไฟล์ที่นี่)  │                │  (เตรียม commit)  │                  │  (history บนเครื่อง) │
└──────────────────┘                └──────────────────┘                  └──────────────────┘
```

### ขั้นตอนที่ 1 — ตั้งค่าครั้งแรก (ทำแค่ครั้งเดียว)

```bash
git config --global user.name "ชื่อของคุณ"
git config --global user.email "email@example.com"

# ตรวจสอบการตั้งค่า
git config --list
```

### ขั้นตอนที่ 2 — เริ่ม Repository ใหม่

```bash
# เข้าไปในโฟลเดอร์โปรเจกต์
cd myproject

# เริ่มต้น git repository
git init

# ตรวจสอบสถานะ (คำสั่งที่จะใช้บ่อยที่สุด!)
git status
```

### ขั้นตอนที่ 3 — เพิ่มเนื้อหาในไฟล์

เปิดไฟล์ `README.md` และเพิ่มข้อความ:

```bash
echo "# My First Project" >> README.md
echo "โปรเจกต์แรกของฉัน" >> README.md
```

ตรวจดูอีกครั้ง:

```bash
git status
# ควรเห็น README.md อยู่ใน "Untracked files"
```

### ขั้นตอนที่ 4 — Add และ Commit

```bash
# เพิ่มไฟล์เดียวเข้า staging
git add README.md

# ดูสถานะหลัง add
git status
# README.md จะย้ายมาอยู่ใน "Changes to be committed"

# เพิ่มทุกไฟล์พร้อมกัน (ใช้ได้ แต่ต้องระวัง)
git add .

# บันทึก commit
git commit -m "feat: add initial project files"
```

### ขั้นตอนที่ 5 — ดูประวัติ

```bash
git log              # แสดงประวัติแบบละเอียด
git log --oneline    # แสดงแบบสั้น (แนะนำ)
```

### 📝 รูปแบบ Commit Message ที่ดี

```
feat: เพิ่มฟีเจอร์ใหม่
fix: แก้ไข bug
docs: แก้ไขเอกสาร
style: จัด format โค้ด
refactor: ปรับปรุงโค้ดโดยไม่เพิ่มฟีเจอร์หรือแก้ bug
```

### 🏋️ แบบฝึกหัดที่ 2

1. เพิ่มเนื้อหาใน `src/index.html`
2. ทำ `git add` และ `git commit` ด้วย message ที่เหมาะสม
3. แก้ไข `README.md` อีกครั้ง แล้ว commit ใหม่
4. ดูประวัติด้วย `git log --oneline`

---

## 🐙 Session 3 — GitHub & Remote Repository

> เวลา: ~60 นาที  
> เป้าหมาย: สร้าง repo บน GitHub และ push/pull ได้

### แนวคิด Local vs Remote

```
┌─────────────────────┐                    ┌─────────────────────┐
│   เครื่องของเรา       │                    │   GitHub (Cloud)    │
│                     │   git push ──────► │                     │
│  Local Repository   │                    │  Remote Repository  │
│                     │  ◄────── git pull  │                     │
└─────────────────────┘                    └─────────────────────┘
                              git clone (ครั้งแรกเท่านั้น)
```

### ขั้นตอนที่ 1 — สร้าง Repository บน GitHub

1. ไปที่ https://github.com
2. คลิก **"New"** หรือ **"+"** มุมขวาบน
3. ตั้งชื่อ Repository (เช่น `myproject`)
4. เลือก **Public** หรือ **Private**
5. **ไม่ต้องติ๊ก** "Add a README file" (เพราะเรามีอยู่แล้ว)
6. คลิก **"Create repository"**

### ขั้นตอนที่ 2 — เชื่อมต่อ Local กับ Remote

หลังสร้าง repo GitHub จะแสดง URL ให้ ใช้คำสั่งนี้:

```bash
# เพิ่ม remote origin (เปลี่ยน URL ให้ตรงกับของคุณ)
git remote add origin https://github.com/username/myproject.git

# ตรวจสอบว่าเชื่อมต่อแล้ว
git remote -v
```

### ขั้นตอนที่ 3 — Push ขึ้น GitHub ครั้งแรก

```bash
# Push พร้อมตั้ง upstream branch (-u ทำแค่ครั้งแรก)
git push -u origin main

# ครั้งต่อไปใช้แค่
git push
```

### ขั้นตอนที่ 4 — Clone Repository (กรณีเริ่มจาก repo ที่มีอยู่แล้ว)

```bash
# Clone repo ลงมาในเครื่อง (ใช้แค่ครั้งแรก)
git clone https://github.com/username/myproject.git

# เข้าไปในโฟลเดอร์ที่ clone มา
cd myproject
```

> **สำคัญ:** `git clone` ใช้แค่ครั้งแรกเท่านั้น  
> หลังจากนั้นถ้าอยากดึงการเปลี่ยนแปลงใหม่ ใช้ `git pull`

### ขั้นตอนที่ 5 — Pull (ดึงการเปลี่ยนแปลงจาก Remote)

```bash
# ดึงการเปลี่ยนแปลงล่าสุดจาก GitHub
git pull

# หรือระบุ branch ชัดเจน
git pull origin main
```

### 🏋️ แบบฝึกหัดที่ 3 — จับคู่ทำงานร่วมกัน

จับคู่กัน 2 คน:

1. **คนที่ 1:** สร้าง repo บน GitHub และ push ไฟล์ขึ้นไป
2. **คนที่ 2:** Clone repo ของคนที่ 1 ลงมา แก้ไขไฟล์ แล้ว push ขึ้นไป
3. **คนที่ 1:** ทำ `git pull` เพื่อดึงการเปลี่ยนแปลงของคนที่ 2 มา
4. สลับบทบาทกัน

---

## 🔄 Session 4 — Workflow จริงและปัญหาที่พบบ่อย

> เวลา: ~45 นาที  
> เป้าหมาย: ใช้งานได้จริงในชีวิตประจำวัน

### Daily Workflow ที่ควรทำเป็นนิสัย

```bash
# 1. ดึงการเปลี่ยนแปลงล่าสุดก่อนเสมอ
git pull

# 2. แก้ไขโค้ด / เพิ่มไฟล์ ...

# 3. ตรวจสอบว่าอะไรเปลี่ยนไปบ้าง
git status

# 4. ดูความแตกต่างของไฟล์
git diff

# 5. เพิ่มไฟล์เข้า staging
git add .

# 6. commit พร้อม message ที่ชัดเจน
git commit -m "fix: แก้ bug การแสดงผลหน้าแรก"

# 7. push ขึ้น remote
git push
```

### ⚠️ ปัญหาที่พบบ่อยและวิธีแก้

#### ปัญหา 1: Push ไม่ได้เพราะ Remote เปลี่ยนไปแล้ว

```
error: failed to push some refs to 'origin'
hint: Updates were rejected because the remote contains work...
```

**วิธีแก้:**

```bash
git pull        # ดึงมาก่อน
# ถ้ามี conflict ให้แก้ไขไฟล์ที่ขัดแย้ง จากนั้น
git add .
git commit -m "merge: resolve conflict"
git push
```

#### ปัญหา 2: Commit ผิด อยากแก้ Message

```bash
# แก้ commit message ล่าสุด (ก่อน push เท่านั้น)
git commit --amend -m "ข้อความใหม่"
```

#### ปัญหา 3: Add ไฟล์ผิด อยากเอาออกจาก Staging

```bash
# เอาไฟล์ออกจาก staging (ไฟล์ไม่ถูกลบ)
git restore --staged ชื่อไฟล์.txt

# เอาทุกไฟล์ออกจาก staging
git restore --staged .
```

#### ปัญหา 4: อยากดูว่า Remote URL คืออะไร

```bash
git remote -v
```

#### ปัญหา 5: ลืมว่า push ขึ้นไปหรือยัง

```bash
git status
# ถ้าขึ้น "Your branch is ahead of 'origin/main' by X commits"
# หมายความว่ายังไม่ได้ push
```

### 📁 .gitignore — ไฟล์ที่ไม่ควร Push ขึ้น GitHub

สร้างไฟล์ `.gitignore` ในโฟลเดอร์โปรเจกต์:

```bash
touch .gitignore
```

ตัวอย่างเนื้อหาใน `.gitignore`:

```
# ไฟล์ระบบ
.DS_Store
Thumbs.db

# ไฟล์ environment (มักมี password หรือ secret key)
.env
.env.local

# โฟลเดอร์ dependencies
node_modules/
__pycache__/

# ไฟล์ build
dist/
build/
*.log
```

---

## 📌 Cheat Sheet สรุปคำสั่ง

### Terminal

| คำสั่ง | ความหมาย |
|--------|-----------|
| `pwd` | แสดง path ปัจจุบัน |
| `ls -la` | แสดงไฟล์ทั้งหมดรวมถึงไฟล์ซ่อน |
| `cd โฟลเดอร์` | เข้าโฟลเดอร์ |
| `cd ..` | ออกมา 1 ระดับ |
| `mkdir ชื่อ` | สร้างโฟลเดอร์ |
| `touch ชื่อไฟล์` | สร้างไฟล์เปล่า |
| `cat ไฟล์` | อ่านเนื้อหาไฟล์ |
| `clear` | ล้างหน้าจอ |

### Git — ตั้งค่า

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git config --global user.name "ชื่อ"` | ตั้งชื่อผู้ใช้ |
| `git config --global user.email "email"` | ตั้งอีเมล |
| `git config --list` | ดูการตั้งค่าทั้งหมด |

### Git — การทำงานประจำวัน

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git init` | เริ่ม repo ใหม่ |
| `git status` | ดูสถานะไฟล์ |
| `git diff` | ดูสิ่งที่เปลี่ยนแปลง |
| `git add ไฟล์` | เพิ่มไฟล์เข้า staging |
| `git add .` | เพิ่มทุกไฟล์เข้า staging |
| `git commit -m "message"` | บันทึก commit |
| `git log --oneline` | ดูประวัติ commit แบบย่อ |

### Git — Remote (GitHub)

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git remote add origin URL` | เชื่อม local กับ GitHub |
| `git remote -v` | ดู remote URL |
| `git push -u origin main` | push ครั้งแรก |
| `git push` | push ครั้งต่อไป |
| `git pull` | ดึงการเปลี่ยนแปลงจาก remote |
| `git clone URL` | คัดลอก repo จาก GitHub (ครั้งแรก) |

### Git — แก้ไขและย้อนกลับ

| คำสั่ง | ความหมาย |
|--------|-----------|
| `git restore --staged ไฟล์` | เอาไฟล์ออกจาก staging |
| `git restore ไฟล์` | ยกเลิกการแก้ไขไฟล์ (ระวัง! ไม่สามารถกู้คืนได้) |
| `git commit --amend -m "ใหม่"` | แก้ message ของ commit ล่าสุด |

---

## 🎯 สรุป Flow หลักที่ต้องจำ

```
git pull  →  แก้ไขโค้ด  →  git add .  →  git commit -m "..."  →  git push
```

---

*Workshop นี้จัดทำสำหรับผู้เริ่มต้น — ใช้เวลารวมประมาณ 3-4 ชั่วโมง*
