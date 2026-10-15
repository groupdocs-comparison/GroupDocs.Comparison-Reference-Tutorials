---
categories:
- Java Development
date: '2026-10-15'
description: เรียนรู้วิธีตั้งสตรีมใบอนุญาต GroupDocs ใน Java ด้วยผู้จัดการศูนย์กลาง
  พร้อมคำแนะนำทีละขั้นตอน การแก้ไขปัญหา และแนวปฏิบัติที่ดีที่สุดสำหรับปี 2026
keywords:
- set groupdocs license stream
- centralized license manager
- stream‑based licensing
- GroupDocs Java licensing
lastmod: '2026-10-15'
linktitle: บทแนะนำการใช้งานใบอนุญาต GroupDocs สำหรับ Java
og_description: ตั้งสตรีมใบอนุญาต GroupDocs ใน Java ด้วยผู้จัดการศูนย์กลาง ปฏิบัติตามคู่มือปี
  2026 นี้เพื่อการให้สิทธิ์ที่ปลอดภัยและเป็นมิตรกับคอนเทนเนอร์ รวมถึงการแก้ไขปัญหา
og_image_alt: Guide showing Java code for loading GroupDocs license from a stream
og_title: วิธีตั้งสตรีมใบอนุญาต GroupDocs ใน Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-15'
  description: Learn how to set GroupDocs license stream in Java with a centralized
    manager, including troubleshooting and best practices.
  headline: How to set GroupDocs license stream in Java
  type: TechArticle
- description: Learn how to set GroupDocs license stream in Java with a centralized
    manager, including troubleshooting and best practices.
  name: How to set GroupDocs license stream in Java
  steps:
  - name: Verify license file integrity
    text: Check that the XML is well‑formed and matches the license you purchased.
      A corrupted file will raise a `LicenseException`.
  - name: Debug stream creation
    text: Print the size of the byte array (`licenseBytes.length`) before passing
      it to `setLicense()`; a size of zero indicates an empty stream.
  - name: Test license application
    text: Run a simple comparison task after loading the license. If the output contains
      watermarks, the license was not applied correctly.
  type: HowTo
- questions:
  - answer: No. Once a stream is read, it’s exhausted. Create a fresh stream each
      time or cache the raw byte array and wrap it in a new `ByteArrayInputStream`.
    question: Can I use the same license stream multiple times?
  - answer: GroupDocs runs in evaluation mode, inserting watermarks and limiting the
      number of processed pages.
    question: What happens if I don’t set a license?
  - answer: Yes. By loading the license directly from memory you avoid leaving a readable
      file on disk, which mitigates accidental exposure.
    question: Is stream‑based licensing more secure than file‑based?
  - answer: Absolutely. Call `LicenseManager.setLicense(newStream)` whenever you need
      to change the active license—for example, per‑tenant or per‑feature licensing.
    question: Can I switch licenses at runtime?
  - answer: Each node must load the license independently. Use a shared configuration
      service (Consul, Spring Cloud Config) or environment variables so every instance
      receives the same license data.
    question: How do I handle licensing in a clustered environment?
  type: FAQPage
tags:
- groupdocs
- java-licensing
- document-processing
- stream-api
- license-management
title: วิธีตั้งสตรีมใบอนุญาต GroupDocs ใน Java
type: docs
url: /th/java/licensing-configuration/set-groupdocs-license-stream-java-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้งสตรีมใบอนุญาต GroupDocs ใน Java

หากคุณกำลังบูรณาการ **GroupDocs.Comparison for Java** เข้ากับแอปพลิเคชันสมัยใหม่ วิธีที่เชื่อถือได้ที่สุดในการจัดการใบอนุญาตคือด้วย **centralized license manager** ที่ทำงานกับ Java streams วิธีนี้ช่วยให้คุณโหลดใบอนุญาตจากไฟล์, แหล่งทรัพยากรใน classpath, URL, หรือ vault ที่ปลอดภัย—โดยกำจัดเส้นทางที่กำหนดไว้ล่วงหน้าและเพิ่มความปลอดภัย.

## คำตอบอย่างรวดเร็ว
- **What is a centralized license manager?** เป็นคอมโพเนนต์ที่ใช้ซ้ำได้ซึ่งโหลดและใช้ใบอนุญาต GroupDocs สำหรับแอปพลิเคชันทั้งหมด โดยปกติเป็น singleton หรือ Spring bean.  
- **Why use streams for licensing?** Streams ทำให้คุณอ่านใบอนุญาตจากแหล่งใดก็ได้ (ไฟล์, classpath, URL, vault) โดยไม่ต้องบันทึกลงดิสก์ ซึ่งเพิ่มความปลอดภัยและความเข้ากันได้กับคอนเทนเนอร์.  
- **When should I switch from file‑based to stream‑based?** ทุกครั้งที่คุณทำการ deploy ไปยัง Docker, Kubernetes หรือสภาพแวดล้อมคลาวด์ใด ๆ ที่การเมานท์ไฟล์ไม่สะดวก.  
- **How do I avoid memory leaks?** ห่อ InputStream ด้วยบล็อก try‑with‑resources หรือปิดอย่างชัดเจนหลังจากเรียก `setLicense()`.  
- **Can I change the license at runtime?** ใช่—เรียก `setLicense()` พร้อมสตรีมใหม่เมื่อคุณต้องการสลับใบอนุญาตสำหรับ tenant หรือชุดฟีเจอร์.

## ตัวจัดการใบอนุญาตแบบศูนย์กลางคืออะไร?
A **centralized license manager** คือคลาสหรือเซอร์วิสเดียวที่บรรจุตรรกะทั้งหมดสำหรับการโหลด, การใช้, และการรีเฟรชใบอนุญาต GroupDocs โดยการเก็บตรรกะนี้ไว้ในที่เดียว คุณจะกำจัดโค้ดซ้ำซ้อน, ทำให้การเปลี่ยนแปลงการกำหนดค่าง่ายขึ้น, และรับประกันว่าทุกส่วนของแอปพลิเคชันใช้ใบอนุญาตที่ถูกต้องเดียวกัน.

## ทำไมต้องเลือกการให้ใบอนุญาตแบบสตรีม?
การใช้สตรีมเพื่อโหลดใบอนุญาต GroupDocs ให้ประโยชน์หลายประการเมื่อเทียบกับวิธีการใช้ไฟล์‑พาธแบบคลาสสิก มันแยกตำแหน่งของใบอนุญาตออกจากแอปพลิเคชัน, เปิดใช้งานการจัดการในหน่วยความจำอย่างปลอดภัย, ทำงานได้อย่างราบรื่นในสภาพแวดล้อมคอนเทนเนอร์, และอนุญาตให้เปลี่ยนใบอนุญาตแบบไดนามิกใน runtime ซึ่งทั้งหมดนี้ช่วยเพิ่มความยืดหยุ่น, ความปลอดภัย, และความสามารถในการขยาย.

## ข้อกำหนดเบื้องต้นและการตั้งค่าสภาพแวดล้อม

### ไลบรารีและเวอร์ชันที่ต้องการ
- **GroupDocs.Comparison for Java** – เวอร์ชัน **25.2** หรือใหม่กว่า (รุ่นล่าสุด 2026).  
- **Java Development Kit (JDK)** – เวอร์ชัน **8+** (แนะนำ JDK 11+ เพื่อการสนับสนุนโมดูลที่ดีกว่า).  
- **Maven หรือ Gradle** – สำหรับการจัดการ dependencies (ตัวอย่างด้านล่างใช้ Maven).

### การกำหนดค่า Maven
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

### การรับใบอนุญาตของคุณ
1. **Start with the free trial** – คุณจะได้รับการเข้าถึง API เต็มรูปแบบเป็นเวลา 30 วัน.  
2. **Request a temporary license** – เหมาะสำหรับการประเมินระยะยาวใน pipeline ของ CI.  
3. **Purchase a production license** – จำเป็นสำหรับการใช้งานเชิงพาณิชย์และจะลบลายน้ำการประเมินออก.

*Pro tip*: เก็บสตริงใบอนุญาตดิบใน secret manager (AWS Secrets Manager, Azure Key Vault, HashiCorp Vault) และดึงมาใช้ใน runtime. วิธีนี้ทำให้ใบอนุญาตไม่อยู่ใน source control และระบบไฟล์.

## ตรวจสอบแหล่งที่มาของใบอนุญาต
ก่อนที่คุณจะสร้างสตรีม, ตรวจสอบให้แน่ใจว่าแหล่งที่คุณตั้งใจอ่านสามารถเข้าถึงได้ ไฟล์ที่หายไปหรือ URL ที่ไม่สามารถเข้าถึงได้เป็นสาเหตุที่พบบ่อยที่สุดของข้อผิดพลาดใบอนุญาต.

```java
if (new File("YOUR_DOCUMENT_DIRECTORY/LicensePath.lic").exists()) {
    // Proceed to create an input stream
} else {
    System.out.println("License file does not exist. Please obtain a license from GroupDocs.");
}
```

> **Why this matters** – การตรวจจับแหล่งที่หายไปตั้งแต่ต้นจะป้องกันข้อผิดพลาด `LicenseException` ใน runtime ที่อาจทำให้การประมวลผลเอกสารถูกหยุด.

## สร้าง InputStream อย่างถูกต้อง
`InputStream` คือคลาสแอ็บสแตรกต์ของ Java ที่เป็นตัวแทนของแหล่งไบต์สำหรับอ่านข้อมูล.

คุณสามารถแปลงแหล่งต่าง ๆ ให้เป็น `InputStream` ได้หลายแบบ:

```java
InputStream stream = new FileInputStream(new File("YOUR_DOCUMENT_DIRECTORY/LicensePath.lic"));
try {
    // Initialize a License object
} finally {
    if (stream != null) {
        stream.close();
    }
}
```

**ตัวเลือกทั่วไป**
- **Classpath resource** – `getClass().getResourceAsStream("/licenses/my-license.lic")`  
- **Byte array** – `new ByteArrayInputStream(licenseBytes)`  
- **Remote URL** – `new URL("https://secure.mycompany.com/license").openStream()`

แต่ละรายการจะคืนสตรีมใหม่ที่สามารถส่งต่อโดยตรงให้กับอ็อบเจ็กต์ `License` ของ GroupDocs.

## ใช้ใบอนุญาต
`License` คือคลาสของ GroupDocs ที่รับผิดชอบการโหลดและใช้ใบอนุญาตกับ SDK.

```java
try {
    License license = new License();
    license.setLicense(stream);
} catch (Exception e) {
    System.out.println("Failed to set license: " + e.getMessage());
}
```

> **Important** – `setLicense()` ใช้สตรีมทั้งหมด, ดังนั้นสตรีมต้องอยู่ที่ตำแหน่งเริ่มต้นทุกครั้งที่เรียกใช้. การใช้สตรีมเดียวกันที่หมดแล้วซ้ำจะทำให้เกิดข้อผิดพลาด “License file is empty”.

## การจัดการทรัพยากร (สำคัญ!)
ห้ามปล่อยให้สตรีมค้างอยู่ในหน่วยความจำ. ในบริการที่ทำงานต่อเนื่องเป็นเวลานาน, สตรีมที่ไม่ได้ปิดอาจทำให้เกิดความกดดันหน่วยความจำอย่างละเอียดและในที่สุดทำให้เกิด `OutOfMemoryError`.

```java
finally {
    if (stream != null) {
        try {
            stream.close();
        } catch (IOException e) {
            // Log the exception but don't let it mask other issues
            System.err.println("Warning: Failed to close license stream: " + e.getMessage());
        }
    }
}
```

## การสร้างตัวจัดการใบอนุญาตแบบศูนย์กลาง
`LicenseManager` คือคลาสยูทิลิตี้ที่กำหนดเองซึ่งบรรจุการโหลดและตั้งค่าใบอนุญาต GroupDocs.

คลาส `LicenseManager` เป็น wrapper ที่บางเบาซึ่งรวมศูนย์การดำเนินการใบอนุญาตทั้งหมด, เปิดเผยเมธอด `initializeLicense()` หนึ่งเมธอดสำหรับการเริ่มต้นแอปพลิเคชันและเมธอด `setLicense(InputStream stream)` สำหรับการเปลี่ยนแปลงใน runtime.

```java
public class LicenseManager {
    private static volatile boolean licenseSet = false;
    
    public static synchronized void initializeLicense() {
        if (!licenseSet) {
            // Your stream‑based license setup here
            licenseSet = true;
        }
    }
}
```

> **Tip** – เรียก `LicenseManager.initializeLicense()` หนึ่งครั้งระหว่างการเริ่มต้นแอปพลิเคชัน (เช่นใน `ServletContextListener`, Spring `@PostConstruct`, หรือเมธอด `main()`). ส่วนประกอบต่อมาสามารถพึ่งพาใบอนุญาตที่เปิดใช้งานอยู่แล้วได้อย่างง่ายดาย.

## ข้อผิดพลาดทั่วไปและวิธีแก้

### ปัญหา 1: “ไม่พบไฟล์ใบอนุญาต”
**Cause** – ความแตกต่างของไดเรกทอรีทำงานระหว่าง IDE, CI, และคอนเทนเนอร์การผลิต.  
**Fix** – ควรใช้เส้นทางแบบ absolute หรือแหล่งทรัพยากรใน classpath, และบันทึกเส้นทางที่แก้ไขแล้วสำหรับการดีบัก.

```java
InputStream stream = getClass().getClassLoader().getResourceAsStream("licenses/license.lic");
```

### ปัญหา 2: การรั่วไหลของหน่วยความจำจากสตรีมที่ไม่ได้ปิด
**Fix** – ใช้ try‑with‑resources ของ Java (มีตั้งแต่ Java 7) เพื่อรับประกันการปิด.

```java
try (InputStream stream = new FileInputStream(licenseFile)) {
    License license = new License();
    license.setLicense(stream);
} catch (Exception e) {
    // Handle licensing errors
}
```

### ปัญหา 3: รูปแบบใบอนุญาตไม่ถูกต้อง
**Fix** – ตรวจสอบว่าไฟล์เข้ารหัสเป็น UTF‑8 และมีโครงสร้าง XML ที่ตรงกับที่ GroupDocs ให้มา. เมื่อสร้างสตรีมจาก `String`, ห่อด้วย `new ByteArrayInputStream(str.getBytes(StandardCharsets.UTF_8))`.

```java
byte[] licenseBytes = licenseString.getBytes(StandardCharsets.UTF_8);
InputStream stream = new ByteArrayInputStream(licenseBytes);
```

## แนวทางปฏิบัติที่ดีที่สุดสำหรับแอปพลิเคชันการผลิต
1. **Centralize all licensing code** – เก็บไว้ในคลาส `LicenseManager` เดียวเพื่อหลีกเลี่ยงการซ้ำซ้อน.  
2. **Environment‑specific configuration** – ใช้ environment variables ใน dev, vault ที่ปลอดภัยใน prod, และ CI secrets สำหรับการทดสอบอัตโนมัติ.  
3. **Graceful degradation** – บันทึกข้อผิดพลาดการให้ใบอนุญาตและอาจกลับไปใช้โหมดประเมินพร้อมคำเตือนที่ชัดเจนต่อผู้ใช้.  
4. **Cache the license** – หลังจากโหลดสำเร็จครั้งแรก, เก็บ byte array ในหน่วยความจำเพื่อหลีกเลี่ยง I/O ซ้ำในแต่ละคำขอ.

## สถานการณ์การใช้งานจริง

### สถานการณ์ 1: สถาปัตยกรรมไมโครเซอร์วิส
```java
// Retrieve license from config service
String licenseData = configService.getLicense();
byte[] licenseBytes = Base64.getDecoder().decode(licenseData);
InputStream stream = new ByteArrayInputStream(licenseBytes);
```

แต่ละไมโครเซอร์วิสโหลดใบอนุญาตจาก secret store ที่แชร์ในช่วง bootstrap, ทำให้การให้ใบอนุญาตสอดคล้องกันทั่ว mesh โดยไม่ต้องพึ่งพาไฟล์ระบบ.

### สถานการณ์ 2: แอปพลิเคชันหลาย tenant
```java
public void setTenantLicense(String tenantId) {
    InputStream licenseStream = licenseRepository.getLicenseStream(tenantId);
    // Apply tenant‑specific license
}
```

ใบอนุญาตเฉพาะ tenant สามารถดึงจากตารางฐานข้อมูล, แปลงเป็นสตรีม, และใช้ทันทีก่อนประมวลผลเอกสารสำหรับ tenant นั้น.

### สถานการณ์ 3: พายไลน์การทดสอบอัตโนมัติ
```java
@BeforeEach
void setupTestLicense() {
    InputStream testLicense = getClass().getResourceAsStream("/test-licenses/temp-license.lic");
    License license = new License();
    license.setLicense(testLicense);
}
```

พายไลน์ CI ดึงใบอนุญาตจาก environment variable ที่เข้ารหัส, ใช้ครั้งเดียวต่อการรันทดสอบ, แล้วทิ้งสำเนาในหน่วยความจำ, ทำให้สภาพแวดล้อม CI สะอาด.

## การพิจารณาประสิทธิภาพและการปรับแต่ง
- **Cache the license** หลังจากโหลดครั้งแรก; การเรียก `setLicense()` ต่อไปสามารถใช้ byte array ที่แคชไว้, ลดความล่าช้าของดิสก์หรือเครือข่าย.  
- **Use buffered streams** (`BufferedInputStream`) เมื่ออ่านไฟล์ใบอนุญาตขนาดใหญ่จาก URL ระยะไกลเพื่อ ลดภาระ I/O.  
- **Set the license early** (เช่นใน `static` initializer) เพื่อให้การประมวลผลเอกสารเริ่มต้นด้วยใบอนุญาตที่ถูกต้อง, ป้องกันค่าใช้จ่ายครั้งเดียวเล็กน้อยในคำขอแรก.

### ลอจิกการลองใหม่สำหรับแหล่งเครือข่าย
```java
int maxRetries = 3;
for (int i = 0; i < maxRetries; i++) {
    try {
        // Attempt license setup
        break;
    } catch (Exception e) {
        if (i == maxRetries - 1) throw e;
        Thread.sleep(1000 * (i + 1));
    }
}
```

ใช้ exponential back‑off เมื่อดึงใบอนุญาตจาก endpoint ระยะไกล. วิธีนี้ป้องกันข้อบกพร่องเครือข่ายชั่วคราวจากการทำให้บริการล่ม.

## คู่มือแก้ไขปัญหา

### ขั้นตอน 1: ตรวจสอบความสมบูรณ์ของไฟล์ใบอนุญาต
```java
System.out.println("License file exists: " + licenseFile.exists());
System.out.println("License file size: " + licenseFile.length() + " bytes");
System.out.println("Can read file: " + licenseFile.canRead());
```

ตรวจสอบว่า XML มีรูปแบบที่ถูกต้องและตรงกับใบอนุญาตที่คุณซื้อ. ไฟล์ที่เสียหายจะทำให้เกิด `LicenseException`.

### ขั้นตอน 2: ดีบักการสร้างสตรีม
```java
// Add logging to understand what's happening
System.out.println("License file exists: " + licenseFile.exists());
System.out.println("License file size: " + licenseFile.length() + " bytes");
System.out.println("Can read file: " + licenseFile.canRead());
```

พิมพ์ขนาดของ byte array (`licenseBytes.length`) ก่อนส่งให้ `setLicense()`; ขนาดเป็นศูนย์บ่งบอกสตรีมว่าง.

### ขั้นตอน 3: ทดสอบการใช้ใบอนุญาต
```java
try {
    License license = new License();
    license.setLicense(stream);
    System.out.println("License applied successfully");
} catch (Exception e) {
    System.err.println("License application failed: " + e.getClass().getSimpleName() + " - " + e.getMessage());
    e.printStackTrace();
}
```

รันงานเปรียบเทียบง่ายหลังจากโหลดใบอนุญาต. หากผลลัพธ์มีลายน้ำ, แสดงว่าใบอนุญาตไม่ได้ถูกใช้อย่างถูกต้อง.

## คำถามที่พบบ่อย

**Q: ฉันสามารถใช้สตรีมใบอนุญาตเดียวกันหลายครั้งได้หรือไม่?**  
A: ไม่. เมื่อสตรีมถูกอ่านแล้วจะหมด. สร้างสตรีมใหม่ทุกครั้งหรือแคช byte array ดิบและห่อด้วย `ByteArrayInputStream` ใหม่.

**Q: จะเกิดอะไรขึ้นถ้าฉันไม่ตั้งค่าใบอนุญาต?**  
A: GroupDocs จะทำงานในโหมดประเมิน, แทรกลายน้ำและจำกัดจำนวนหน้าที่ประมวลผล.

**Q: การให้ใบอนุญาตแบบสตรีมปลอดภัยกว่าการใช้ไฟล์หรือไม่?**  
A: ใช่. การโหลดใบอนุญาตโดยตรงจากหน่วยความจำทำให้ไม่ต้องทิ้งไฟล์ที่อ่านได้บนดิสก์, ซึ่งช่วยลดความเสี่ยงจากการเปิดเผยโดยบังเอิญ.

**Q: ฉันสามารถสลับใบอนุญาตใน runtime ได้หรือไม่?**  
A: แน่นอน. เรียก `LicenseManager.setLicense(newStream)` เมื่อคุณต้องการเปลี่ยนใบอนุญาตที่ใช้งานอยู่—เช่นตาม tenant หรือฟีเจอร์.

**Q: ฉันจะจัดการใบอนุญาตในสภาพแวดล้อมคลัสเตอร์อย่างไร?**  
A: แต่ละโหนดต้องโหลดใบอนุญาตแยกกัน. ใช้บริการกำหนดค่าที่แชร์ (Consul, Spring Cloud Config) หรือ environment variables เพื่อให้ทุกอินสแตนซ์ได้รับข้อมูลใบอนุญาตเดียวกัน.

**Q: ผลกระทบต่อประสิทธิภาพของการใช้สตรีมเป็นอย่างไร?**  
A: ไม่สำคัญ. ใบอนุญาตมักตั้งค่าเพียงครั้งเดียวที่เริ่มต้น; การอ่านสตรีมใช้เพียงไม่กี่กิโลไบต์, น้อยกว่ามากเมื่อเทียบกับเมกะไบต์ที่ประมวลผลในขั้นตอนเปรียบเทียบเอกสาร.

## สรุป
คุณมี **centralized license manager** ที่สร้างบน Java streams แล้ว, ให้ความยืดหยุ่น, ความปลอดภัย, และความสามารถในการขยายที่จำเป็นสำหรับการปรับใช้คลาวด์‑เนทีฟสมัยใหม่. ด้วยการทำตามขั้นตอน, แนวปฏิบัติที่ดีที่สุด, และเคล็ดลับการแก้ปัญหาในคู่มือนี้, คุณสามารถใช้ใบอนุญาต GroupDocs อย่างมั่นใจในคอนเทนเนอร์, ไมโครเซอร์วิส, และสถาปัตยกรรมหลาย tenant โดยไม่ต้องเจอปัญหาเส้นทางไฟล์.

## แหล่งข้อมูลเพิ่มเติม
- [เอกสาร GroupDocs.Comparison สำหรับ Java](https://docs.groupdocs.com/comparison/java/)
- [คู่มืออ้างอิง API ฉบับเต็ม](https://reference.groupdocs.com/comparison/java/)
- [การปล่อยเวอร์ชัน GroupDocs](https://releases.groupdocs.com/comparison/java/)
- [ซื้อใบอนุญาต GroupDocs](https://purchase.groupdocs.com/buy)
- [ฟอรั่มชุมชน GroupDocs](https://forum.groupdocs.com/c/comparison)

**อัปเดตล่าสุด:** 2026-10-15  
**ทดสอบด้วย:** GroupDocs.Comparison 25.2 (Java)  
**ผู้เขียน:** GroupDocs  

## บทแนะนำที่เกี่ยวข้อง
- [คู่มือการตั้งค่าใบอนุญาต GroupDocs.Comparison Java - การกำหนดค่าครบถ้วน](/comparison/java/licensing-configuration/)
- [การตั้งค่าใบอนุญาต GroupDocs Comparison Java - คู่มือการกำหนดค่า URL ครบถ้วน](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)
- [วิธีใช้ GroupDocs - สตรีมการเปรียบเทียบเอกสาร Java – คู่มือฉบับเต็ม](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}