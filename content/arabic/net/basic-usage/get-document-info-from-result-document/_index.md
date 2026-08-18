---
categories:
- Document Comparison
date: '2026-06-15'
description: تعلم كيفية استخراج البيانات الوصفية من نتائج مقارنة .NET باستخدام GroupDocs.Comparison.
  دليل خطوة بخطوة مع أمثلة على الشيفرة ونصائح عملية.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: استخراج معلومات المستند من نتائج المقارنة
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: كيفية استخراج البيانات الوصفية من نتائج مقارنة .NET – دليل كامل
type: docs
url: /ar/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# كيفية استخراج البيانات الوصفية من نتائج مقارنة .NET – دليل كامل

عند العمل على مقارنة المستندات في تطبيقات .NET، قد تتساءل **كيف تستخرج البيانات الوصفية** من نتائج المقارنة. البيانات الوصفية مثل نوع الملف، عدد الصفحات، وحجم المستند يمكن أن تكون حاسمة لسجلات التدقيق، تحسين الأداء، أو ببساطة عرض معلومات مفيدة للمستخدمين النهائيين. هذا الدرس يشرح لك كيفية استرجاع هذه البيانات بكفاءة باستخدام GroupDocs.Comparison لـ .NET.

## الإجابات السريعة
- **ما هو الصنف الرئيسي للمقارنة؟** `Comparer` يحمل المستند المصدر ويشغل محرك المقارنة.  
- **ما هي الطريقة التي تُعيد البيانات الوصفية؟** `GetDocumentInfo()` على مستند الهدف تُعيد كائن `IDocumentInfo`.  
- **هل يمكنني الحصول على حجم المستند في .NET؟** نعم – خاصية `Size` في `IDocumentInfo` تُعيد الحجم بالبايت.  
- **هل أحتاج إلى ترخيص لاستخراج البيانات الوصفية؟** ترخيص صالح لـ GroupDocs.Comparison مطلوب للاستخدام في الإنتاج؛ النسخة التجريبية المجانية تدعم جميع ميزات البيانات الوصفية.  
- **هل الـ API متوافق مع .NET 6؟** بالتأكيد – GroupDocs.Comparison يدعم .NET Framework 4.6.1+، .NET Core 2.0+، و .NET 5/6+.

طريقة `GetDocumentInfo()` تُعيد كائن `IDocumentInfo` يحتوي على البيانات الوصفية للمستند.

## ما هو استخراج البيانات الوصفية في مقارنة المستندات؟
استخراج البيانات الوصفية هو عملية استرجاع معلومات وصفية—مثل نوع الملف، عدد الصفحات، وحجم الملف—من المستندات المشاركة في عملية المقارنة. يتيح GroupDocs.Comparison هذه البيانات عبر API موحد، مما يجعل من السهل تسجيلها، عرضها، أو استخدامها في معالجة شرطية.

## لماذا استخراج البيانات الوصفية من نتائج المقارنة؟
استخراج البيانات الوصفية يتيح لك إنشاء سجلات تدقيق مفصلة، توجيه الملفات بناءً على النوع، وتعديل استراتيجيات المعالجة للمستندات الكبيرة. بمعرفة نوع الملف، عدد الصفحات، والحجم يمكنك تطبيق قواعد الامتثال، تقدير زمن المعالجة، وتقديم معلومات واضحة للمستخدمين قبل بدء المقارنة.

## المتطلبات المسبقة

1. **GroupDocs.Comparison for .NET** – تثبيت المكتبة من [صفحة الإصدارات الرسمية](https://releases.groupdocs.com/comparison/net/).  
   يمكنك أيضًا تصفح جميع الإصدارات في [صفحة إصدارات GroupDocs](https://releases.groupdocs.com/).  
2. **بيئة التطوير** – Visual Studio، VS Code، أو أي بيئة تطوير تدعم .NET 6+.  
3. **مستندات عينة** – ملفان (مثل `SOURCE.docx` و `TARGET.docx`) للاختبار. الـ API يعمل مع أكثر من **50 تنسيق مستند**.

## استيراد مساحات الأسماء

التوجيهات `using` التالية تمنحك الوصول إلى محرك المقارنة الأساسي، أدوات التعامل مع الملفات، وواجهات البيانات الوصفية.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

هذه الاستيرادات مطلوبة قبل إنشاء أي كائنات من GroupDocs.

## كيفية استخراج البيانات الوصفية من نتائج المقارنة؟

الصنف `Comparer` يحمل المستند المصدر وينسق عملية المقارنة.

لاسترجاع البيانات الوصفية، قم أولاً بتحميل المستند المصدر باستخدام مثيل `Comparer`، ثم أضف مستند(ات) الهدف. بعد تهيئة محرك المقارنة، استدعِ `GetDocumentInfo()` على كل هدف للحصول على كائن `IDocumentInfo` يحتوي على خصائص مثل نوع الملف، عدد الصفحات، والحجم. هذا النهج يعمل بشكل موحد عبر جميع الصيغ المدعومة.

### الخطوة 1: تهيئة Comparer مع مستند المصدر

`Comparer` هو الصنف الأساسي في GroupDocs.Comparison الذي يحمل المستند المصدر وينسق عمليات المقارنة. استخدام كتلة `using` يضمن تحرير جميع الموارد غير المُدارة تلقائيًا.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **نصيحة احترافية:** يمكنك تمرير أي `Stream` (ملف، ذاكرة، سحابة) إلى مُنشئ `Comparer`، وليس مجرد مسار ملف.

### الخطوة 2: إضافة مستند الهدف للمقارنة

طريقة `Add()` تقبل تدفقات إضافية أو مسارات ملفات، مما يتيح مقارنات من نوع واحد إلى متعدد.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **مهم:** ترتيب المستندات المضافة يؤثر على طريقة إبراز التغييرات في التقرير النهائي.

### الخطوة 3: استرجاع معلومات المستند من مستند النتيجة

`IDocumentInfo` يوفر عرضًا موحدًا للبيانات الوصفية مثل نوع الملف، عدد الصفحات، والحجم عبر جميع الصيغ المدعومة.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **فهم البيانات:** الكائن المرتجع يعمل بنفس الطريقة للـ DOCX، PDF، XLSX، و PPTX، لذا يمكنك كتابة كود غير معتمد على الصيغة.

### الخطوة 4: عرض معلومات المستند

بمجرد حصولك على مثيل `IDocumentInfo`، يمكنك تسجيله، تخزينه، أو عرض خصائصه.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

الخصائص الثلاث الأكثر استخدامًا هي:

- **FileType** – مثال: `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – إجمالي الصفحات أو الشرائح.  
- **Size** – حجم الملف بالبايت (مفيد لحسابات التخزين).

## كيفية الحصول على حجم المستند في .NET؟

خاصية `Size` تُعيد حجم الملف بالبايت.

يمكن الوصول إلى حجم المستند مباشرةً من مثيل `IDocumentInfo` عبر خاصية `Size`. تُعيد هذه الخاصية العدد الدقيق للبايتات للملف الأصلي، مما يتيح لك تحويله إلى كيلوبايت أو ميغابايت للعرض أو حسابات التخزين. تعكس هذه القيمة حجم الملف المصدر، وليس أي نسخة معالجة.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **ملاحظة:** قيمة `Size` تعكس حجم الملف الأصلي، وليس الحجم بعد أي معالجة داخلية أو ضغط.

## حالات الاستخدام الشائعة والتطبيقات العملية

- **معالجة دفعات:** استخدم نوع الملف لتوجيه ملفات DOCX إلى سير عمل خاص بـ Word وملفات PDF إلى خط أنابيب مُحسّن للـ PDF.  
- **إدارة التخزين:** أرشف المستندات التي يزيد حجمها عن 10 ميغابايت إلى حاوية تخزين بارد تلقائيًا.  
- **ردود فعل المستخدم:** اعرض عدد الصفحات والحجم قبل المقارنة لتحديد توقعات واقعية لوقت المعالجة.  
- **ضمان الجودة:** تحقق من اكتمال الملفات المرفوعة بمقارنة عدد الصفحات المتوقع مع الفعلي.

## استكشاف الأخطاء الشائعة وإصلاحها

- **أخطاء الوصول إلى الملف:** تحقق من أذونات القراءة واستخدم مسارات مطلقة أثناء التطوير.  
- **ضغط الذاكرة مع الملفات الكبيرة:** يفضَّل استخدام البث (`File.OpenRead`) بدلاً من تحميل الملف بالكامل في الذاكرة.  
- **استثناءات مرجعية فارغة:** قد تُعيد `FirstOrDefault()` قيمة `null` إذا لم يُضاف أي هدف؛ تحقق دائمًا قبل استدعاء `GetDocumentInfo()`.

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **بيانات وصفية محدودة للنص العادي:** الصيغ مثل `.txt` قد لا تُظهر `PageCount` ذات معنى. احرص على التعامل مع القيم المفقودة.

## اعتبارات الأداء

- **إدارة التدفقات:** احرص دائمًا على تغليف التدفقات بعبارات `using` لتحرير مقابض الملفات بسرعة.  
- **التخزين المؤقت:** احفظ البيانات الوصفية التي تُستدعى كثيرًا في ذاكرة مؤقتة لتجنب الاستخراج المتكرر.  
- **عمليات الدفعات:** عالج المستندات على مجموعات لتقليل الحمل وتحسين الإنتاجية.

## أفضل الممارسات للاستخدام في الإنتاج

- **معالجة أخطاء قوية:** ضع استخراج البيانات الوصفية داخل كتل try‑catch للتعامل مع الملفات الفاسدة أو غير المدعومة بأمان.  
- **تسجيل شامل:** سجِّل نوع المستند، حجمه، وعدد صفحاته لكل مقارنة لتسهيل استكشاف الأخطاء والامتثال للتدقيق.  
- **نظافة الأمان:** تجنّب كشف مسارات الملفات الكاملة أو تفاصيل الخادم الداخلية في رسائل واجهة المستخدم.  
- **تحرير الموارد:** حرِّر مثيلات `Comparer` فور الانتهاء، خاصة في خدمات الويب التي تتعامل مع طلبات متزامنة كثيرة.

## سيناريوهات متقدمة

### مستندات هدف متعددة

إذا قمت بمقارنة مصدر واحد مع عدة أهداف، قم بالتكرار عبر مجموعة `Targets` واستخرج البيانات الوصفية من كلٍ منها.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### معالجة شرطية بناءً على البيانات الوصفية

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### تخزين البيانات الوصفية في قاعدة بيانات

احفظ `FileType`، `PageCount`، و `Size` في جدول علائقي لتمكين التقارير والتحليلات عبر آلاف المقارنات.

## الأسئلة المتكررة

**س: هل GroupDocs.Comparison for .NET متوافق مع صيغ المستندات المتعددة؟**  
ج: نعم، يدعم **أكثر من 50 صيغة** بما فيها DOCX، PDF، PPTX، XLSX، TXT، والعديد غيرها، مع استخراج بيانات وصفية متسق عبرها.

**س: هل يمكنني تخصيص إعدادات المقارنة دون التأثير على استخراج البيانات الوصفية؟**  
ج: بالطبع. الإعدادات مثل الحساسية، أنواع التغييرات، وصيغة الإخراج مستقلة عن استدعاء `GetDocumentInfo()`.

**س: هل هناك نسخة تجريبية يمكنني استخدامها للتقييم؟**  
ج: نعم، حمّل نسخة تجريبية مجانية من [صفحة إصدارات GroupDocs](https://releases.groupdocs.com/). النسخة التجريبية تشمل جميع ميزات استخراج البيانات الوصفية.

**س: أين يمكنني الحصول على دعم لأسئلة التنفيذ؟**  
ج: استخدم [منتدى GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) للحصول على مساعدة المجتمع والدعم الرسمي من فريق GroupDocs.

**س: ما هي خيارات الترخيص المتاحة للنشر في بيئات الإنتاج؟**  
ج: تقدم GroupDocs تراخيص للمطورين، للموقع، ولـ OEM. خيارات الشراء مُدرجة في [صفحة شراء GroupDocs](https://purchase.groupdocs.com/buy).

---

**آخر تحديث:** 2026-06-15  
**تم الاختبار مع:** GroupDocs.Comparison 6.0 لـ .NET  
**المؤلف:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## دروس ذات صلة

- [إدارة بيانات المستند الوصفية .NET - دليل كامل لـ GroupDocs.Comparison](/comparison/net/metadata-management/)
- [الحصول على خصائص المستند C# .NET - استخراج بيانات الملف](/comparison/net/basic-usage/get-document-info-from-path/)
- [حفظ بيانات الهدف الوصفية مع GroupDocs.Comparison – درس .NET](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)