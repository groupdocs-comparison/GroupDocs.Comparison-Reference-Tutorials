---
title: รับข้อมูลเอกสารจากเอกสารผลลัพธ์ - GroupDocs.Comparison สำหรับ .NET
linktitle: รับข้อมูลเอกสารจากเอกสารผลลัพธ์ - GroupDocs.Comparison สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธีดึงข้อมูลเอกสารจากเอกสารผลลัพธ์โดยใช้ GroupDocs.Comparison สำหรับ .NET อธิบายขั้นตอนง่ายๆ สำหรับนักพัฒนา .NET
weight: 12
url: /th/net/basic-usage/get-document-info-from-result-document/
---

# รับข้อมูลเอกสารจากเอกสารผลลัพธ์ - GroupDocs.Comparison สำหรับ .NET

## การแนะนำ
ในด้านการพัฒนา .NET การจัดการและการเปรียบเทียบเอกสารถือเป็นข้อกำหนดทั่วไป GroupDocs.Comparison สำหรับ .NET นำเสนอโซลูชันที่มีประสิทธิภาพสำหรับงานนี้ ช่วยให้นักพัฒนาสามารถรวมฟังก์ชันการเปรียบเทียบเอกสารเข้ากับแอปพลิเคชันของตนได้อย่างราบรื่น บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการใช้ GroupDocs.Comparison สำหรับ .NET เพื่อดึงข้อมูลเอกสารจากเอกสารผลลัพธ์ 
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. GroupDocs.Comparison สำหรับ .NET: ติดตั้ง GroupDocs.Comparison สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/comparison/net/).
2. สภาพแวดล้อมการพัฒนา: ตั้งค่าสภาพแวดล้อมการพัฒนา .NET ของคุณ รวมถึง IDE (เช่น Visual Studio) และการกำหนดค่าที่จำเป็น
3.  ไฟล์เอกสาร: เตรียมไฟล์เอกสารต้นทางและเป้าหมาย (เช่น`SOURCE.docx` และ`TARGET.docx`) เพื่อการเปรียบเทียบ

## นำเข้าเนมสเปซ
ประการแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงฟังก์ชัน GroupDocs.Comparison

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

## ขั้นตอนที่ 1: เริ่มต้นตัวเปรียบเทียบด้วยเอกสารต้นฉบับ
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```
 ในขั้นตอนนี้ เราจะเริ่มต้น a`Comparer` วัตถุที่มีเอกสารต้นฉบับ (`SOURCE.docx` ในกรณีนี้) โดยใช้ a`using` คำแถลงเพื่อให้แน่ใจว่ามีการกำจัดทรัพยากรอย่างเหมาะสม
## ขั้นตอนที่ 2: เพิ่มเอกสารเป้าหมายสำหรับการเปรียบเทียบ
```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```
ที่นี่เราเพิ่มเอกสารเป้าหมาย (`TARGET.docx`) ไปยังวัตถุเปรียบเทียบเพื่อการเปรียบเทียบ
## ขั้นตอนที่ 3: ดึงข้อมูลเอกสารจากเอกสารผลลัพธ์
```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```
 ขั้นตอนนี้จะดึงข้อมูลเอกสารจากเอกสารผลลัพธ์ มันเข้าถึงเอกสารเป้าหมายโดยใช้`FirstOrDefault()` แล้วก็โทรมา`GetDocumentInfo()`เพื่อรับข้อมูล เช่น ประเภทไฟล์ จำนวนหน้า และขนาดเอกสาร
## ขั้นตอนที่ 4: แสดงข้อมูลเอกสาร
```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```
ที่นี่ เราแสดงข้อมูลเอกสารที่ดึงมา รวมถึงประเภทไฟล์ จำนวนหน้า และขนาดเอกสารเป็นไบต์

## บทสรุป
GroupDocs.Comparison สำหรับ .NET ช่วยให้กระบวนการเปรียบเทียบเอกสารในแอปพลิเคชัน .NET ง่ายขึ้น เมื่อทำตามบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีดึงข้อมูลเอกสารจากเอกสารผลลัพธ์โดยใช้ GroupDocs.Comparison สำหรับ .NET รวมเทคนิคเหล่านี้เข้ากับโครงการของคุณเพื่อเพิ่มความสามารถในการจัดการเอกสาร
## คำถามที่พบบ่อย
### GroupDocs.Comparison สำหรับ .NET เข้ากันได้กับรูปแบบเอกสารต่างๆ หรือไม่
ใช่ GroupDocs.Comparison สำหรับ .NET รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, PPTX, XLSX และอื่นๆ
### ฉันสามารถปรับแต่งการตั้งค่าการเปรียบเทียบเอกสารได้หรือไม่
แน่นอนว่า GroupDocs.Comparison สำหรับ .NET นำเสนอตัวเลือกการปรับแต่งที่ครอบคลุมสำหรับการเปรียบเทียบเอกสารเพื่อให้เหมาะกับความต้องการเฉพาะของคุณ
### มีรุ่นทดลองใช้สำหรับการประเมินหรือไม่?
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Comparison สำหรับ .NET ได้อย่างไร
 คุณสามารถขอความช่วยเหลือและมีส่วนร่วมกับชุมชนได้ที่ฟอรัม GroupDocs.Comparison[ที่นี่](https://forum.groupdocs.com/c/comparison/12).
### ตัวเลือกสิทธิ์การใช้งานสำหรับ GroupDocs.Comparison สำหรับ .NET มีอะไรบ้าง
 คุณสามารถสำรวจตัวเลือกใบอนุญาตและซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).