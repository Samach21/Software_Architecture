<div align="center" id="top"> 
  <img src="./.github/app.gif" alt="Software_Architecture" />

  &#xa0;

  <!-- <a href="https://software_architecture.netlify.app">Demo</a> -->
</div>

<h1 align="center">Architectural Patterns/Styles</h1>

<!-- <p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8">

  <img alt="Github language count" src="https://img.shields.io/github/languages/count/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8">

  <img alt="License" src="https://img.shields.io/github/license/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8">

  <!-- <img alt="Github issues" src="https://img.shields.io/github/issues/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8" /> -->

  <!-- <img alt="Github forks" src="https://img.shields.io/github/forks/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8" /> -->

  <!-- <img alt="Github stars" src="https://img.shields.io/github/stars/{{YOUR_GITHUB_USERNAME}}/software_architecture?color=56BEB8" /> -->
<!-- </p>  -->

<!-- Status -->

<!-- <h4 align="center"> 
	🚧  Software_Architecture 🚀 Under construction...  🚧
</h4> 

<hr> -->

<!-- <p align="center">
  <a href="#dart-about">About</a> &#xa0; | &#xa0; 
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#rocket-technologies">Technologies</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requirements">Requirements</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-starting">Starting</a> &#xa0; | &#xa0;
  <a href="#memo-license">License</a> &#xa0; | &#xa0;
  <a href="https://github.com/{{YOUR_GITHUB_USERNAME}}" target="_blank">Author</a>
</p> -->

<br>

# <img src='https://www.audacityteam.org/wp-content/themes/wp_audacity/img/logo.png' height=30/> Audacity #

**Audacity** เป็นตัวบันทึกและตัดต่อเสียงแบบ multi-track
<br>

<div align="center">
	<img src='https://wiki.audacityteam.org/w/images/1/13/AudacityBlocks.png' height=360/>
	<h4 align="center">Architectural Patterns/Styles of Audacity</h4>
</div>


รูปแบบสถาปัตยกรรมที่ Audacity ใช้คือรูปแบบ **Layer architectural**

**Layer สีเหลือง** เป็นตัวสื่อสารระหว่าง Layer สีเขียว กับ Audacity อย่าง BlockFile ใช้ file system ของ OS เพื่อเก็บข้อมูลเสียงใน chunk เล็กๆ หลายอัน เพื่อง่ายต่อการตัด คัดลอก และวางเสียง

**Layer สีเขียว** เป็นตัวสื่อสาร OS และเป็นพื้นให้ Layer สีเหลือง อย่าง wxWidgets เป็น library สำคัญในการสร้าง UI และ PortAudio ที่คอยเป็นตัวกลางช่วยให้เราเล่น และบันทึกเสียงผ่าน hardware ได้

### :sparkles: Quality attribute scenarios ###

:heavy_check_mark: Scenario 1: Integrability
```bash
Source:			ผู้ใช้งาน
Stimulus:		ต้องการเพิ่ม Plugin ให้กับ Audacity
Environment:		Deployment, Deployment, Runtime, Integration
Response:		New Configuration
Response Measure:	มี Plugin ใหม่
```
:heavy_check_mark: Scenario 2: Performance
```bash
Source:			Hacker
Stimulus:		Library ที่ใช้งานไม่ปลอดภัย
Environment:		Plugin Online
Response:		Data, Resource
Response Measure:	Intrustion detection devices
```
:heavy_check_mark: Scenario 3: Portability
```bash
Source:			ผู้ใช้งาน
Stimulus:		ต้องการ run Audacity ใน OS ที่แตกต่างกัน
Environment:		OS
Response:		Run Audacity in different OS
Response Measure:	Audacity can run in any casual OS
```

source:

- [Audacity by James Crook](http://www.aosabook.org/en/audacity.html)
- [ArchitecturalDesign](https://wiki.audacityteam.org/wiki/ArchitecturalDesign)


<br>

# <img src='https://matplotlib.org/3.4.0/_static/logo2_compressed.svg' height=25/> Matplotlib #

**Matplotlib** เป็น library ของภาษา Python ที่สร้างกราฟ หรือแผนภาพทางคณิตศาสตร์ เพื่อให้ง่ายต่อการวิเคราะห์ข้อมูล
<br>

<div align="center">
	<img src='https://user-images.githubusercontent.com/69465282/190190817-66545365-fbfd-4618-8997-0d43bd1f1eb5.png' height=360/>
	<h4 align="center">Architectural Patterns/Styles of Matplotlib</h4>
</div>


รูปแบบสถาปัตยกรรมที่ Matplotlib ใช้คือรูปแบบ **Layer architectural**

**Backend Layer** ทำการประมวลผลข้อมูล โดยจะแสดงผลออกมาเป็นภาพ ที่แสดงอยู่ใน figure 

**Artist Layer** ใช้ข้อมูลที่ Backend Layer ส่งมา นำมาจัดเรียงใน figure โดยที่ layer นี้จะคอยจัดการ figure ได้ทุกอย่าง เช่น title อยู่ด้านบน รูปอยู่ตรงกลาง แกน ขนาดตัวหนังสือ และสีทั้งหมดใน figure โดยสามารถปรับแต่งได้โดย Scripting layer

**Scripting layer** ใช้สำหรับการเขียนโปรแกรม โดยในส่วนนี้จะเป็นการเขียนโปรแกรมเพื่อใช้งานกับ Matplotlib โดยจะเขียนโปรแกรมเพื่อสร้างกราฟ และส่วนนี้จะเป็นส่วนที่ผู้ใช้งานสามารถเขียนโปรแกรมเพื่อใช้งานกับ Matplotlib ได้

### :sparkles: Quality attribute scenarios ###

:heavy_check_mark: Scenario 1: Modifiability
```bash
Source:			ผู้พัฒนา
Stimulus:		ต้องการเพิ่มคุณสมบัติใหม่
Environment:		เวลาที่ใช้ในการพัฒนา
Response:		ระบบที่สามารถเพิ่มคุณสมบัติใหม่ได้
Response Measure:	เวลาที่ใช้ในการพัฒนา
```
:heavy_check_mark: Scenario 2: Performance
```bash
Source:			ผู้ใช้งาน
Stimulus:		คำสั่งสร้างกราฟจากผู้ใช้งาน
Environment:		Deployment, Runtime, Integration
Response:		เวลาที่ใช้ในการสร้างกราฟ
Response Measure:	Latency
```
:heavy_check_mark: Scenario 3: Usability
```bash
Source:			ผู้ใช้งาน
Stimulus:		ใช้งาน matplotlib ในการสร้างกราฟด้วย python
Environment:		Deployment, Runtime, Integration
Response:		กราฟที่สร้างจาก matplotlib
Response Measure:	มีการแสดงกราฟออกมา
```

source:

- [Matplotlib by James Crook and Michael Droettboom](http://aosabook.org/en/matplotlib.html)
- [Mastering Matplotlib: Part 1](https://medium.com/dataseries/mastering-matplotlib-part-1-a480109171e3)

<br>

# <img src='https://killbill.io/wp-content/uploads/2016/04/killbill.png' height=25/> Kill Bill #

**Kill Bill** is a open-source subscription billing and payments platform. Fully extensible, you can build your business logic on top of it for a customized billing and payments solution
<br>

<div align="center">
	<img src='https://killbill.io/wp-content/uploads/2014/01/kbcoreservices1.png' height=360/>
	<h4 align="center">Architectural Patterns/Styles of Kill Bill</h4>
</div>


รูปแบบสถาปัตยกรรมที่ Kill Bill ใช้คือรูปแบบ **Layer architectural**

**The catalog service**, whose role is to provide the catalog information that is pertinent to a given tenant. The catalog service offers an API to retrieve product information, alignment rules, prices,..

**The entitlement service** offers an API for managing all the entitlement information associated to a given subscription — its state (started, paused, resumed, stopped,…), its ownership, the various dates where state transition,… The entitlement system offers a different view than what is reflected in the invoices to allow fine tuning of what should be billed versus how the service is provided. In addition to that API, it will generate (persistent) bus events that other services can register to.

**The invoice service** offers an API to retrieve past invoices, make any adjustments, or even trigger future invoices. In addition to that API, it will generate bus events that other services can register to.

**The payment system** offers an API to retrieve past payment/refund information or to trigger new payments/refunds.  In addition to that API, it will also generate bus events.

**The overdue system** is a generic system that is driven through a configuration, to take action when payments are failing and users end up not paying. A complex set of phases can be implemented to gradually terminate the service, notify the users, … if needed. It also offers an API and generates bus events.

### :sparkles: Quality attribute scenarios ###

:heavy_check_mark: Scenario 1: Availability
```bash
Source:			ผู้พัฒนา software
Stimulus:		การใช้งาน kill bill
Environment:		Kill Bill, REST APIs
Response:		ใช้งาน kill bill ได้ตลอดเวลา
Response Measure:	Availability percentage
```
:heavy_check_mark: Scenario 2: Security
```bash
Source:			ผู้พัฒนา software
Stimulus:		api ถูกโจมตี
Environment:		Kill Bill, REST APIs
Response:		ระบบสามารถกลับมาใช้งานได้อย่างรวดเร็ว
Response Measure:	MTTR ที่น้อย
```
:heavy_check_mark: Scenario 3: Usability
```bash
Source:			ผู้พัฒนา software
Stimulus:		ต้องการนำ kill bill ไปใช้ในระบบตัวเอง
Environment:		Kill Bill, REST APIs
Response:		ระบบที่สามารถจัดการระบบการเงิน
Response Measure:	ระบบใช้งานได้ไม่มีปัญหา
```

source:

- [Kill Bill](https://killbill.io/)
- [Kill Bill: Billing System Architecture](https://killbill.io/blog/kill-bill-billing-system-architecture/)

## :memo: License ##

Made with :heart: by <a href="https://github.com/Samach21" target="_blank">Samach21</a>

&#xa0;

<a href="#top">Back to top</a>
