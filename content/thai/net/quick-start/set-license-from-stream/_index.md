---
title: ตั้งค่าใบอนุญาตจากสตรีม - การเปรียบเทียบ GroupDocs สำหรับ .NET
linktitle: ตั้งค่าใบอนุญาตจากสตรีม - การเปรียบเทียบ GroupDocs สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีการตั้งค่าใบอนุญาตโดยใช้ GroupDocs.Comparison สำหรับ .NET อย่างมีประสิทธิภาพ ตรวจสอบความถูกต้องของเอกสารและประหยัดเวลาด้วยบทช่วยสอนนี้
weight: 11
url: /th/net/quick-start/set-license-from-stream/
---

# ตั้งค่าใบอนุญาตจากสตรีม - การเปรียบเทียบ GroupDocs สำหรับ .NET

## การแนะนำ
ในโลกของการพัฒนา .NET การจัดการและการเปรียบเทียบเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญ ไม่ว่าคุณจะทำงานเกี่ยวกับสัญญาทางกฎหมาย รายงานทางการเงิน หรือแอปพลิเคชันอื่นๆ ที่ต้องใช้เอกสารจำนวนมาก ความสามารถในการเปรียบเทียบเอกสารอย่างแม่นยำสามารถประหยัดเวลาและรับรองความถูกต้องได้ นี่คือจุดที่ GroupDocs.Comparison สำหรับ .NET เข้ามามีบทบาท 
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับกรอบงาน C# และ .NET
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
-  ติดตั้ง GroupDocs.Comparison สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/comparison/net/).
-  เข้าถึง GroupDocs.Comparison สำหรับเอกสาร .NET[ที่นี่](https://tutorials.groupdocs.com/comparison/net/).

## นำเข้าเนมสเปซ
หากต้องการเริ่มใช้ GroupDocs.Comparison สำหรับ .NET คุณจะต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ ต่อไปนี้คือวิธีที่คุณสามารถทำได้:

ในโปรเจ็กต์ของคุณ ให้เพิ่มการอ้างอิงเนมสเปซต่อไปนี้ที่ด้านบนของไฟล์โค้ดของคุณ:
```csharp
using System;
using System.IO;
```
เนมสเปซเหล่านี้ให้การเข้าถึงคลาสที่จำเป็นและวิธีการที่จำเป็นสำหรับงานการเปรียบเทียบเอกสาร

## ขั้นตอนที่ 1: ตรวจสอบการมีอยู่ของไฟล์ลิขสิทธิ์
```csharp
if (File.Exists(Constants.LicensePath))
{
```
ขั้นตอนนี้จะตรวจสอบว่าไฟล์ลิขสิทธิ์อยู่ในเส้นทางที่ระบุหรือไม่
## ขั้นตอนที่ 2: ตั้งค่าใบอนุญาตจากสตรีม
```csharp
using (FileStream stream = File.OpenRead(Constants.LicensePath))
{
    License license = new License();
    license.SetLicense(stream);
}
```
 หากมีไฟล์ใบอนุญาต ขั้นตอนนี้จะสร้างสตรีมไฟล์เพื่ออ่านไฟล์ใบอนุญาตและตั้งค่าใบอนุญาตสำหรับ GroupDocs.Comparison โดยใช้`SetLicense` วิธี.
## ขั้นตอนที่ 3: จัดการกับการขาดใบอนุญาต
```csharp
Console.WriteLine("License set successfully.");
```
หากตั้งค่าใบอนุญาตสำเร็จ ขั้นตอนนี้จะพิมพ์ข้อความแสดงความสำเร็จ
## ขั้นตอนที่ 4: แจ้งให้ขอรับใบอนุญาต
```csharp
Console.WriteLine("\nWe do not ship any license with this example. " +
                  "\nVisit the GroupDocs site to obtain either a temporary or permanent license. " +
                  "\nLearn more about licensing at https://buy.groupdocs.com/faqs/licensing -
                  "\nLear how to request temporary license at https://buy.groupdocs.com/temporary-license");
```
หากไม่มีไฟล์ใบอนุญาต ขั้นตอนนี้จะแจ้งให้ผู้ใช้ขอรับใบอนุญาตจากเว็บไซต์ GroupDocs

## บทสรุป
ในบทช่วยสอนนี้ เราได้ศึกษาวิธีการตั้งค่าใบอนุญาตโดยใช้ GroupDocs.Comparison สำหรับ .NET ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถจัดการและเปรียบเทียบเอกสารในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ รับประกันความถูกต้องแม่นยำและประหยัดเวลาอันมีค่า
## คำถามที่พบบ่อย
### ฉันต้องมีใบอนุญาตเพื่อใช้ GroupDocs.Comparison สำหรับ .NET หรือไม่
ใช่ คุณต้องมีใบอนุญาตเพื่อใช้ GroupDocs.Comparison สำหรับ .NET คุณสามารถขอรับใบอนุญาตชั่วคราวหรือถาวรได้จากเว็บไซต์ GroupDocs
### ฉันสามารถลองใช้ GroupDocs.Comparison สำหรับ .NET ก่อนซื้อได้หรือไม่
ได้ คุณสามารถขอทดลองใช้ฟรีได้จากเว็บไซต์ GroupDocs เพื่อประเมินผลิตภัณฑ์ก่อนตัดสินใจซื้อ
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Comparison สำหรับ .NET ได้อย่างไร
 คุณสามารถรับการสนับสนุนจากฟอรัม GroupDocs สำหรับการเปรียบเทียบโดยเฉพาะ[ที่นี่](https://forum.groupdocs.com/c/comparison/12).
### ฉันควรทำอย่างไรหากประสบปัญหาด้านใบอนุญาต
 หากคุณพบปัญหาเกี่ยวกับใบอนุญาต โปรดดูคำถามที่พบบ่อยเกี่ยวกับใบอนุญาต[ที่นี่](https://purchase.groupdocs.com/faqs/licensing) หรือติดต่อฝ่ายสนับสนุน GroupDocs
### ฉันจะหาบทช่วยสอนและทรัพยากรเพิ่มเติมสำหรับ GroupDocs.Comparison สำหรับ .NET ได้ที่ไหน
 คุณสามารถค้นหาเอกสารและบทช่วยสอนที่ครอบคลุมได้จากเว็บไซต์ GroupDocs[ที่นี่](https://tutorials.groupdocs.com/comparison/net/).