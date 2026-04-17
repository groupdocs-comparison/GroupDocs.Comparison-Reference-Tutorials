---
categories:
- File Comparison
date: '2026-04-10'
description: เรียนรู้วิธีเปรียบเทียบไฟล์ Excel อย่างโปรแกรมเมติกใน .NET ด้วย GroupDocs.Comparison
  การสอนแบบขั้นตอนพร้อมตัวอย่างโค้ด การแก้ไขปัญหา และแนวปฏิบัติที่ดีที่สุด.
keywords:
- how to compare excel
- excel file diff tool
- automate excel comparison
lastmod: '2026-04-10'
linktitle: คู่มือ .NET การเปรียบเทียบไฟล์ Excel
tags:
- excel
- dotnet
- groupdocs
- file-comparison
- csharp
title: วิธีเปรียบเทียบไฟล์ Excel ใน .NET
type: docs
url: /th/net/basic-comparison/compare-excel-files-dotnet-groupdocs-comparison/
weight: 1
---

# วิธีเปรียบเทียบไฟล์ Excel ใน .NET

เคยพบว่าตัวเองต้องตรวจสอบความแตกต่างระหว่างไฟล์ Excel สองไฟล์ด้วยตนเองหรือไม่? ไม่ว่าจะเป็นการติดตามการเปลี่ยนแปลงในรายงานการเงิน, การเปรียบเทียบเวอร์ชันของชุดข้อมูล, หรือการตรวจสอบความสมบูรณ์ของข้อมูล, การเปรียบเทียบด้วยมือใช้เวลามากและเสี่ยงต่อข้อผิดพลาด. ในคู่มือนี้, **คุณจะได้เรียนรู้วิธีเปรียบเทียบไฟล์ excel อย่างรวดเร็วและเชื่อถือได้โดยใช้ GroupDocs.Comparison สำหรับ .NET**.

## คำตอบอย่างรวดเร็ว
- **ไลบรารีที่ฉันสามารถใช้ได้คืออะไร?** GroupDocs.Comparison for .NET  
- **ต้องใช้บรรทัดโค้ดกี่บรรทัด?** น้อยกว่า 10 บรรทัดสำหรับการเปรียบเทียบพื้นฐาน  
- **ฉันสามารถเปรียบเทียบ Excel workbook ขนาดใหญ่ได้หรือไม่?** ใช่ – ใช้ตัวเลือกประสิทธิภาพเพื่อจัดการไฟล์ขนาดใหญ่  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานจริง  
- **เป็นไปได้หรือไม่ที่จะทำการเปรียบเทียบ excel แบบอัตโนมัติในเว็บ API?** แน่นอน – ดูตัวอย่างคอนโทรลเลอร์ ASP.NET  

## ทำไมต้องเปรียบเทียบไฟล์ Excel ด้วยโปรแกรม?
ก่อนที่เราจะลงมือเขียนโค้ด, มาพูดถึงเหตุผลที่การเปรียบเทียบ Excel แบบอัตโนมัติเป็นการเปลี่ยนเกม:

- **การควบคุมเวอร์ชัน** – ติดตามการเปลี่ยนแปลงระหว่างเวอร์ชันของเอกสารโดยอัตโนมัติโดยไม่ต้องเปิดไฟล์ด้วยตนเอง  
- **การตรวจสอบข้อมูล** – รับประกันความสอดคล้องของข้อมูลระหว่างแผนกและระบบต่าง ๆ  
- **การประกันคุณภาพ** – ตรวจจับความคลาดเคลื่อนในรายงานก่อนที่ข้อมูลจะถึงผู้มีส่วนได้ส่วนเสีย  
- **การอัตโนมัติกระบวนการทำงาน** – ผสานตรรกะการเปรียบเทียบเข้าไปในกระบวนการธุรกิจที่ใหญ่ขึ้น  

ไลบรารี GroupDocs.Comparison จัดการงานหนักทั้งหมด, ดังนั้นคุณไม่ต้องกังวลเรื่องการแยกวิเคราะห์รูปแบบ Excel หรือการเขียนอัลกอริธึม diff ที่ซับซ้อน.

## เครื่องมือเปรียบเทียบไฟล์ Excel คืออะไร?
**เครื่องมือเปรียบเทียบไฟล์ excel** เปรียบเทียบเวอร์ชันสเปรดชีตสองเวอร์ชันและไฮไลท์การเพิ่ม, การลบ, และการแก้ไข. GroupDocs.Comparison ทำหน้าที่เป็นเครื่องมือ diff ที่ทรงพลังและทำงานโดยตรงจากโค้ด .NET ของคุณ.

## ข้อกำหนดเบื้องต้นและการตั้งค่า

### สิ่งที่คุณต้องการ
- **สภาพแวดล้อมการพัฒนา**: Visual Studio 2019 หรือใหม่กว่า (VS Code ก็ใช้ได้เช่นกัน)  
- **ไลบรารี GroupDocs.Comparison**: Version 25.4.0 หรือใหม่กว่า  
- **ความรู้พื้นฐาน**: ความคุ้นเคยกับ C# และการจัดการไฟล์ใน .NET  
- **ไฟล์ตัวอย่าง**: ไฟล์ Excel สองไฟล์สำหรับทดสอบ (เราจะแสดงวิธีสร้างสถานการณ์ทดสอบ)

### การติดตั้ง GroupDocs.Comparison สำหรับ .NET
คุณมีตัวเลือกการติดตั้งหลายวิธี:

#### ตัวเลือกที่ 1: คอนโซล NuGet Package Manager
```shell
dotnet add package GroupDocs.Comparison --version 25.4.0
```

#### ตัวเลือกที่ 2: Visual Studio Package Manager
1. คลิกขวาที่โปรเจกต์ของคุณใน Solution Explorer  
2. เลือก **Manage NuGet Packages**  
3. ค้นหา **GroupDocs.Comparison**  
4. ติดตั้งเวอร์ชันล่าสุด  

### ตัวเลือกการให้ลิขสิทธิ์
ขณะเริ่มต้น, คุณสามารถใช้ GroupDocs.Comparison ด้วยการทดลองใช้ฟรี. สำหรับการใช้งานในผลิตภัณฑ์, คุณจะต้องมีไลเซนส์:

- **ทดลองใช้ฟรี**: ฟังก์ชันเต็มพร้อมลายน้ำการประเมิน  
- **ไลเซนส์ชั่วคราว**: [ขอที่นี่](https://purchase.groupdocs.com/temporary-license/) for testing  
- **ไลเซนส์เชิงพาณิชย์**: [ตัวเลือกการซื้อ](https://purchase.groupdocs.com/buy) for production use  

## วิธีเปรียบเทียบไฟล์ Excel ด้วย GroupDocs.Comparison
ตอนนี้เราจะสร้างโซลูชันการเปรียบเทียบไฟล์ Excel ที่สมบูรณ์. เราจะเริ่มจากพื้นฐานและเพิ่มฟีเจอร์ที่ซับซ้อนขึ้นตามลำดับ.

### ขั้นตอนที่ 1: การตั้งค่าโปรเจกต์พื้นฐาน
แรกเริ่ม, สร้างโปรเจกต์ C# ใหม่และเพิ่ม `using` statements ที่จำเป็น:

```csharp
using GroupDocs.Comparison;
using System;
using System.IO;
```

### ขั้นตอนที่ 2: กำหนดเส้นทางไฟล์
ตั้งค่าเส้นทางไฟล์ของคุณในรูปแบบที่สะอาดและดูแลได้ง่าย:

```csharp
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string resultOutputDirectory = "YOUR_OUTPUT_DIRECTORY";

string sourceFilePath = Path.Combine(documentDirectory, "source_cells.xlsx");
string targetFilePath = Path.Combine(documentDirectory, "target_cells.xlsx");
string resultFilePath = Path.Combine(resultOutputDirectory, "comparison_result.xlsx");
```

**Pro Tip**: ใช้เส้นทางแบบ relative เพื่อความพกพาที่ดีกว่าในสภาพแวดล้อมการพัฒนา. ตัวอย่างเช่น `Path.Combine("TestData", "source_cells.xlsx")` ทำงานได้ดีในหลายสถานการณ์.

### ขั้นตอนที่ 3: เริ่มต้น Comparer
นี่คือจุดที่เวทมนตร์เกิดขึ้น. คลาส `Comparer` เป็นจุดเริ่มต้นสำหรับการดำเนินการเปรียบเทียบทั้งหมด:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Add target file for comparison
    comparer.Add(targetFilePath);
}
```

**What's happening here?** ตัวสร้าง `Comparer` โหลดไฟล์ Excel ต้นฉบับของคุณเข้าสู่หน่วยความจำและเตรียมพร้อมสำหรับการเปรียบเทียบ. คำสั่ง `using` ทำให้แน่ใจว่ามีการทำความสะอาดทรัพยากรอย่างเหมาะสม – สิ่งนี้สำคัญเมื่อจัดการไฟล์ Excel ที่อาจมีขนาดใหญ่.

### ขั้นตอนที่ 4: ดำเนินการเปรียบเทียบ
ต่อไปคือการเปรียบเทียบจริง. มันง่ายกว่าที่คิด:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath);
    // Compare and save results
    comparer.Compare(resultFilePath);
}
```

**Behind the scenes**, GroupDocs.Comparison วิเคราะห์ไฟล์ทั้งสองเซลล์ต่อเซลล์, ระบุ:
- แถวและคอลัมน์ที่เพิ่มเข้ามา  
- เนื้อหาที่ถูกลบ  
- ค่าเซลล์ที่แก้ไข  
- การเปลี่ยนแปลงรูปแบบ  
- ความแตกต่างของสูตร  

ผลลัพธ์จะถูกบันทึกลงไฟล์ผลลัพธ์ที่คุณระบุพร้อมกับการไฮไลท์ความแตกต่างอย่างชัดเจน.

### ขั้นตอนที่ 5: ตัวอย่างการทำงานที่สมบูรณ์
นี่คือตัวอย่างเต็มรูปแบบที่พร้อมใช้งานในสภาพแวดล้อมการผลิต:

```csharp
using GroupDocs.Comparison;
using System;
using System.IO;

class Program
{
    static Main()
    {
        try
        {
            // Set up file paths
            string documentDirectory = @"C:\TestFiles";
            string outputDirectory = @"C:\ComparisonResults";
            
            string sourceFile = Path.Combine(documentDirectory, "quarterly_report_v1.xlsx");
            string targetFile = Path.Combine(documentDirectory, "quarterly_report_v2.xlsx");
            string resultFile = Path.Combine(outputDirectory, "comparison_result.xlsx");
            
            // Ensure output directory exists
            Directory.CreateDirectory(outputDirectory);
            
            // Perform comparison
            using (Comparer comparer = new Comparer(sourceFile))
            {
                comparer.Add(targetFile);
                comparer.Compare(resultFile);
            }
            
            Console.WriteLine($"Comparison complete! Results saved to: {resultFile}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error during comparison: {ex.Message}");
        }
    }
}
```

## ทำให้การเปรียบเทียบ Excel เป็นอัตโนมัติ – ตัวเลือกการกำหนดค่าขั้นสูง
การเปรียบเทียบพื้นฐานมีประสิทธิภาพ, แต่คุณอาจต้องการการควบคุมที่ละเอียดขึ้น. นี่คือตัวเลือกขั้นสูงบางส่วน.

### ปรับแต่งการตั้งค่าการเปรียบเทียบ
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath);
    
    // Configure comparison options
    CompareOptions options = new CompareOptions()
    {
        ShowRevisions = true,
        DetectStyleChanges = true,
        GenerateSummaryPage = true
    };
    
    comparer.Compare(resultFilePath, options);
}
```

### การเปรียบเทียบหลายไฟล์
ต้องการเปรียบเทียบมากกว่าสองไฟล์? ไม่มีปัญหา:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFile1Path);
    comparer.Add(targetFile2Path);
    comparer.Add(targetFile3Path);
    
    comparer.Compare(resultFilePath);
}
```

## ตัวอย่างการใช้งานจริง

### สถานการณ์ที่ 1: การตรวจสอบรายงานการเงิน
```csharp
public class FinancialReportValidator
{
    public bool ValidateReportChanges(string previousReport, string currentReport)
    {
        string comparisonResult = Path.GetTempFileName() + ".xlsx";
        
        using (Comparer comparer = new Comparer(previousReport))
        {
            comparer.Add(currentReport);
            comparer.Compare(comparisonResult);
            
            // Check if there are significant changes
            return HasSignificantChanges(comparisonResult);
        }
    }
    
    private bool HasSignificantChanges(string comparisonFile)
    {
        // Your business logic here
        // For example, check if revenue columns changed by more than 5%
        return false;
    }
}
```

### สถานการณ์ที่ 2: การตรวจสอบการย้ายข้อมูล
```csharp
public class DataMigrationValidator
{
    public async Task<bool> VerifyMigration(string sourceData, string migratedData)
    {
        try
        {
            string resultPath = $"migration_validation_{DateTime.Now:yyyyMMdd_HHmmss}.xlsx";
            
            using (Comparer comparer = new Comparer(sourceData))
            {
                comparer.Add(migratedData);
                comparer.Compare(resultPath);
            }
            
            // Send result to stakeholders
            await NotifyStakeholders(resultPath);
            return true;
        }
        catch (Exception ex)
        {
            // Log error and handle gracefully
            Console.WriteLine($"Migration validation failed: {ex.Message}");
            return false;
        }
    }
}
```

## ปัญหาทั่วไปและวิธีแก้
แม้จะใช้ API ที่ตรงไปตรงมา, คุณอาจเจอความท้าทายบางอย่าง. นี่คือปัญหาที่พบบ่อยที่สุดและวิธีแก้ไข.

### ปัญหา 1: "File is being used by another process"
**Problem**: ไฟล์ Excel ถูกล็อกโดยแอปพลิเคชันอื่น.  
**Solution**: ใช้คำสั่ง `using` เสมอและตรวจสอบให้แน่ใจว่า Excel ไม่ได้เปิดอยู่:

```csharp
// Good practice
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Your comparison logic
}

// Check if file is in use before comparison
private bool IsFileLocked(string filePath)
{
    try
    {
        using (FileStream stream = File.Open(filePath, FileMode.Open, FileAccess.Read, FileShare.None))
        {
            return false;
        }
    }
    catch (IOException)
    {
        return true;
    }
}
```

### ปัญหา 2: ประสิทธิภาพไฟล์ขนาดใหญ่
**Problem**: การเปรียบเทียบใช้เวลานานเกินไปกับไฟล์ Excel ขนาดใหญ่.  
**Solution**: พิจารณากลยุทธ์การเพิ่มประสิทธิภาพต่อไปนี้:

```csharp
// Process files in chunks or limit comparison scope
CompareOptions options = new CompareOptions()
{
    // Only compare content, skip formatting for speed
    DetectStyleChanges = false,
    
    // Limit comparison to specific ranges if possible
    // Note: Range limitation may require custom implementation
};
```

### ปัญหา 3: การใช้หน่วยความจำ
**Problem**: แอปพลิเคชันใช้หน่วยความจำมากเกินไปกับไฟล์ขนาดใหญ่.  
**Solution**: ดำเนินการจัดการทรัพยากรอย่างเหมาะสม:

```csharp
public void CompareFilesWithMemoryManagement(string source, string target, string output)
{
    // Ensure garbage collection
    GC.Collect();
    GC.WaitForPendingFinalizers();
    
    using (Comparer comparer = new Comparer(source))
    {
        comparer.Add(target);
        comparer.Compare(output);
    }
    
    // Force cleanup
    GC.Collect();
}
```

## เคล็ดลับการเพิ่มประสิทธิภาพ – ตรวจจับการเปลี่ยนแปลงใน Excel อย่างรวดเร็ว

### แนวทางปฏิบัติที่ดีที่สุดในการจัดการหน่วยความจำ
1. **Always use `using` statements** for automatic resource disposal  
2. **Process files sequentially** rather than in parallel for large files  
3. **Consider file size limits** – break down massive files into smaller chunks  
4. **Monitor memory usage** during development and testing  

### การเพิ่มความเร็ว
```csharp
// Optimize for speed
CompareOptions fastOptions = new CompareOptions()
{
    DetectStyleChanges = false,        // Skip formatting comparison
    ShowRevisions = false,             // Skip revision tracking
    GenerateSummaryPage = false        // Skip summary generation
};
```

### กลยุทธ์การประมวลผลแบบแบตช์ – เปรียบเทียบ Excel Workbook ขนาดใหญ่อย่างมีประสิทธิภาพ
```csharp
public async Task CompareMultipleFilePairs(List<(string source, string target)> filePairs)
{
    foreach (var (source, target) in filePairs)
    {
        string output = $"comparison_{Path.GetFileNameWithoutExtension(source)}.xlsx";
        
        using (Comparer comparer = new Comparer(source))
        {
            comparer.Add(target);
            comparer.Compare(output);
        }
        
        // Small delay to prevent resource exhaustion
        await Task.Delay(100);
    }
}
```

## การรวมกับแอปพลิเคชัน ASP.NET – ทำให้การเปรียบเทียบ Excel เป็นอัตโนมัติผ่าน API
ต้องการเพิ่มการเปรียบเทียบ Excel ลงในเว็บแอปของคุณ? นี่คือตัวอย่างคอนโทรลเลอร์พื้นฐาน:

```csharp
[ApiController]
[Route("api/[controller]")]
public class ExcelComparisonController : ControllerBase
{
    [HttpPost("compare")]
    public async Task<IActionResult> CompareExcelFiles(IFormFile sourceFile, IFormFile targetFile)
    {
        if (sourceFile == null || targetFile == null)
            return BadRequest("Both source and target files are required.");
        
        try
        {
            // Save uploaded files temporarily
            string tempDir = Path.GetTempPath();
            string sourcePath = Path.Combine(tempDir, sourceFile.FileName);
            string targetPath = Path.Combine(tempDir, targetFile.FileName);
            string resultPath = Path.Combine(tempDir, $"comparison_{Guid.NewGuid()}.xlsx");
            
            using (var sourceStream = new FileStream(sourcePath, FileMode.Create))
            {
                await sourceFile.CopyToAsync(sourceStream);
            }
            
            using (var targetStream = new FileStream(targetPath, FileMode.Create))
            {
                await targetFile.CopyToAsync(targetStream);
            }
            
            // Perform comparison
            using (Comparer comparer = new Comparer(sourcePath))
            {
                comparer.Add(targetPath);
                comparer.Compare(resultPath);
            }
            
            // Return result file
            var resultBytes = await System.IO.File.ReadAllBytesAsync(resultPath);
            
            // Cleanup temporary files
            System.IO.File.Delete(sourcePath);
            System.IO.File.Delete(targetPath);
            System.IO.File.Delete(resultPath);
            
            return File(resultBytes, "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet", "comparison_result.xlsx");
        }
        catch (Exception ex)
        {
            return StatusCode(500, $"Comparison failed: {ex.Message}");
        }
    }
}
```

## เมื่อใดควรใช้การเปรียบเทียบไฟล์ Excel
การเปรียบเทียบ Excel มีคุณค่าเป็นพิเศษในสถานการณ์ต่อไปนี้:

### บริการทางการเงิน
- **การตรวจสอบรายงานไตรมาส** – เปรียบเทียบรายงานไตรมาสปัจจุบันกับไตรมาสก่อนหน้า  
- **การติดตามงบประมาณ** – ตรวจสอบการเปลี่ยนแปลงงบประมาณระหว่างแผนกต่าง ๆ  
- **การเตรียมการตรวจสอบ** – รับประกันความสอดคล้องของข้อมูลก่อนการตรวจสอบภายนอก  

### การจัดการข้อมูล
- **การตรวจสอบ ETL** – ยืนยันการแปลงข้อมูลระหว่างการย้ายข้อมูล  
- **การประกันคุณภาพ** – ตรวจสอบว่าข้อมูลที่นำเข้าแมตช์กับระบบต้นทาง  
- **การควบคุมเวอร์ชัน** – ติดตามการเปลี่ยนแปลงในไฟล์ข้อมูลหลัก  

### ข่าวกรองธุรกิจ
- **การตรวจสอบรายงาน** – เปรียบเทียบรายงานอัตโนมัติกับการคำนวณด้วยมือ  
- **การกระทบยอดข้อมูล** – จับคู่ข้อมูลระหว่างระบบต่าง ๆ  
- **การติดตามการเปลี่ยนแปลง** – ตรวจสอบการเปลี่ยนแปลง KPI ตามช่วงเวลา  

## คำถามที่พบบ่อย

**Q: ขนาดไฟล์สูงสุดที่ GroupDocs.Comparison สามารถจัดการได้คือเท่าไหร่?**  
A: ไลบรารีสามารถจัดการไฟล์ได้ถึงหลายร้อย MB, แต่ประสิทธิภาพขึ้นอยู่กับหน่วยความจำที่มี. สำหรับไฟล์ที่ใหญ่กว่า 50 MB, ควรพิจารณาการประมวลผลแบบแบ่งส่วนหรือวิธีการสตรีม.

**Q: ฉันสามารถเปรียบเทียบไฟล์ Excel ที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ได้, แต่คุณต้องระบุรหัสผ่านในกระบวนการเปรียบเทียบ. ไลบรารีรองรับไฟล์ Excel ที่เข้ารหัสด้วยข้อมูลประจำตัวที่เหมาะสม.

**Q: ความแม่นยำของการเปรียบเทียบไฟล์ Excel ที่ซับซ้อนพร้อมสูตรเป็นอย่างไร?**  
A: GroupDocs.Comparison ตรวจจับการเปลี่ยนแปลงสูตรได้อย่างแม่นยำ, รวมถึงการอ้างอิงเซลล์และการแก้ไขฟังก์ชัน. มันถือสูตรเป็นการเปลี่ยนแปลงเนื้อหาและไฮไลท์ตามนั้น.

**Q: ฉันสามารถปรับแต่งผลลัพธ์การเปรียบเทียบให้เป็นรูปแบบที่ต้องการได้หรือไม่?**  
A: ไลบรารีมีสไตล์การไฮไลท์ในตัวหลายแบบ. สำหรับการสไตล์แบบกำหนดเอง, คุณสามารถทำ post‑process ไฟล์ผลลัพธ์หรือสำรวจตัวเลือกสไตล์ของ API.

**Q: มีวิธีเปรียบเทียบเฉพาะ worksheets ที่ต้องการในไฟล์ Excel หรือไม่?**  
A: แม้ไลบรารีจะเปรียบเทียบไฟล์ทั้งหมดโดยค่าเริ่มต้น, คุณสามารถทำ pre‑process ไฟล์เพื่อดึง worksheets ที่ต้องการก่อนเปรียบเทียบ, หรือ post‑process ผลลัพธ์เพื่อกรองการเปลี่ยนแปลงที่เกี่ยวข้อง.

**Q: GroupDocs.Comparison ตรวจจับการเปลี่ยนแปลงใน Excel อย่างไร?**  
A: มันทำการ diff แบบ cell‑by‑cell, ตรวจสอบค่า, สูตร, การจัดรูปแบบ, และการเปลี่ยนแปลงโครงสร้างเช่นแถว/คอลัมน์ที่เพิ่มหรือถูกลบ.

**Q: เครื่องมือนี้ทำงานได้ดีกับ Excel Workbook ขนาดใหญ่มากหรือไม่?**  
A: ใช่ – โดยการปิดการตรวจจับสไตล์ (`DetectStyleChanges = false`) และใช้การประมวลผลแบบ batch คุณสามารถเปรียบเทียบไฟล์ Excel ขนาดใหญ่ได้อย่างมีประสิทธิภาพ.

## แหล่งข้อมูลเพิ่มเติม
- **เอกสารประกอบ**: [เอกสาร GroupDocs Comparison .NET](https://docs.groupdocs.com/comparison/net/)  
- **อ้างอิง API**: [อ้างอิง API GroupDocs Comparison .NET](https://reference.groupdocs.com/comparison/net/)  
- **ดาวน์โหลด**: [GroupDocs Releases for .NET](https://releases.groupdocs.com/comparison/net/)  
- **ซื้อไลเซนส์**: [ซื้อไลเซนส์ GroupDocs](https://purchase.groupdocs.com/buy)  
- **ทดลองใช้ฟรี**: [GroupDocs Free Trial](https://releases.groupdocs.com/comparison/net/)  
- **ไลเซนส์ชั่วคราว**: [ขอไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)  
- **ฟอรั่มสนับสนุน**: [Community สนับสนุน GroupDocs](https://forum.groupdocs.com/c/comparison/)  

---

**อัปเดตล่าสุด:** 2026-04-10  
**ทดสอบด้วย:** GroupDocs.Comparison 25.4.0  
**ผู้เขียน:** GroupDocs