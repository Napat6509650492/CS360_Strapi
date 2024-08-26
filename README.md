
# Strapi คืออะไร มีไว้ทำไม?

Strapi เป็น CMS(Content Management System) แบบ Headless หรือที่เรียกว่า Headless CMS ใช้เพื่อจัดการเนื้อหาผ่าน API โดยรองรับทั้ง REST API และ GraphQL ที่รันบน NodeJs ซึ่งช่วยให้ นักพัฒนา(Developer) ประหยัดเวลาในการพัฒนาได้มากขึ้น

  

## ประเภทของ CMS

CMS คือ ซอฟแวร์(Software) ที่ไว้ใช้จัดการเนื้อหาภายในเว็ปไซต์ มี 2 ประเภท

1.  **Traditional CMS** คือตัวจัดการเนื้อหาที่รวมทั้ง Fontend และ Backend เข้าไว้ด้วยกัน

- ทำให้ขาดความยืดหยุ่นในการพัฒนา เช่น Wordpress

2.  **Headless CMS** คือตัวจัดการเนื้อหาที่คล้ายกับ Traditional CMS แต่ตัดส่วนของ Fontend ออก เหลือไว้เพียง Backend และใช้ API ในการจัดการเนื้อหา

- ทำให้มีความยืดหยุ่นในการเลือกใช้เครืองมือในการทำ Fontend ได้หลากหลาย เช่น Strapi

  

![enter image description here](https://images.contentstack.io/v3/assets/bltc5a09bf374882538/blt5cef60475dbd148a/61fdbd1eb6c9bd47dae9105c/cms-architectures.jpeg)

Ref: https://www.contentstack.com/cms-guides/headless-cms-vs-traditional-cms

  

## ขั้นตอนการติดตั้ง

**ความต้องการระบบ**

-  **NodeJS** v.18 upto v.20

-  **npm** < v.6

**ขั้นตอน**

1. เปิด Terminal

2. cd เข้าไปในโฟลเดอร์ที่ต้องการเก็บ project Strapi แล้วใช้คำสั่ง

``` bash
npx  create-strapi-app@latest  my-strapi-project  --quickstart
# เมื่อรัน Terminal จะถามเราว่าให้ Login/SignIn หรือ Skip ให้เลือกตามความสะดวก
```
3. เมื่อติดตั้งเสร็จจะเด้งเข้าสู่หน้าสมัคร admin `localhost:1337/admin/register` อัตโนมัติ

4. กรอกข้อมูลสมัครให้เรียบร้อย

5. เข้าใช้งานระบบได้

  

**Start Strapi**

``` bash
# run
npm  run  develop
```

  

## องค์ประกอบของ Strapi

Strapi จะมีองค์ประกอบ หรือ ฟีเจอร์ หลักๆ ที่คอยจัดการ Content อยู่ 2 ส่วน ได้แก่ `Content Manager`และ `Content-Type Builder` ที่ให้มาพร้อมการติดตั้ง Strapi Project

-  **Content-Type Builder**

เป็นตัวสร้างและจัดการ Content Type

> Content Type หมายถึง โครงสร้างของข้อมูล หรือ Schema เช่น User มีฟิลด์ Username , Email , Password , Role ฯลฯ (เป็นแค่ Schema ไม่มีข้อมูล)

ซึ่งแบ่งออกเป็น 2 ประเภท

-  **Collection Type** หมายถึง ประเภทข้อมูลที่เก็บหลายๆตัว เช่น User มีหลายคน , Product มีหลายชิ้น

-  **Single Type** หมายถึง ประเภทข้อมูลที่เก็บเพียงตัวเดียวเดี่ยวๆ เช่น เนื้อหาในหน้า Home , Contact

  

![enter image description here](https://docs.strapi.io/img/assets/content-type-builder/content-types-builder.png)

Ref: https://docs.strapi.io/user-docs/content-type-builder

  

โดยมีประเภทข้อมูลต่าง ดังรูป

![enter image description here](https://docs.strapi.io/img/assets/content-type-builder/fields-selection.png)

Ref : https://docs.strapi.io/user-docs/content-type-builder/configuring-fields-content-type

-  **Content Manager**

เป็นตัวจัดการ Content Type ที่ถูกสร้างขึ้นจาก `Content-Type Builder` นำเอา Content Type ที่กำหนด โครงสร้างข้อมูลมาใส่ข้อมูลเข้าไป เช่น

-  **User** ( Collection Type ) มีได้หลายตัว

<br>



|Username |Email |Password  |Role|
|--|--|--|--|
|Save|example@gg.com|123456|student|
|Jonh|Jonh@g.com|456123|Teacher|


<br>

-  **Contact** ( Single Type ) มีเพียงตัวเดียว
<br>

  

|LineID|Phone |Address|
|--|--|--|--|
|stt|099999999 |example|

  

![Ref](https://docs.strapi.io/img/assets/content-manager/content-manager_list-view.png)

Ref: https://docs.strapi.io/user-docs/content-manager

นอกจากทั้ง 2 ฟีเจอร์นี้ ยังมีฟีเจอร์อื่นๆ เช่น Media Libraly , User-Role & Premission และ Plugin หรือส่วนเสริมต่างๆ อ่านเพิ่มเติมได้ที่ [>>Click<<](https://docs.strapi.io/user-docs/intro)


## กรณีการใช้งาน (Use Case)

สร้าง API สำหรับดึงข้อมูล Product ที่เก็บเป็น Collection ออกมา

1. เข้าไปยังหนน้า Content-Type Builder กด `create new collection type`
2. สร้าง  Schema  ตั้งชื่อว่า Product และสร้างฟิลด์ `name (Text)` , `description (Text)` , `count (number)` ตามลำดับและกด `save`
3. ไปยังหน้า Content Manager และเลือกที่ `Product`
4. กด Create new entry แล้วใส่ข้อมูลลงไปตาม Schema ที่เราสร้างไว้
5. กด Publish 
6. ไปยังหน้า `setting` > `Roles` เลือกแก้ไขในหมวด public เพื่อนให้ใครดึงข้อมูลก็ได้
7. เลือกที่ Product และติ๊ก find , findOne และกด save  
8. เรียกใช้ API , `localhost:1337/api/products`แล้วจะได้ข้อมูลออกมา