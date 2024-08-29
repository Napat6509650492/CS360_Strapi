# Strapi คืออะไร?
Strapi เป็น CMS(Content Management System) แบบ Headless หรือที่เรียกว่า Headless CMS ใช้เพื่อจัดการเนื้อหาผ่าน API โดยรองรับทั้ง REST API และ GraphQL ที่รันบน NodeJs ซึ่งช่วยให้ นักพัฒนา(Developer) ประหยัดเวลาในการพัฒนาได้มากขึ้น

# สารบัญ
- [ประเภทของ CMS](#%E0%B8%9B%E0%B8%A3%E0%B8%B0%E0%B9%80%E0%B8%A0%E0%B8%97%E0%B8%82%E0%B8%AD%E0%B8%87-cms)
- [องค์ประกอบของ Strapi](#%E0%B8%AD%E0%B8%87%E0%B8%84%E0%B9%8C%E0%B8%9B%E0%B8%A3%E0%B8%B0%E0%B8%81%E0%B8%AD%E0%B8%9A%E0%B8%82%E0%B8%AD%E0%B8%87-strapi)
- [ขั้นตอนการติดตั้ง](#%E0%B8%82%E0%B8%B1%E0%B9%89%E0%B8%99%E0%B8%95%E0%B8%AD%E0%B8%99%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87)
- [กรณีการใช้งาน](#%E0%B8%81%E0%B8%A3%E0%B8%93%E0%B8%B5%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%83%E0%B8%8A%E0%B9%89%E0%B8%87%E0%B8%B2%E0%B8%99)
- [อธืบาย gitignore](#gitignore)
- [Deployment](#deployment)

## ประเภทของ CMS

  

CMS คือ ซอฟแวร์(Software) ที่ไว้ใช้จัดการเนื้อหาภายในเว็ปไซต์ มี 2 ประเภท

  

1.  **Traditional CMS** คือตัวจัดการเนื้อหาที่รวมทั้ง Fontend และ Backend เข้าไว้ด้วยกัน

  

- ทำให้ขาดความยืดหยุ่นในการพัฒนา เช่น Wordpress

  

2.  **Headless CMS** คือตัวจัดการเนื้อหาที่คล้ายกับ Traditional CMS แต่ตัดส่วนของ Fontend ออก เหลือไว้เพียง Backend และใช้ API ในการจัดการเนื้อหา

  

- ทำให้มีความยืดหยุ่นในการเลือกใช้เครืองมือในการทำ Fontend ได้หลากหลาย เช่น Strapi

  

  

![enter image description here](https://images.contentstack.io/v3/assets/bltc5a09bf374882538/blt5cef60475dbd148a/61fdbd1eb6c9bd47dae9105c/cms-architectures.jpeg)

  

Ref: https://www.contentstack.com/cms-guides/headless-cms-vs-traditional-cms

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

  
  
  
|Username |Email |Password |Role|
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


## กรณีการใช้งาน
- ใช้สร้าง API สำหรับธุรกิจ
- ใช้สร้าง Backend ที่สามารถปรับแต่งได้ง่าย 
- การจัดการสิทธิการเข้าถึง
- Web Application
- Mobile Application


## gitignore 
เป็นไฟล์สำหรับใส่ชื่อของ โฟลเดอร์ หรือ **ไฟล์ที่ไม่ต้อง**การให้ git ทำการติดตามและจัดเก็บไว้ใน **repository** เพราะ ไม่ต้องการเก็บไฟล์ หรือ โฟลเดอร์ `ที่มีข้อมูลส่วนตัว` ,`ข้อมูลชั่วคราว` เช่น `.env` `log` `/build/`

## Deployment

1. ### Setup AWS Instance
	1. Launch **`AWS EC2`** instance 
		- **Instance Type** : t2.medium
		- **Operating System** : Ubuntu 24.04
		- **Security Group Rules**
			-   **Type:**  `SSH`,  **Protocol:**  `TCP`,  **Port Range**  `22`,  **Source:**  `::/0`
			-   **Type:**  `HTTP`,  **Protocol:**  `TCP`,  **Port Range**  `80`,  **Source:**  `0.0.0.0/0, ::/0`
			-   **Type:**  `HTTPS`,  **Protocol:**  `TCP`,  **Port Range**  `443`,  **Source:**  `0.0.0.0/0, ::/0`
			-   **Type:**  `Custom TCP Rule`,  **Protocol:**  `TCP`,  **Port Range**  `1337`,  **Source:**  `0.0.0.0/0`
			
	2. SSH เข้าสู่  EC2 Instance ที่สร้าง
	3. ใช้คำสั่ง **`sudo apt update`** เพื่ออัพเดทระบบ
	4. ใช้คำสั่ง **`sudo apt install curl -y`** เพื่อติดตั้ง curl
	5. ติดตั้ง **NodeJS** 
		```bash
		# ใช้คำสั่ง
		curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
		
		# ตามด้วย
		sudo apt install -y nodejs
		
		# ตรวจสอบว่าติดตั้งสำเร็จ
		node -v && npm -v 
		```
		- ตั้งค่า npm global directory
			```bash 
			cd ~
			mkdir ~/.npm-global
			npm config set prefix '~/.npm-global'
			```
		- เพิ่ม Path Evironment
			```bash 
			sudo nano ~/.profile

			นำ export PATH=~/.npm-global/bin:$PATH ใส่ไว้ด้านล่างสุด

			source ~/.profile
			```
	6. ติดตั้ง **PM2 Runtime** `npm install pm2@latest -g`
	7. ติดตั้ง **Git** `sudo apt install git -y` (หากในเครื่องยังไม่มี)

2. ### Strapi Project
	1. ใช้คำสั่ง `git clone <url>` ดึงโปรเจ็คจาก GitHub Repository
	2. `cd ` เข้าไปยังโฟลเดอร์ที่ได้มา 
	3.  ทำตามด้านล่าง
		```bash
		# ติดตั้ง Libray
		npm install
		
		# Build Project
		NODE_ENV=production npm run build
		```
3. ### Configure Pm2 Runtime
	1. ใช้ **nano** สร้างไฟล์ ecosystem.config.js 
		```bash
		cd ~
		pm2 init
		sudo nano ecosystem.config.js
		```
	 2. **Copy** ข้อความด้านล่าง เข้าไปใส่
		```javascript
		module.exports = {
		   apps: [
		     {
		       name: 'CS360_Strapi', // 
		       cwd: '/home/ubuntu/CS360_Strapi', // Path ของ Project
		       script: 'npm', // npm ,yarn หรือตัวจัดการแพ็คเกตอื่น
		       args: 'start',
		       env: {
		         APP_KEYS: 'your app keys', // หาจากไฟล์ .env ตอน develop บนเครื่อง local 
		         API_TOKEN_SALT: 'your api token salt',
		         ADMIN_JWT_SECRET: 'your admin jwt secret',
		         JWT_SECRET: 'your jwt secret',
		         NODE_ENV: 'production',
		         TRANSFER_TOKEN_SALT:'',
		         DATABASE_CLIENT:'sqlite',
		         DATABASE_FILENAME:'.tmp/data.db',
		         HOST:'0.0.0.0',
		         PORE:'1337'
		       },
		     },
		   ],
		 };
		```
	3. เมื่อทำเสร็จให้ใช้คำสั่งด้านล่างเพื่อ **start** ขึ้นมา
		```bash
		pm2 start ecosystem.config.js
		```
- **ตั้งค่าให้ pm2 รันเมื่อ Strat Instance**
	```bash
	pm2 startup systemd
	# เมื่อรันคำสั่ง จะมีวิธีให้ทำตาม
	
	#[PM2] Init System found: systemd  
	#[PM2] To setup the Startup Script, copy/paste the following command:  
	#sudo  env  PATH=$PATH:/usr/bin /usr/lib/node_modules/pm2/bin/pm2 startup systemd -u your-name --hp /home/your-name

	#หลังจากทำตามวิธีเสร็จ
	pm2 save
	```
Ref: https://docs.strapi.io/dev-docs/deployment/amazon-aws