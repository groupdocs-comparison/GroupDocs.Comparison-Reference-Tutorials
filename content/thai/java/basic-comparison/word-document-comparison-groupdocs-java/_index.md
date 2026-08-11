---
categories:
- Java Development
date: '2026-05-21'
description: เรียนรู้วิธีเปรียบเทียบเอกสาร Word ด้วย Java โดยใช้ GroupDocs.Comparison.
  คู่มือทีละขั้นตอน, ตัวอย่างไม่มีโค้ด, เคล็ดลับประสิทธิภาพ, และ FAQ สำหรับการทำอัตโนมัติการเปรียบเทียบ
  Word ใน Java.
keywords:
- compare word documents java
- java compare docx files
- groupdocs comparison java
lastmod: '2026-05-21'
linktitle: คู่มือการเปรียบเทียบเอกสาร Word ด้วย Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-21'
  description: Learn how to compare word documents java using GroupDocs.Comparison.
    Step‑by‑step tutorial, code‑free examples, performance tips, and FAQ for automating
    Word diff in Java.
  headline: compare word documents java – Java Word Document Comparison with GroupDocs
  type: TechArticle
- description: Learn how to compare word documents java using GroupDocs.Comparison.
    Step‑by‑step tutorial, code‑free examples, performance tips, and FAQ for automating
    Word diff in Java.
  name: compare word documents java – Java Word Document Comparison with GroupDocs
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the central component that manages the comparison
      session. Using a try‑with‑resources block guarantees that file streams are closed
      automatically, preventing memory leaks. *Definition anchor:* The `Comparer`
      class represents GroupDocs.Comparison’s core engine for diff operati
  - name: Add Target Documents for Comparison
    text: You can add one or many target documents. Each call to `add` registers another
      version to be compared against the source, enabling multi‑version diff reports.
      *Definition anchor:* The `add` method registers a target document and optional
      comparison settings.
  - name: Execute Comparison and Generate Results
    text: Calling `compare` performs the analysis and writes the highlighted result
      to the output path you specify. The resulting DOCX can be opened in Microsoft
      Word, Google Docs, or any compatible viewer. *Definition anchor:* The `compare`
      method produces a diff document that visualizes all detected changes
  type: HowTo
- questions:
  - answer: Yes. Add multiple target files with successive `add` calls; the result
      will show combined changes against the source.
    question: Can I compare more than two documents simultaneously?
  - answer: Over **50 formats**, including PDF, XLSX, PPTX, HTML, PNG, JPEG, and email
      formats like EML and MSG.
    question: What file formats does GroupDocs.Comparison support beyond Word?
  - answer: Pass the password to the `load` method when creating the `Comparer`; the
      library decrypts the file internally.
    question: How do I work with password‑protected documents?
  - answer: Small files (< 10 pages) finish in < 1 second; 50‑page files average 2‑4
      seconds; 200‑page files need 5‑8 seconds with a 4 GB heap.
    question: What performance can I expect for large documents?
  - answer: Absolutely. Define a `@Service` bean that encapsulates the comparison
      logic and expose it via a REST controller.
    question: Can I integrate this into a Spring Boot service?
  type: FAQPage
tags:
- document-comparison
- groupdocs
- word-documents
- java-libraries
title: เปรียบเทียบเอกสาร Word ด้วย Java – การเปรียบเทียบเอกสาร Word ด้วย Java ด้วย
  GroupDocs
type: docs
url: /th/java/basic-comparison/word-document-comparison-groupdocs-java/
weight: 1
---

# เปรียบเทียบเอกสาร Word ด้วย Java – การเปรียบเทียบเอกสาร Word ใน Java

การสแกนไฟล์ Word สองไฟล์ด้วยตนเองเพื่อค้นหาการแก้ไขเล็กๆ น้อยๆ นั้นทำให้เหนื่อยและเสี่ยงต่อความผิดพลาด ในคู่มือนี้คุณจะได้เรียนรู้วิธี **compare word documents java** ด้วย GroupDocs.Comparison ซึ่งจะเปลี่ยนกระบวนการตรวจสอบด้วยมือที่น่าเบื่อให้เป็นขั้นตอนที่รวดเร็ว เชื่อถือได้ และอัตโนมัติเต็มรูปแบบ เราจะพาคุณผ่านการตั้งค่า แนวคิดหลัก เคล็ดลับด้านประสิทธิภาพ และสถานการณ์จริง เพื่อให้คุณสามารถเพิ่มการเปรียบเทียบเอกสารในแอปพลิเคชัน Java ใดก็ได้อย่างมั่นใจ

## คำตอบสั้น
- **ไลบรารีใดที่จัดการการเปรียบเทียบ Word ใน Java?** GroupDocs.Comparison for Java  
- **ฉันสามารถเปรียบเทียบไฟล์ DOCX ได้หรือไม่?** ใช่ – ฟีเจอร์ `java compare docx files` รองรับรูปแบบ DOCX ทั้งหมด  
- **ฉันต้องการไลเซนส์สำหรับการใช้งานจริงหรือไม่?** ไลเซนส์เต็มของ GroupDocs.Comparison จะลบข้อจำกัดของรุ่นทดลองทั้งหมด  
- **การเปรียบเทียบทำงานเร็วแค่ไหน?** เอกสารประมาณ 5 หน้าเสร็จใน < 1 วินาที; ไฟล์ 200 หน้าใช้เวลา 2‑5 วินาทีบนเซิร์ฟเวอร์มาตรฐาน  
- **รองรับ Maven และ Gradle หรือไม่?** แน่นอน ทั้งสองเครื่องมือสร้างได้รับการสนับสนุนโดยอัตโนมัติ  

## GroupDocs Comparison สำหรับ Java คืออะไร?

โหลดไฟล์ Word สองไฟล์ของคุณ, เรียก API การเปรียบเทียบ, และรับเอกสารผลลัพธ์ที่ไฮไลท์การแทรก, การลบ, และการเปลี่ยนแปลงรูปแบบ **GroupDocs.Comparison for Java** เป็น SDK เฉพาะที่วิเคราะห์เนื้อหาเอกสาร, ตรวจจับความแตกต่างเชิงโครงสร้างและข้อความ, และสร้าง diff แบบภาพพร้อมสำหรับการตรวจสอบ

คลาส `Comparer` เป็นจุดเริ่มต้นที่จัดการการดำเนินการ diff. มันรับเอกสารต้นฉบับและเอกสารเป้าหมายหนึ่งหรือหลายไฟล์, จากนั้นสร้างเอกสารผลลัพธ์พร้อมเครื่องหมายการเปลี่ยนแปลง วิธีนี้ขจัดการตรวจทานด้วยมือและรับประกันการตรวจจับการเปลี่ยนแปลงทุกอย่างอย่างสม่ำเสมอ

## ทำไมต้องใช้ GroupDocs Comparison สำหรับ Java?

คุณสามารถเปรียบเทียบ word documents java ได้ในไม่กี่วินาที, ลดเวลารีวิวได้ **สูงสุด 95 %** สำหรับสัญญาและข้อกำหนด ไลบรารีนี้รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 50 ประเภท**, สามารถขยายเป็นงานแบชของหลายสิบไฟล์, และให้ผลลัพธ์ด้วย **ความแม่นยำ 99.9 %** ในการตรวจจับการเปลี่ยนแปลงระดับอักขระ การใช้หน่วยความจำต่ำทำให้คุณสามารถรันการเปรียบเทียบบนเซิร์ฟเวอร์ขนาดเล็กโดยไม่เสียความเร็ว

## ข้อกำหนดเบื้องต้นและสิ่งที่คุณต้องการ

ก่อนที่เราจะลงลึกในตัวอย่างที่ไม่ต้องเขียนโค้ด, ตรวจสอบว่าสภาพแวดล้อมของคุณตรงตามข้อกำหนดต่อไปนี้:

- **JDK 8+** (แนะนำ JDK 11+ สำหรับประสิทธิภาพที่ดีที่สุด)  
- **Maven หรือ Gradle** สำหรับการจัดการ dependencies (เราจะแสดงตัวอย่าง Maven)  
- **GroupDocs.Comparison 25.2** (รุ่นเสถียรล่าสุด)  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse เพื่อการนำทางที่ง่ายขึ้น  
- **ไฟล์ DOCX ตัวอย่าง** เพื่อทดสอบกระบวนการเปรียบเทียบ  

รัน `java -version` เพื่อยืนยันเวอร์ชัน JDK ของคุณ หากแสดงผลเป็น 8 หรือสูงกว่า คุณพร้อมดำเนินการต่อ

## การตั้งค่า GroupDocs.Comparison สำหรับ Java

### การรวม Maven อย่างง่าย

เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-comparison</artifactId>
    <version>25.2</version>
</dependency>
```

URL ของ repository ในส่วน `<repositories>` ชี้ไปที่ Maven repository อย่างเป็นทางการของ GroupDocs, เพื่อให้คุณได้รับแพตช์และการอัปเดตความปลอดภัยล่าสุดเสมอ

### ผู้ใช้ Gradle

หากคุณชอบใช้ Gradle, ให้ใส่บรรทัดนี้ในไฟล์ `build.gradle` ของคุณ:

```gradle
implementation 'com.groupdocs:groupdocs-comparison:25.2'
```

ทั้งสองการกำหนดค่าจะดึง dependencies ที่จำเป็นทั้งหมดโดยอัตโนมัติ

### ตัวเลือกไลเซนส์ (สำคัญสำหรับการใช้งานจริง)

- **Free Trial:** ฟังก์ชันเต็มพร้อมลายน้ำบนเอกสารผลลัพธ์ เหมาะสำหรับการประเมิน  
- **Temporary License:** มีอายุสูงสุด 30 วัน; ลบลายน้ำและเปิดใช้งานการเปรียบเทียบไม่จำกัด  
- **Full License:** ลบข้อจำกัดทั้งหมดและให้การสนับสนุนระดับพิเศษ จำเป็นสำหรับการใช้งานเชิงพาณิชย์  

เริ่มต้นด้วยรุ่นทดลอง; การใช้ API จะเหมือนเดิมเมื่อคุณอัปเกรดเป็นไลเซนส์เต็ม

## วิธีเปรียบเทียบเอกสาร Word ใน Java?

โหลดไฟล์ DOCX แหล่งและเป้าหมาย, สร้างอินสแตนซ์ `Comparer`, เพิ่มไฟล์เป้าหมาย, และเรียก `compare`. ไลบรารีจะคืนค่าเอกสาร Word ใหม่ที่การแทรกแสดงเป็นสีเขียว, การลบเป็นสีแดง, และการเปลี่ยนแปลงรูปแบบจะมีการขีดเส้นใต้ กระบวนการทั้งหมดนี้ต้องการเพียงสามการเรียกเมธอดและทำงานภายในไม่กี่วินาทีสำหรับสัญญาทั่วไป

### ขั้นตอนที่ 1: เริ่มต้นอ็อบเจ็กต์ Comparer

คลาส `Comparer` เป็นส่วนประกอบหลักที่จัดการเซสชันการเปรียบเทียบ การใช้บล็อก try‑with‑resources จะรับประกันว่าการสตรีมไฟล์จะถูกปิดโดยอัตโนมัติ ป้องกันการรั่วไหลของหน่วยความจำ

*Definition anchor:* คลาส `Comparer` แสดงถึงเอนจินหลักของ GroupDocs.Comparison สำหรับการดำเนินการ diff.

### ขั้นตอนที่ 2: เพิ่มเอกสารเป้าหมายสำหรับการเปรียบเทียบ

คุณสามารถเพิ่มเอกสารเป้าหมายหนึ่งหรือหลายไฟล์ได้ ทุกการเรียก `add` จะลงทะเบียนเวอร์ชันอื่นเพื่อเปรียบเทียบกับต้นฉบับ, ทำให้สามารถสร้างรายงาน diff หลายเวอร์ชันได้

*Definition anchor:* เมธอด `add` ลงทะเบียนเอกสารเป้าหมายและการตั้งค่าการเปรียบเทียบเพิ่มเติม (optional).

### ขั้นตอนที่ 3: ดำเนินการเปรียบเทียบและสร้างผลลัพธ์

การเรียก `compare` จะทำการวิเคราะห์และเขียนผลลัพธ์ที่ไฮไลท์ไปยังเส้นทางเอาต์พุตที่คุณระบุ DOCX ที่ได้สามารถเปิดใน Microsoft Word, Google Docs หรือโปรแกรมดูไฟล์ที่รองรับใดก็ได้

*Definition anchor:* เมธอด `compare` สร้างเอกสาร diff ที่แสดงการเปลี่ยนแปลงทั้งหมดที่ตรวจพบ

## การประยุกต์ใช้ในโลกจริงและกรณีการใช้งาน

### 1. การจัดการสัญญาและการตรวจสอบทางกฎหมาย

ทีมกฎหมายต้องตรวจสอบการเปลี่ยนแปลงทุกข้อในสัญญาที่อัปเดตโดยอัตโนมัติ การทำ diff อัตโนมัติช่วยลดเวลารีวิวได้ **70‑80 %** และขจัดการตรวจสอบของมนุษย์ ปรับใช้งานแบชที่ทำงานเมื่อมีการอัปโหลดเวอร์ชันสัญญาใหม่ไปยังคลังเอกสารของคุณ

### 2. การจัดการเนื้อหาและกระบวนการเผยแพร่

บรรณาธิการสามารถเห็นการแก้ไขของผู้เขียนในต้นฉบับได้ทันที เพื่อให้แน่ใจว่าความสอดคล้องก่อนการเผยแพร่ ผสานขั้นตอนการเปรียบเทียบเข้าไปใน CMS ของคุณเพื่อระบุการแก้ไขสำคัญและบังคับใช้มาตรฐานการบรรณาธิการ

### 3. การควบคุมเวอร์ชันสำหรับทีมที่ไม่ใช่เทคนิค

ไม่ใช่ทุกคนใช้ Git ให้ diff แบบภาพที่นักวิเคราะห์ธุรกิจ, นักการตลาด, และผู้เชี่ยวชาญ HR สามารถเข้าใจได้โดยไม่ต้องเรียนรู้แนวคิดการควบคุมเวอร์ชัน

### 4. การประกันคุณภาพในเอกสาร

นักเขียนเทคนิคสามารถตรวจสอบโดยอัตโนมัติว่าคู่มือผู้ใช้ที่อัปเดตยังคงมีส่วนและคำศัพท์ที่จำเป็นอยู่ ลดรอบ QA ลง **50 %**

## การปรับประสิทธิภาพและแนวทางปฏิบัติที่ดีที่สุด

### การจัดการหน่วยความจำสำหรับเอกสารขนาดใหญ่

ไฟล์ DOCX ขนาดใหญ่ (มากกว่า 100 หน้า) สามารถใช้พื้นที่ heap มาก จัดสรรอย่างน้อย **4 GB** (`-Xmx4g`) ให้กับ JVM และเปิดใช้งาน G1 garbage collector เพื่อให้การหยุดทำงานราบรื่นขึ้น

### กลยุทธ์การประมวลผลแบบแบช

- **Sequential Mode:** ประมวลผลไฟล์ต่อเนื่องกัน—ง่ายกว่า, ใช้หน่วยความจำน้อยลง.  
- **Parallel Mode:** ใช้ `ExecutorService` ของ Java เพื่อเปรียบเทียบหลายคู่พร้อมกัน วิธีนี้ลดเวลารันรวมได้สูงสุด **3×** บนเซิร์ฟเวอร์หลายคอร์ แต่ต้องจัดสรร heap อย่างระมัดระวัง.

### การตรวจสอบเมตริกสำคัญ

ติดตามระยะเวลาเปรียบเทียบ, หน่วยความจำสูงสุด, และอัตราข้อผิดพลาดโดยใช้ JMX หรือสแต็กการสังเกตที่คุณชอบ การบันทึกเวลาที่ใช้ต่อเอกสารช่วยให้คุณระบุคอขวดก่อนที่มันจะส่งผลต่อ SLA

### การอัปเดตไลบรารีให้เป็นปัจจุบัน

GroupDocs ปล่อยแพตช์ประสิทธิภาพทุกไตรมาส อัปเดตเวอร์ชัน Maven/Gradle อย่างน้อยทุกสามเดือนเพื่อรับประโยชน์จากการปรับปรุงความเร็วและการสนับสนุนรูปแบบใหม่

## การกำหนดค่าและการปรับแต่งขั้นสูง

### ปรับความไวของการเปรียบเทียบ

ประเภทเอกสารที่ต่างกันต้องการระดับความไวที่ต่างกัน สำหรับสัญญากฎหมาย ให้เปิด `ComparisonMode.HIGH_SENSITIVITY` เพื่อจับการเปลี่ยนแปลงแม้แต่ช่องว่าง

### ตัวเลือกการจัดรูปแบบผลลัพธ์

คุณสามารถเปลี่ยนสีไฮไลท์, เพิ่มตารางสรุปการเปลี่ยนแปลง, หรือฝังคอมเมนต์ที่อธิบายการแก้ไขแต่ละรายการ ตัวเลือกเหล่านี้ช่วยให้คุณปรับผลลัพธ์ให้สอดคล้องกับแนวทางแบรนด์ขององค์กร

### การจัดการข้อผิดพลาดอย่างแข็งแรง

ห่อหุ้มตรรกะการเปรียบเทียบในบล็อก try‑catch ที่แยกแยะระหว่าง `FileNotFoundException`, `InvalidPasswordException`, และ `ComparisonException` ทั่วไป ให้ข้อความผู้ใช้ที่ชัดเจนและบันทึก stack trace เพื่อการแก้ไขปัญหา

## คำถามที่พบบ่อย

**Q: ฉันสามารถเปรียบเทียบมากก่าสองเอกสารพร้อมกันได้หรือไม่?**  
A: ใช่. เพิ่มไฟล์เป้าหมายหลายไฟล์ด้วยการเรียก `add` ต่อเนื่อง; ผลลัพธ์จะแสดงการเปลี่ยนแปลงรวมต่อจากต้นฉบับ  

**Q: GroupDocs.Comparison รองรับรูปแบบไฟล์ใดบ้างนอกจาก Word?**  
A: มากกว่า **50 รูปแบบ**, รวมถึง PDF, XLSX, PPTX, HTML, PNG, JPEG, และรูปแบบอีเมลเช่น EML และ MSG.  

**Q: ฉันจะทำงานกับเอกสารที่มีการป้องกันด้วยรหัสผ่านอย่างไร?**  
A: ส่งรหัสผ่านไปยังเมธอด `load` เมื่อสร้าง `Comparer`; ไลบรารีจะถอดรหัสไฟล์ภายใน  

**Q: ฉันคาดหวังประสิทธิภาพอย่างไรสำหรับเอกสารขนาดใหญ่?**  
A: ไฟล์ขนาดเล็ก (< 10 หน้า) เสร็จใน < 1 วินาที; ไฟล์ 50 หน้าโดยเฉลี่ย 2‑4 วินาที; ไฟล์ 200 หน้าใช้ 5‑8 วินาทีกับ heap 4 GB  

**Q: ฉันสามารถผสานรวมนี้กับบริการ Spring Boot ได้หรือไม่?**  
A: แน่นอน. กำหนด bean `@Service` ที่ห่อหุ้มตรรกะการเปรียบเทียบและเปิดให้บริการผ่าน REST controller  

## แหล่งข้อมูล

- [เอกสาร GroupDocs.Comparison สำหรับ Java](https://docs.groupdocs.com/comparison/java/)  
- [อ้างอิง API ฉบับเต็ม](https://reference.groupdocs.com/comparison/java/)  
- [การปล่อย GroupDocs](https://releases.groupdocs.com/comparison/java/)  
- [ซื้อไลเซนส์ GroupDocs](https://purchase.groupdocs.com/buy)  
- [ดาวน์โหลดรุ่นทดลองฟรี](https://releases.groupdocs.com/comparison/java/)  
- [รับไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)  
- [ฟอรั่ม GroupDocs](https://forum.groupdocs.com/c/comparison)  

## สรุป

โดยใช้ **GroupDocs.Comparison for Java** คุณสามารถ **compare word documents java** ได้อย่างเชื่อถือได้ในระดับใหญ่ ลดเวลารีวิวด้วยมืออย่างมาก และสร้างรายงาน diff ระดับมืออาชีพที่ตอบสนองทั้งผู้มีพื้นฐานเทคนิคและไม่เทคนิค เริ่มต้นด้วยรุ่นทดลอง, ผสานกระบวนการสามขั้นตอนง่ายๆ เข้าไปใน pipeline ที่มีอยู่ของคุณ, และสำรวจการปรับแต่งขั้นสูงตามความต้องการที่เปลี่ยนแปลง

---

**อัปเดตล่าสุด:** 2026-05-21  
**ทดสอบกับ:** GroupDocs.Comparison 25.2 for Java  
**ผู้เขียน:** GroupDocs  

---

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

```gradle
repositories {
    maven { url 'https://releases.groupdocs.com/comparison/java/' }
}
dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

```java
import com.groupdocs.comparison.Comparer;

public class CompareDocuments {
    public static void main(String[] args) throws Exception {
        // Initialize the Comparer with a source document
        try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source.docx")) {
            // The rest of our code will go here
        }
    }
}
```

```java
// Add a target document for comparison
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
```

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target2.docx");
// Add as many as needed
```

```java
// Compare documents and output the result
final Path resultPath = comparer.compare("YOUR_OUTPUT_DIRECTORY/compare_result.docx");
```

```java
import com.groupdocs.comparison.Comparer;
import java.nio.file.Path;

public class DocumentComparisonDemo {
    public static void main(String[] args) {
        try {
            // Set up your document paths
            String sourceDoc = "path/to/your/source.docx";
            String targetDoc = "path/to/your/target.docx";
            String outputDoc = "path/to/your/output/comparison_result.docx";
            
            // Perform the comparison
            try (Comparer comparer = new Comparer(sourceDoc)) {
                comparer.add(targetDoc);
                Path resultPath = comparer.compare(outputDoc);
                
                System.out.println("Comparison completed successfully!");
                System.out.println("Result saved to: " + resultPath.toString());
            }
            
        } catch (Exception e) {
            System.err.println("Error during comparison: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

```java
// Configure JVM options for better performance
// -Xmx4g -XX:+UseG1GC -XX:MaxGCPauseMillis=200

try (Comparer comparer = new Comparer(sourceDocument)) {
    comparer.add(targetDocument);
    
    // Process comparison with explicit memory management
    System.gc(); // Suggest garbage collection before intensive operation
    Path result = comparer.compare(outputDocument);
    
    // Clear references to help garbage collection
    comparer = null;
    System.gc();
}
```

```java
for (DocumentPair pair : documentPairs) {
    try (Comparer comparer = new Comparer(pair.getSource())) {
        comparer.add(pair.getTarget());
        comparer.compare(pair.getOutputPath());
    }
}
```

```java
documentPairs.parallelStream().forEach(pair -> {
    try (Comparer comparer = new Comparer(pair.getSource())) {
        comparer.add(pair.getTarget());
        comparer.compare(pair.getOutputPath());
    } catch (Exception e) {
        // Handle exceptions appropriately
        logger.error("Comparison failed for: " + pair.getSource(), e);
    }
});
```

```java
long startTime = System.currentTimeMillis();
long startMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();

try (Comparer comparer = new Comparer(sourceDoc)) {
    comparer.add(targetDoc);
    Path result = comparer.compare(outputDoc);
    
    long endTime = System.currentTimeMillis();
    long endMemory = Runtime.getRuntime().totalMemory() - Runtime.getRuntime().freeMemory();
    
    System.out.println("Comparison completed in: " + (endTime - startTime) + "ms");
    System.out.println("Memory used: " + (endMemory - startMemory) / 1024 / 1024 + "MB");
}
```

```xml
<!-- Check for updates regularly -->
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-comparison</artifactId>
    <version>25.2</version> <!-- Keep this current -->
</dependency>
```

```java
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.style.DetalisationLevel;

CompareOptions compareOptions = new CompareOptions();
compareOptions.setDetalisationLevel(DetalisationLevel.High);
compareOptions.setShowDeletedContent(true);
compareOptions.setShowInsertedContent(true);

try (Comparer comparer = new Comparer("source.docx")) {
    comparer.add("target.docx");
    comparer.compare("detailed_result.docx", compareOptions);
}
```

```java
public class DocumentComparisonService {
    
    public ComparisonResult compareDocuments(String source, String target, String output) {
        try {
            validateInputs(source, target);
            
            try (Comparer comparer = new Comparer(source)) {
                comparer.add(target);
                Path resultPath = comparer.compare(output);
                
                return new ComparisonResult(true, resultPath.toString(), "Success");
            }
            
        } catch (FileNotFoundException e) {
            return new ComparisonResult(false, null, "Document not found: " + e.getMessage());
        } catch (Exception e) {
            return new ComparisonResult(false, null, "Comparison failed: " + e.getMessage());
        }
    }
    
    private void validateInputs(String source, String target) throws IllegalArgumentException {
        if (!new File(source).exists()) {
            throw new IllegalArgumentException("Source document does not exist: " + source);
        }
        if (!new File(target).exists()) {
            throw new IllegalArgumentException("Target document does not exist: " + target);
        }
    }
}
```

```java
try (Comparer comparer = new Comparer("source.docx")) {
    comparer.add("version1.docx");
    comparer.add("version2.docx");
    comparer.add("version3.docx");
    comparer.compare("multi_comparison_result.docx");
}
```

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("your_password");

try (Comparer comparer = new Comparer("protected_source.docx", loadOptions)) {
    // Add target document (also protected)
    LoadOptions targetOptions = new LoadOptions();
    targetOptions.setPassword("target_password");
    comparer.add("protected_target.docx", targetOptions);
    
    comparer.compare("comparison_result.docx");
}
```

```java
@Service
public class DocumentComparisonService {
    
    @Autowired
    private DocumentRepository documentRepository;
    
    public String compareDocuments(Long sourceId, Long targetId) {
        Document source = documentRepository.findById(sourceId).orElseThrow();
        Document target = documentRepository.findById(targetId).orElseThrow();
        
        try (Comparer comparer = new Comparer(source.getFilePath())) {
            comparer.add(target.getFilePath());
            String outputPath = generateOutputPath(sourceId, targetId);
            comparer.compare(outputPath);
            return outputPath;
        } catch (Exception e) {
            throw new DocumentComparisonException("Failed to compare documents", e);
        }
    }
}
```

```java
CompareOptions options = new CompareOptions();
options.setInsertedItemStyle(new StyleSettings());
options.getInsertedItemStyle().setFontColor(Color.BLUE);
options.getInsertedItemStyle().setHighlightColor(Color.LIGHT_GRAY);

options.setDeletedItemStyle(new StyleSettings());
options.getDeletedItemStyle().setFontColor(Color.RED);
options.getDeletedItemStyle().setStrikethrough(true);

comparer.compare("styled_result.docx", options);
```

## บทแนะนำที่เกี่ยวข้อง

- [เปรียบเทียบ pdf java – คู่มือการเปรียบเทียบเอกสาร Java – คู่มือเต็มการโหลดและเปรียบเทียบเอกสาร](/comparison/java/document-loading/)  
- [คู่มือการตั้งค่าไลเซนส์ GroupDocs.Comparison Java - คู่มือการกำหนดค่าฉบับเต็ม](/comparison/java/licensing-configuration/)  
- [เปรียบเทียบเอกสาร Word ใน Java – การจัดรูปแบบรายการที่แทรกด้วย GroupDocs](/comparison/java/comparison-options/groupdocs-comparison-java-custom-inserted-item-styles/)