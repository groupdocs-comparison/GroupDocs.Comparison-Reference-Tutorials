---
categories:
- Image Processing
date: '2026-05-31'
description: تعلم كيفية مقارنة الصور في .NET باستخدام GroupDocs.Comparison مع تعطيل
  صفحة الملخص. يغطي هذا الدليل الإعداد، الكود، نصائح الأداء، وحالات الاستخدام الواقعية.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: مقارنة الصور .NET بدون ملخص
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: كيفية مقارنة الصور في .NET – تخطي صفحة الملخص
type: docs
url: /ar/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# كيفية مقارنة الصور في .NET – تخطي صفحة الملخص

عندما تحتاج إلى **how to compare images** برمجيًا في تطبيق .NET، آخر شيء تريده هو صفحة ملخص إضافية تضيع الوقت والمساحة. سواء كنت تبني خط تحكم جودة، أو خط أنابيب إدارة محتوى، أو مجموعة اختبارات انحدار بصري آلية، فإن تخطي صفحة الملخص يمكن أن يوفر ثوانٍ من كل تشغيل ويحافظ على بصمة القرص الخاصة بك خفيفة.

في هذا الدرس ستتعلم كيفية استخدام **GroupDocs.Comparison for .NET** لمقارنة صورتين بكفاءة، وتكوين المكتبة لتقليل إنشاء الملخص، وتطبيق حيل الأداء وفقًا لأفضل الممارسات. سنستكشف أيضًا لماذا هذا مهم، ومتى يتم استخدامه، وكيفية تجنب المشكلات الشائعة.

## إجابات سريعة
- **ما هي أسرع طريقة لمقارنة الصور دون صفحة ملخص؟** استخدم `Comparer` مع `CompareOptions` واضبط `GenerateSummaryPage = false`.  
- **أي مكتبة تدعم هذا مباشرةً؟** GroupDocs.Comparison for .NET (v25.4.0+).  
- **هل أحتاج إلى ترخيص؟** نعم، يلزم ترخيص تجاري للإنتاج؛ نسخة تجريبية مجانية تعمل للتطوير.  
- **هل يمكنني مقارنة أكثر من صورتين في آن واحد؟** بالتأكيد – استدعِ `Add()` عدة مرات قبل `Compare()`.  
- **هل هذا النهج مناسب للوظائف الدفعية على نطاق واسع؟** نعم، عند الجمع مع معالجة دفعات وإدارة الذاكرة بشكل صحيح.

## ما هو GroupDocs.Comparison؟
`GroupDocs.Comparison` هي مكتبة .NET تكتشف الاختلافات البصرية بين المستندات والصور، وتنتج نتائج جنبًا إلى جنب أو كطبقة فوق الأخرى. تدعم **50+ تنسيقًا للإدخال والإخراج**، بما في ذلك JPEG و PNG و BMP و TIFF و GIF، ويمكنها معالجة ملفات مئات الصفحات دون تحميل الملف بالكامل إلى الذاكرة.

## لماذا تخطي صفحة الملخص؟
تعطيل صفحة الملخص يقلل من عمليات الإدخال/الإخراج بنسبة تصل إلى **70 %** لمقارنات الصور فقط ويقلل زمن المعالجة بحوالي **30 %** في المتوسط، وفقًا لمجموعة الاختبارات المرجعية للمكتبة. عندما تحتاج فقط إلى صورة الفرق (للاختبار الآلي أو قرارات QC للنجاح/الفشل)، لا تضيف تقرير HTML الإضافي أي قيمة وتستهلك مساحة القرص فقط.

## المتطلبات المسبقة وإعداد البيئة

### ما ستحتاجه
- **GroupDocs.Comparison for .NET** الإصدار **25.4.0** أو أحدث  
- Visual Studio 2019 + أو أي بيئة تطوير متوافقة مع .NET  
- .NET Framework 4.6.1 + **أو** .NET Core 2.0 +  
- معرفة أساسية بـ C# وإلمام بملفات I/O  

### إضافات موصى بها
- مشروع اختبار صغير يحتوي على زوج من الصور النموذجية (مثال: `source.png` و `target.png`).  
- اختياري: إعداد حقن الاعتمادية إذا كنت تفضل بنية موجهة للخدمات.  

### لماذا هذه المتطلبات مهمة
الإصدار المحدد من المكتبة يتضمن علم `GenerateSummaryPage` وتحسينات الأداء التي تفتقدها الإصدارات القديمة. استخدام بيئة تطوير حديثة يضمن إمكانية الاستفادة من إدارة الحزم عبر NuGet ورؤية التحذيرات أثناء التجميع مبكرًا.

## كيفية تثبيت GroupDocs.Comparison
يمكن إضافة GroupDocs.Comparison إلى أي مشروع .NET عبر NuGet، الذي يتولى تنزيل الثنائيات وتحديث ملف المشروع. اختر الطريقة التي تتناسب مع سير عملك: وحدة تحكم مدير الحزم لمستخدمي Visual Studio أو .NET CLI لبيئات سطر الأوامر. كلا الأمرين يحلان الاعتمادات تلقائيًا ويضمنان الإشارة إلى الإصدار الصحيح.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(استبدل `25.4.0` بالإصدار الدقيق الذي تنوي تثبيته.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
كلا الأمرين يضيفان المكتبة إلى ملف المشروع الخاص بك ويستعيدان الثنائيات اللازمة.

**نصيحة احترافية:** قم بتثبيت الإصدار في ملف `.csproj` الخاص بك لتجنب الترقيات العرضية التي قد تغير سلوك الـ API.

## اعتبارات الترخيص
يتطلب GroupDocs.Comparison ترخيصًا لأي نشر في بيئة الإنتاج. يمكنك البدء بـ **نسخة تجريبية مجانية** توفر جميع الوظائف، ثم الترقية إلى **ترخيص مؤقت** للاختبار الموسع، وأخيرًا إلى **ترخيص تجاري كامل** للإنتاج. تذكر وضع ملف `GroupDocs.Comparison.lic` في جذر التطبيق أو تحديد مساره برمجيًا.

## إعداد المشروع الأساسي
أنشئ تطبيقًا جديدًا من نوع console (أو دمجه في خدمة موجودة) وأضف الشيفرة الأساسية التالية. يوضح هذا المقتطف الإعداد الأدنى المطلوب قبل الخوض في منطق المقارنة.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **مهم:** استخدم دائمًا `Path.Combine()` لمسارات الملفات. فهو يتعامل تلقائيًا مع فواصل المسار الخاصة بنظام التشغيل ويتجنب الأخطاء الدقيقة عند الانتقال بين حاويات Windows و Linux.

## دليل التنفيذ خطوة بخطوة

### كيف أقارن الصور دون صفحة ملخص؟
`Comparer` هو الفئة الأساسية في GroupDocs.Comparison التي تنسق عمليات مقارنة المستندات والصور. `CompareOptions` يحتوي على إعدادات التكوين التي تتحكم في كيفية إجراء المقارنة، مثل ما إذا كان سيتم إنشاء صفحة ملخص. حمّل صورة المصدر، واضبط `CompareOptions` لتعطيل الملخص، أضف صورة الهدف، واستدعِ `Compare()`. تُعيد الطريقة كائن `ComparisonResult` يحتوي على تدفق صورة الفرق، والذي يمكنك كتابته إلى القرص، أو إرساله عبر الشبكة، أو تضمينه في مكوّن واجهة المستخدم. يضمن هذا النهج إنتاج الفرق الأساسي فقط، متجنبًا أي تقارير HTML أو PDF إضافية.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

الشيفرة أعلاه تقوم بإجراء المقارنة بالكامل في **أربع خطوات منطقية** وتكتب صورة الفرق فقط، متجنبة أي ملخص HTML أو PDF.

### الخطوة 1: تهيئة كائن Comparer
فئة `Comparer` هي البوابة إلى جميع عمليات المقارنة. إنها تنفّذ `IDisposable`، لذا فإن تغليفها في كتلة `using` يضمن تحرير مقبض الملفات والذاكرة غير المُدارة بسرعة، حتى إذا تم رمي استثناء.

### الخطوة 2: تكوين CompareOptions بدون ملخص
اضبط `GenerateSummaryPage = false` على كائن `CompareOptions`. هذا العلم يُخبر المحرك بتخطي إنشاء تقرير HTML الافتراضي، وهو المصدر الرئيسي للعمليات الإضافية في سيناريوهات الصور فقط.

### الخطوة 3: إضافة صورة (صور) الهدف للمقارنة
يمكنك استدعاء `Add()` عدة مرات لمقارنة مصدر واحد مع عدة أهداف في دفعة واحدة. يمكن لكل استدعاء أن يتلقى `CompareOptions` خاصًا به إذا كنت تحتاج إلى تخصيصات لكل صورة.

### الخطوة 4: تنفيذ المقارنة وحفظ النتائج
`Comparer.Compare()` يقوم بالعمل الشاق ويعيد كائن `ComparisonResult`. يحتوي الناتج على `Stream` يحتوي على صورة الفرق، والتي يمكنك حفظها مباشرة إلى القرص، أو إرسالها عبر الشبكة، أو تضمينها في مكوّن واجهة المستخدم.

## طريقة جاهزة للإنتاج بالكامل
فيما يلي طريقة جاهزة للاستخدام يمكنك إدراجها في أي خدمة .NET. تتضمن التحقق من صحة المسار، ومعالجة الاستثناءات، وربط اختياري للتسجيل.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## مشكلات التنفيذ الشائعة (وكيفية تجنبها)

- **مشكلات المسار:** تحقق دائمًا من وجود كل من ملفات المصدر والهدف باستخدام `File.Exists()`. سيؤدي عدم وجود ملف إلى رمي استثناء `FileNotFoundException` يمكن التقاطه مبكرًا.  
- **ضغط الذاكرة:** الصور الكبيرة (أكثر من 10 ميغابايت) يمكن أن تستهلك ذاكرة RAM كبيرة. عالجها على دفعات وفكّر في تقليل الدقة إذا لم تكن الدقة البكسلية المثالية مطلوبة.  
- **قفل الملفات:** تأكد من عدم احتفاظ أي عملية أخرى بقفل حصري على ملفات الصور. هذا مهم بشكل خاص في بيئات متعددة الخيوط أو الحاويات.  

## التطبيقات العملية وحالات الاستخدام

### التحكم في الجودة في التصنيع
خط الإنتاج يلتقط صورًا لكل عنصر ويقارنها بمرجع ذهبي. تخطي صفحة الملخص يسمح للنظام باتخاذ قرار “نجاح” أو “فشل” خلال مللي ثانية، مما يحافظ على سرعة الخط.

### أنظمة إدارة المحتوى
عند رفع المستخدمين للملفات، يمكن لنظام إدارة المحتوى اكتشاف النسخ المكررة أو القريبة على الفور، مما يمنع تضخم التخزين ويحسن صلة البحث. يمكن تخزين صورة الفرق كصورة مصغرة للفحص البصري السريع.

### اختبار واجهة المستخدم الآلي (الانحدار البصري)
يمكن لـ Selenium أو Playwright التقاط لقطات شاشة لصفحة ويب، ثم تمريرها إلى روتين المقارنة هذا. تُظهر صورة الفرق تغييرات الواجهة، وبما أنه لا يتم إنشاء ملخص، يبقى خط أنابيب CI سريعًا وخفيفًا.

### التصوير الطبي (مع التدقيق)
تحتاج بعض عمليات تدفق عمل الأشعة إلى الإشارة إلى تغييرات بين الفحوص المتتالية. بينما قد لا يزال من الضروري إنشاء سجل تدقيق مفصل، يمكن إنتاج صورة الفرق نفسها دون صفحة ملخص، مما يقلل زمن المعالجة للملفات الكبيرة المحولة من DICOM إلى PNG.

## اعتبارات الأداء والتحسين

### أفضل ممارسات إدارة الذاكرة
عالج الصور في **دفعات من 20 إلى 50** حسب ذاكرة الخادم RAM. حرّر كل كائن `Comparer` على الفور واستدعِ `GC.Collect()` فقط إذا لاحظت ارتفاعًا مفاجئًا في الذاكرة أثناء الوظائف الطويلة.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### تحسين إدخال/إخراج القرص
ضع أدلة الإدخال والإخراج والملفات المؤقتة على نفس وحدة SSD السريعة. احذف الملفات المؤقتة فورًا بعد حفظ صورة الفرق لتجنب استهلاك غير ضروري للقرص.

### اعتبارات الخيوط والبرمجة غير المتزامنة
GroupDocs.Comparison آمن للخيوط للعمليات القراءة فقط، لكن تجنّب مشاركة كائن `Comparer` واحد عبر الخيوط. بدلاً من ذلك، أنشئ مهام مستقلة:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## استكشاف الأخطاء الشائعة

### أخطاء مسار الملف والأذونات
- **العَرَض:** `FileNotFoundException` أو `UnauthorizedAccessException`.  
- **الحل:** استخدم `Path.GetFullPath()` لتصحيح مسار الحل، وتأكد من أن هوية مجموعة تطبيقات الويب (أو مستخدم حاوية Docker) لديها صلاحيات القراءة/الكتابة، وتحقق مرة أخرى من أن المسار لم يُقَصَ بواسطة متغيرات البيئة.  

### عنق الزجاجة في الذاكرة والأداء
- **العَرَض:** `Slow runs` أو `OutOfMemoryException`.  
- **الحل:** غيّر حجم الصور إلى دقة مشتركة (مثال: 1024 × 768) عندما لا تكون المقارنة البكسلية الدقيقة مطلوبة. راقب الذاكرة بأدوات مثل dotMemory أو أداة Performance Profiler المدمجة.  

### مشاكل الترخيص
- **العَرَض:** صورة الفرق مائية أو `LicenseException`.  
- **الحل:** تأكد من أن `GroupDocs.Comparison.lic` موجود في دليل التنفيذ أو حمّله صراحةً عبر `License license = new License(); license.SetLicense("path/to/license.file");`.  

## خيارات التكوين المتقدمة

### تخصيص حساسية المقارنة
يمكنك ضبط دقة تعامل المحرك مع اختلافات البكسل الطفيفة (مثل تشوهات الضغط) عن طريق تعديل خاصية `Sensitivity` في `CompareOptions`. القيم الأقل تجعل المقارنة أكثر صرامة.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### تحسين تنسيق الإخراج
إذا كنت تحتاج صورة الفرق بتنسيق محدد (PNG مقابل JPEG)، اضبط خاصية `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## التكامل مع أطر .NET الشائعة

### مثال خدمة ASP.NET Core
اعرض نقطة نهاية HTTP خفيفة الوزن تقبل تدفقين للصور، وتنفّذ المقارنة، وتعيد صورة الفرق كـ `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### تسجيل حقن الاعتمادية
أضف الـ comparer كخدمة scoped في `Program.cs` أو `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## الأسئلة المتكررة

**س: ما هي الميزة الرئيسية لتخطي صفحة الملخص؟**  
**ج:** يقلل زمن المعالجة بنسبة تصل إلى 30 % ويقلل استخدام القرص بحوالي 70 % لمقارنات الصور فقط، وهو أمر حاسم لخطوط الأنابيب ذات الإنتاجية العالية.

**س: هل لا يزال بإمكاني استرجاع بيانات تعريف التغييرات التفصيلية دون صفحة ملخص؟**  
**ج:** نعم. كائن `ComparisonResult` يكشف عن مجموعة `Changes` التي تحتوي على معلومات برمجية حول كل اختلاف تم اكتشافه.

**س: ما هي صيغ الصور المدعومة؟**  
**ج:** JPEG, PNG, BMP, TIFF, GIF، والعديد غيرها—أكثر من 50 صيغة إجمالاً.

**س: كيف يجب أن أتعامل مع الصور الكبيرة جدًا (مثلاً >20 ميغابايت)؟**  
**ج:** عالجها على دفعات أصغر، واختياريًا قلل من دقتها، وراقب استهلاك الذاكرة. استخدام `Comparer` داخل كتلة `using` يضمن تحرير الموارد بسرعة.

**س: هل هذا النهج آمن لتطبيقات متعددة الخيوط؟**  
**ج:** نعم، طالما أن كل خيط ينشئ كائن `Comparer` خاص به. مشاركة كائن واحد قد تؤدي إلى ظروف سباق.

## موارد إضافية
- [وثائق GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [مرجع API](https://reference.groupdocs.com/comparison/net/)
- [تحميل](https://releases.groupdocs.com/comparison/net/)
- [شراء](https://purchase.groupdocs.com/buy)
- [نسخة تجريبية مجانية](https://releases.groupdocs.com/comparison/net/)
- [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)
- [منتدى الدعم](https://forum.groupdocs.com/c/comparison/)

---

**آخر تحديث:** 2026-05-31  
**تم الاختبار مع:** GroupDocs.Comparison 25.4.0 for .NET  
**المؤلف:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```
```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```
```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```
```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```
```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```
```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```
```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## دروس ذات صلة
- [مقارنة الصور .NET - مقارنة الصور برمجيًا](/comparison/net/image-comparison/compare-images-from-path/)
- [مقارنة الصور .NET - مقارنة الصور من تدفق](/comparison/net/image-comparison/compare-images-from-stream/)
- [دليل GroupDocs Comparison .NET - دليل الاستخدام الأساسي الكامل](/comparison/net/basic-usage/)