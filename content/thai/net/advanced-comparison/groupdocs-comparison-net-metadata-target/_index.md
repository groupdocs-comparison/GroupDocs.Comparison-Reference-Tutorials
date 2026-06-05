---
categories:
- Document Comparison
date: '2026-06-05'
description: เรียนรู้วิธีการรักษา metadata ด้วย GroupDocs Comparison สำหรับ .NET,
  step‑by‑step guide เพื่อเก็บคุณสมบัติของเอกสารเป้าหมายระหว่างการเปรียบเทียบ.
keywords:
- how to preserve metadata
- keep custom properties
- metadata preservation .NET
lastmod: '2026-06-05'
linktitle: Metadata Preservation Tutorial
schemas:
- author: GroupDocs
  dateModified: '2026-06-05'
  description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  headline: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  type: TechArticle
- description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  name: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  steps:
  - name: Initialize Your Comparer Object
    text: 'The `Comparer` class is the core component that performs document comparison
      and controls output options. Load the source (original) file and create a `Comparer`
      instance: **Why use `using` statements?** They automatically dispose of resources,
      preventing memory leaks when processing large documents'
  - name: Add the Target Document
    text: 'The `Add` method registers the target document whose changes will be compared
      against the source. Specify the updated file you want to compare: **Common mistake**:
      Confusing source and target. Think of it this way—source is your “original,”
      target is your “updated version.”'
  - name: Set the Metadata Type (The Magic Happens Here)
    text: '`CloneMetadataType` property determines which document''s metadata is copied
      to the result. Tell the comparer to keep the target’s metadata: **What’s happening?**
      `CloneMetadataType = MetadataType.Target` tells GroupDocs.Comparison: “Hey,
      I want to keep the target document’s metadata in my final resu'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'Use a `LoadOptions` object with the password, then pass it to the `Comparer`
      constructor:'
    question: How do I handle password‑protected documents?
  - answer: The current API preserves **all** metadata from the chosen source (Target
      or Source). For granular control you’d need to extract the properties after
      comparison and re‑apply them manually.
    question: Is there a way to preserve only selected metadata properties?
  - answer: Most common business formats—DOCX, PDF, PPTX, XLSX, and many others—support
      metadata preservation. See the official docs for the full list.
    question: Which document formats support metadata preservation?
  type: FAQPage
tags:
- GroupDocs.Comparison
- metadata-preservation
- dotnet-tutorial
- document-management
title: วิธีการรักษา Metadata ด้วย GroupDocs Comparison – .NET Tutorial
type: docs
url: /th/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# วิธีการรักษา Metadata กับ GroupDocs Comparison – .NET Tutorial

## บทนำ

เคยเปรียบเทียบเอกสารสองไฟล์แล้วทำให้ metadata ที่สำคัญหายไปหรือไม่? คุณไม่ได้เป็นคนเดียว เมื่อคุณต้อง **preserve target metadata** ขณะเปรียบเทียบเอกสารในแอปพลิเคชัน .NET งานนี้อาจดูซับซ้อน—แต่ไม่จำเป็นต้องเป็นเช่นนั้น บทเรียนนี้จะแสดง **how to preserve metadata** เพื่อให้ไฟล์ผลลัพธ์คงผู้เขียน วันที่สร้าง และคุณสมบัติที่กำหนดเองที่คุณต้องการไว้

## คำตอบอย่างรวดเร็ว
- **What does “preserve target metadata” mean?** มันจะเก็บ metadata (ผู้เขียน, วันที่สร้าง, คุณสมบัติที่กำหนดเอง ฯลฯ) จากเอกสารที่คุณกำหนดเป็น target เมื่อสร้างผลลัพธ์การเปรียบเทียบ  
- **Which GroupDocs.Comparison version is required?** เวอร์ชัน 25.4.0 หรือใหม่กว่า  
- **Can I use this with .NET Core?** ใช่ – .NET Core 2.0+ หรือ .NET Framework 4.6.1+  
- **Is a license needed for production?** จำเป็นต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง; เวอร์ชันทดลองฟรีใช้ได้สำหรับการเรียนรู้  
- **Will the feature work with PDF and DOCX?** ใช่ – รูปแบบ Office และ PDF หลักทั้งหมดรองรับการรักษา metadata  

## การรักษา metadata คืออะไร?
การรักษา metadata หมายถึงการคงข้อมูลอธิบายของเอกสารต้นฉบับ—เช่น ผู้เขียน, ชื่อเรื่อง, หมายเลขรุ่น, และคุณสมบัติที่กำหนดเอง—ให้คงอยู่หลังการประมวลผล ใน GroupDocs.Comparison คุณสามารถกำหนดได้ว่า metadata ของเอกสาร source หรือ target จะคงอยู่ในผลลัพธ์การเปรียบเทียบสุดท้าย

## ทำไมการรักษา Metadata ถึงสำคัญ
การรักษา metadata มีความสำคัญเพราะหลายอุตสาหกรรมถือว่าเป็นหลักฐานทางกฎหมายหรือข้อมูลที่สำคัญต่อธุรกิจ **ทำไม?** เนื่องจาก metadata บันทึกความเป็นเจ้าของ, ป้ายกำกับการปฏิบัติตาม, ประวัติรุ่น, และเส้นทางการตรวจสอบที่องค์กรพึ่งพาเพื่อการรายงานตามกฎระเบียบ, การจัดการสัญญา, และการอ้างอิงเชิงวิชาการ การสูญเสียข้อมูลนี้อาจทำให้เอกสารสูญเสียสถานะทางกฎหมายหรือทำให้กระบวนการอัตโนมัติเกิดข้อผิดพลาด

## ข้อกำหนดเบื้องต้น

### ไลบรารีและเวอร์ชันที่ต้องการ
- **GroupDocs.Comparison for .NET**: เวอร์ชัน 25.4.0 หรือใหม่กว่า (เวอร์ชันก่อนหน้ามีตัวเลือก metadata จำกัด)  
- **.NET Framework**: 4.6.1 หรือสูงกว่า, หรือ .NET Core 2.0+  

### การตั้งค่าสภาพแวดล้อม
- Visual Studio (หรือ IDE C# ใดก็ได้ที่คุณชอบ)  
- ความรู้พื้นฐาน C# (ไม่มีอะไรซับซ้อนเกินไป, สัญญา!)  
- เอกสารตัวอย่างสองไฟล์สำหรับการทดสอบ (Word *.docx* ทำงานได้ดี)  

### ความรู้ที่ต้องมีล่วงหน้า
คุณไม่จำเป็นต้องเป็นผู้เชี่ยวชาญ GroupDocs, แต่ควรคุ้นเคยกับ:
- คำสั่ง `using` ของ C# และการจัดการไฟล์  
- แนวคิดพื้นฐานของการประมวลผลเอกสาร  
- ความหมายของ metadata (ผู้เขียน, ชื่อเรื่อง, คุณสมบัติที่กำหนดเอง ฯลฯ)  

พร้อมหรือยัง? มาเริ่มตั้งค่ากัน

## การตั้งค่า GroupDocs.Comparison สำหรับ .NET

การติดตั้ง GroupDocs.Comparison นั้นง่ายดาย, แต่มีข้อควรระวังบางอย่างที่ต้องใส่ใจ

### ตัวเลือกการติดตั้ง

**NuGet Package Manager Console** (วิธีที่ง่ายที่สุด):
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI** (หากคุณต้องการใช้บรรทัดคำสั่ง):
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**Pro tip**: ควรระบุเวอร์ชันเสมอเพื่อหลีกเลี่ยงการเปลี่ยนแปลงที่ทำให้โค้ดเสียหายในโครงการของคุณ

### การได้รับลิขสิทธิ์
นี่คือจุดที่นักพัฒนาหลายคนติดขัดในตอนแรก GroupDocs.Comparison ไม่ฟรี, แต่คุณมีตัวเลือก:
- **Free Trial** – ฟังก์ชันเต็มสำหรับ 30 วัน, เหมาะสำหรับการประเมิน  
- **Temporary License** – ระยะเวลาประเมินต่อเนื่องหากคุณต้องการเวลาเพิ่ม  
- **Commercial License** – สำหรับการใช้งานในผลิตภัณฑ์ (มีระดับราคาให้เลือกหลายระดับ)  

ไม่ต้องกังวลเรื่องลิขสิทธิ์ในตอนนี้หากคุณเพียงแค่เรียนรู้—เวอร์ชันทดลองรวมคุณสมบัติ **preserve target metadata** ทั้งหมด

### การตรวจสอบการตั้งค่าเบื้องต้น
มาทดสอบให้แน่ใจว่าทุกอย่างทำงานด้วยการทดสอบง่าย ๆ:
```csharp
using System.IO;
using GroupDocs.Comparison;

string sourceFilePath = "source.docx";
string targetFilePath = "target.docx";

// Initialize the Comparer object.
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Add the target document for comparison.
    comparer.Add(targetFilePath);
}
```

หากโค้ดนี้คอมไพล์โดยไม่มีข้อผิดพลาด, คุณพร้อมแล้ว. หากไม่, ตรวจสอบการติดตั้งแพ็กเกจและคำสั่ง `using` อีกครั้ง

## วิธีการรักษา Target Metadata
เพื่อรักษา target metadata, คุณต้องกำหนดค่า comparer ให้คัดลอก metadata จากเอกสาร target ก่อนสร้างผลลัพธ์ ซึ่งทำโดยตั้งค่า property `CloneMetadataType` เป็น `MetadataType.Target` บนอินสแตนซ์ `Comparer` ด้วยวิธีนี้ ฟิลด์ metadata ทั้งหมด—ผู้เขียน, วันที่สร้าง, คุณสมบัติที่กำหนดเอง—จะถูกคัดลอกจาก target ไปยังไฟล์ผลลัพธ์, ทำให้ข้อมูลของเอกสารที่อัปเดตถูกเก็บไว้

### ทำความเข้าใจการไหลของ Metadata
ในกระบวนการเปรียบเทียบทั่วไป:
1. **Source document** ให้เนื้อหาพื้นฐาน.  
2. **Target document** ให้การเปลี่ยนแปลงเพื่อเปรียบเทียบ.  
3. **output document** รวมทั้งสอง, แต่ metadata ของใครจะชนะ?  

โดยค่าเริ่มต้น, GroupDocs.Comparison ใช้ metadata ของเอกสาร source. เพื่อ **preserve target metadata**, คุณต้องบอก API อย่างชัดเจน

### การดำเนินการทีละขั้นตอน

#### ขั้นตอนที่ 1: เริ่มต้นอ็อบเจ็กต์ Comparer ของคุณ
คลาส `Comparer` เป็นส่วนสำคัญที่ทำการเปรียบเทียบเอกสารและควบคุมตัวเลือกผลลัพธ์ โหลดไฟล์ source (ต้นฉบับ) และสร้างอินสแตนซ์ `Comparer`:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**Why use `using` statements?** พวกมันจะทำการปล่อยทรัพยากรโดยอัตโนมัติ, ป้องกันการรั่วของหน่วยความจำเมื่อประมวลผลเอกสารขนาดใหญ่ เชื่อฉันเถอะ คุณจะขอบคุณตัวเองในภายหลังเมื่อจัดการไฟล์ Word ขนาด 50 MB

#### ขั้นตอนที่ 2: เพิ่มเอกสาร Target
เมธอด `Add` ลงทะเบียนเอกสาร target ที่การเปลี่ยนแปลงจะถูกเปรียบเทียบกับ source. ระบุไฟล์ที่อัปเดตที่คุณต้องการเปรียบเทียบ:
```csharp
comparer.Add(targetFilePath);
```

**Common mistake**: สับสนระหว่าง source และ target. คิดแบบนี้—source คือ “ต้นฉบับ”, target คือ “เวอร์ชันที่อัปเดต”

#### ขั้นตอนที่ 3: ตั้งค่า Metadata Type (จุดที่สำคัญเกิดขึ้นที่นี่)
property `CloneMetadataType` กำหนดว่า metadata ของเอกสารใดจะถูกคัดลอกไปยังผลลัพธ์ บอก comparer ให้เก็บ metadata ของ target:
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**What’s happening?** `CloneMetadataType = MetadataType.Target` บอก GroupDocs.Comparison ว่า “ฉันต้องการเก็บ metadata ของเอกสาร target ไว้ในผลลัพธ์สุดท้าย”

### ตัวอย่างการทำงานครบถ้วน
นี่คือทั้งหมดรวมกันในโปรแกรมที่สามารถรันได้:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            string sourceFile = "original_document.docx";
            string targetFile = "updated_document.docx";
            string outputFile = "comparison_result.docx";
            
            using (Comparer comparer = new Comparer(sourceFile))
            {
                comparer.Add(targetFile);
                
                // Preserve target document metadata
                comparer.Compare(outputFile, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                
                Console.WriteLine($"Comparison completed! Check {outputFile}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error during comparison: {ex.Message}");
        }
    }
}
```

### ข้อผิดพลาดทั่วไปที่ควรหลีกเลี่ยง
**File Path Issues** – ควรใช้เส้นทางเต็มหรือให้แน่ใจว่าไฟล์ของคุณอยู่ในไดเรกทอรีทำงาน:
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

**Memory Management** – สำหรับเอกสารขนาดใหญ่, ควรห่ออ็อบเจ็กต์ `Comparer` ด้วยคำสั่ง `using` เสมอ

**Version Compatibility** – รุ่นต่าง ๆ ของ GroupDocs.Comparison มีตัวเลือก metadata ที่แตกต่างกัน—ใช้เวอร์ชัน 25.4.0 หรือใหม่กว่าเพื่อผลลัพธ์ที่ดีที่สุด

## สถานการณ์ Metadata ขั้นสูง

### เมื่อใดควรใช้ Target หรือ Source Metadata
| สถานการณ์ | Prefer **Target** Metadata | Prefer **Source** Metadata |
|----------|----------------------------|----------------------------|
| ต้องการข้อมูลผู้เขียนที่อัปเดต | ✅ | ❌ |
| เอกสารต้นฉบับมีอำนาจทางกฎหมาย | ❌ | ✅ |
| คุณสมบัติที่กำหนดเองเพิ่มเฉพาะในไฟล์ใหม่ | ✅ | ❌ |
| คุณต้องการเก็บประวัติของเอกสาร “หลัก” | ❌ | ✅ |

### การจัดการหลายเอกสาร Target
คุณสามารถเปรียบเทียบกับหลาย target ได้พร้อมกับยังคงรักษา metadata จาก target แรกที่คุณเพิ่ม:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath1);
    comparer.Add(targetFilePath2);
    comparer.Add(targetFilePath3);
    
    // Metadata will come from the first target document
    comparer.Compare(outputFileName, new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    });
}
```

## การประยุกต์ใช้และกรณีการใช้งาน

### การจัดการเอกสารทางกฎหมาย
บริษัทกฎหมายมักต้องการเปรียบเทียบเวอร์ชันสัญญาโดยคงรักษาตัวบ่งชี้ metadata เฉพาะ:
```csharp
// Preserve client metadata from updated contract
using (Comparer comparer = new Comparer("original_contract.docx"))
{
    comparer.Add("client_revised_contract.docx");
    
    comparer.Compare("final_contract_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep client's metadata
    });
}
```

### การทำงานร่วมกันทางวิชาการและการวิจัย
เมื่อหลายนักวิจัยทำงานร่วมกัน, คุณต้องการรักษาข้อมูลผู้เขียนล่าสุด:
```csharp
// Keep metadata from the researcher's latest submission
using (Comparer comparer = new Comparer("draft_paper.docx"))
{
    comparer.Add("researcher_updates.docx");
    
    comparer.Compare("paper_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Preserve researcher metadata
    });
}
```

### กระบวนการปฏิบัติตามข้อกำหนดขององค์กร
ในอุตสาหกรรมที่มีการควบคุม, การรักษา metadata การปฏิบัติตามเป็นสิ่งสำคัญ:
```csharp
// Preserve compliance tags from updated policy document
using (Comparer comparer = new Comparer("old_policy.docx"))
{
    comparer.Add("compliance_approved_policy.docx");
    
    comparer.Compare("policy_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep compliance metadata
    });
}
```

## การแก้ไขปัญหาทั่วไป

### ข้อผิดพลาด “File Not Found”
ปัญหาที่พบบ่อยที่สุด. ดีบักด้วยการตรวจสอบอย่างชัดเจน:
```csharp
string sourceFile = "source.docx";

// Always check if files exist before comparison
if (!File.Exists(sourceFile))
{
    Console.WriteLine($"Source file not found: {Path.GetFullPath(sourceFile)}");
    return;
}

// Same for target files
if (!File.Exists(targetFile))
{
    Console.WriteLine($"Target file not found: {Path.GetFullPath(targetFile)}");
    return;
}
```

### ปัญหาหน่วยความจำกับเอกสารขนาดใหญ่
สำหรับเอกสารที่มีขนาดเกิน 10 MB, พิจารณาการปรับแต่งต่อไปนี้:
```csharp
// Use explicit disposal for large documents
using (var comparer = new Comparer(sourceFile))
{
    comparer.Add(targetFile);
    
    var saveOptions = new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    };
    
    comparer.Compare(outputFile, saveOptions);
    
    // Explicitly clean up
    GC.Collect();
    GC.WaitForPendingFinalizers();
}
```

### ปัญหาการอนุญาตและการเข้าถึง
เมื่อทำงานกับไฟล์ที่ป้องกันหรือแชร์บนเครือข่าย:
```csharp
try
{
    using (var comparer = new Comparer(sourceFile))
    {
        comparer.Add(targetFile);
        comparer.Compare(outputFile, new SaveOptions() 
        { 
            CloneMetadataType = MetadataType.Target 
        });
    }
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine("Access denied. Check file permissions.");
    Console.WriteLine($"Details: {ex.Message}");
}
catch (IOException ex)
{
    Console.WriteLine("File I/O error occurred.");
    Console.WriteLine($"Details: {ex.Message}");
}
```

## การพิจารณาประสิทธิภาพและแนวทางปฏิบัติที่ดีที่สุด

### การจัดการหน่วยความจำ
GroupDocs.Comparison สามารถใช้หน่วยความจำมาก. ใช้คำสั่ง `using` เพื่อรับประกันการปล่อยทรัพยากร:
```csharp
// Good - automatic resource cleanup
using (var comparer = new Comparer(sourceFile))
{
    // comparison logic here
}

// Bad - potential memory leaks
var comparer = new Comparer(sourceFile);
// ... comparison logic
// comparer.Dispose(); // Easy to forget!
```

**Process Documents in Batches** – หากคุณกำลังเปรียบเทียบหลายไฟล์, ให้จัดการเป็นกลุ่มเล็ก ๆ เพื่อรักษาการใช้หน่วยความจำน้อย

### การทำงานแบบ Async เพื่อประสิทธิภาพที่ดีขึ้น
สำหรับแอปเดสก์ท็อปหรือเว็บ, ห่อการเปรียบเทียบในเมธอด async:
```csharp
public async Task<bool> CompareDocumentsAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                comparer.Compare(output, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```

### แนวทางขนาดไฟล์
- **Small (< 1 MB)** – ประมวลผลโดยตรง.  
- **Medium (1‑10 MB)** – แสดงความคืบหน้าเพื่อให้ UI ตอบสนอง.  
- **Large (> 10 MB)** – ควรใช้การประมวลผลแบบ async เสมอและพิจารณาเรียก GC อย่างชัดเจนตามที่แสดงข้างต้น  

## การบูรณาการกับระบบขนาดใหญ่

### การบูรณาการกับ ASP.NET Core
ด้านล่างเป็นคอนโทรลเลอร์พร้อมใช้งานที่รับไฟล์อัปโหลดสองไฟล์, ทำการเปรียบเทียบ, และส่งคืนผลลัพธ์พร้อม **preserving target metadata**:
```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare-with-target-metadata")]
    public async Task<IActionResult> CompareWithTargetMetadata(
        IFormFile sourceFile, 
        IFormFile targetFile)
    {
        var tempSource = Path.GetTempFileName();
        var tempTarget = Path.GetTempFileName();
        var outputPath = Path.GetTempFileName();
        
        try
        {
            // Save uploaded files temporarily
            await sourceFile.CopyToAsync(new FileStream(tempSource, FileMode.Create));
            await targetFile.CopyToAsync(new FileStream(tempTarget, FileMode.Create));
            
            // Perform comparison with target metadata preservation
            using (var comparer = new Comparer(tempSource))
            {
                comparer.Add(tempTarget);
                comparer.Compare(outputPath, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
            }
            
            // Return comparison result
            var resultBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(resultBytes, "application/vnd.openxmlformats-officedocument.wordprocessingml.document", 
                       "comparison_result.docx");
        }
        finally
        {
            // Clean up temporary files
            if (System.IO.File.Exists(tempSource)) System.IO.File.Delete(tempSource);
            if (System.IO.File.Exists(tempTarget)) System.IO.File.Delete(tempTarget);
            if (System.IO.File.Exists(outputPath)) System.IO.File.Delete(outputPath);
        }
    }
}
```

## คำถามที่พบบ่อย

**Q: Can I preserve metadata from multiple target documents when comparing?**  
A: เมื่อคุณเพิ่มไฟล์ target หลายไฟล์, GroupDocs.Comparison จะใช้ metadata จากเอกสาร target **แรก** ที่เพิ่มเข้ามา. ให้เพิ่มเอกสารที่คุณต้องการเก็บ metadata ก่อนเป็นอันดับแรกในลำดับ  

**Q: What happens if the target document lacks some metadata fields?**  
A: จะคัดลอกเฉพาะ metadata ที่มีอยู่ใน target ไปยังผลลัพธ์. ฟิลด์ที่ขาดหายจะถูกละเว้น; การเปรียบเทียบยังคงสำเร็จ  

**Q: How do I handle password‑protected documents?**  
A: ใช้วัตถุ `LoadOptions` พร้อมรหัสผ่าน, แล้วส่งให้กับคอนสตรัคเตอร์ของ `Comparer`:
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**Q: Is there a way to preserve only selected metadata properties?**  
A: API ปัจจุบันจะรักษา **ทั้งหมด** ของ metadata จากแหล่งที่เลือก (Target หรือ Source). หากต้องการควบคุมแบบละเอียด คุณต้องดึงคุณสมบัตินั้นหลังการเปรียบเทียบและนำกลับมาใช้ใหม่ด้วยตนเอง  

**Q: Which document formats support metadata preservation?**  
A: รูปแบบธุรกิจที่พบบ่อย—DOCX, PDF, PPTX, XLSX, และอื่น ๆ มากมาย—รองรับการรักษา metadata. ดูเอกสารอย่างเป็นทางการสำหรับรายการเต็ม  

**Q: Where can I get help if I run into issues?**  
A: เยี่ยมชม [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) เพื่อรับความช่วยเหลือจากชุมชน, หรือ ติดต่อฝ่ายสนับสนุนของ GroupDocs โดยตรงหากคุณมีลิขสิทธิ์เชิงพาณิชย์  

## แหล่งข้อมูลเพิ่มเติม
- **Official Documentation**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **API Reference**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Download Latest Version**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Free Trial**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Purchase Options**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)  

---

**Last Updated:** 2026-06-05  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs  

---

## บทเรียนที่เกี่ยวข้อง
- [Metadata ของเอกสาร .NET - บันทึกและรักษาคุณสมบัติที่กำหนดเอง](/comparison/net/loading-and-saving-documents/saving-user-defined-document-metadata/)  
- [การจัดการ Metadata ของเอกสาร .NET - คู่มือครบสำหรับ GroupDocs.Comparison](/comparison/net/metadata-management/)  
- [รับคุณสมบัติของเอกสาร C# .NET - ดึง Metadata ของไฟล์](/comparison/net/basic-usage/get-document-info-from-path/)