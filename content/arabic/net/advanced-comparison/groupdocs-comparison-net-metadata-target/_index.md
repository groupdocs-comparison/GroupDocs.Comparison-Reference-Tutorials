---
categories:
- Document Comparison
date: '2026-06-05'
description: تعلم كيفية حفظ البيانات الوصفية باستخدام GroupDocs Comparison لـ .NET،
  دليل خطوة بخطوة للحفاظ على خصائص المستند الهدف أثناء المقارنة.
keywords:
- how to preserve metadata
- keep custom properties
- metadata preservation .NET
lastmod: '2026-06-05'
linktitle: دليل حفظ البيانات الوصفية
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
title: كيفية حفظ البيانات الوصفية باستخدام GroupDocs Comparison – دليل .NET
type: docs
url: /ar/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# كيفية الحفاظ على البيانات الوصفية باستخدام GroupDocs Comparison – دليل .NET

## المقدمة

هل قمت بمقارنة مستندين فقط لتفقد البيانات الوصفية المهمة في العملية؟ لست وحدك. عندما تحتاج إلى **الحفاظ على بيانات التعريف الهدف** أثناء مقارنة المستندات في تطبيق .NET، قد يبدو الأمر صعبًا—لكن لا يجب أن يكون كذلك. يوضح هذا الدليل **كيفية الحفاظ على البيانات الوصفية** بحيث يبقى الملف الناتج يحتوي على المؤلف، تاريخ الإنشاء، والخصائص المخصصة التي تتوقعها.

## إجابات سريعة
- **ماذا يعني “preserve target metadata”؟** يحتفظ بالبيانات الوصفية (المؤلف، تاريخ الإنشاء، الخصائص المخصصة، إلخ) من المستند الذي تحدده كهدف عند إنشاء نتيجة المقارنة.  
- **ما هو إصدار GroupDocs.Comparison المطلوب؟** الإصدار 25.4.0 أو أحدث.  
- **هل يمكن استخدامه مع .NET Core؟** نعم – .NET Core 2.0+ أو .NET Framework 4.6.1+.  
- **هل يلزم ترخيص للإنتاج؟** الترخيص التجاري مطلوب للإنتاج؛ النسخة التجريبية المجانية تكفي للتعلم.  
- **هل تعمل الميزة مع PDF و DOCX؟** نعم – جميع صيغ Office و PDF الرئيسية تدعم الحفاظ على البيانات الوصفية.

## ما هو الحفاظ على البيانات الوصفية؟
يعني الحفاظ على البيانات الوصفية الاحتفاظ بالمعلومات الوصفية للمستند الأصلي—مثل المؤلف، العنوان، رقم المراجعة، والخصائص المخصصة—بعد عملية المعالجة. في GroupDocs.Comparison، يمكنك تحديد ما إذا كانت بيانات التعريف للمستند المصدر أو الهدف هي التي تبقى في ناتج المقارنة النهائي.

## لماذا يعتبر الحفاظ على البيانات الوصفية مهمًا
الحفاظ على البيانات الوصفية أمر أساسي لأن العديد من الصناعات تعتبرها دليلًا قانونيًا أو معلومات حيوية للأعمال. **لماذا؟** لأن البيانات الوصفية تسجل الملكية، وسوم الامتثال، وسجل الإصدارات، ومسارات التدقيق التي تعتمد عليها المؤسسات للتقارير التنظيمية، وإدارة العقود، والنسب الأكاديمي. فقدان هذه البيانات قد يبطل الصفة القانونية للمستند أو يعرقل سير العمل الآلي.

## المتطلبات المسبقة

### المكتبات المطلوبة والإصدارات
- **GroupDocs.Comparison for .NET**: الإصدار 25.4.0 أو أحدث (الإصدارات السابقة لديها خيارات بيانات وصفية محدودة).  
- **.NET Framework**: 4.6.1 أو أعلى، أو .NET Core 2.0+.

### إعداد البيئة
- Visual Studio (أو أي بيئة تطوير C# تفضلها).  
- معرفة أساسية بـ C# (لا شيء معقد، وعد).  
- مستندان تجريان للاختبار (ملف Word *.docx* يعمل بشكل ممتاز).

### المتطلبات المعرفية
لا تحتاج أن تكون خبيرًا في GroupDocs، لكن يجب أن تكون مرتاحًا مع:
- عبارات `using` في C# وتعامل الملفات.  
- مفاهيم معالجة المستندات الأساسية.  
- ما هي البيانات الوصفية فعليًا (المؤلف، العنوان، الخصائص المخصصة، إلخ).

هل أنت جاهز؟ لنبدأ الإعداد.

## إعداد GroupDocs.Comparison لـ .NET

تثبيت GroupDocs.Comparison سهل، لكن هناك بعض النقاط التي يجب الانتباه إليها.

### خيارات التثبيت

**NuGet Package Manager Console** (أسهل طريقة):
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI** (إذا كنت تفضل سطر الأوامر):
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**نصيحة احترافية**: دائمًا حدد الإصدار لتجنب تغييرات كسرية غير متوقعة في مشروعك.

### الحصول على الترخيص
هنا يواجه العديد من المطورين صعوبة في البداية. GroupDocs.Comparison ليس مجانيًا، لكن لديك خيارات:

- **نسخة تجريبية مجانية** – وظائف كاملة لمدة 30 يومًا، مثالية للتقييم.  
- **ترخيص مؤقت** – فترة تقييم ممتدة إذا احتجت وقتًا إضافيًا.  
- **ترخيص تجاري** – للاستخدام الإنتاجي (تتوفر مستويات تسعير مختلفة).

لا تقلق بشأن الترخيص الآن إذا كنت تتعلم فقط—النسخة التجريبية تشمل جميع ميزات **preserve target metadata**.

### التحقق من الإعداد الأساسي

لنضمن أن كل شيء يعمل باختبار بسيط:

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

إذا تم تجميعه دون أخطاء، فأنت جاهز للانطلاق. إذا لم يحدث ذلك، تحقق مرة أخرى من تثبيت الحزمة وعبارات `using`.

## كيفية الحفاظ على بيانات التعريف الهدف

للحفاظ على بيانات التعريف الهدف، تقوم بتكوين المقارن لنسخ البيانات الوصفية من المستند الهدف قبل إنشاء النتيجة. يتم ذلك عبر تعيين خاصية `CloneMetadataType` إلى `MetadataType.Target` على كائن `Comparer`. بهذه الطريقة تُنسخ جميع حقول البيانات الوصفية—المؤلف، تاريخ الإنشاء، الخصائص المخصصة—من الهدف إلى ملف الإخراج، مما يضمن بقاء معلومات المستند المحدثة.

### فهم تدفق البيانات الوصفية

أثناء مقارنة نموذجية:

1. **المستند المصدر** يوفر المحتوى الأساسي.  
2. **المستند الهدف** يوفر التغييرات التي ستُقارن مع المصدر.  
3. **المستند الناتج** يجمع الاثنين، لكن أي بيانات وصفية تنتصر؟

بشكل افتراضي، يستخدم GroupDocs.Comparison بيانات الوصفية للمستند المصدر. لت **preserve target metadata**، عليك إبلاغ الـ API صراحةً.

### تنفيذ خطوة بخطوة

#### الخطوة 1: تهيئة كائن Comparer الخاص بك

فئة `Comparer` هي المكوّن الأساسي الذي يُجري مقارنة المستندات ويسيطر على خيارات الإخراج.  
حمّل الملف الأصلي (source) وأنشئ مثيل `Comparer`:

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**لماذا نستخدم عبارات `using`؟** لأنها تُحرّر الموارد تلقائيًا، مما يمنع تسرب الذاكرة عند معالجة مستندات كبيرة. صدقني، ستشكر نفسك لاحقًا عند التعامل مع ملفات Word بحجم 50 ميغابايت.

#### الخطوة 2: إضافة المستند الهدف

طريقة `Add` تُسجّل المستند الهدف الذي ستُقارن التغييرات فيه مقابل المصدر.  
حدد الملف المحدث الذي تريد مقارنته:

```csharp
comparer.Add(targetFilePath);
```

**خطأ شائع**: الخلط بين المصدر والهدف. فكر هكذا—المصدر هو “الأصلي”، والهدف هو “الإصدار المحدث”.

#### الخطوة 3: تعيين نوع البيانات الوصفية (السحر يحدث هنا)

خاصية `CloneMetadataType` تحدد أي مستند تُنسخ بياناته الوصفية إلى النتيجة.  
أخبر المقارن بالحفاظ على بيانات الوصفية للهدف:

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**ما الذي يحدث؟** `CloneMetadataType = MetadataType.Target` يخبر GroupDocs.Comparison: “أريد الاحتفاظ ببيانات الوصفية للمستند الهدف في النتيجة النهائية”.

### مثال عملي كامل

إليك كل شيء معًا في برنامج قابل للتنفيذ:

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

### الأخطاء الشائعة التي يجب تجنبها

**مشكلات مسار الملف** – استخدم دائمًا مسارات كاملة أو تأكد من وجود الملفات في دليل العمل:

```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

**إدارة الذاكرة** – بالنسبة للمستندات الكبيرة، احرص دائمًا على وضع كائنات `Comparer` داخل عبارات `using`.

**توافق الإصدارات** – إصدارات GroupDocs.Comparison المختلفة تعرض خيارات بيانات وصفية مختلفة—التزم بالإصدار 25.4.0 أو أحدث للحصول على أفضل النتائج.

## سيناريوهات البيانات الوصفية المتقدمة

### متى تستخدم بيانات التعريف الهدف مقابل المصدر

| السيناريو | يفضّل **بيانات الهدف** | يفضّل **بيانات المصدر** |
|----------|------------------------|--------------------------|
| الحاجة إلى معلومات مؤلف محدثة | ✅ | ❌ |
| المستند الأصلي له أسبقية قانونية | ❌ | ✅ |
| الخصائص المخصصة أضيفت فقط في الملف الأحدث | ✅ | ❌ |
| تريد الحفاظ على تاريخ “الملف الرئيسي” | ❌ | ✅ |

### التعامل مع مستندات هدف متعددة

يمكنك مقارنة عدة أهداف مع الاستمرار في الحفاظ على البيانات الوصفية من أول هدف تضيفه:

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

## التطبيقات العملية وحالات الاستخدام

### إدارة المستندات القانونية
تحتاج مكاتب المحاماة غالبًا إلى مقارنة إصدارات العقود مع الحفاظ على علامات البيانات الوصفية المحددة:

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

### التعاون الأكاديمي والبحثي
عند تعاون عدة باحثين، تريد الحفاظ على أحدث معلومات المؤلف:

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

### تدفقات عمل الامتثال المؤسسي
في الصناعات الخاضعة للتنظيم، الحفاظ على بيانات الوصفية للامتثال أمر حاسم:

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

## استكشاف الأخطاء الشائعة

### أخطاء “الملف غير موجود”
أكثر الأخطاء شيوعًا. قم بالتنقيح باستخدام فحوص صريحة:

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

### مشاكل الذاكرة مع المستندات الكبيرة
للمستندات التي يزيد حجمها عن 10 ميغابايت، ضع في اعتبارك التحسينات التالية:

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

### مشاكل الأذونات والوصول
عند العمل مع ملفات محمية أو مشاركات شبكة:

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

## اعتبارات الأداء وأفضل الممارسات

### إدارة الذاكرة
GroupDocs.Comparison قد يستهلك ذاكرةً كبيرة. استخدم عبارات `using` لضمان تحرير الموارد:

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

**معالجة المستندات على دفعات** – إذا كنت تقارن العديد من الملفات، عالجها في مجموعات أصغر لتقليل استهلاك الذاكرة.

### عمليات غير متزامنة لتحسين الاستجابة
في تطبيقات سطح المكتب أو الويب، غلف عملية المقارنة في طريقة غير متزامنة:

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

### إرشادات حجم الملف
- **صغير (< 1 ميغابايت)** – عالج مباشرة.  
- **متوسط (1‑10 ميغابايت)** – أظهر تقدمًا للحفاظ على استجابة الواجهة.  
- **كبير (> 10 ميغابايت)** – استخدم دائمًا المعالجة غير المتزامنة وفكر في استدعاء GC صريح كما هو موضح أعلاه.

## التكامل مع الأنظمة الأكبر

### تكامل ASP.NET Core
فيما يلي وحدة تحكم جاهزة تستقبل ملفين مرفوعين، تُجري المقارنة، وتعيد النتيجة مع **preserve target metadata**:

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

## الأسئلة المتكررة

**س: هل يمكنني الحفاظ على البيانات الوصفية من عدة مستندات هدف عند المقارنة؟**  
ج: عندما تضيف عدة ملفات هدف، يستخدم GroupDocs.Comparison البيانات الوصفية من **أول** مستند هدف تمت إضافته. ضع المستند الذي تريد الاحتفاظ ببياناته الوصفية أولًا في السلسلة.

**س: ماذا يحدث إذا كان المستند الهدف يفتقر إلى بعض حقول البيانات الوصفية؟**  
ج: تُنسخ فقط البيانات الوصفية الموجودة في الهدف إلى الناتج. الحقول المفقودة تُهمل؛ وتستمر المقارنة بنجاح.

**س: كيف أتعامل مع المستندات المحمية بكلمة مرور؟**  
ج: استخدم كائن `LoadOptions` مع كلمة المرور، ثم مرره إلى مُنشئ `Comparer`:

```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**س: هل هناك طريقة للحفاظ على خصائص بيانات وصفية مختارة فقط؟**  
ج: الـ API الحالي يحافظ على **جميع** البيانات الوصفية من المصدر المختار (Target أو Source). للتحكم الدقيق تحتاج إلى استخراج الخصائص بعد المقارنة وإعادة تطبيقها يدويًا.

**س: أي صيغ مستندات تدعم الحفاظ على البيانات الوصفية؟**  
ج: معظم صيغ الأعمال الشائعة—DOCX، PDF، PPTX، XLSX، والعديد غيرها—تدعم الحفاظ على البيانات الوصفية. راجع الوثائق الرسمية للقائمة الكاملة.

**س: أين يمكنني الحصول على مساعدة إذا واجهت مشاكل؟**  
ج: زر [منتدى دعم GroupDocs](https://forum.groupdocs.com/c/comparison) للمساعدة المجتمعية، أو تواصل مع دعم GroupDocs مباشرة إذا كان لديك ترخيص تجاري.

## موارد إضافية

- **الوثائق الرسمية**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **مرجع API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **تحميل أحدث نسخة**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **نسخة تجريبية مجانية**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **خيارات الشراء**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**آخر تحديث:** 2026-06-05  
**تم الاختبار مع:** GroupDocs.Comparison 25.4.0 for .NET  
**المؤلف:** GroupDocs  

---

## دروس ذات صلة

- [Document Metadata .NET - Save & Preserve Custom Properties](/comparison/net/loading-and-saving-documents/saving-user-defined-document-metadata/)
- [Document Metadata Management .NET - Complete Guide for GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Get Document Properties C# .NET - Extract File Metadata](/comparison/net/basic-usage/get-document-info-from-path/)