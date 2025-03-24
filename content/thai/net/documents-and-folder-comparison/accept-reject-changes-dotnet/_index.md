---
title: ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET
linktitle: ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET
second_title: GroupDocs.Comparison .NET API
description: เรียนรู้วิธียอมรับและปฏิเสธการเปลี่ยนแปลงในเอกสารโดยใช้ GroupDocs comparison สำหรับ .NET ปรับปรุงขั้นตอนการทำงานเอกสารของคุณได้อย่างง่ายดาย
weight: 10
url: /th/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET

## การแนะนำ
ในขอบเขตของการจัดการเอกสารและการทำงานร่วมกัน การรับรองความถูกต้องและความสมบูรณ์ของไฟล์เป็นสิ่งสำคัญยิ่ง การเปรียบเทียบ GroupDocs สำหรับ .NET กลายเป็นโซลูชันที่แข็งแกร่ง ช่วยให้นักพัฒนายอมรับและปฏิเสธการเปลี่ยนแปลงภายในเอกสารได้อย่างง่ายดาย จึงทำให้เวิร์กโฟลว์คล่องตัวและปรับปรุงประสิทธิภาพการทำงาน บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการยอมรับและปฏิเสธการเปลี่ยนแปลงโดยใช้การเปรียบเทียบ GroupDocs สำหรับ .NET โดยแจกแจงรายละเอียดแต่ละขั้นตอนเพื่อความชัดเจนและความง่ายในการใช้งาน
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
### การตั้งค่าสภาพแวดล้อม
1. ติดตั้ง .NET SDK: หากคุณยังไม่ได้ดาวน์โหลด ให้ดาวน์โหลดและติดตั้ง .NET SDK ที่เหมาะกับระบบปฏิบัติการของคุณจากเว็บไซต์ .NET
2.  ติดตั้ง GroupDocs comparison สำหรับ .NET: รับเวอร์ชันล่าสุดของ GroupDocs comparison สำหรับ .NET จากไฟล์ที่ให้มา[ลิ้งค์ดาวน์โหลด](https://releases.groupdocs.com/comparison/net/) และปฏิบัติตามคำแนะนำในการติดตั้ง
3. ความคุ้นเคยกับการเขียนโปรแกรม C#: บทช่วยสอนนี้ถือว่าความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# และไวยากรณ์ของมัน

## นำเข้าเนมสเปซ
ขั้นแรก ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ เนมสเปซเหล่านี้จะให้การเข้าถึงฟังก์ชันที่จำเป็นสำหรับการเปรียบเทียบและการจัดการเอกสาร

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## ขั้นตอนที่ 1: ระบุไดเร็กทอรีเอาต์พุตและชื่อไฟล์
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 ให้แน่ใจว่าจะเปลี่ยน`"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีเอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: เริ่มต้นตัวเปรียบเทียบและเปรียบเทียบเอกสาร
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
โค้ดนี้เตรียมข้อมูลเบื้องต้นให้กับอ็อบเจ็กต์ Comparer ด้วยเอกสารต้นฉบับ และเพิ่มเอกสารเป้าหมายสำหรับการเปรียบเทียบ จากนั้นจึงดำเนินการกระบวนการเปรียบเทียบ
## ขั้นตอนที่ 3: ดึงข้อมูลและจัดการการเปลี่ยนแปลง
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
ดึงข้อมูลการเปลี่ยนแปลงจากการเปรียบเทียบและจัดการตามความจำเป็น ในตัวอย่างนี้ การเปลี่ยนแปลงจะถูกปฏิเสธก่อนแล้วจึงยอมรับ เอกสารผลลัพธ์จะถูกบันทึกตามนั้น

## บทสรุป
โดยสรุป GroupDocs comparison สำหรับ .NET นำเสนอโซลูชันที่ราบรื่นสำหรับการยอมรับและปฏิเสธการเปลี่ยนแปลงภายในเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถรวมฟังก์ชันการทำงานนี้เข้ากับแอปพลิเคชันของตนได้อย่างมีประสิทธิภาพ ช่วยให้มั่นใจในความถูกต้องของเอกสารและปรับปรุงการทำงานร่วมกัน
## คำถามที่พบบ่อย
### GroupDocs comparison สำหรับ .NET สามารถเปรียบเทียบเอกสารที่มีรูปแบบต่างกันได้หรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบระหว่างเอกสารในรูปแบบต่างๆ เช่น DOCX, PDF, PPTX และอื่นๆ
### การเปรียบเทียบ GroupDocs สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งลักษณะที่ปรากฏของการเปลี่ยนแปลงในเอกสารที่เปรียบเทียบได้หรือไม่
แน่นอนว่าการเปรียบเทียบ GroupDocs สำหรับ .NET มีตัวเลือกมากมายสำหรับการปรับแต่งรูปลักษณ์ของการเปลี่ยนแปลง รวมถึงสี สไตล์ และอื่นๆ
### การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบเอกสารหลายหน้าหรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบเอกสารหลายหน้าด้วยความแม่นยำและแม่นยำ
### มีเวอร์ชันทดลองใช้สำหรับ GroupDocs comparison สำหรับ .NET หรือไม่
 ใช่ คุณสามารถทดลองใช้ GroupDocs comparison สำหรับ .NET ได้ฟรีจากข้อมูลที่ให้ไว้[ลิงค์](https://releases.groupdocs.com/).