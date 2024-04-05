---
title: เปรียบเทียบรูปภาพจากเส้นทาง - GroupDocs.Comparison สำหรับ .NET
linktitle: เปรียบเทียบรูปภาพจากเส้นทาง - GroupDocs.Comparison สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีเปรียบเทียบรูปภาพอย่างมีประสิทธิภาพใน .NET โดยใช้ไลบรารี GroupDocs.Comparison ปฏิบัติตามคำแนะนำทีละขั้นตอนเพื่อการผสานรวมที่ราบรื่น
type: docs
weight: 10
url: /th/net/image-comparison/compare-images-from-path/
---
## การแนะนำ
ในขอบเขตของการพัฒนา .NET ความสามารถในการเปรียบเทียบเอกสารและรูปภาพอย่างมีประสิทธิภาพเป็นสิ่งสำคัญสำหรับแอปพลิเคชันต่างๆ ไม่ว่าจะเป็นการระบุการเปลี่ยนแปลง การตรวจสอบความถูกต้อง หรือการปฏิบัติตามข้อกำหนด นักพัฒนาซอฟต์แวร์ต่างมองหาเครื่องมือที่เชื่อถือได้ซึ่งจะช่วยปรับปรุงกระบวนการเปรียบเทียบให้มีประสิทธิภาพยิ่งขึ้น GroupDocs.Comparison สำหรับ .NET กลายเป็นโซลูชันที่แข็งแกร่ง โดยนำเสนอชุดคุณลักษณะที่ปรับแต่งให้ตอบสนองความต้องการเหล่านี้ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกถึงความซับซ้อนของการใช้ GroupDocs.Comparison สำหรับ .NET โปรดตรวจสอบให้แน่ใจว่ามีคุณสมบัติตรงตามข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Comparison สำหรับ .NET
 ดาวน์โหลดห้องสมุดได้จาก[ที่นี่](https://releases.groupdocs.com/comparison/net/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้ในเอกสารประกอบ[ที่นี่](https://reference.groupdocs.com/comparison/net/).
### 2. รับใบอนุญาต
 หากต้องการปลดล็อกศักยภาพสูงสุดของ GroupDocs.Comparison สำหรับ .NET โปรดขอรับใบอนุญาตจาก[ที่นี่](https://purchase.groupdocs.com/buy) หรือใช้ใบอนุญาตชั่วคราวที่มีอยู่[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### 3. คุ้นเคยกับการเขียนโปรแกรม C#
ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# เป็นสิ่งจำเป็นเพื่อใช้ฟังก์ชันการเปรียบเทียบได้อย่างมีประสิทธิภาพ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Comparison สำหรับ .NET:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

ตอนนี้ เราจะแบ่งตัวอย่างที่ให้ไว้ออกเป็นหลายขั้นตอนเพื่อเปรียบเทียบรูปภาพอย่างมีประสิทธิภาพโดยใช้ GroupDocs.Comparison สำหรับ .NET:
## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.png");
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Directory"` ด้วยเส้นทางไดเร็กทอรีที่ต้องการซึ่งคุณต้องการเก็บผลการเปรียบเทียบ
## ขั้นตอนที่ 2: เริ่มต้นวัตถุ Comparer
```csharp
using (Comparer comparer = new Comparer("SOURCE.png"))
```
 สร้างอินสแตนซ์ใหม่ของ`Comparer`คลาสโดยการจัดเตรียมเส้นทางของอิมเมจต้นฉบับ (`"SOURCE.png"` ในตัวอย่างนี้)
## ขั้นตอนที่ 3: กำหนดค่าตัวเลือกการเปรียบเทียบ
```csharp
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```
 ปรับแต่งตัวเลือกการเปรียบเทียบตามความต้องการของคุณ ในกรณีนี้ เรากำลังตั้งค่า`GenerateSummaryPage` ถึง`false` เพื่อแยกหน้าสรุปออกจากเอาต์พุต
## ขั้นตอนที่ 4: เพิ่มภาพเป้าหมายเพื่อการเปรียบเทียบ
```csharp
comparer.Add("TARGET.png");
```
เพิ่มภาพเป้าหมาย (`"TARGET.png"`) เพื่อเปรียบเทียบกับอิมเมจต้นฉบับ
## ขั้นตอนที่ 5: ทำการเปรียบเทียบและบันทึกผลลัพธ์
```csharp
comparer.Compare(outputFileName, options);
```
ดำเนินการกระบวนการเปรียบเทียบและบันทึกผลลัพธ์ลงในไฟล์เอาต์พุตที่ระบุ (`"RESULT.png"`-
## ขั้นตอนที่ 6: แสดงตำแหน่งเอาต์พุต
```csharp
Console.WriteLine($"\nImages compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
แจ้งให้ผู้ใช้ทราบเกี่ยวกับความสำเร็จของกระบวนการเปรียบเทียบ และระบุตำแหน่งที่บันทึกผลลัพธ์

## บทสรุป
โดยสรุป GroupDocs.Comparison สำหรับ .NET ช่วยให้นักพัฒนามีชุดเครื่องมือที่ครอบคลุมเพื่อการเปรียบเทียบรูปภาพและเอกสารภายในแอปพลิเคชัน .NET ได้อย่างมีประสิทธิภาพ ด้วยการทำตามขั้นตอนที่ระบุไว้และใช้ประโยชน์จากความสามารถของไลบรารีนี้ นักพัฒนาสามารถรวมฟังก์ชันการเปรียบเทียบขั้นสูงเข้ากับโปรเจ็กต์ของตนได้อย่างราบรื่น ช่วยเพิ่มผลผลิตและความแม่นยำ
## คำถามที่พบบ่อย
### GroupDocs.Comparison สำหรับ .NET สามารถเปรียบเทียบเอกสารอื่นที่ไม่ใช่รูปภาพได้หรือไม่
ใช่ GroupDocs.Comparison สำหรับ .NET รองรับการเปรียบเทียบรูปแบบเอกสารต่างๆ รวมถึง Word, Excel, PowerPoint, PDF และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ GroupDocs.Comparison สำหรับ .NET หรือไม่
 ใช่ คุณสามารถเข้าถึงเวอร์ชันทดลองได้[ที่นี่](https://releases.groupdocs.com/) เพื่อประเมินคุณสมบัติก่อนตัดสินใจซื้อ
### ฉันสามารถปรับแต่งรูปแบบผลลัพธ์ของผลลัพธ์การเปรียบเทียบได้หรือไม่
แน่นอนว่า GroupDocs.Comparison สำหรับ .NET ให้ความยืดหยุ่นในการกำหนดค่ารูปแบบเอาต์พุตตามความต้องการของคุณ
### GroupDocs.Comparison สำหรับ .NET รองรับการประมวลผลเป็นชุดหรือไม่
ใช่ นักพัฒนาสามารถใช้ประโยชน์จากความสามารถในการประมวลผลเป็นชุดเพื่อเปรียบเทียบไฟล์หลายไฟล์พร้อมกัน เพื่อปรับปรุงประสิทธิภาพ
### ฉันจะขอความช่วยเหลือได้ที่ไหนหากฉันประสบปัญหาใดๆ ระหว่างการใช้งาน
 คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Comparison[ที่นี่](https://forum.groupdocs.com/c/comparison/12) เพื่อขอการสนับสนุนจากชุมชนและผู้เชี่ยวชาญ