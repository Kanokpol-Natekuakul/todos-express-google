# Todo Express Starter

แอปพลิเคชัน Todo List ที่สมบูรณ์ที่สร้างด้วย Express.js พร้อมระบบยืนยันตัวตนแบบ Google OAuth การจัดการเซสชัน และอินเทอร์เฟซที่สวยงามในสไตล์ TodoMVC

## เครดิต

โปรเจกต์นี้สร้างจากเทมเพลตเริ่มต้นที่ยอดเยียม:
```bash
git clone https://github.com/passport/todos-express-starter.git
```

ผู้สร้างต้นฉบับ: [Jared Hanson](https://www.jaredhanson.me/)  
เป็นส่วนหนึ่งของโปรเจกต์ [TodoMVC](https://todomvc.com)  
ระบบยืนยันตัวตนขับเคลื่อนโดย [Passport.js](https://www.passportjs.org)

## คุณสมบัติ

- **ระบบยืนยันตัวตน Google OAuth**: เข้าสู่ระบบด้วยบัญชี Google อย่างปลอดภัย
- **การจัดการเซสชัน**: เซสชันผู้ใช้ที่คงอยู่ด้วยการจัดเก็บ SQLite
- **การจัดการ Todo**: สร้าง อ่าน อัปเดต และลบ todo
- **การกรอง**: ดู todo ทั้งหมด ที่ใช้งานอยู่ หรือเสร็จแล้ว
- **การดำเนินการแบบกลุ่ม**: สลับสถานะ todo ทั้งหมด หรือล้าง todo ที่เสร็จแล้ว
- **การออกแบบที่ตอบสนอง**: อินเทอร์เฟซที่สะอาดและเป็นมิตรกับมือถือ
- **การจัดเก็บข้อมูลถาวร**: ฐานข้อมูล SQLite สำหรับผู้ใช้และ todo

## เทคโนโลยีที่ใช้

- **Backend**: Node.js, Express.js
- **ระบบยืนยันตัวตน**: Passport.js ด้วย Google OAuth 2.0 Strategy
- **ฐานข้อมูล**: SQLite3 พร้อมสคีมาที่กำหนดเอง
- **การจัดเก็บเซสชัน**: การจัดเก็บเซสชันแบบ SQLite
- **View Engine**: เทมเพลต EJS
- **การจัดแต่งหน้าตา**: CSS ที่กำหนดเองพร้อมสไตล์ TodoMVC
- **การรักษาความปลอดภัย**: OAuth 2.0 และการจัดการเซสชันที่เข้ารหัส

## ข้อกำหนดเบื้องต้น

- Node.js (เวอร์ชัน 12 ขึ้นไป)
- npm หรือ yarn package manager
- บัญชี Google Cloud Platform (สำหรับตั้งค่า OAuth)

## การติดตั้ง

1. โคลน repository:
```bash
git clone https://github.com/passport/todos-express-starter.git
cd todos-express-starter
```

2. ติดตั้ง dependencies:
```bash
npm install
```

3. ตั้งค่า Google OAuth:
   - ไปที่ [Google Cloud Console](https://console.cloud.google.com/)
   - สร้างโปรเจกต์ใหม่หรือเลือกโปรเจกต์ที่มีอยู่
   - เปิดใช้งาน Google+ API
   - สร้าง OAuth 2.0 credentials
   - เพิ่ม `http://localhost:3000/oauth2/redirect/google` ใน Authorized redirect URIs

4. สร้างไฟล์ `.env` และเพิ่มข้อมูล Google OAuth:
```bash
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
PORT=3000
```

5. เริ่มต้นแอปพลิเคชัน:
```bash
npm start
```

6. เปิดเบราว์เซอร์และไปที่:
```
http://localhost:3000
```

## บัญชีผู้ใช้เริ่มต้น

สำหรับการทดสอบ มีการสร้างบัญชีผู้ใช้เริ่มต้น:
- **ชื่อผู้ใช้**: `alice`
- **รหัสผ่าน**: `letmein`

*หมายเหตุ: ในเวอร์ชันปัจจุบันนี้ ระบบใช้ Google OAuth เป็นหลัก และไม่มีระบบ local authentication*

## โครงสร้างโปรเจกต์

```
├── .gitignore            # ไฟล์ที่ไม่ต้องการใน version control
├── LICENSE               # ลิขสิทธิ์สาธารณะ (Unlicense)
├── app.js                # แอปพลิเคชัน Express หลัก
├── bin/www               # สคริปต์เริ่มต้นเซิร์ฟเวอร์
├── db.js                 # การตั้งค่าและเริ่มต้นฐานข้อมูล
├── package.json          # dependencies และสคริปต์ของโปรเจกต์
├── routes/
│   ├── auth.js          # เส้นทางระบบยืนยันตัวตน Google OAuth
│   └── index.js         # เส้นทางการจัดการ Todo
├── views/
│   ├── error.ejs        # เทมเพลตหน้าแสดงข้อผิดพลาด
│   ├── home.ejs         # หน้าแรกสำหรับผู้ใช้ที่ยังไม่ได้ยืนยันตัวตน
│   ├── index.ejs        # อินเทอร์เฟซแอปพลิเคชัน Todo หลัก
│   ├── login.ejs        # หน้าเข้าสู่ระบบด้วย Google
│   ├── signup.ejs       # หน้าสมัครสมาชิก
│   └── login/email/     # เทมเพลตยืนยันอีเมล
├── public/
│   └── css/
│       ├── app.css      # สไตล์การนำทางและอินเทอร์เฟซผู้ใช้
│       ├── base.css     # สไตล์ TodoMVC พื้นฐาน
│       ├── home.css     # สไตล์หน้าแรก
│       ├── index.css    # สไตล์แอปพลิเคชันหลัก
│       └── login.css    # สไตล์หน้าเข้าสู่ระบบ
└── var/db/              # ไฟล์ฐานข้อมูล (สร้างอัตโนมัติ)
```

## สคีมาฐานข้อมูล

แอปพลิเคชันใช้ SQLite พร้อมตารางหลัก 3 ตาราง:

### ตารางผู้ใช้ (Users)
```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    username TEXT UNIQUE,
    hashed_password BLOB,
    salt BLOB,
    name TEXT,
    email TEXT UNIQUE,
    email_verified INTEGER
);
```

### ตาราง Todos
```sql
CREATE TABLE todos (
    id INTEGER PRIMARY KEY,
    owner_id INTEGER NOT NULL,
    title TEXT NOT NULL,
    completed INTEGER
);
```

### ตารางข้อมูลยืนยันตัวตนแบบ Federated
```sql
CREATE TABLE federated_credentials (
    id INTEGER PRIMARY KEY,
    user_id INTEGER NOT NULL,
    provider TEXT NOT NULL,
    subject TEXT NOT NULL,
    UNIQUE (provider, subject)
);
```

## API Endpoints

### เส้นทางระบบยืนยันตัวตน
- `GET /login` - แสดงหน้าเข้าสู่ระบบ
- `GET /login/federated/google` - เริ่มต้นการเข้าสู่ระบบด้วย Google
- `GET /oauth2/redirect/google` - Callback URL สำหรับ Google OAuth
- `POST /logout` - ออกจากระบบผู้ใช้

### เส้นทางการจัดการ Todo
- `GET /` - แสดง todo ทั้งหมด (ต้องยืนยันตัวตน)
- `GET /active` - แสดง todo ที่ใช้งานอยู่ (ยังไม่เสร็จ)
- `GET /completed` - แสดง todo ที่เสร็จแล้ว
- `POST /` - สร้าง todo ใหม่
- `POST /:id` - อัปเดต todo ที่มีอยู่
- `POST /:id/delete` - ลบ todo ที่ระบุ
- `POST /toggle-all` - สลับสถานะการเสร็จสิ้นของ todo ทั้งหมด
- `POST /clear-completed` - ลบ todo ที่เสร็จแล้วทั้งหมด

## การตั้งค่า

### ตัวแปรสภาพแวดล้อม
สร้างไฟล์ `.env` สำหรับการตั้งค่า:
```bash
# Google OAuth Configuration
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here

# Server Configuration
PORT=3000
NODE_ENV=development
```

### การตั้งค่าเซสชัน
เซสชันจัดเก็บใน SQLite (`var/db/sessions.db`) ด้วยการตั้งค่าดังนี้:
- คีย์ลับสำหรับการเข้ารหัส
- ไม่บันทึกอัตโนมัติสำหรับเซสชันที่ไม่ได้เริ่มต้น
- การจัดเก็บถาวรข้ามการรีสตาร์ทเซิร์ฟเวอร์

### การตั้งค่า Google OAuth

1. **สร้างโปรเจกต์ใน Google Cloud Console**:
   - ไปที่ https://console.cloud.google.com/
   - สร้างโปรเจกต์ใหม่หรือเลือกโปรเจกต์ที่มีอยู่

2. **เปิดใช้งาน APIs**:
   - ไปที่ "APIs & Services" > "Library"
   - ค้นหาและเปิดใช้งาน "Google+ API"

3. **สร้าง OAuth 2.0 Credentials**:
   - ไปที่ "APIs & Services" > "Credentials"
   - คลิก "Create Credentials" > "OAuth 2.0 Client IDs"
   - เลือก "Web application"
   - เพิ่ม `http://localhost:3000/oauth2/redirect/google` ใน "Authorized redirect URIs"

4. **คัดลอก Client ID และ Client Secret** ไปใส่ในไฟล์ `.env`

## คุณสมบัติด้านความปลอดภัย

- **Google OAuth 2.0**: ระบบยืนยันตัวตนที่ปลอดภัยผ่าน Google
- **ความปลอดภัยเซสชัน**: การจัดเก็บเซสชันที่เข้ารหัส
- **การป้องกัน SQL Injection**: คิวรีแบบพารามิเตอร์
- **การป้องกัน CSRF**: การส่งฟอร์มพร้อมการตรวจสอบที่เหมาะสม
- **การตรวจสอบข้อมูลนำเข้า**: การตรวจสอบฝั่งเซิร์ฟเวอร์สำหรับข้อมูลผู้ใช้ทั้งหมด

## การพัฒนา

### การรันในโหมดพัฒนา
```bash
npm start
```
เซิร์ฟเวอร์จะเริ่มต้นที่พอร์ต 3000 พร้อมการบันทึกล็อกสำหรับการพัฒนา

### การรีเซ็ตฐานข้อมูล
หากต้องการรีเซ็ตฐานข้อมูล เพียงลบไฟล์ฐานข้อมูล:
```bash
rm -rf var/
```
ฐานข้อมูลจะถูกสร้างใหม่ในการเริ่มต้นครั้งถัดไป

### ไฟล์ที่ถูกละเว้นใน Git (.gitignore)
```
.env                    # ไฟล์ตัวแปรสภาพแวดล้อม (ข้อมูลลับ)
var/                    # ไฟล์ฐานข้อมูลและเซสชัน
node_modules/           # Dependencies ของ Node.js
npm-debug.log*          # ไฟล์ล็อก npm
.DS_Store              # ไฟล์ระบบ macOS
```

## การแก้ไขปัญหา

### ปัญหาที่พบบ่อย

1. **Google OAuth ไม่ทำงาน**:
   - ตรวจสอบ `GOOGLE_CLIENT_ID` และ `GOOGLE_CLIENT_SECRET` ในไฟล์ `.env`
   - ยืนยันว่า Redirect URI ตั้งค่าถูกต้องใน Google Cloud Console

2. **ฐานข้อมูลไม่สามารถเขียนได้**:
   - ตรวจสอบสิทธิ์การเขียนในโฟลเดอร์ `var/db/`
   - ลองลบโฟลเดอร์ `var/` และเริ่มต้นใหม่

3. **เซสชันหายหลังรีสตาร์ท**:
   - ตรวจสอบว่าโฟลเดอร์ `var/db/` ยังคงอยู่หลังรีสตาร์ท
   - ตรวจสอบการตั้งค่า SQLiteStore ในไฟล์ `app.js`

## Dependencies หลัก

- **express**: เฟรมเวิร์ค web สำหรับ Node.js
- **passport**: middleware สำหรับระบบยืนยันตัวตน
- **passport-google-oidc**: Passport strategy สำหรับ Google OAuth
- **sqlite3**: ฐานข้อมูล SQLite สำหรับ Node.js
- **express-session**: การจัดการเซสชันสำหรับ Express
- **connect-sqlite3**: การจัดเก็บเซสชันใน SQLite
- **ejs**: Template engine สำหรับ Node.js

## ลิขสิทธิ์

ซอฟต์แวร์นี้เผยแพร่สู่สาธารณะภายใต้ [Unlicense](http://unlicense.org/) คุณมีอิสระในการใช้ แก้ไข และแจกจ่ายโค้ดนี้เพื่อวัตถุประสงค์ใดๆ ทั้งเชิงพาณิชย์และไม่เชิงพาณิชย์

## การมีส่วนร่วม

นี่คือเทมเพลตเริ่มต้นที่ออกแบบมาสำหรับการเรียนรู้และการทดลอง สามารถ fork และแก้ไขตามความต้องการของคุณได้

## การสนับสนุน

สำหรับคำถามเกี่ยวกับกลยุทธ์การยืนยันตัวตน Passport.js เข้าชม [เอกสาร Passport.js](https://www.passportjs.org/docs/)

สำหรับการตั้งค่า Google OAuth ดูได้ที่ [Google Identity Platform](https://developers.google.com/identity)

สำหรับคำถามที่เกี่ยวข้องกับ TodoMVC ตรวจสอบได้ที่ [เว็บไซต์ TodoMVC](https://todomvc.com)

---

**ขอให้การเขียนโค้ดเป็นไปด้วยดี! 🚀**
