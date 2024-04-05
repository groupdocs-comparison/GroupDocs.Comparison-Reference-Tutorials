---
title: حفظ بيانات تعريف المستند المحددة من قبل المستخدم في مقارنة GroupDocs لـ .NET
linktitle: حفظ بيانات تعريف المستند المحددة من قبل المستخدم في مقارنة GroupDocs لـ .NET
second_title: GroupDocs.Comparison .NET API
description: تعرف على كيفية حفظ بيانات تعريف المستند المعرفة بواسطة المستخدم باستخدام GroupDocs Comparison for .NET. يمكنك بسهولة مقارنة البيانات الوصفية ومعالجتها من خلال تعليمات خطوة بخطوة.
type: docs
weight: 16
url: /ar/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية حفظ البيانات التعريفية للمستندات المعرفة من قبل المستخدم باستخدام GroupDocs Comparison for .NET. تعتبر البيانات الوصفية ضرورية لتنظيم المستندات وإدارتها بكفاءة. باستخدام GroupDocs Comparison، يمكنك بسهولة مقارنة بيانات التعريف ومعالجتها لتلبية متطلباتك المحددة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1.  مقارنة GroupDocs لـ .NET: قم بتنزيل وتثبيت GroupDocs Comparison لـ .NET من[هنا](https://releases.groupdocs.com/comparison/net/).
2. بيئة التطوير: تأكد من أن لديك بيئة تطوير مناسبة مثل Visual Studio المثبتة على نظامك.
3. المستندات المصدر والهدف: قم بإعداد المستندات المصدر والهدف التي تريد مقارنتها ومعالجة بيانات التعريف الخاصة بها.

## استيراد مساحات الأسماء
أولاً، قم باستيراد مساحات الأسماء الضرورية للوصول إلى الوظائف التي توفرها GroupDocs Comparison لـ .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## الخطوة 1: تحديد دليل الإخراج واسم الملف
حدد الدليل الذي تريد حفظ المستند المقارن فيه وحدد اسم ملف الإخراج.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## الخطوة 2: تهيئة المقارن وإضافة المستندات
 تهيئة`Comparer` كائن مع المستند المصدر وإضافة المستند الهدف للمقارنة.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## الخطوة 3: تحديد خيارات البيانات التعريفية
 حدد خيارات البيانات التعريفية للحفظ في الوثيقة المقارنة. في هذا المثال، قمنا بتعيين`CloneMetadataType` ل`MetadataType.FileAuthor` وتقديم تفاصيل عن`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## الخطوة 4: مقارنة المستندات وحفظ البيانات التعريفية
قارن المستندات بخيارات البيانات التعريفية المحددة واحفظ المستند المقارن.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## الخطوة 5: عرض رسالة النجاح
عرض رسالة نجاح تشير إلى أنه تمت مقارنة المستندات بنجاح وموقع الإخراج.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية حفظ بيانات تعريف المستند المعرفة من قبل المستخدم باستخدام GroupDocs Comparison for .NET. باتباع هذه الخطوات، يمكنك مقارنة المستندات بكفاءة مع الحفاظ على بيانات التعريف ومعالجتها وفقًا لمتطلباتك.
## الأسئلة الشائعة
### هل تستطيع مقارنة GroupDocs لـ .NET التعامل مع تنسيقات المستندات المختلفة؟
نعم، تدعم GroupDocs Comparison نطاقًا واسعًا من تنسيقات المستندات بما في ذلك DOCX وPDF وPPTX وXLSX والمزيد.
### هل تتوفر نسخة تجريبية مجانية من GroupDocs Comparison لـ .NET؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية[هنا](https://releases.groupdocs.com/).
### هل يمكنني تخصيص خيارات البيانات الوصفية وفقًا لاحتياجاتي؟
بالتأكيد، توفر GroupDocs Comparison خيارات مرنة لتخصيص معالجة بيانات التعريف أثناء مقارنة المستندات.
### هل تقدم GroupDocs Comparison الدعم الفني؟
نعم، يمكنك الحصول على الدعم الفني من منتدى مقارنة GroupDocs[هنا](https://forum.groupdocs.com/c/comparison/12).
### أين يمكنني شراء ترخيص GroupDocs Comparison لـ .NET؟
 يمكنك شراء ترخيص من موقع GroupDocs على الويب[هنا](https://purchase.groupdocs.com/buy).