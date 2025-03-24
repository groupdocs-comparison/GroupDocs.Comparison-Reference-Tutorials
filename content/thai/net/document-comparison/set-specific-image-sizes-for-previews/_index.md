---
title: ตั้งค่าขนาดรูปภาพเฉพาะสำหรับการดูตัวอย่าง
linktitle: ตั้งค่าขนาดรูปภาพเฉพาะสำหรับการดูตัวอย่าง
second_title: GroupDocs.Comparison .NET API
description: รวมฟังก์ชันการเปรียบเทียบเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณกับ GroupDocs.Comparison สำหรับ .NET ได้อย่างง่ายดาย
weight: 14
url: /th/net/document-comparison/set-specific-image-sizes-for-previews/
---

# ตั้งค่าขนาดรูปภาพเฉพาะสำหรับการดูตัวอย่าง

## การแนะนำ
ในขอบเขตของการพัฒนาซอฟต์แวร์ การเปรียบเทียบเอกสารที่มีประสิทธิภาพและถูกต้องถือเป็นสิ่งสำคัญในการรับรองความสมบูรณ์และความสม่ำเสมอของข้อมูล GroupDocs.Comparison สำหรับ .NET มอบโซลูชันที่มีประสิทธิภาพสำหรับนักพัฒนาที่ต้องการรวมฟังก์ชันการเปรียบเทียบเอกสารเข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึกถึงการใช้งานการเปรียบเทียบเอกสารโดยใช้ GroupDocs.Comparison สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. ติดตั้ง GroupDocs.Comparison สำหรับ .NET
 ในการเริ่มต้น คุณจะต้องติดตั้ง GroupDocs.Comparison สำหรับ .NET ในสภาพแวดล้อมการพัฒนาของคุณ คุณสามารถดาวน์โหลดไฟล์ที่จำเป็นได้จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/comparison/net/).
### 2. ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณ
ตรวจสอบให้แน่ใจว่าคุณได้กำหนดค่าสภาพแวดล้อมการพัฒนาที่เหมาะสม รวมถึง Visual Studio หรือ IDE การพัฒนา .NET ที่ต้องการ
### 3. ความคุ้นเคยกับ .NET Framework
ความเข้าใจพื้นฐานเกี่ยวกับกรอบงาน .NET และภาษาการเขียนโปรแกรม C# ถือเป็นสิ่งสำคัญต่อการใช้ GroupDocs.Comparison สำหรับ .NET ได้อย่างมีประสิทธิภาพ

## นำเข้าเนมสเปซ
ก่อนที่จะใช้ฟังก์ชันการเปรียบเทียบเอกสาร คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการที่จำเป็น
```csharp
using System;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเร็กทอรีเอาต์พุตและชื่อไฟล์
ขั้นแรก ให้กำหนดไดเร็กทอรีเอาต์พุตและชื่อไฟล์ที่จะบันทึกเอกสารที่เปรียบเทียบ
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## ขั้นตอนที่ 2: เริ่มต้นตัวเปรียบเทียบ
 ยกตัวอย่าง`Comparer` วัตถุโดยการส่งเส้นทางเอกสารต้นทางเป็นพารามิเตอร์
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
```
## ขั้นตอนที่ 3: เพิ่มเอกสารเป้าหมาย
เพิ่มเอกสารเป้าหมายที่คุณต้องการเปรียบเทียบกับเอกสารต้นฉบับ
```csharp
comparer.Add("TARGET.pptx");
```
## ขั้นตอนที่ 4: ทำการเปรียบเทียบ
 เรียกใช้`Compare` วิธีดำเนินการเปรียบเทียบเอกสารและบันทึกผลลัพธ์
```csharp
comparer.Compare(File.Create(outputFileName));
```
## ขั้นตอนที่ 5: สร้างตัวอย่างเอกสาร
สร้างการแสดงตัวอย่างเอกสารที่เปรียบเทียบเพื่อการตรวจสอบด้วยภาพ
```csharp
Document document = new Document(File.OpenRead(outputFileName));
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2 };
previewOptions.Height = 1000;
previewOptions.Width = 1000;
document.GeneratePreview(previewOptions);
```
## ขั้นตอนที่ 6: แสดงผลเอาต์พุต
แสดงข้อความแสดงความสำเร็จพร้อมเส้นทางไปยังตัวอย่างเอกสารที่สร้างขึ้น
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## บทสรุป
การรวมฟังก์ชันการเปรียบเทียบเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณนั้นง่ายขึ้นด้วย GroupDocs.Comparison สำหรับ .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ นักพัฒนาสามารถผสานรวมเครื่องมืออันทรงพลังนี้ได้อย่างราบรื่น เพื่อรับรองความถูกต้องและสม่ำเสมอในกระบวนการจัดการเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Comparison สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
GroupDocs.Comparison สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, PPTX, XLSX และอื่นๆ
### ฉันสามารถปรับแต่งตัวเลือกการเปรียบเทียบตามความต้องการของฉันได้หรือไม่
ใช่ GroupDocs.Comparison สำหรับ .NET มีตัวเลือกมากมายสำหรับการปรับแต่งกระบวนการเปรียบเทียบตามความต้องการเฉพาะ
### GroupDocs.Comparison สำหรับ .NET รองรับการกำหนดเวอร์ชันเอกสารหรือไม่
แม้ว่า GroupDocs.Comparison สำหรับ .NET จะมุ่งเน้นไปที่การเปรียบเทียบเอกสารเป็นหลัก แต่ก็สามารถรวมเข้ากับระบบควบคุมเวอร์ชันสำหรับโซลูชันการจัดการเอกสารที่ครอบคลุมได้
### GroupDocs.Comparison สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถทดลองใช้ GroupDocs.Comparison สำหรับ .NET ได้ฟรีจาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนและความช่วยเหลือเพิ่มเติมสำหรับ GroupDocs.Comparison สำหรับ .NET ได้ที่ไหน
 คุณสามารถสำรวจเฉพาะ[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/comparison/12) สำหรับ GroupDocs.Comparison สำหรับ .NET เพื่อขอความช่วยเหลือ แบ่งปันประสบการณ์ และเชื่อมต่อกับชุมชน