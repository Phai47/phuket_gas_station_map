# Amenity Finder (คู่มือภาษาไทย)

เว็บแอปสำหรับค้นหาสถานที่อำนวยความสะดวก (amenities) รอบตำแหน่งที่ระบุ โดยดึงข้อมูลจาก OpenStreetMap ผ่าน Overpass API

## สรุปฟีเจอร์
- เลย์เอาท์แบ่งหน้าจอ (แผงฟอร์มซ้าย / แผนที่ขวา)
- กรองประเภทสถานที่และรัศมี (กม.)
- ปักหมุดและแสดงป๊อปอัพรายละเอียด
- ตรวจจับตำแหน่งผู้ใช้ (Geolocation)
- ไอคอนกำหนดเองสำหรับแต่ละประเภท

## รายการ amenity ที่รองรับ (ตัวอย่าง)
- hospital (โรงพยาบาล)
- parking (ที่จอดรถ)
- telephone (โทรศัพท์สาธารณะ)
- cafe (คาเฟ่)
- restaurant (ร้านอาหาร)
- supermarket (ซูเปอร์มาร์เก็ต)
- pharmacy (ร้านขายยา)
- bank (ธนาคาร)

## การติดตั้งและใช้งาน (สั้น)
1. วางไฟล์ทั้งหมดไว้ในโฟลเดอร์โปรเจค (เช่น d:\AJ_Kai\Project\mobile-gis-main)
2. สร้างไฟล์ favicon.ico และวางไว้ที่ root ของโปรเจค (หรือปรับ href ใน index.html ให้ชี้ตำแหน่งที่ถูกต้อง)
3. เปิดไฟล์ index.html ในเบราว์เซอร์ (หรือเซิร์ฟเวอร์ท้องถิ่น) เพื่อใช้งาน

## วิธีสร้าง Favicon (แนะนำ)
1. ขนาดแนะนำ: 16x16, 32x32 หรือสร้าง .ico ที่มีหลายขนาด
2. วิธีง่าย (เว็บ): ใช้เว็บ generator เช่น
   - https://favicon.io
   - https://realfavicongenerator.net
   ขั้นตอน: อัพโหลดภาพ (PNG/SVG) → ดาวน์โหลด favicon.ico → วางไฟล์ในโฟลเดอร์โปรเจค
3. วิธีด้วยโปรแกรมภาพ: สร้างภาพ 64x64/32x32 แล้วบันทึกเป็น PNG จากนั้นแปลงเป็น .ico ด้วยเครื่องมือออนไลน์
4. ใน index.html ให้เพิ่มบรรทัดใน <head>:
   <link rel="icon" type="image/x-icon" href="favicon.ico">

## Attribution / แหล่งที่มา
- ข้อมูล (Dataset): OpenStreetMap — ใช้ Overpass API เพื่อดึง POI
- แผนที่ (Tiles): OpenStreetMap tiles (https://www.openstreetmap.org)
- ไลบรารีแผนที่: Leaflet.js (https://leafletjs.com)
- สไตล์: W3.CSS (https://www.w3schools.com/w3css/)
- ไอคอน: Iconmonstr (https://iconmonstr.com)
  - License: Iconmonstr License (https://iconmonstr.com/license/)
  - ดาวน์โหลดและใช้งานฟรี ไม่ต้องให้เครดิต แต่ห้ามขายต่อหรือแจกจ่ายไฟล์ไอคอนโดยตรง
  - ไฟล์ไอคอนเก็บไว้ใน image/mappings/

## วิธีแพ็กโปรเจคเป็น ZIP เพื่อส่งงาน (Windows - PowerShell)
1. เปิด PowerShell และเข้าไปที่โฟลเดอร์ที่อยู่เหนือโฟลเดอร์โปรเจค
2. รันคำสั่ง:
   Compress-Archive -Path .\mobile-gis-main\* -DestinationPath .\mobile-gis-main.zip
3. ไฟล์ mobile-gis-main.zip จะถูกสร้างในโฟลเดอร์ปัจจุบัน — อัพโหลดไฟล์นี้ตามคำสั่งส่งงาน

(ถ้าใช้ Windows Explorer: คลิกขวาที่โฟลเดอร์ mobile-gis-main → Send to → Compressed (zipped) folder)

## หมายเหตุปฏิบัติการ
- หากใช้ไอคอนจากแหล่งอื่น ให้แนบไฟล์ใบอนุญาต (LICENSE) หรือบันทึกแหล่งที่มาไว้ใน README
- หากต้องการปรับธีม/ขนาดไอคอน ให้แก้พารามิเตอร์ iconSize/iconAnchor ในสคริปต์ของ index.html

## การใช้ไอคอนจาก Iconmonstr
1. เข้าไปที่ https://iconmonstr.com
2. ค้นหาไอคอนที่ต้องการ (เช่น hospital, cafe, bank)
3. เลือกดาวน์โหลดเป็น PNG
   - แนะนำขนาด: 42x42 pixels (ตามที่กำหนดใน index.html)
   - สีตามต้องการ (เช่น สีดำ หรือสีที่ต้องการ)
4. บันทึกไฟล์และตั้งชื่อตาม amenity (เช่น hospital.png)
5. วางไฟล์ไว้ในโฟลเดอร์ image/mappings/

## ตัวอย่างการเพิ่มไอคอนในโปรเจค (สั้น)
1. วางไฟล์ `cafe.png` ไปที่ `image/mappings/cafe.png`  
2. ใน `index.html` มี switch-case ที่จะเลือกไฟล์ไอคอนตามค่า `amenity` (เช่น `case 'cafe': pathIcon = 'image/mappings/cafe.png';`)  
3. รีเฟรชหน้าเว็บ — ไอคอนจะแสดงตามไฟล์ที่วางไว้

## เพิ่มเติมเกี่ยวกับ Attribution
- หากใช้ไอคอนที่มีข้อจำกัด ให้ระบุแหล่งที่มาใน README เช่น:
  "Icons: Streamline (licensed, [ประเภทไลเซนส์], ลิงก์ใบอนุญาต)"  
- ตัวอย่างบรรทัดที่ควรใส่ใน README/footer:
  - Data: OpenStreetMap (Overpass API)  
  - Map: Leaflet.js  
  - Tiles: OpenStreetMap  
  - CSS: W3.CSS  
  - Icons: Streamline (licensed) — ระบุลิงก์ไลเซนส์หรือไฟล์ใบอนุญาตที่มาพร้อมการซื้อ

