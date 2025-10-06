---
"description": "เรียนรู้วิธีการยอมรับและปฏิเสธการเปลี่ยนแปลงในเอกสารโดยใช้การเปรียบเทียบ GroupDocs สำหรับ .NET ปรับปรุงเวิร์กโฟลว์เอกสารของคุณได้อย่างง่ายดาย"
"linktitle": "ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET"
"second_title": "API การเปรียบเทียบ GroupDocs .NET"
"title": "ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET"
"url": "/th/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# ยอมรับและปฏิเสธการเปลี่ยนแปลงในการเปรียบเทียบ GroupDocs สำหรับ .NET

## การแนะนำ
ในด้านการจัดการเอกสารและการทำงานร่วมกัน การรับรองความถูกต้องและความสมบูรณ์ของไฟล์ถือเป็นสิ่งสำคัญที่สุด GroupDocs Comparison for .NET ถือเป็นโซลูชันที่มีประสิทธิภาพ ช่วยให้ผู้พัฒนายอมรับและปฏิเสธการเปลี่ยนแปลงภายในเอกสารได้อย่างง่ายดาย จึงทำให้เวิร์กโฟลว์มีประสิทธิภาพและเพิ่มประสิทธิภาพการทำงาน บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการยอมรับและปฏิเสธการเปลี่ยนแปลงโดยใช้ GroupDocs Comparison for .NET โดยแบ่งขั้นตอนต่างๆ ออกเป็นส่วนๆ เพื่อความชัดเจนและง่ายต่อการนำไปใช้
## ข้อกำหนดเบื้องต้น
ก่อนจะเริ่มบทช่วยสอนนี้ ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
### การตั้งค่าสภาพแวดล้อม
1. ติดตั้ง .NET SDK: หากคุณยังไม่ได้ดาวน์โหลดและติดตั้ง .NET SDK ที่เหมาะสมกับระบบปฏิบัติการของคุณจากเว็บไซต์ .NET
2. ติดตั้ง GroupDocs Comparison สำหรับ .NET: รับเวอร์ชันล่าสุดของ GroupDocs Comparison สำหรับ .NET จากที่ให้มา [ลิงค์ดาวน์โหลด](https://releases.groupdocs.com/comparison/net/) และทำตามคำแนะนำการติดตั้ง
3. ความคุ้นเคยกับการเขียนโปรแกรม C#: บทช่วยสอนนี้ถือว่าคุณมีความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C# และรูปแบบไวยากรณ์ของมัน

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโครงการของคุณ เนมสเปซเหล่านี้จะช่วยให้เข้าถึงฟังก์ชันต่างๆ ที่จำเป็นสำหรับการเปรียบเทียบและจัดการเอกสาร

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## ขั้นตอนที่ 1: ระบุไดเรกทอรีเอาต์พุตและชื่อไฟล์
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
ให้แน่ใจว่าจะเปลี่ยน `"Your Document Directory"` พร้อมเส้นทางไปยังไดเร็กทอรีเอาท์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: เริ่มต้น Comparer และเปรียบเทียบเอกสาร
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
โค้ดนี้จะเริ่มต้นวัตถุ Comparer ด้วยเอกสารต้นฉบับและเพิ่มเอกสารเป้าหมายสำหรับการเปรียบเทียบ จากนั้นจึงดำเนินการกระบวนการเปรียบเทียบ
## ขั้นตอนที่ 3: ดึงข้อมูลและจัดการการเปลี่ยนแปลง
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
ดึงข้อมูลการเปลี่ยนแปลงจากการเปรียบเทียบและจัดการตามความจำเป็น ในตัวอย่างนี้ การเปลี่ยนแปลงจะถูกปฏิเสธก่อนแล้วจึงยอมรับ เอกสารที่ได้จะถูกบันทึกตามนั้น

## บทสรุป
โดยสรุป การเปรียบเทียบ GroupDocs สำหรับ .NET นำเสนอโซลูชันที่ราบรื่นสำหรับการยอมรับและปฏิเสธการเปลี่ยนแปลงภายในเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ นักพัฒนาสามารถผสานรวมฟังก์ชันนี้ลงในแอปพลิเคชันของตนได้อย่างมีประสิทธิภาพ ช่วยให้มั่นใจถึงความถูกต้องของเอกสารและปรับปรุงการทำงานร่วมกัน
## คำถามที่พบบ่อย
### การเปรียบเทียบ GroupDocs สำหรับ .NET สามารถเปรียบเทียบเอกสารที่มีรูปแบบต่างกันได้หรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบระหว่างเอกสารในรูปแบบต่างๆ เช่น DOCX, PDF, PPTX และอื่นๆ
### การเปรียบเทียบ GroupDocs สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งลักษณะการเปลี่ยนแปลงในเอกสารที่เปรียบเทียบได้หรือไม่
อย่างแน่นอน การเปรียบเทียบ GroupDocs สำหรับ .NET มีตัวเลือกมากมายในการปรับแต่งลักษณะที่ปรากฏของการเปลี่ยนแปลง รวมถึงสี สไตล์ และอื่นๆ อีกมากมาย
### การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบเอกสารหลายหน้าหรือไม่
ใช่ การเปรียบเทียบ GroupDocs สำหรับ .NET รองรับการเปรียบเทียบเอกสารหลายหน้าด้วยความแม่นยำและความถูกต้อง
### มีเวอร์ชันทดลองใช้สำหรับ GroupDocs Comparison สำหรับ .NET หรือไม่
ใช่ คุณสามารถทดลองใช้ GroupDocs Comparison สำหรับ .NET ได้ฟรีจากเว็บไซต์ที่ให้มา [ลิงค์](https://releases-groupdocs.com/).