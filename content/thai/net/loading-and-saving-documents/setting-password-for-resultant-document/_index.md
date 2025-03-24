---
title: การตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์ในการเปรียบเทียบ GroupDocs สำหรับ .NET
linktitle: การตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์ในการเปรียบเทียบ GroupDocs สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์ใน GroupDocs comparison for .NET เพิ่มความปลอดภัยและปกป้องไฟล์ที่เปรียบเทียบของคุณ
weight: 17
url: /th/net/loading-and-saving-documents/setting-password-for-resultant-document/
---

# การตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์ในการเปรียบเทียบ GroupDocs สำหรับ .NET

## การแนะนำ
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์โดยใช้ GroupDocs comparison สำหรับ .NET ฟีเจอร์นี้เพิ่มการรักษาความปลอดภัยอีกชั้นพิเศษให้กับเอกสารที่เปรียบเทียบของคุณ เพื่อให้มั่นใจว่ามีเพียงบุคคลที่ได้รับอนุญาตเท่านั้นที่สามารถเข้าถึงได้
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  การเปรียบเทียบ GroupDocs สำหรับ .NET: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้งไลบรารีการเปรียบเทียบ GroupDocs ในสภาพแวดล้อม .NET ของคุณ คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/comparison/net/).
2. เอกสารต้นทางและเป้าหมาย: เตรียมเอกสารต้นทาง (`SOURCE.docx`) และเอกสารเป้าหมาย (`TARGET.docx`) ที่คุณต้องการเปรียบเทียบและตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นไปยังโปรเจ็กต์ C# ของคุณเพื่อใช้ฟังก์ชันการเปรียบเทียบ GroupDocs:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
ระบุไดเร็กทอรีที่คุณต้องการบันทึกเอกสารผลลัพธ์ และกำหนดชื่อสำหรับเอาต์พุตไฟล์
## ขั้นตอนที่ 2: เปรียบเทียบเอกสารกับการตั้งค่ารหัสผ่าน
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
 ที่นี่เราเริ่มต้น a`Comparer` วัตถุที่มีเอกสารต้นฉบับ จากนั้นเราเพิ่มเอกสารเป้าหมายที่จะเปรียบเทียบ เราตั้งค่า`PasswordSaveOption` ถึง`User` เพื่อระบุว่ารหัสผ่านจะถูกนำไปใช้กับเอกสารผลลัพธ์ ระบุรหัสผ่านที่ต้องการใน`Password` ทรัพย์สินของ`SaveOptions` วัตถุ.
## ขั้นตอนที่ 3: แสดงข้อความแสดงความสำเร็จ
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
สุดท้ายนี้ เราจะแสดงข้อความแสดงความสำเร็จที่ระบุว่าเอกสารได้รับการเปรียบเทียบเรียบร้อยแล้ว และเอกสารผลลัพธ์ที่มีรหัสผ่านที่ตั้งไว้ได้ถูกบันทึกลงในไดเร็กทอรีที่ระบุ

## บทสรุป
การตั้งรหัสผ่านสำหรับเอกสารผลลัพธ์ในการเปรียบเทียบ GroupDocs สำหรับ .NET จะเพิ่มการรักษาความปลอดภัยอีกชั้นพิเศษให้กับเอกสารที่เปรียบเทียบของคุณ ทำให้มั่นใจได้ถึงการรักษาความลับและความสมบูรณ์ ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถนำคุณสมบัตินี้ไปใช้ในแอปพลิเคชัน .NET ของคุณได้อย่างง่ายดาย
## คำถามที่พบบ่อย
### ฉันสามารถเปรียบเทียบเอกสารในรูปแบบต่างๆ ได้หรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบเอกสารในรูปแบบต่างๆ เช่น DOCX, PDF, PPTX, XLSX และอื่นๆ
### มีรุ่นทดลองใช้งานหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนได้อย่างไรหากฉันประสบปัญหาใดๆ
 คุณสามารถขอความช่วยเหลือได้จากฟอรัมชุมชนการเปรียบเทียบ GroupDocs[ที่นี่](https://forum.groupdocs.com/c/comparison/12).
### ฉันต้องมีใบอนุญาตเพื่อใช้ GroupDocs comparison สำหรับ .NET หรือไม่
 ใช่ คุณสามารถซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy) หรือได้รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### มีเอกสารสำหรับการเปรียบเทียบ GroupDocs สำหรับ .NET หรือไม่
 ใช่ คุณสามารถเข้าถึงเอกสารได้[ที่นี่](https://tutorials.groupdocs.com/comparison/net/).