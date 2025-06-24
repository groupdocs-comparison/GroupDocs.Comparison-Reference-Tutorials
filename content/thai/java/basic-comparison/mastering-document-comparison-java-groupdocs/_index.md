---
"date": "2025-05-05"
"description": "เรียนรู้วิธีการเปรียบเทียบเอกสารอย่างแม่นยำด้วย GroupDocs.Comparison สำหรับ Java ปรับแต่งรูปแบบ ปรับความไว และละเว้นส่วนหัว/ส่วนท้ายได้อย่างง่ายดาย"
"title": "การเปรียบเทียบเอกสารหลักใน Java โดยใช้ GroupDocs.Comparison API"
"url": "/th/java/basic-comparison/mastering-document-comparison-java-groupdocs/"
"weight": 1
---

# เรียนรู้การเปรียบเทียบเอกสารใน Java โดยใช้ GroupDocs.Comparison API

## การแนะนำ

เบื่อกับการเปรียบเทียบเอกสารด้วยตนเองหรือไม่ ไม่ว่าจะเป็นการระบุการเปลี่ยนแปลงในส่วนหัว ส่วนท้าย หรือเนื้อหา การเปรียบเทียบเอกสารอาจเป็นงานที่น่ากังวล ไลบรารี GroupDocs.Comparison สำหรับ Java จะทำให้กระบวนการนี้เป็นอัตโนมัติและปรับปรุงอย่างแม่นยำและง่ายดาย

บทช่วยสอนที่ครอบคลุมนี้จะแนะนำคุณเกี่ยวกับการใช้ประโยชน์จาก GroupDocs.Comparison ใน Java เพื่อปรับแต่งรูปแบบการเปรียบเทียบเอกสาร ปรับการตั้งค่าความไว ละเว้นการเปรียบเทียบส่วนหัว/ส่วนท้าย ตั้งค่าขนาดกระดาษเอาต์พุต และอื่นๆ อีกมากมาย เมื่ออ่านคู่มือนี้จบ คุณจะสามารถปรับกระบวนการทำงานของคุณให้มีประสิทธิภาพมากขึ้น

**สิ่งที่คุณจะได้เรียนรู้:**
- ละเว้นส่วนหัวและส่วนท้ายในระหว่างการเปรียบเทียบเอกสาร
- ปรับแต่งการเปลี่ยนแปลงด้วยการปรับปรุงสไตล์
- ปรับความไวในการเปรียบเทียบเพื่อการวิเคราะห์โดยละเอียด
- ตั้งค่าขนาดกระดาษเอาต์พุตในแอปพลิเคชัน Java
- นำคุณสมบัติเหล่านี้ไปใช้ในสถานการณ์โลกแห่งความเป็นจริง

ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นที่จำเป็นก่อนที่จะลงลึกไปสู่ประเด็นเชิงปฏิบัติ

## ข้อกำหนดเบื้องต้น

หากต้องการเริ่มต้นใช้งาน GroupDocs.Comparison สำหรับ Java โปรดแน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. **ชุดพัฒนา Java (JDK):** ตรวจสอบให้แน่ใจว่าได้ติดตั้ง JDK ไว้ในเครื่องของคุณแล้ว เวอร์ชันใดๆ ก็ตามที่สูงกว่า 8 ก็เพียงพอแล้ว
2. **เมเวน:** บทช่วยสอนนี้ถือว่าคุณกำลังใช้ Maven ในการจัดการการอ้างอิงของโครงการ
3. **ไลบรารีการเปรียบเทียบ GroupDocs:**
   - เพิ่มการอ้างอิงต่อไปนี้ให้กับของคุณ `pom.xml`-

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
4. **ใบอนุญาต:** รับรุ่นทดลองใช้งานฟรี ใบอนุญาตชั่วคราว หรือซื้อเวอร์ชันเต็มจาก GroupDocs

เมื่อตั้งค่าเหล่านี้เสร็จเรียบร้อยแล้ว คุณก็พร้อมที่จะเริ่มต้นใช้งานคุณลักษณะการเปรียบเทียบเอกสารในแอปพลิเคชัน Java ของคุณได้

## การตั้งค่า GroupDocs.Comparison สำหรับ Java

ตรวจสอบให้แน่ใจว่าสภาพแวดล้อมของเราได้รับการกำหนดค่าอย่างถูกต้อง:

### การติดตั้งผ่าน Maven

เพิ่มโค้ด XML ข้างต้นลงในโครงการของคุณ `pom.xml`ขั้นตอนนี้จะช่วยให้แน่ใจว่า Maven รู้จักที่เก็บข้อมูลและการอ้างอิงที่จำเป็น 

### การขอใบอนุญาต
- **ทดลองใช้งานฟรี:** ดาวน์โหลดเวอร์ชันทดลองใช้ได้จาก [ดาวน์โหลด GroupDocs](https://releases-groupdocs.com/comparison/java/).
- **ใบอนุญาตชั่วคราว:** ขอใบอนุญาตชั่วคราวผ่าน [การสนับสนุน GroupDocs](https://purchase.groupdocs.com/temporary-license/) เพื่อประเมินคุณสมบัติครบถ้วน
- **ซื้อ:** สำหรับการใช้งานระยะยาว ให้ซื้อใบอนุญาตผ่าน [การซื้อ GroupDocs](https://purchase-groupdocs.com/buy).

หลังจากได้รับและตั้งค่าไฟล์ใบอนุญาตตามเอกสาร GroupDocs แล้ว ให้เริ่มต้น GroupDocs.Comparison ดังต่อไปนี้:

```java
// ตัวอย่างการเริ่มต้นขั้นพื้นฐาน
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

## คู่มือการใช้งาน

### คุณสมบัติ 1: ละเว้นการเปรียบเทียบส่วนหัว/ส่วนท้าย

**ภาพรวม:** ส่วนหัวและส่วนท้ายมักประกอบด้วยข้อมูล เช่น หมายเลขหน้าหรือชื่อเอกสาร ซึ่งอาจไม่เกี่ยวข้องกับการเปรียบเทียบการเปลี่ยนแปลงเนื้อหา

#### การตั้งค่าตัวเลือก

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import java.io.FileOutputStream;

public class IgnoreHeaderFooterExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/IgnoreHeaderFooter_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_with_footer.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target_with_footer.docx");

            // ตั้งค่าตัวเลือกการเปรียบเทียบเพื่อละเว้นส่วนหัวและส่วนท้าย
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

#### คำอธิบาย
- **`CompareOptions.Builder().setHeaderFootersComparison(false)`**การตั้งค่านี้จะสั่งให้ไลบรารีข้ามการเปรียบเทียบส่วนหัวและส่วนท้าย
- **`try-with-resources`-** ช่วยให้แน่ใจว่าน้ำทุกสายปิดอย่างถูกต้องหลังใช้งาน

### คุณสมบัติ 2: ตั้งค่าขนาดกระดาษเอาท์พุต

**ภาพรวม:** การปรับแต่งขนาดกระดาษเอาต์พุตเป็นสิ่งสำคัญสำหรับการสร้างเอกสารที่พิมพ์ได้ ต่อไปนี้คือวิธีปรับแต่งระหว่างการเปรียบเทียบเอกสาร

#### ขั้นตอนการดำเนินการ

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.PaperSize;

public class SetOutputPaperSizeExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetOutputPaperSize_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // ตั้งค่าขนาดกระดาษเป็น A6
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### คำอธิบาย
- **`CompareOptions.Builder().setPaperSize(PaperSize.A6)`**: ตั้งค่าขนาดกระดาษเอาต์พุตเป็น A6

### คุณสมบัติที่ 3: ปรับความไวในการเปรียบเทียบ

**ภาพรวม:** การปรับความไวในการเปรียบเทียบให้ละเอียดจะช่วยให้ระบุการเปลี่ยนแปลงแม้เพียงเล็กน้อยได้ ต่อไปนี้คือวิธีปรับแต่ง:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // ตั้งค่าความไวเป็น 100
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### คำอธิบาย
- **`CompareOptions.Builder().setSensitivityOfComparison(100)`**: ปรับระดับความไวในการตรวจจับการเปลี่ยนแปลง

### คุณลักษณะที่ 4: ปรับแต่งรูปแบบการเปลี่ยนแปลง (โดยใช้สตรีม)

**ภาพรวม:** การแยกความแตกต่างระหว่างข้อความที่แทรก ลบ และเปลี่ยนแปลงทำให้การเปรียบเทียบมีความชัดเจนมากขึ้น ต่อไปนี้คือวิธีปรับแต่งรูปแบบโดยใช้สตรีม:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.save.SaveOptions;
import com.groupdocs.comparison.options.style.StyleSettings;

import java.awt.Color;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class CustomizeChangesStylesStreamExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CustomizeChangesStylesStream_result.docx";

        try (InputStream sourceFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source_word.docx");
             InputStream targetFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer(sourceFile)) {

            comparer.add(targetFile);

            // ปรับแต่งรูปแบบการเปลี่ยนแปลง
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // สีเขียวสำหรับการแทรก
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // สีแดงสำหรับการลบ
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // สีฟ้าเพื่อการเปลี่ยนแปลง

            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setInsertedItemStyle(insertedStyle)
                    .setDeletedItemStyle(deletedStyle)
                    .setChangedItemStyle(changedStyle)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### คำอธิบาย
- **การตั้งค่ารูปแบบที่กำหนดเอง**: ใช้ `StyleSettings` เพื่อกำหนดสีเน้นสำหรับการแทรก (สีเขียว) การลบ (สีแดง) และการเปลี่ยนแปลง (สีน้ำเงิน)
- **`CompareOptions.Builder()`-** ใช้รูปแบบเหล่านี้ในระหว่างกระบวนการเปรียบเทียบ

## บทสรุป

การใช้ประโยชน์จาก GroupDocs.Comparison สำหรับ Java ช่วยให้คุณสามารถเปรียบเทียบเอกสารได้อย่างแม่นยำและอัตโนมัติ บทช่วยสอนนี้ครอบคลุมถึงการละเว้นส่วนหัว/ส่วนท้าย การกำหนดขนาดกระดาษเอาต์พุต การปรับความไว และการปรับแต่งรูปแบบการเปลี่ยนแปลง การนำคุณลักษณะเหล่านี้ไปใช้จะปรับปรุงเวิร์กโฟลว์ของคุณและปรับปรุงการวิเคราะห์เอกสารในแอปพลิเคชัน Java

## คำถามที่พบบ่อย

### 1. ฉันสามารถละเว้นส่วนหัวและส่วนท้ายในระหว่างการเปรียบเทียบใน GroupDocs สำหรับ Java ได้หรือไม่  

ใช่ครับ ใช้ `setHeaderFootersComparison(false)` ใน `CompareOptions` เพื่อแยกส่วนหัวและส่วนท้ายออกจากการเปรียบเทียบ

### 2. ฉันจะตั้งค่าขนาดกระดาษเอาต์พุตใน Java โดยใช้ GroupDocs ได้อย่างไร  

นำมาใช้ `setPaperSize(PaperSize.A6)` หรือขนาดอื่นๆใน `CompareOptions` เพื่อปรับขนาดกระดาษของเอกสารขั้นสุดท้าย

### 3. สามารถปรับแต่งความไวในการเปรียบเทียบได้หรือไม่  

ใช่ครับ ใช้ `setSensitivityOfComparison()` ใน `CompareOptions` เพื่อปรับความไวในการตรวจจับการเปลี่ยนแปลงเล็กน้อยหรือใหญ่ตามความเหมาะสม

### 4. ฉันสามารถกำหนดรูปแบบข้อความที่แทรก ลบ และเปลี่ยนแปลงระหว่างการเปรียบเทียบได้หรือไม่  

แน่นอน ปรับแต่งสไตล์ผ่าน `StyleSettings` สำหรับประเภทการเปลี่ยนแปลงที่แตกต่างกันและนำไปใช้ใน `CompareOptions`-

### 5. ข้อกำหนดเบื้องต้นในการเริ่มต้นใช้งานการเปรียบเทียบ GroupDocs ใน Java มีอะไรบ้าง  

ติดตั้ง JDK จัดการการอ้างอิงด้วย Maven รับใบอนุญาต และเพิ่มไลบรารี GroupDocs.Comparison ลงในโปรเจ็กต์ของคุณ