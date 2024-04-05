---
title: ทำความสะอาดทรัพยากรหลังจากดูตัวอย่างหน้า
linktitle: ทำความสะอาดทรัพยากรหลังจากดูตัวอย่างหน้า
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีเปรียบเทียบเอกสารโดยใช้ GroupDocs.Comparison สำหรับ .NET ทีละขั้นตอน ปรับปรุงแอปพลิเคชัน .NET ของคุณด้วยการจัดการเอกสารที่มีประสิทธิภาพ
type: docs
weight: 13
url: /th/net/document-comparison/clean-resources-after-page-previews/
---
## การแนะนำ
ในโลกของการพัฒนา .NET การจัดการและการเปรียบเทียบเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญสำหรับการใช้งานต่างๆ ตั้งแต่บริษัทกฎหมายไปจนถึงสถาบันการศึกษา โชคดีที่มีเครื่องมืออย่าง GroupDocs.Comparison สำหรับ .NET นักพัฒนาจึงสามารถปรับปรุงกระบวนการเปรียบเทียบเอกสารได้อย่างง่ายดาย ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Comparison สำหรับ .NET เพื่อเปรียบเทียบเอกสารทีละขั้นตอน
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1.  GroupDocs.Comparison สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/comparison/net/).
2. สภาพแวดล้อมการพัฒนา .NET: ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ที่ใช้งานได้บนเครื่องของคุณ
3. ตัวอย่างเอกสาร: เตรียมเอกสารต้นทางและเป้าหมายที่คุณต้องการเปรียบเทียบ

## นำเข้าเนมสเปซ
ในโปรเจ็กต์ .NET ของคุณ ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Comparison สำหรับ .NET

```csharp
using System;
using System.IO;
```

## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## ขั้นตอนที่ 2: เริ่มต้นตัวเปรียบเทียบและเพิ่มเอกสาร
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```
## ขั้นตอนที่ 3: ทำการเปรียบเทียบและสร้างผลลัพธ์
```csharp
    comparer.Compare(File.Create(outputFileName));
```
## ขั้นตอนที่ 4: สร้างตัวอย่างเอกสาร
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    document.GeneratePreview(previewOptions);
}
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## บทสรุป
โดยสรุป GroupDocs.Comparison สำหรับ .NET มอบโซลูชันที่มีประสิทธิภาพสำหรับการเปรียบเทียบเอกสารภายในแอปพลิเคชัน .NET ได้อย่างง่ายดาย ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถรวมฟังก์ชันการเปรียบเทียบเอกสารเข้ากับโปรเจ็กต์ของตนได้อย่างราบรื่น ช่วยเพิ่มผลผลิตและประสิทธิภาพ
## คำถามที่พบบ่อย
### GroupDocs.Comparison สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารที่แตกต่างกันหรือไม่
ใช่ GroupDocs.Comparison สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PPTX, XLSX, PDF และอื่นๆ
### ฉันสามารถปรับแต่งรูปแบบผลลัพธ์ของเอกสารที่เปรียบเทียบได้หรือไม่
แน่นอนว่า GroupDocs.Comparison สำหรับ .NET ให้ความยืดหยุ่นในการเลือกรูปแบบเอาต์พุตตามความต้องการของคุณ
### มีรุ่นทดลองใช้สำหรับการทดสอบหรือไม่?
 ได้ คุณสามารถสำรวจคุณลักษณะต่างๆ ของ GroupDocs.Comparison สำหรับ .NET ได้พร้อมให้ทดลองใช้งานฟรี[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับปัญหาหรือข้อสงสัยที่เกี่ยวข้องกับ GroupDocs.Comparison สำหรับ .NET ได้อย่างไร
 คุณสามารถขอความช่วยเหลือได้จากฟอรัมชุมชน GroupDocs.Comparison[ที่นี่](https://forum.groupdocs.com/c/comparison/12).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Comparison สำหรับ .NET ได้ที่ไหน
คุณสามารถซื้อใบอนุญาตสำหรับ GroupDocs.Comparison สำหรับ .NET ได้จาก[ลิงค์นี้](https://purchase.groupdocs.com/buy).