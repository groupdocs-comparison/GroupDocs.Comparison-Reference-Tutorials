---
title: สร้างการแสดงตัวอย่างหน้าสำหรับเอกสารต้นฉบับ
linktitle: สร้างการแสดงตัวอย่างหน้าสำหรับเอกสารต้นฉบับ
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีใช้ Groupdocs.Comparison สำหรับ .NET เพื่อปรับปรุงกระบวนการเปรียบเทียบเอกสารในโปรเจ็กต์ C# ของคุณอย่างมีประสิทธิภาพ
weight: 11
url: /th/net/document-comparison/generate-page-previews-source-document/
---
## การแนะนำ
ในโลกดิจิทัลที่เปลี่ยนแปลงอย่างรวดเร็วในปัจจุบัน การจัดการเอกสารและการเปรียบเทียบมีบทบาทสำคัญในอุตสาหกรรมต่างๆ นักพัฒนาที่กำลังมองหาโซลูชันที่มีประสิทธิภาพมักจะหันมาใช้ Groupdocs.Comparison สำหรับ .NET เครื่องมืออันทรงพลังนี้ช่วยให้นักพัฒนาสามารถเปรียบเทียบเอกสารได้อย่างง่ายดาย ช่วยให้พวกเขาปรับปรุงขั้นตอนการทำงานและปรับปรุงประสิทธิภาพการทำงานได้ ในบทช่วยสอนนี้ เราจะสำรวจสิ่งสำคัญของ Groupdocs.Comparison สำหรับ .NET โดยแจกแจงรายละเอียดแต่ละขั้นตอนเพื่อให้แน่ใจว่าจะได้รับประสบการณ์การเรียนรู้ที่ราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเจาะลึก Groupdocs.Comparison สำหรับ .NET ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### 1. การตั้งค่าสภาพแวดล้อมการพัฒนา .NET
ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้ รวมถึง Visual Studio หรือ IDE อื่นๆ ที่คุณเลือก
### 2. Groupdocs.Comparison สำหรับการติดตั้ง .NET
 ดาวน์โหลดและติดตั้ง Groupdocs.Comparison สำหรับ .NET จาก[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/comparison/net/).
### 3. ความเข้าใจพื้นฐานเกี่ยวกับ C#
ทำความคุ้นเคยกับพื้นฐานภาษาการเขียนโปรแกรม C# เพื่อใช้งาน Groupdocs.Comparison สำหรับ .NET ได้อย่างมีประสิทธิภาพ

## นำเข้าเนมสเปซ
ในโปรเจ็กต์ C# ของคุณ ให้นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน Groupdocs.Comparison

```csharp
using System;
using System.IO;
```

ตอนนี้ เรามาเจาะลึกกระบวนการสร้างหน้าตัวอย่างสำหรับเอกสารต้นฉบับโดยใช้ Groupdocs.Comparison สำหรับ .NET กัน
## ขั้นตอนที่ 1: เริ่มต้นวัตถุ Comparer
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 2: กำหนดตัวเลือกการแสดงตัวอย่าง
```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
    return File.Create(pagePath);
});
```
## ขั้นตอนที่ 3: ระบุรูปแบบการแสดงตัวอย่างและหมายเลขหน้า
```csharp
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2 };
```
## ขั้นตอนที่ 4: สร้างตัวอย่างเอกสาร
```csharp
comparer.Source.GeneratePreview(previewOptions);
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```

## บทสรุป
โดยสรุป Groupdocs.Comparison สำหรับ .NET นำเสนอโซลูชันที่ครอบคลุมสำหรับการเปรียบเทียบเอกสารในแอปพลิเคชัน C# ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมเครื่องมืออันทรงพลังนี้เข้ากับโปรเจ็กต์ของคุณได้อย่างมีประสิทธิภาพ ซึ่งช่วยเพิ่มประสิทธิภาพและประสิทธิผล
## คำถามที่พบบ่อย
### Groupdocs.Comparison สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารที่แตกต่างกันหรือไม่
ใช่ Groupdocs.Comparison สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, PPTX และอื่นๆ
### ฉันสามารถปรับแต่งตัวเลือกการเปรียบเทียบตามความต้องการของฉันได้หรือไม่
แน่นอนว่า Groupdocs.Comparison สำหรับ .NET มีตัวเลือกการปรับแต่งที่ครอบคลุมเพื่อปรับแต่งกระบวนการเปรียบเทียบให้ตรงตามความต้องการเฉพาะของคุณ
### Groupdocs.Comparison สำหรับ .NET มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง Groupdocs.Comparison สำหรับ .NET รุ่นทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะขอความช่วยเหลือหรือสนับสนุน Groupdocs.Comparison สำหรับ .NET ได้อย่างไร
 คุณสามารถเยี่ยมชม Groupdocs.Comparison[ฟอรั่ม](https://forum.groupdocs.com/c/comparison/12) สำหรับข้อสงสัยหรือการสนับสนุนที่เกี่ยวข้องกับเครื่องมือ
### ฉันจะซื้อใบอนุญาตสำหรับ Groupdocs.Comparison สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตสำหรับ Groupdocs.Comparison สำหรับ .NET ได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy).