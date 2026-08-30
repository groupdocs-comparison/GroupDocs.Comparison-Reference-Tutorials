---
categories:
- Java Development
date: '2026-08-30'
description: เรียนรู้วิธีตั้งค่าไลเซนส์ GroupDocs สำหรับ Java อย่างรวดเร็ว ทำความเข้าใจการตั้งค่าไลเซนส์แบบไฟล์,
  สตรีม, และ URL, เข้าใจโมเดลการให้ลิขสิทธิ์, และแก้ไขปัญหาที่พบบ่อยเพื่อการผสานรวม
  Java อย่างราบรื่น
keywords:
- set groupdocs license java
- groupdocs java licensing
- groupdocs comparison license setup
- java license from stream
- java license from url
lastmod: '2026-08-30'
linktitle: การให้ลิขสิทธิ์และการกำหนดค่า Java
og_description: เรียนรู้วิธีตั้งค่าไลเซนส์ GroupDocs สำหรับ Java อย่างรวดเร็ว คู่มือนี้ครอบคลุมการให้ลิขสิทธิ์แบบไฟล์,
  สตรีม, และ URL, อธิบายแต่ละโมเดล, และให้เคล็ดลับการแก้ไขปัญหาแก่ผู้พัฒนา Java
og_image_alt: Guide showing how to set GroupDocs license java using file, stream,
  and URL methods
og_title: วิธีตั้งค่าไลเซนส์ GroupDocs สำหรับ Java – คู่มือฉบับสมบูรณ์
schemas:
- author: GroupDocs
  dateModified: '2026-08-30'
  description: Learn how to set GroupDocs license java quickly. Master file, stream,
    and URL license setup, understand licensing models, and troubleshoot common issues
    for seamless Java integration.
  headline: How to set GroupDocs license java – complete guide
  type: TechArticle
- description: Learn how to set GroupDocs license java quickly. Master file, stream,
    and URL license setup, understand licensing models, and troubleshoot common issues
    for seamless Java integration.
  name: How to set GroupDocs license java – complete guide
  steps:
  - name: '**File‑based licensing** – Store the XML license file on the local filesystem
      and load it at startup. Ideal for on‑prem servers with stable storage.'
    text: '**File‑based licensing** – Store the XML license file on the local filesystem
      and load it at startup. Ideal for on‑prem servers with stable storage.'
  - name: '**Stream‑based licensing** – Load the license from an `InputStream`. Perfect
      for Docker containers, encrypted stores, or when the license is kept in a database.'
    text: '**Stream‑based licensing** – Load the license from an `InputStream`. Perfect
      for Docker containers, encrypted stores, or when the license is kept in a database.'
  - name: '**URL‑based licensing** – Retrieve the license from a remote HTTPS endpoint,
      enabling centralized management and automatic updates across multiple instances.'
    text: '**URL‑based licensing** – Retrieve the license from a remote HTTPS endpoint,
      enabling centralized management and automatic updates across multiple instances.'
  - name: '**Metered licensing** – Pay‑per‑use model that reports usage to the GroupDocs
      licensing service; great for variable processing volumes.'
    text: '**Metered licensing** – Pay‑per‑use model that reports usage to the GroupDocs
      licensing service; great for variable processing volumes.'
  - name: '**Add the GroupDocs.Comparison Maven dependency** to your `pom.xml` or
      Gradle file so the `License` class is available at compile time.'
    text: '**Add the GroupDocs.Comparison Maven dependency** to your `pom.xml` or
      Gradle file so the `License` class is available at compile time.'
  - name: '**Place the license file** (`GroupDocs.Comparison.lic`) in a secure location—e.g.,
      a resources folder, an encrypted volume, or a cloud bucket.'
    text: '**Place the license file** (`GroupDocs.Comparison.lic`) in a secure location—e.g.,
      a resources folder, an encrypted volume, or a cloud bucket.'
  - name: '**Choose the loading method**:'
    text: '**Choose the loading method**:'
  - name: '**Initialize early** – put the call in a static block, a Spring `@PostConstruct`
      method, or the main method before any comparison operation.'
    text: '**Initialize early** – put the call in a static block, a Spring `@PostConstruct`
      method, or the main method before any comparison operation.'
  - name: '**Verify** – run a simple comparison task; if no licensing exception appears,
      the license is active.'
    text: '**Verify** – run a simple comparison task; if no licensing exception appears,
      the license is active.'
  - name: '**Verify license validity** – ensure the license has not expired and matches
      the product (GroupDocs.Comparison).'
    text: '**Verify license validity** – ensure the license has not expired and matches
      the product (GroupDocs.Comparison).'
  type: HowTo
- questions:
  - answer: Yes – change the initialization code to point to a file, stream, or URL
      and restart the JVM; no code recompilation is required.
    question: Can I switch licensing methods without redeploying the whole app?
  - answer: Check for updates at startup and optionally schedule a daily refresh;
      this ensures you pick up renewals or upgrades automatically.
    question: How often should I refresh a URL‑based license?
  - answer: Absolutely. Decrypt the file first, then pass the resulting `InputStream`
      to the `License.setLicense` method.
    question: Does stream‑based licensing work with encrypted license files?
  - answer: The next comparison operation throws a licensing exception; monitor the
      logs and set up alerts to renew before expiration.
    question: What happens if the license expires while the app is running?
  - answer: Yes – as long as the server can reach the GroupDocs licensing service
      to report usage, metered licensing works in any environment.
    question: Is metered licensing compatible with on‑prem deployments?
  type: FAQPage
tags:
- licensing
- configuration
- groupdocs
- java
- document-comparison
title: วิธีตั้งค่าไลเซนส์ GroupDocs สำหรับ Java – คู่มือฉบับสมบูรณ์
type: docs
url: /th/java/licensing-configuration/
weight: 10
---

# วิธีตั้งค่าใบอนุญาต GroupDocs java – คู่มือเต็ม

ในบทแนะนำที่ครอบคลุมนี้คุณจะได้เรียนรู้ **วิธีตั้งค่าใบอนุญาต GroupDocs java** สำหรับแอปพลิเคชันของคุณ ไม่ว่าจะเลือกใช้ไฟล์ในเครื่อง, สตรีมในหน่วยความจำ, หรือ URL ระยะไกล การตั้งค่าใบอนุญาตที่ถูกต้องจะลบลายน้ำการประเมินผล, ปลดล็อกฟีเจอร์ทั้งหมด, และรับประกันประสิทธิภาพที่เสถียรในสภาพการผลิต เราจะอธิบายแต่ละวิธี, แบ่งปันสถานการณ์จริง, และให้เคล็ดลับการแก้ปัญหาเพื่อให้คุณสามารถผสานการตั้งค่าใบอนุญาตได้อย่างมั่นใจ.

## คำตอบด่วน
- **วิธีที่ง่ายที่สุดในการโหลดใบอนุญาต GroupDocs คืออะไร?** โหลดไฟล์ใบอนุญาต XML ในเครื่องระหว่างการเริ่มต้นแอปพลิเคชัน.  
- **ฉันสามารถโหลดใบอนุญาตจากหน่วยความจำได้หรือไม่?** ได้ – ส่ง `InputStream` ที่มี XML ของใบอนุญาตให้กับคลาส `License`.  
- **การตั้งค่าใบอนุญาตแบบ URL รองรับหรือไม่?** รองรับอย่างแน่นอน; ชี้ API ไปที่ URL HTTPS ระยะไกลและไลบรารีจะดาวน์โหลดและใช้ใบอนุญาตโดยอัตโนมัติ.  
- **ฉันต้องตั้งค่าใบอนุญาตก่อนการเปรียบเทียบทุกครั้งหรือไม่?** ไม่ – เริ่มต้นเพียงครั้งเดียว, ปกติใน static initializer หรือ Spring bean, และมันจะคงอยู่ตลอดอายุการทำงานของ JVM.  
- **ควรทำอย่างไรหากใบอนุญาตไม่ถูกจดจำ?** ตรวจสอบโครงสร้าง XML, ยืนยันสิทธิ์การเข้าถึงไฟล์, และเปิดการบันทึกดีบักเพื่อดูข้อผิดพลาดที่แน่นอน.

## ใบอนุญาต GroupDocs ใน Java คืออะไร?
ใบอนุญาต GroupDocs ใน Java กำหนดว่า API ฟีเจอร์ใดจะถูกปลดล็อกและลบข้อจำกัดการประเมินผลเช่นลายน้ำ ใบอนุญาตที่ถูกต้องให้การเข้าถึงเต็มรูปแบบของเอนจินการเปรียบเทียบ, เปิดใช้งานตัวเลือกขั้นสูง, และรับประกันการปฏิบัติตามเงื่อนไขการใช้ใบอนุญาต นอกจากนี้ยังช่วยเพิ่มความเสถียรและประสิทธิภาพโดยให้ SDK ทำงานโดยไม่มีข้อจำกัดการประเมินผล.

## ทำไมการกำหนดค่าการใช้ใบอนุญาตที่ถูกต้องจึงสำคัญ
การกำหนดค่าการใช้ใบอนุญาตที่ถูกต้องจะปลดล็อกฟีเจอร์ทั้งหมด, ลบลายน้ำการประเมินผล, และรับประกันว่าการเปรียบเทียบเอกสารของคุณทำงานอย่างเชื่อถือได้ในสภาพการผลิต นอกจากนี้ยังช่วยให้สอดคล้องกับนโยบายการใช้ใบอนุญาตขององค์กร, ให้ประสิทธิภาพเสถียรภายใต้โหลด, และป้องกันข้อผิดพลาดรันไทม์ที่ไม่คาดคิดจากการขาดหรือใบอนุญาตที่ไม่ถูกต้อง, ลดภาระการบำรุงรักษา.

## ทำความเข้าใจประเภทใบอนุญาต GroupDocs
GroupDocs มี **สี่** โมเดลการให้ใบอนุญาตที่แตกต่างกัน, แต่ละแบบออกแบบมาสำหรับรูปแบบการปรับใช้ที่เฉพาะเจาะจง:
1. **การให้ใบอนุญาตแบบไฟล์** – เก็บไฟล์ใบอนุญาต XML ไว้ในระบบไฟล์ท้องถิ่นและโหลดในช่วงเริ่มต้น เหมาะสำหรับเซิร์ฟเวอร์ในสถานที่ที่มีการจัดเก็บที่เสถียร.  
2. **การให้ใบอนุญาตแบบสตรีม** – โหลดใบอนุญาตจาก `InputStream` เหมาะสำหรับคอนเทนเนอร์ Docker, ที่เก็บข้อมูลเข้ารหัส, หรือเมื่อใบอนุญาตถูกเก็บในฐานข้อมูล.  
3. **การให้ใบอนุญาตแบบ URL** – ดึงใบอนุญาตจาก endpoint HTTPS ระยะไกล, ทำให้สามารถจัดการศูนย์กลางและอัปเดตอัตโนมัติในหลายอินสแตนซ์.  
4. **การให้ใบอนุญาตแบบตามการใช้งาน** – โมเดลจ่ายตามการใช้ที่รายงานการใช้งานไปยังบริการใบอนุญาตของ GroupDocs; เหมาะกับปริมาณการประมวลผลที่เปลี่ยนแปลง.

## บทแนะนำการตั้งค่าใบอนุญาตที่พร้อมใช้งาน

### [วิธีตั้งค่าใบอนุญาต GroupDocs จากสตรีมใน Java: คู่มือขั้นตอนต่อขั้นตอน](./set-groupdocs-license-stream-java-guide/)
เรียนรู้วิธีตั้งค่าใบอนุญาต GroupDocs ด้วยการใช้ input stream ใน Java, เพื่อให้การผสานรวมกับแอปพลิเคชันของคุณเป็นไปอย่างราบรื่น บทแนะนำนี้ครอบคลุมสถานการณ์การให้ใบอนุญาตแบบหน่วยความจำ, การพิจารณาด้านความปลอดภัย, และรูปแบบการปรับใช้แบบคอนเทนเนอร์.

### [วิธีตั้งค่าใบอนุญาตจากไฟล์ใน GroupDocs.Comparison สำหรับ Java: คู่มือครอบคลุม](./groupdocs-comparison-license-setup-java/)
เรียนรู้วิธีตั้งค่าไฟล์ใบอนุญาตใน GroupDocs.Comparison สำหรับ Java ด้วยคู่มือขั้นตอนต่อขั้นตอนนี้ ปลดล็อกฟีเจอร์ทั้งหมดและเพิ่มประสิทธิภาพการเปรียบเทียบเอกสารอย่างมีประสิทธิภาพ รวมถึงการแก้ปัญหาสำหรับปัญหาเส้นทางไฟล์และสิทธิ์ที่พบบ่อย.

### [การตั้งค่าใบอนุญาต GroupDocs.Comparison ผ่าน URL ใน Java: ทำให้การอัตโนมัติการให้ใบอนุญาตง่ายขึ้น](./set-groupdocs-comparison-license-url-java/)
เรียนรู้วิธีอัตโนมัติการให้ใบอนุญาตสำหรับ GroupDocs.Comparison ด้วย URL ใน Java ทำให้การตั้งค่าของคุณเป็นระเบียบและรับประกันว่าใบอนุญาตจะเป็นเวอร์ชันล่าสุดเสมอ เหมาะสำหรับ pipeline CI/CD และการปรับใช้บนคลาวด์.

## ฉันจะตั้งค่าใบอนุญาต GroupDocs java ในแอปพลิเคชันของฉันอย่างไร?
`License` เป็นคลาสที่มาจาก GroupDocs.Comparison SDK ซึ่งทำการโหลดและตรวจสอบความถูกต้องของไฟล์ใบอนุญาต โหลดใบอนุญาตเพียงครั้งเดียวระหว่างการเริ่มต้นแอปพลิเคชัน: สร้างอ็อบเจ็กต์ `License`, เรียก `setLicense` พร้อมเส้นทางไฟล์, `InputStream`, หรือสตริง URL, แล้วให้ไลบรารีจัดการการตรวจสอบ การเรียกใช้ครั้งเดียวนี้จะเปิดใช้งานใบอนุญาตสำหรับ JVM ทั้งหมด, ลดความจำเป็นในการตั้งค่าซ้ำ.

### คู่มือขั้นตอนต่อขั้นตอน (ไม่มีบล็อกโค้ด)

1. **เพิ่ม dependency ของ GroupDocs.Comparison ใน Maven** ไปยังไฟล์ `pom.xml` หรือ Gradle ของคุณ เพื่อให้คลาส `License` พร้อมใช้งานในขั้นตอนคอมไพล์.  
2. **วางไฟล์ใบอนุญาต** (`GroupDocs.Comparison.lic`) ในตำแหน่งที่ปลอดภัย—เช่นโฟลเดอร์ resources, โวลุ่มที่เข้ารหัส, หรือ bucket บนคลาวด์.  
3. **เลือกวิธีการโหลด**:
   - *ไฟล์*: `new License().setLicense("path/to/GroupDocs.Comparison.lic");`
   - *สตรีม*: เปิด `InputStream` (เช่นจาก BLOB ของฐานข้อมูล) แล้วส่งให้ `setLicense`.
   - *URL*: ระบุสตริง URL HTTPS; SDK จะดาวน์โหลดและใช้ใบอนุญาตโดยอัตโนมัติ.  
4. **เริ่มต้นตั้งแต่ต้น** – ใส่การเรียกใช้ใน static block, เมธอด Spring `@PostConstruct`, หรือเมธอด main ก่อนทำการเปรียบเทียบใด ๆ.  
5. **ตรวจสอบ** – รันงานเปรียบเทียบง่าย ๆ; หากไม่มีข้อยกเว้นเกี่ยวกับใบอนุญาตแสดงขึ้น, ใบอนุญาตจะทำงาน.

## ความท้าทายและวิธีแก้ไขการตั้งค่าที่พบบ่อย
**ปัญหา #1: ไม่พบไฟล์ใบอนุญาต** – ตรวจสอบเส้นทางแบบ absolute หรือ classpath‑relative อีกครั้ง, และยืนยันว่าไฟล์ถูกบรรจุใน JAR ของคุณหรือปรับใช้พร้อมกับไฟล์ executable.  

**ปัญหา #2: รูปแบบใบอนุญาตไม่ถูกต้อง** – ยืนยันว่าคุณใช้ใบอนุญาตที่สร้างเฉพาะสำหรับ GroupDocs.Comparison (ไม่ใช่ผลิตภัณฑ์ GroupDocs อื่น) และ XML ไม่ถูกแก้ไขระหว่างการโอนย้าย.  

**ปัญหา #3: ปัญหาการปิดสตรีม** – รักษา `InputStream` เปิดอยู่จนกว่า `setLicense` จะคืนค่า; การปิดก่อนเวลาอาจทำให้การให้ใบอนุญาตล้มเหลว.  

**ปัญหา #4: เวลาการเชื่อมต่อหมดอายุกับการให้ใบอนุญาตแบบ URL** – ใช้ตรรกะการลองใหม่ด้วย exponential back‑off และกำหนดค่า timeout การเชื่อมต่อ/อ่านที่เหมาะสมเพื่อจัดการกับข้อขัดข้องเครือข่ายชั่วคราว.

## เคล็ดลับการเพิ่มประสิทธิภาพการทำงาน
- **เริ่มต้นเพียงครั้งเดียว** – ตั้งค่าใบอนุญาตในช่วงเริ่มต้นแอปพลิเคชันแทนการทำก่อนแต่ละการเรียกเปรียบเทียบ.  
- **แคชการตรวจสอบใบอนุญาต** – ไลบรารีทำการตรวจสอบใบอนุญาตภายใน; หลีกเลี่ยงการตรวจสอบซ้ำในโค้ดของคุณ.  
- **ตรวจสอบการใช้หน่วยความจำ** – การให้ใบอนุญาตแบบสตรีมเก็บ XML ในหน่วยความจำ, ดังนั้นควรเฝ้าดู heap ในสถานการณ์ที่ผ่านสูง.  
- **ใช้การโหลดแบบอะซิงโครนัสสำหรับ URL** – ดึงใบอนุญาตในเธรดพื้นหลังระหว่างการ warm‑up เพื่อหลีกเลี่ยงการบล็อกคำขอแรก.

## เคล็ดลับระดับมืออาชีพสำหรับการปรับใช้ระดับองค์กร
- **การจัดการใบอนุญาตแบบศูนย์กลาง** – เก็บใบอนุญาตใน object store ที่ปลอดภัยเช่น AWS S3 หรือ Azure Blob Storage, แล้วโหลดผ่าน URL พร้อมแคชในเครื่อง.  
- **การกำหนดค่าตามสภาพแวดล้อม** – ใช้การให้ใบอนุญาตแบบไฟล์สำหรับการพัฒนาในเครื่อง, แบบสตรีมสำหรับคอนเทนเนอร์ staging, และแบบ URL สำหรับคลัสเตอร์การผลิต.  
- **กลยุทธ์สำรอง** – เก็บสำเนาใบอนุญาตในเครื่องเป็นสำรองหากแหล่งระยะไกลไม่สามารถเข้าถึงได้.  
- **แนวทางปฏิบัติด้านความปลอดภัย** – อย่า hard‑code เส้นทางหรือข้อมูลรับรองของใบอนุญาต; ให้อ่านจากตัวแปรสภาพแวดล้อมหรือ secrets manager.

## การแก้ไขปัญหาใบอนุญาต
1. **ตรวจสอบความถูกต้องของใบอนุญาต** – ยืนยันว่าใบอนุญาตยังไม่หมดอายุและตรงกับผลิตภัณฑ์ (GroupDocs.Comparison).  
2. **ตรวจสอบสิทธิ์ของแอปพลิเคชัน** – กระบวนการ Java ต้องมีสิทธิ์อ่านไฟล์ระบบหรือ endpoint เครือข่าย.  
3. **ตรวจสอบการกำหนดค่า classpath** – สำหรับการให้ใบอนุญาตแบบไฟล์, ยืนยันว่าไฟล์ใบอนุญาตอยู่บน classpath หรือให้เส้นทาง absolute ที่ถูกต้อง.  
4. **เปิดการบันทึกดีบัก** – ตั้งค่า `log4j.logger.com.groupdocs=DEBUG` (หรือการกำหนดค่า SLF4J ที่เทียบเท่า) เพื่อดูข้อความการเริ่มต้นอย่างละเอียด.  
5. **ทดสอบแยกส่วน** – สร้างคลาส Java ขนาดเล็กที่โหลดใบอนุญาตเท่านั้น; นี้ช่วยแยกความขัดแย้งกับไลบรารีอื่น.

## ควรใช้วิธีการให้ใบอนุญาตแต่ละแบบเมื่อใด
เลือกวิธีการให้ใบอนุญาตที่ตรงกับสถานการณ์การปรับใช้ของคุณ: การให้ใบอนุญาตแบบไฟล์เหมาะสำหรับเซิร์ฟเวอร์ในสถานที่ที่มีการจัดเก็บภายในที่เสถียร; การให้ใบอนุญาตแบบสตรีมทำงานดีที่สุดในสภาพแวดล้อมคอนเทนเนอร์หรือคลาวด์ที่ใบอนุญาตเก็บในฐานข้อมูลหรือ secret manager; การให้ใบอนุญาตแบบ URL เหมาะกับไมโครเซอร์วิสกระจายที่ต้องการใบอนุญาตที่จัดการศูนย์กลาง; และการให้ใบอนุญาตแบบตามการใช้งานเหมาะกับโมเดลจ่ายตามการใช้ที่มีปริมาณการประมวลผลเปลี่ยนแปลง.

## แหล่งข้อมูลเพิ่มเติม
- [เอกสาร GroupDocs.Comparison สำหรับ Java](https://docs.groupdocs.com/comparison/java/)
- [อ้างอิง API GroupDocs.Comparison สำหรับ Java](https://reference.groupdocs.com/comparison/java/)
- [ดาวน์โหลด GroupDocs.Comparison สำหรับ Java](https://releases.groupdocs.com/comparison/java/)
- [ฟอรั่ม GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison)
- [สนับสนุนฟรี](https://forum.groupdocs.com/)
- [ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถสลับวิธีการให้ใบอนุญาตโดยไม่ต้องปรับใช้แอปทั้งหมดใหม่ได้หรือไม่?**  
ตอบ: ได้ – เปลี่ยนโค้ดการเริ่มต้นให้ชี้ไปที่ไฟล์, สตรีม, หรือ URL แล้วรีสตาร์ท JVM; ไม่จำเป็นต้องคอมไพล์โค้ดใหม่.

**ถาม: ควรรีเฟรชใบอนุญาตแบบ URL บ่อยแค่ไหน?**  
ตอบ: ตรวจสอบการอัปเดตที่การเริ่มต้นและอาจกำหนดเวลารีเฟรชรายวัน; นี้ทำให้คุณรับการต่ออายุหรืออัปเกรดโดยอัตโนมัติ.

**ถาม: การให้ใบอนุญาตแบบสตรีมทำงานกับไฟล์ใบอนุญาตที่เข้ารหัสหรือไม่?**  
ตอบ: แน่นอน. ถอดรหัสไฟล์ก่อน, แล้วส่ง `InputStream` ที่ได้ให้กับเมธอด `License.setLicense`.

**ถาม: จะเกิดอะไรขึ้นหากใบอนุญาตหมดอายุขณะแอปกำลังทำงาน?**  
ตอบ: การดำเนินการเปรียบเทียบครั้งถัดไปจะโยนข้อยกเว้นเกี่ยวกับใบอนุญาต; ตรวจสอบบันทึกและตั้งค่าแจ้งเตือนเพื่อต่ออายุก่อนหมดอายุ.

**ถาม: การให้ใบอนุญาตแบบตามการใช้งานเข้ากันได้กับการปรับใช้ในสถานที่หรือไม่?**  
ตอบ: ได้ – ตราบใดที่เซิร์ฟเวอร์สามารถเข้าถึงบริการใบอนุญาตของ GroupDocs เพื่อรายงานการใช้, การให้ใบอนุญาตแบบตามการใช้งานทำงานได้ในทุกสภาพแวดล้อม.

---

**อัปเดตล่าสุด:** 2026-08-30  
**ทดสอบกับ:** GroupDocs.Comparison Java 23.12 (latest at time of writing)  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [วิธีใช้ใบอนุญาต: คู่มือการกำหนดค่า URL สำหรับ GroupDocs Comparison Java](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)
- [GroupDocs Java: ตัวจัดการใบอนญาตศูนย์กลางผ่านสตรีม](/comparison/java/licensing-configuration/set-groupdocs-license-stream-java-guide/)
- [เปรียบเทียบ PDF ใน Java – คู่มือ GroupDocs ครบถ้วน](/comparison/java/basic-comparison/master-java-document-comparison-preview-groupdocs/)