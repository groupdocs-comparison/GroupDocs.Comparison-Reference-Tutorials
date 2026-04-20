---
categories:
- Document Comparison
date: '2026-03-06'
description: تعلم كيفية الحفاظ على بيانات التعريف المستهدفة أثناء مقارنة المستندات
  باستخدام GroupDocs.Comparison لـ .NET. دليل خطوة بخطوة مع أمثلة بلغة C#.
keywords: preserve target metadata, GroupDocs.Comparison metadata preservation, .NET
  document comparison, metadata preservation tutorial
lastmod: '2026-03-06'
linktitle: Metadata Preservation Tutorial
tags:
- GroupDocs.Comparison
- metadata-preservation
- dotnet-tutorial
- document-management
title: حفظ بيانات التعريف الهدف باستخدام GroupDocs.Comparison – دليل .NET
type: docs
url: /ar/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# الحفاظ على بيانات التعريف الهدف مع GroupDocs.Comparison – دليل .NET

## المقدمة

هل قمت يومًا بمقارنة مستندين فقط لتفقد بيانات التعريف المهمة في العملية؟ لست وحدك. عندما تحتاج إلى **preserve target metadata** أثناء مقارنة المستندات في تطبيق .NET، قد يبدو الأمر صعبًا—ولكن لا يجب أن يكون كذلك.

يتيح لك GroupDocs.Comparison for .NET تحديد أي مستند سيحتفظ ببيانات التعريف الخاصة به في نتيجة المقارنة. سواء كنت تبني نظام إدارة مستندات، أو تتعامل مع عقود قانونية، أو تدير محتوى تعاوني، فإنك ستحتاج إلى بيانات التعريف من المستند المصدر الصحيح في كل مرة.

في هذا الدليل ستتعلم كيفية **preserve target metadata** أثناء المقارنة، وتجنب الأخطاء الشائعة، وتطبيق الحل في سيناريوهات واقعية.

## إجابات سريعة
- **ماذا يعني “preserve target metadata”؟** يحتفظ ببيانات التعريف (المؤلف، تاريخ الإنشاء، الخصائص المخصصة، إلخ) من المستند الذي تحدده كهدف عند إنشاء نتيجة المقارنة.  
- **ما هو إصدار GroupDocs.Comparison المطلوب؟** الإصدار 25.4.0 أو أحدث.  
- **هل يمكنني استخدامه مع .NET Core؟** نعم – .NET Core 2.0+ أو .NET Framework 4.6.1+.  
- **هل تحتاج إلى ترخيص للإنتاج؟** يلزم ترخيص تجاري للإنتاج؛ النسخة التجريبية المجانية تكفي للتعلم.  
- **هل تعمل الميزة مع PDF و DOCX؟** نعم – جميع صيغ Office و PDF الرئيسية تدعم حفظ بيانات التعريف.

## لماذا حفظ بيانات التعريف مهم

قبل الانتقال إلى الكود، دعنا نتحدث عن سبب أهمية حفظ بيانات التعريف الهدف. بيانات تعريف المستند ليست مجرد “إضافة لطيفة”—بل غالبًا ما تكون مطلوبة قانونيًا أو حيوية للأعمال:

- **المستندات القانونية** – تحتاج إلى الاحتفاظ بعلامات سرية المحاماة‑العميل.  
- **ملفات الشركات** – يجب الاحتفاظ بوسوم الامتثال وسلاسل الموافقة.  
- **الأوراق الأكاديمية** – إسناد المؤلف وتاريخ المراجعات أمران أساسيان.  
- **الوثائق التقنية** – التحكم في الإصدارات وحالة المراجعة مهمان.

بدون معالجة صحيحة، قد تقوم عن طريق الخطأ بإزالة معلومات استغرق تأسيسها شهورًا. هنا يبرز دور خيار **preserve target metadata**.

## المتطلبات المسبقة

### المكتبات والإصدارات المطلوبة
- **GroupDocs.Comparison for .NET**: الإصدار 25.4.0 أو أحدث (الإصدارات السابقة لديها خيارات محدودة لبيانات التعريف).  
- **.NET Framework**: 4.6.1 أو أعلى، أو .NET Core 2.0+.

### إعداد البيئة
- Visual Studio (أو أي بيئة تطوير C# تفضلها).  
- معرفة أساسية بـ C# (لا شيء معقد، وعد!).  
- مستندان تجريبيان للاختبار (Word *.docx* يعمل بشكل ممتاز).

### متطلبات المعرفة
ليس عليك أن تكون خبيرًا في GroupDocs، لكن يجب أن تكون مرتاحًا مع:
- عبارات `using` في C# ومعالجة الملفات.  
- مفاهيم أساسية لمعالجة المستندات.  
- ما هي بيانات التعريف فعليًا (المؤلف، العنوان، الخصائص المخصصة، إلخ).

جاهز؟ لنقم بالإعداد.

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

هنا حيث يواجه العديد من المطورين صعوبة في البداية. GroupDocs.Comparison ليس مجانيًا، لكن لديك خيارات:
- **نسخة تجريبية مجانية** – وظائف كاملة لمدة 30 يوم، مثالية للتقييم.  
- **ترخيص مؤقت** – فترة تقييم ممتدة إذا كنت بحاجة إلى مزيد من الوقت.  
- **ترخيص تجاري** – للاستخدام في الإنتاج (تتوفر مستويات أسعار مختلفة).

لا تقلق بشأن الترخيص الآن إذا كنت تتعلم فقط—النسخة التجريبية تشمل جميع ميزات **preserve target metadata**.

### التحقق من الإعداد الأساسي

لنتأكد من أن كل شيء يعمل باختبار بسيط:
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

إذا تم تجميعه بدون أخطاء، فأنت جاهز. إذا لم يحدث ذلك، تحقق مرة أخرى من تثبيت الحزمة وعبارات `using`.

## كيفية حفظ بيانات التعريف الهدف

الآن إلى الجزء الرئيسي—حفظ بيانات التعريف فعليًا أثناء مقارنة المستندات. هنا يبرز أداء GroupDocs.Comparison.

### فهم تدفق بيانات التعريف

أثناء مقارنة نمطية:
1. **المستند المصدر** يوفر المحتوى الأساسي.  
2. **المستند الهدف** يوفر التغييرات للمقارنة.  
3. **المستند الناتج** يجمع بينهما، لكن أي بيانات تعريف تفوز؟

بشكل افتراضي، يستخدم GroupDocs.Comparison بيانات تعريف المستند المصدر. لتطبيق **preserve target metadata**، يجب إبلاغ الـ API صراحةً.

### تنفيذ خطوة بخطوة

#### الخطوة 1: تهيئة كائن المقارن الخاص بك

هذا يحدد المستند “الأساسي”—المستند الذي تقارنه ضده:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**لماذا نستخدم عبارات `using`؟** لأنها تقوم تلقائيًا بتحرير الموارد، مما يمنع تسرب الذاكرة عند معالجة مستندات كبيرة. صدقني، ستشكر نفسك لاحقًا عند التعامل مع ملفات Word بحجم 50 ميغابايت.

#### الخطوة 2: إضافة المستند الهدف

أخبر المقارن أي مستند يحتوي على التغييرات التي تريد تحليلها:
```csharp
comparer.Add(targetFilePath);
```

**خطأ شائع**: الخلط بين المصدر والهدف. فكر بهذه الطريقة—المصدر هو “الأصلي”، والهدف هو “الإصدار المحدث”.

#### الخطوة 3: تعيين نوع بيانات التعريف (هنا يحدث السحر)

حدد أي مستند يجب أن يحتفظ ببيانات التعريف في الناتج:
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**ما الذي يحدث؟** `CloneMetadataType = MetadataType.Target` يخبر GroupDocs.Comparison: “أريد الاحتفاظ ببيانات تعريف المستند الهدف في النتيجة النهائية.”

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
- **مشكلات مسار الملف** – استخدم دائمًا المسارات الكاملة أو تأكد من وجود ملفاتك في دليل العمل:
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

- **إدارة الذاكرة** – للمستندات الكبيرة، احرص دائمًا على تغليف كائنات `Comparer` بعبارات `using`.

- **توافق الإصدارات** – إصدارات GroupDocs.Comparison المختلفة تعرض خيارات بيانات تعريف مختلفة—التزم بالإصدار 25.4.0 أو أحدث للحصول على أفضل النتائج.

## سيناريوهات متقدمة لبيانات التعريف

### متى تستخدم بيانات التعريف الهدف مقابل المصدر

| السيناريو | يفضل بيانات التعريف **الهدف** | يفضل بيانات التعريف **المصدر** |
|----------|----------------------------|----------------------------|
| مطلوب تحديث معلومات المؤلف | ✅ | ❌ |
| المستند الأصلي له أولوية قانونية | ❌ | ✅ |
| تمّت إضافة خصائص مخصصة فقط في الملف الأحدث | ✅ | ❌ |
| تريد الاحتفاظ بتاريخ المستند “الرئيسي” | ❌ | ✅ |

### التعامل مع مستندات هدف متعددة

يمكنك مقارنة عدة أهداف مع الحفاظ على بيانات التعريف من أول هدف تضيفه:
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
غالبًا ما تحتاج مكاتب المحاماة إلى مقارنة إصدارات العقود مع الحفاظ على علامات بيانات التعريف المحددة:
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

### سير عمل الامتثال المؤسسي
في الصناعات المنظمة، الحفاظ على بيانات تعريف الامتثال أمر حاسم:
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
أكثر المشاكل شيوعًا. قم بالتصحيح باستخدام فحوصات صريحة:
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
للمستندات التي يزيد حجمها عن 10 ميغابايت، ضع في اعتبارك هذه التحسينات:
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
GroupDocs.Comparison يمكن أن يكون مستهلكًا للذاكرة. استخدم عبارات `using` لضمان تحرير الموارد:
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

**معالجة المستندات على دفعات** – إذا كنت تقارن العديد من الملفات، عالجها في مجموعات أصغر للحفاظ على استهلاك الذاكرة منخفضًا.

### عمليات غير متزامنة لتحسين الاستجابة
لتطبيقات سطح المكتب أو الويب، غلف المقارنة في طريقة غير متزامنة:
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
- **صغير (< 1 ميغابايت)** – معالجة مباشرة.  
- **متوسط (1‑10 ميغابايت)** – إظهار تقدم للحفاظ على استجابة واجهة المستخدم.  
- **كبير (> 10 ميغابايت)** – استخدم دائمًا معالجة غير متزامنة وفكر في استدعاء جمع القمامة صراحةً كما هو موضح أعلاه.

## التكامل مع الأنظمة الأكبر

### تكامل ASP.NET Core
فيما يلي وحدة تحكم جاهزة للاستخدام تقبل ملفين مرفوعين، تجري المقارنة، وتعيد النتيجة مع **preserving target metadata**:
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

**س: هل يمكنني حفظ بيانات التعريف من مستندات هدف متعددة عند المقارنة؟**  
**ج:** عندما تضيف عدة ملفات هدف، يستخدم GroupDocs.Comparison بيانات التعريف من **أول** مستند هدف تم إضافته. أضف المستند الذي تريد الاحتفاظ ببيانات تعريفه أولاً في السلسلة.

**س: ماذا يحدث إذا كان المستند الهدف يفتقر إلى بعض حقول بيانات التعريف؟**  
**ج:** يتم نسخ فقط بيانات التعريف الموجودة في الهدف إلى الناتج. الحقول المفقودة تُهمل؛ وتستمر المقارنة بنجاح.

**س: كيف أتعامل مع المستندات المحمية بكلمة مرور؟**  
**ج:** استخدم كائن `LoadOptions` مع كلمة المرور، ثم مرره إلى مُنشئ `Comparer`:
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**س: هل هناك طريقة لحفظ خصائص بيانات التعريف المختارة فقط؟**  
**ج:** الـ API الحالي يحفظ **جميع** بيانات التعريف من المصدر المختار (Target أو Source). للتحكم الدقيق تحتاج إلى استخراج الخصائص بعد المقارنة وإعادة تطبيقها يدويًا.

**س: أي صيغ المستندات تدعم حفظ بيانات التعريف؟**  
**ج:** معظم صيغ الأعمال الشائعة—DOCX, PDF, PPTX, XLSX، والعديد غيرها—تدعم حفظ بيانات التعريف. راجع الوثائق الرسمية للقائمة الكاملة.

**س: أين يمكنني الحصول على المساعدة إذا واجهت مشاكل؟**  
**ج:** زر [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) للحصول على مساعدة المجتمع، أو اتصل بدعم GroupDocs مباشرة إذا كان لديك ترخيص تجاري.

## موارد إضافية

- **الوثائق الرسمية**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **مرجع الـ API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **تحميل أحدث نسخة**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **نسخة تجريبية مجانية**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **خيارات الشراء**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**آخر تحديث:** 2026-03-06  
**تم الاختبار مع:** GroupDocs.Comparison 25.4.0 for .NET  
**المؤلف:** GroupDocs