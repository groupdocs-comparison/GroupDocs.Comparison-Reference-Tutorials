---
categories:
- String Manipulation
date: '2026-06-10'
description: เรียนรู้วิธีเปรียบเทียบสตริงใน C# ด้วย GroupDocs.Comparison ที่ให้ประสิทธิภาพการเปรียบเทียบสตริงที่รวดเร็วโดยไม่ต้องทำงานกับไฟล์
  – เหมาะสำหรับนักพัฒนา .NET
keywords:
- how to compare strings
- string comparison performance
- compare strings c#
- groupdocs comparison .net
- direct string comparison
lastmod: '2026-06-10'
linktitle: C# String Comparison บทแนะนำ
schemas:
- author: GroupDocs
  dateModified: '2026-06-10'
  description: Learn how to compare strings in C# using GroupDocs.Comparison, delivering
    fast string comparison performance without file operations – perfect for .NET
    developers.
  headline: How to Compare Strings in C# Without Files - GroupDocs Tutorial
  type: TechArticle
- description: Learn how to compare strings in C# using GroupDocs.Comparison, delivering
    fast string comparison performance without file operations – perfect for .NET
    developers.
  name: How to Compare Strings in C# Without Files - GroupDocs Tutorial
  steps:
  - name: Set Up Your Comparer Object
    text: 'The `Comparer` class is the core engine that evaluates differences between
      two pieces of text. `LoadOptions` specifies how the input is interpreted, allowing
      you to load raw text directly. Create the comparer with your source string and
      tell the library that you are loading raw text: **Why a `using`'
  - name: Add Your Target Text
    text: '`Add` registers a new document or string to be compared with the source.
      Now feed the text you want to compare against. You can add multiple targets
      if needed. The `Add` method registers a new document (or string) to be compared
      with the original source. You can call `Add` repeatedly to compare the '
  - name: Execute the Comparison
    text: '`Compare` runs the diff engine and returns a `ComparisonResult` containing
      change data. Trigger the diff algorithm. The `Compare` method performs the actual
      analysis, producing a `ComparisonResult` object that holds all change metadata.
      The underlying algorithm works at the character level, detectin'
  - name: Get Your Results
    text: '`GetResultString()` generates an HTML string highlighting insertions, deletions,
      and modifications. Finally, pull out a human‑readable diff. The `GetResultString()`
      method returns an HTML‑styled string where additions are highlighted in green,
      deletions in red, and modifications in yellow. You can r'
  type: HowTo
- questions:
  - answer: Yes, the algorithm scales linearly and remains fast for strings up to
      several megabytes; for > 10 MB, consider file‑based comparison for optimal performance.
    question: Can I compare strings of vastly different lengths efficiently?
  - answer: The library returns an empty diff, but it’s best practice to check `string.IsNullOrEmpty`
      beforehand to provide a clear user message.
    question: What happens if I try to compare null or empty strings?
  - answer: Each `Comparer` instance is single‑threaded; create a separate instance
      per thread or use a thread‑local pool for high concurrency.
    question: Is this thread‑safe for concurrent comparisons?
  - answer: '`string.Equals()` only tells you if the texts are identical. GroupDocs.Comparison
      adds diff detection with only a modest overhead—typically 3‑5 ms for 100 KB
      strings versus < 1 ms for a plain equality check.'
    question: How does this perform compared to `string.Equals()`?
  - answer: Yes, `ComparisonOptions` lets you change HTML markup, CSS classes, and
      even export to plain text or PDF.
    question: Can I customize the diff output format?
  type: FAQPage
tags:
- csharp
- dotnet
- text-comparison
- groupdocs
title: วิธีเปรียบเทียบสตริงใน C# โดยไม่ใช้ไฟล์ - GroupDocs Tutorial
type: docs
url: /th/net/basic-comparison/groupdocs-comparison-net-text-string-compare/
weight: 1
---

# วิธีเปรียบเทียบสตริงใน C# โดยไม่ใช้ไฟล์ - บทแนะนำ GroupDocs

เคยต้องเปรียบเทียบสตริงข้อความสองชุดในแอป .NET ของคุณ แต่กลัวความซับซ้อนของวิธีเปรียบเทียบแบบดั้งเดิมหรือไม่? คุณไม่ได้อยู่คนเดียว ไม่ว่าคุณจะกำลังสร้างระบบควบคุมเวอร์ชัน, ตรวจสอบข้อมูลผู้ใช้, หรือแค่ต้องการหาความแตกต่างระหว่างข้อความสองส่วน, การเปรียบเทียบสตริงอาจกลายเป็นปัญหาได้อย่างรวดเร็ว **ในคู่มือนี้คุณจะได้เรียนรู้วิธีเปรียบเทียบสตริงอย่างมีประสิทธิภาพ**, โดยใช้ GroupDocs.Comparison เพื่อไม่ต้องสัมผัสระบบไฟล์เลย

## คำตอบด่วน
- **ไลบรารีที่จัดการการเปรียบเทียบสตริงโดยตรงคืออะไร?** GroupDocs.Comparison for .NET.
- **ฉันต้องเขียนไฟล์ก่อนหรือไม่?** ไม่ – API ทำงานโดยตรงกับตัวแปรสตริง
- **เวอร์ชัน .NET ที่รองรับคืออะไร?** .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5/6/7.
- **ต้องมีลิขสิทธิ์สำหรับการใช้งานในโปรดักชันหรือไม่?** ใช่, จำเป็นต้องมีลิขสิทธิ์เต็มหรือชั่วคราวสำหรับการใช้งานในโปรดักชัน
- **ความเร็วของการเปรียบเทียบเป็นเท่าไหร่?** ทำงานในหน่วยความจำและโดยทั่วไปเร็วกว่า 3‑5× เท่ากว่าการเปรียบเทียบแบบไฟล์สำหรับข้อความขนาดเล็กถึงกลาง

## ทำไมต้องเลือกการเปรียบเทียบสตริงโดยตรง?

การเปรียบเทียบสตริงโดยตรงช่วยขจัดภาระการทำ I/O ของดิสก์, ให้คุณ **ได้เร็วขึ้นถึง 5×** สำหรับข้อความทั่วไปที่มีขนาดต่ำกว่า 500 KB. นอกจากนี้ยังลดความกดดันของหน่วยความจำเพราะไม่มีไฟล์ชั่วคราวถูกสร้าง, และทำให้สามารถให้ฟีดแบ็กแบบเรียลไทม์ในแอปพลิเคชันแบบโต้ตอบ เช่น แชทหรือการแก้ไขเอกสารแบบสด

## สิ่งที่คุณต้องเตรียมเพื่อเริ่มต้น

- **สภาพแวดล้อมการพัฒนา** – Visual Studio 2022 (หรือ IDE ที่รองรับ .NET ใดก็ได้) พร้อมติดตั้ง .NET Framework 4.6.1+ หรือ .NET Core 2.0+
- **ทักษะพื้นฐาน C#** – ความสามารถในการสร้างโปรเจกต์คอนโซลหรือเว็บ, เพิ่มคำสั่ง `using`, และสร้างอ็อบเจ็กต์
- **แพ็กเกจ NuGet ของ GroupDocs.Comparison** – เราจะติดตั้งในส่วนต่อไป

## การตั้งค่า GroupDocs.Comparison ในโปรเจกต์ของคุณ

คุณมีสองวิธีง่าย ๆ เพื่อเพิ่มไลบรารีเข้าสู่โซลูชันของคุณ

### ตัวเลือก 1: คอนโซล NuGet Package Manager

เปิด Package Manager Console ใน Visual Studio แล้วรัน:

```shell
Install-Package GroupDocs.Comparison -Version 25.4.0
```

### ตัวเลือก 2: .NET CLI

หากคุณชอบใช้บรรทัดคำสั่ง (หรือใช้ VS Code) ให้ดำเนินการ:

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**เคล็ดลับ**: ระบุเวอร์ชันเป็น `25.4.0` (หรือใหม่กว่า) เพื่อหลีกเลี่ยงการเปลี่ยนแปลงที่ทำให้เกิดปัญหาโดยไม่คาดคิด

### การจัดการลิขสิทธิ์ของคุณ

GroupDocs มีตัวเลือกลิขสิทธิ์หลายแบบตามความต้องการของคุณ:

- **ทดลองใช้ฟรี** – เหมาะสำหรับการทดสอบและโครงการขนาดเล็ก
- **ลิขสิทธิ์ชั่วคราว** – เหมาะสำหรับการประเมินขนาดใหญ่
- **ลิขสิทธิ์เต็ม** – จำเป็นสำหรับงานในโปรดักชัน

ไปที่ [หน้าซื้อ](https://purchase.groupdocs.com/buy) เพื่อสำรวจตัวเลือกเหล่านี้ สำหรับการเรียนรู้, การทดลองใช้ฟรีทำงานได้ดี

## วิธีเปรียบเทียบสตริงโดยตรงใน C#

GroupDocs.Comparison มี API ที่ทำงานในหน่วยความจำซึ่งให้คุณใส่สตริงข้อความสองชุดและรับผล diff อย่างละเอียดทันทีโดยไม่ต้องสัมผัสระบบไฟล์ โดยการสร้างอินสแตนซ์ `Comparer`, เพิ่มสตริงเป้าหมาย, และเรียก `Compare` คุณจะได้ `ComparisonResult` ที่สามารถแสดงเป็น HTML, plain text หรือ PDF ทำให้เหมาะกับแอปพลิเคชันแบบเรียลไทม์

### ขั้นตอนที่ 1: ตั้งค่าอ็อบเจ็กต์ Comparer ของคุณ

คลาส `Comparer` เป็นเอนจินหลักที่ประเมินความแตกต่างระหว่างข้อความสองส่วน

`LoadOptions` ระบุวิธีการตีความอินพุต, ให้คุณโหลดข้อความดิบโดยตรง

```csharp
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

สร้าง comparer ด้วยสตริงต้นฉบับของคุณและบอกไลบรารีว่าคุณกำลังโหลดข้อความดิบ:

```csharp
using (Comparer comparer = new Comparer("source text", new LoadOptions() { LoadText = true }))
{
    // Your comparison logic goes here
}
```

**ทำไมต้องใช้บล็อก `using`?** `Comparer` implements `IDisposable`; การห่อหุ้มช่วยให้แน่ใจว่าทรัพยากรที่ไม่ได้จัดการจะถูกปล่อยทันที, ซึ่งสำคัญเมื่อคุณทำการเปรียบเทียบหลายครั้งในลูป

### ขั้นตอนที่ 2: เพิ่มข้อความเป้าหมายของคุณ

`Add` ลงทะเบียนเอกสารหรือสตริงใหม่เพื่อเปรียบเทียบกับต้นฉบับ

ตอนนี้ใส่ข้อความที่คุณต้องการเปรียบเทียบ คุณสามารถเพิ่มเป้าหมายหลายรายการได้หากต้องการ

เมธอด `Add` ลงทะเบียนเอกสารใหม่ (หรือสตริง) เพื่อเปรียบเทียบกับต้นฉบับเดิม

```csharp
comparer.Add(targetString, new LoadOptions() { LoadText = true });
```

คุณสามารถเรียก `Add` ซ้ำหลายครั้งเพื่อเปรียบเทียบต้นฉบับกับหลายเวอร์ชัน

### ขั้นตอนที่ 3: ดำเนินการเปรียบเทียบ

`Compare` ทำงานของเอนจิน diff และคืนค่า `ComparisonResult` ที่มีข้อมูลการเปลี่ยนแปลง

เรียกใช้อัลกอริทึม diff

เมธอด `Compare` ทำการวิเคราะห์จริง ๆ, สร้างอ็อบเจ็กต์ `ComparisonResult` ที่เก็บเมตาดาต้าการเปลี่ยนแปลงทั้งหมด

```csharp
var result = comparer.Compare();
```

อัลกอริทึมพื้นฐานทำงานระดับอักขระ, ตรวจจับการแทรก, การลบ, และการแก้ไขด้วยเอนจินความคล้ายคลึงที่ได้รับสิทธิบัตร ซึ่งสมดุลระหว่างความเร็วและความแม่นยำ

### ขั้นตอนที่ 4: รับผลลัพธ์ของคุณ

`GetResultString()` สร้างสตริง HTML ที่ไฮไลท์การแทรก, การลบ, และการแก้ไข

สุดท้าย, ดึง diff ที่มนุษย์อ่านได้

เมธอด `GetResultString()` คืนค่าสตริงแบบ HTML ที่การเพิ่มจะแสดงเป็นสีเขียว, การลบเป็นสีแดง, และการแก้ไขเป็นสีเหลือง

```csharp
string diffHtml = result.GetResultString();
```

คุณสามารถเรนเดอร์ `diffHtml` ในเว็บวิว, ส่งในอีเมล, หรือบันทึกเพื่อการตรวจสอบ

## ควรใช้วิธีนี้เมื่อใด?

การเปรียบเทียบสตริงโดยตรงโดดเด่นเมื่อคุณต้องการ diff ที่ทันทีและใช้ทรัพยากรต่ำของข้อมูลในหน่วยความจำ เหมาะสำหรับการตรวจสอบผลลัพธ์ API, การแก้ไขร่วมแบบสด, การตรวจจับการเปลี่ยนแปลงการกำหนดค่า, การตรวจสอบการย้ายข้อมูล, และการเปรียบเทียบข้อความในแอปแชท สำหรับเอกสารขนาดใหญ่ (> 10 MB) หรือเมื่อคุณต้องรักษาเลย์เอาต์ซับซ้อน, การเปรียบเทียบแบบไฟล์อาจเหมาะกว่า

## ข้อผิดพลาดทั่วไปและวิธีหลีกเลี่ยง

### ลืมพารามิเตอร์ LoadOptions

ปัญหา: คุณได้รับข้อยกเว้น “ไฟล์ไม่พบ” แม้ว่าคุณจะส่งสตริงแล้ว  
วิธีแก้: ต้องรวม `new LoadOptions() { LoadText = true }` เสมอเมื่อสร้าง `Comparer` หรือเรียก `Add`

```csharp
// Wrong - will look for files named "source text"
using (Comparer comparer = new Comparer("source text"))

// Right - tells GroupDocs this is raw text
using (Comparer comparer = new Comparer("source text", new LoadOptions() { LoadText = true }))
```

### การรั่วของหน่วยความจำกับการเปรียบเทียบขนาดใหญ่

ปัญหา: การใช้หน่วยความจำเพิ่มขึ้นอย่างต่อเนื่องระหว่างการประมวลผลเป็นชุด  
วิธีแก้: ห่อ `Comparer` แต่ละตัวในบล็อก `using` และทำการ dispose อย่างทันท่วงที

```csharp
// This ensures proper cleanup
using (Comparer comparer = new Comparer(sourceText, new LoadOptions() { LoadText = true }))
{
    comparer.Add(targetText, new LoadOptions() { LoadText = true });
    comparer.Compare();
    string result = comparer.GetResultString();
    // comparer is automatically disposed here
}
```

### การจัดการสตริงที่เป็น Null หรือ Empty

ปัญหา: อินพุตเป็น Null ทำให้เกิด `ArgumentNullException`  
วิธีป้องกัน: ตรวจสอบอินพุตก่อนเรียกใช้ไลบรารี

```csharp
if (string.IsNullOrEmpty(sourceText) || string.IsNullOrEmpty(targetText))
{
    // Handle the edge case appropriately for your application
    return "Cannot compare null or empty strings";
}
```

## เคล็ดลับประสิทธิภาพและแนวปฏิบัติที่ดีที่สุด

### การจัดการหน่วยความจำสำหรับแอปพลิเคชันปริมาณสูง

หากคุณเปรียบเทียบสตริงหลายพันครั้งต่อ นาที, ควรพิจารณาใช้ `Comparer` ตัวเดียวซ้ำโดยใช้ `Reset()` ระหว่างการรัน, หรือทำ batch การเปรียบเทียบหลายรายการในหนึ่งการเรียกเพื่อ ลดการสร้างอ็อบเจ็กต์

### การประมวลผลแบบ Async

สำหรับเว็บ API, ย้ายการเปรียบเทียบไปยังงานเบื้องหลังเพื่อให้เธรดคำขอตอบสนองได้

```csharp
public async Task<string> CompareStringsAsync(string source, string target)
{
    return await Task.Run(() =>
    {
        using (Comparer comparer = new Comparer(source, new LoadOptions() { LoadText = true }))
        {
            comparer.Add(target, new LoadOptions() { LoadText = true });
            comparer.Compare();
            return comparer.GetResultString();
        }
    });
}
```

### เมื่อควรเลือกไฟล์เทียบกับการเปรียบเทียบสตริงโดยตรง

| สถานการณ์ | แนวทางที่แนะนำ |
|----------|----------------------|
| ข้อความที่อยู่ในหน่วยความจำแล้ว, < 500 KB | การเปรียบเทียบสตริงโดยตรง (ในหน่วยความจำ) |
| เอกสาร > 10 MB หรือจำเป็นต้องรักษาเลย์เอาต์อย่างแม่นยำ | การเปรียบเทียบแบบไฟล์ |
| ต้องการรักษาการจัดรูปแบบเดิม (ฟอนต์, รูปภาพ) | การเปรียบเทียบแบบไฟล์ |
| ฟีดแบ็กแบบเรียลไทม์ (เช่น แชท, การแก้ไขสด) | การเปรียบเทียบสตริงโดยตรง |

## การบูรณาการกับ .NET Framework ยอดนิยม

### การบูรณาการ ASP.NET Core Web API

เปิดเผย endpoint REST ที่รับสตริง JSON สองชุดและคืนค่า diff

```csharp
[ApiController]
[Route("api/[controller]")]
public class ComparisonController : ControllerBase
{
    [HttpPost("compare")]
    public IActionResult CompareTexts([FromBody] ComparisonRequest request)
    {
        try
        {
            using (Comparer comparer = new Comparer(request.SourceText, new LoadOptions() { LoadText = true }))
            {
                comparer.Add(request.TargetText, new LoadOptions() { LoadText = true });
                comparer.Compare();
                
                var result = new ComparisonResponse
                {
                    Result = comparer.GetResultString(),
                    Status = "Success"
                };
                
                return Ok(result);
            }
        }
        catch (Exception ex)
        {
            return BadRequest($"Comparison failed: {ex.Message}");
        }
    }
}
```

### การบูรณาการการทดสอบหน่วย

ใช้ไลบรารีในชุดการทดสอบของคุณเพื่อยืนยันว่าการแปลงให้ผลลัพธ์ตามที่คาดหวัง

```csharp
[Test]
public void Should_DetectDifferencesInStrings()
{
    // Arrange
    string expected = "Hello World";
    string actual = "Hello Universe";
    
    // Act
    string comparisonResult;
    using (Comparer comparer = new Comparer(expected, new LoadOptions() { LoadText = true }))
    {
        comparer.Add(actual, new LoadOptions() { LoadText = true });
        comparer.Compare();
        comparisonResult = comparer.GetResultString();
    }
    
    // Assert
    Assert.That(comparisonResult, Does.Contain("World"));
    Assert.That(comparisonResult, Does.Contain("Universe"));
}
```

## การแก้ไขปัญหาทั่วไป

### ข้อผิดพลาด “ไฟล์ไม่พบ”

**สาเหตุ** – ขาด `LoadOptions` หรือ `LoadText = false`. **วิธีแก้** – ตรวจสอบให้แน่ใจว่าทั้งคอนสตรัคเตอร์และการเรียก `Add` มี `new LoadOptions() { LoadText = true }`

### ประสิทธิภาพแย่กับสตริงขนาดใหญ่

**สาเหตุ** – อินพุตขนาดใหญ่มาก (> 1 MB) หรือทำงานบน UI thread. **วิธีแก้** – เปลี่ยนเป็นการเปรียบเทียบแบบไฟล์สำหรับข้อมูลขนาดใหญ่, ตรวจสอบหน่วยความจำ, และย้ายงานไปยังเธรดเบื้องหลัง

### ผลลัพธ์ที่ไม่คาดคิดหรือปัญหาการจัดรูปแบบ

**สาเหตุ** – การเข้ารหัสไม่ตรงกัน, ตัวอักษรที่ซ่อนอยู่ (แท็บ, CR/LF). **วิธีแก้** – ทำให้สตริงเป็นมาตรฐานก่อนเปรียบเทียบ (`string.Normalize(NormalizationForm.FormC)`) และตัด whitespace ที่มองไม่เห็น

## สรุป

คุณมีสูตรที่ครบถ้วนและพร้อมใช้งานในโปรดักชันสำหรับการเปรียบเทียบสตริงโดยตรงใน C# ด้วย GroupDocs.Comparison แล้ว จำไว้ว่า:
- ตั้งค่า `LoadOptions.LoadText = true` เสมอ
- Dispose อ็อบเจ็กต์ `Comparer` อย่างทันท่วงที
- เลือกวิธีทำในหน่วยความจำเพื่อความเร็วเมื่อข้อมูลของคุณอยู่ในตัวแปรแล้ว
- กลับไปใช้การเปรียบเทียบแบบไฟล์สำหรับเอกสารขนาดใหญ่มากหรือที่ต้องการรักษาเลย์เอาต์
- ตรวจสอบอินพุตเพื่อป้องกัน Null และสตริงว่าง

ด้วยเพียงไม่กี่บรรทัดของโค้ดคุณสามารถให้ฟังก์ชัน diff ที่ทรงพลังในแอป .NET ใดก็ได้ — ตั้งแต่บริการแบ็กเอนด์จนถึงเว็บแอปแบบโต้ตอบ

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถเปรียบเทียบสตริงที่มีความยาวแตกต่างกันอย่างมากได้อย่างมีประสิทธิภาพหรือไม่?**  
**ตอบ:** ใช่, อัลกอริทึมสเกลเชิงเส้นและยังคงเร็วสำหรับสตริงขนาดหลายเมกะไบต์; สำหรับ > 10 MB, ควรพิจารณาการเปรียบเทียบแบบไฟล์เพื่อประสิทธิภาพสูงสุด

**ถาม: จะเกิดอะไรขึ้นหากฉันพยายามเปรียบเทียบสตริงที่เป็น null หรือว่าง?**  
**ตอบ:** ไลบรารีจะคืนค่า diff ว่างเปล่า, แต่เป็นแนวปฏิบัติที่ดีในการตรวจสอบ `string.IsNullOrEmpty` ก่อนหน้าเพื่อให้ข้อความผู้ใช้ที่ชัดเจน

**ถาม: วิธีนี้ปลอดภัยต่อเธรดสำหรับการเปรียบเทียบพร้อมกันหรือไม่?**  
**ตอบ:** แต่ละอินสแตนซ์ `Comparer` ทำงานแบบ single‑threaded; สร้างอินสแตนซ์แยกต่อเธรดหรือใช้ pool แบบ thread‑local สำหรับความพร้อมใช้งานสูง

**ถาม: ประสิทธิภาพของวิธีนี้เทียบกับ `string.Equals()` เป็นอย่างไร?**  
**ตอบ:** `string.Equals()` เพียงบอกว่าข้อความเหมือนกันหรือไม่. GroupDocs.Comparison เพิ่มการตรวจจับ diff โดยมีค่าโอเวอร์เฮดเพียงเล็กน้อย — ปกติ 3‑5 ms สำหรับสตริง 100 KB เทียบกับ < 1 ms สำหรับการตรวจสอบความเท่ากันธรรมดา

**ถาม: ฉันสามารถปรับแต่งรูปแบบผลลัพธ์ diff ได้หรือไม่?**  
**ตอบ:** ใช่, `ComparisonOptions` ให้คุณเปลี่ยน markup HTML, คลาส CSS, และแม้กระทั่งส่งออกเป็น plain text หรือ PDF

**ถาม: มีขีดจำกัดขนาดของสตริงที่ฉันสามารถเปรียบเทียบได้หรือไม่?**  
**ตอบ:** ไม่มีขีดจำกัดที่แน่นอน, แต่ประสิทธิภาพลดลงเมื่อเกินประมาณ ~5 MB; สำหรับเอกสารขนาดใหญ่มาก, ควรเปลี่ยนเป็นการเปรียบเทียบแบบไฟล์ตามที่แนะนำ

## แหล่งข้อมูลเพิ่มเติม

- [เอกสาร GroupDocs.Comparison .NET](https://docs.groupdocs.com/comparison/net/)
- [อ้างอิง API ฉบับเต็ม](https://reference.groupdocs.com/comparison/net/)
- [หน้าปล่อยเวอร์ชัน](https://releases.groupdocs.com/comparison/net/)
- [ตัวเลือกการซื้อ](https://purchase.groupdocs.com/buy)
- [ดาวน์โหลดทดลองใช้ฟรี](https://releases.groupdocs.com/comparison/net/)
- [ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/comparison/)

---

**Last Updated:** 2026-06-10  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs

```csharp
comparer.Add("target text", new LoadOptions() { LoadText = true });
```

```csharp
comparer.Compare();
```

```csharp
string resultString = comparer.GetResultString();
Console.WriteLine("Comparison Result:\n" + resultString);
```

## บทแนะนำที่เกี่ยวข้อง

- [บทแนะนำ GroupDocs Comparison .NET - คู่มือการใช้งานพื้นฐานฉบับสมบูรณ์](/comparison/net/basic-usage/)
- [การตั้งค่าใบอนุญาต Metered ของ GroupDocs Comparison .NET - บทแนะนำฉบับสมบูรณ์](/comparison/net/quick-start/set-metered-license/)
- [การเปรียบเทียบเอกสาร .NET - บทแนะนำ C# ฉบับสมบูรณ์](/comparison/net/document-comparison/compare-documents-from-path/)