---
title: การบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดในการเปรียบเทียบ GroupDocs สำหรับ .NET
linktitle: การบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดในการเปรียบเทียบ GroupDocs สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดโดยใช้ GroupDocs comparison สำหรับ .NET เปรียบเทียบและจัดการข้อมูลเมตาได้อย่างง่ายดายด้วยคำแนะนำทีละขั้นตอน
weight: 16
url: /th/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# การบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดในการเปรียบเทียบ GroupDocs สำหรับ .NET

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดโดยใช้ GroupDocs comparison สำหรับ .NET ข้อมูลเมตาเป็นสิ่งสำคัญสำหรับการจัดระเบียบและการจัดการเอกสารอย่างมีประสิทธิภาพ ด้วยการเปรียบเทียบ GroupDocs คุณสามารถเปรียบเทียบและจัดการข้อมูลเมตาเพื่อให้ตรงตามความต้องการเฉพาะของคุณได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  การเปรียบเทียบ GroupDocs สำหรับ .NET: ดาวน์โหลดและติดตั้งการเปรียบเทียบ GroupDocs สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/comparison/net/).
2. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนาที่เหมาะสม เช่น Visual Studio ติดตั้งอยู่บนระบบของคุณ
3. เอกสารต้นทางและเป้าหมาย: เตรียมเอกสารต้นทางและเป้าหมายที่คุณต้องการเปรียบเทียบและจัดการข้อมูลเมตา

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชันการทำงานที่ได้รับจาก GroupDocs comparison สำหรับ .NET
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์
กำหนดไดเร็กทอรีที่คุณต้องการบันทึกเอกสารที่เปรียบเทียบและระบุชื่อไฟล์เอาต์พุต
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## ขั้นตอนที่ 2: เริ่มต้นตัวเปรียบเทียบและเพิ่มเอกสาร
 เริ่มต้น`Comparer` วัตถุกับเอกสารต้นฉบับและเพิ่มเอกสารเป้าหมายเพื่อเปรียบเทียบ
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## ขั้นตอนที่ 3: ระบุตัวเลือกข้อมูลเมตา
 ระบุตัวเลือกข้อมูลเมตาสำหรับการบันทึกในเอกสารที่เปรียบเทียบ ในตัวอย่างนี้ เราตั้งค่า`CloneMetadataType` ถึง`MetadataType.FileAuthor` และแจ้งรายละเอียดให้`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## ขั้นตอนที่ 4: เปรียบเทียบเอกสารและบันทึกข้อมูลเมตา
เปรียบเทียบเอกสารกับตัวเลือกข้อมูลเมตาที่ระบุ และบันทึกเอกสารที่เปรียบเทียบ
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## ขั้นตอนที่ 5: แสดงข้อความแสดงความสำเร็จ
แสดงข้อความแสดงความสำเร็จที่ระบุว่าเอกสารได้รับการเปรียบเทียบเรียบร้อยแล้วและตำแหน่งเอาต์พุต
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีบันทึกข้อมูลเมตาของเอกสารที่ผู้ใช้กำหนดโดยใช้ GroupDocs comparison สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถเปรียบเทียบเอกสารได้อย่างมีประสิทธิภาพในขณะที่รักษาและจัดการข้อมูลเมตาตามความต้องการของคุณ
## คำถามที่พบบ่อย
### การเปรียบเทียบ GroupDocs สำหรับ .NET สามารถจัดการรูปแบบเอกสารต่าง ๆ ได้หรือไม่
ใช่ GroupDocs comparison รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, PPTX, XLSX และอื่นๆ
### มีการทดลองใช้ GroupDocs comparison สำหรับ .NET ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันสามารถปรับแต่งตัวเลือกข้อมูลเมตาตามความต้องการของฉันได้หรือไม่?
การเปรียบเทียบ GroupDocs มอบตัวเลือกที่ยืดหยุ่นเพื่อปรับแต่งการจัดการข้อมูลเมตาระหว่างการเปรียบเทียบเอกสาร
### GroupDocs comparison ให้การสนับสนุนทางเทคนิคหรือไม่
ใช่ คุณสามารถรับการสนับสนุนด้านเทคนิคได้จากฟอรัมการเปรียบเทียบ GroupDocs[ที่นี่](https://forum.groupdocs.com/c/comparison/12).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs comparison สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้จากเว็บไซต์ GroupDocs[ที่นี่](https://purchase.groupdocs.com/buy).