---
categories:
- Java Development
date: '2026-08-25'
description: تعلم كيفية الحصول على عدد صفحات pdf في Java واستخراج بيانات تعريف المستند
  باستخدام GroupDocs.Comparison. استرجع نوع الملف، الحجم، عدد الصفحات، وأكثر مع أمثلة
  code مختصرة ونصائح استكشاف الأخطاء.
keywords:
- java pdf page count
- get file type java
- detect file type java
- read file size java
- java extract file properties
lastmod: '2026-08-25'
linktitle: استخراج بيانات تعريف المستند في Java
og_description: تعلم كيفية الحصول على عدد صفحات pdf في Java واستخراج بيانات تعريف
  المستند باستخدام GroupDocs.Comparison. احصل على نوع الملف، الحجم، وعدد الصفحات بسرعة
  باستخدام code بسيط.
og_image_alt: Guide showing Java code to extract PDF page count and metadata with
  GroupDocs.Comparison
og_title: كيفية الحصول على عدد صفحات pdf في java واستخراج بيانات تعريف المستند
schemas:
- author: GroupDocs
  dateModified: '2026-08-25'
  description: Learn how to java pdf page count and extract document metadata in Java
    using GroupDocs.Comparison. Retrieve file type, size, page count, and more with
    concise code examples and troubleshooting tips.
  headline: How to get java pdf page count and extract document metadata
  type: TechArticle
- description: Learn how to java pdf page count and extract document metadata in Java
    using GroupDocs.Comparison. Retrieve file type, size, page count, and more with
    concise code examples and troubleshooting tips.
  name: How to get java pdf page count and extract document metadata
  steps:
  - name: Maven configuration
    text: 'Add the GroupDocs.Comparison dependency to your `pom.xml`. Place the snippet
      inside the `<dependencies>` section: **Pro tip**: Always verify the latest version
      on the GroupDocs website—using an outdated version can cause compatibility warnings
      and missing features.'
  - name: License setup (don’t skip this!)
    text: GroupDocs.Comparison requires a valid license for production use. 1. **Free
      trial** – ideal for testing and small projects. Download from the [free trial
      page](https://releases.groupdocs.com/comparison/java/). 2. **Temporary license**
      – useful for development and evaluation. Apply for a temporary li
  - name: Verify your setup
    text: 'Create a simple test class to ensure the library loads correctly: If the
      program runs without exceptions, you’re ready to extract metadata.'
  type: HowTo
- questions:
  - answer: Yes, provide the password via `LoadOptions` when constructing the `Comparer`
      instance.
    question: Can I extract metadata from password‑protected documents?
  - answer: GroupDocs.Comparison supports 50+ formats, including DOCX, PDF, XLSX,
      PPTX, TXT, RTF, HTML, and many image types.
    question: What file formats are supported for metadata extraction?
  - answer: Standard `DocumentInfo` covers built‑in properties; for custom properties
      you’ll need to combine GroupDocs with the Office Open XML SDK or a similar library.
    question: Is there a way to extract custom properties from Office documents?
  - answer: Use try‑with‑resources, process files one at a time, and allocate sufficient
      JVM heap (e.g., `-Xmx2g`). The library streams large files, so you rarely need
      to load the entire document into memory.
    question: How do I handle very large files without running out of memory?
  - answer: Yes, download the file to a temporary local path or stream it directly
      into a `ByteArrayInputStream` before passing it to `Comparer`.
    question: Can this work with documents stored in cloud storage?
  type: FAQPage
tags:
- java pdf page count
- groupdocs
- metadata extraction
- java tutorial
title: كيفية الحصول على عدد صفحات pdf في java واستخراج بيانات تعريف المستند
type: docs
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية الحصول على عدد صفحات PDF في جافا واستخراج بيانات تعريف المستند

إذا كنت بحاجة إلى **java pdf page count** دون فتح المستند، فأنت في المكان الصحيح. سواءً كنت تبني نظام إدارة مستندات، أو تتحقق من صحة التحميلات، أو تقوم بأتمتة خط أنابيب المحتوى، فإن استخراج نوع الملف وحجمه وعدد الصفحات برمجيًا يوفر الوقت ويقلل الأخطاء. في هذا الدليل سنرشدك لاستخدام GroupDocs.Comparison for Java للحصول على **java get file type**، **java read file size**، و **java get page count**، بالإضافة إلى نصائح أفضل الممارسات للتعامل مع الحالات الحدية والملفات الكبيرة.

## إجابات سريعة
- **ما المكتبة التي يمكنني استخدامها للحصول على نوع الملف في جافا؟** GroupDocs.Comparison for Java.  
- **هل يمكنني أيضًا استخراج بيانات تعريف PDF في جافا؟** نعم – نفس الـ API يعمل مع ملفات PDF والعديد من الصيغ الأخرى.  
- **هل أحتاج إلى ترخيص؟** ترخيص تجريبي أو مؤقت يعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما نسخة جافا المطلوبة؟** JDK 8+ (يوصى بـ JDK 11+).  
- **هل الشيفرة آمنة للخطوط المتعددة؟** أنشئ نسخة منفصلة من `Comparer` لكل خيط.  

## لماذا استخراج بيانات تعريف المستند؟

يتيح استخراج بيانات تعريف المستند تحديد نوع الملف وحجمه وعدد صفحاته برمجيًا، مما يمكّن من التحقق الآلي، الفهرسة، واتخاذ قرارات سير العمل. يمكنك رفض الصيغ غير المدعومة فورًا، توجيه الملفات الكبيرة إلى طابور معالجة منفصل، أو إنشاء تقارير تلخص مجموعات المستندات. في السيناريوهات الواقعية يقلل ذلك من الجهد اليدوي، يحسن فحوصات الامتثال، ويسرّع عمليات الدُفعات عبر آلاف الملفات.

## ما ستتعلمه في هذا الدليل

ستتعلم في هذا البرنامج التعليمي كيفية إعداد GroupDocs.Comparison لجافا، استرجاع **java pdf page count**، الحصول على نوع الملف وحجمه، ومعالجة الأخطاء الشائعة، بحيث يمكنك دمج استخراج البيانات الوصفية في أي تطبيق جافا. كما ستطلع على أنماط أفضل الممارسات لإدارة الموارد، معالجة الأخطاء، وتحسين الأداء عند العمل مع مستندات كبيرة.

## المتطلبات المسبقة: ما تحتاجه قبل البدء

تحتاج إلى JDK 8 أو أعلى، Maven لإدارة الاعتمادات، وIDE مثل IntelliJ IDEA أو Eclipse أو VS Code، بالإضافة إلى ترخيص GroupDocs.Comparison (تجريبي أو كامل) لتشغيل أمثلة الشيفرة. تعمل المكتبة على أي منصة تدعم Java 8+، ويجب أن تكون لديك صلاحيات القراءة/الكتابة على المجلد الذي يحتوي على المستندات التي تنوي تحليلها.

## إعداد GroupDocs.Comparison لجافا

### الخطوة 1: تكوين Maven

أضف اعتماد GroupDocs.Comparison إلى ملف `pom.xml`. ضع المقتطف داخل قسم `<dependencies>`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>
<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**نصيحة احترافية**: تحقق دائمًا من أحدث نسخة على موقع GroupDocs — استخدام نسخة قديمة قد يسبب تحذيرات توافق وغياب ميزات.

### الخطوة 2: إعداد الترخيص (لا تتخطى هذه الخطوة!)

GroupDocs.Comparison يتطلب ترخيصًا صالحًا للاستخدام في الإنتاج.

1. **نسخة تجريبية مجانية** – مثالية للاختبار والمشاريع الصغيرة. حمّلها من [free trial page](https://releases.groupdocs.com/comparison/java/).  
2. **ترخيص مؤقت** – مفيد للتطوير والتقييم. قدّم طلبًا للحصول على ترخيص مؤقت [here](https://purchase.groupdocs.com/temporary-license/).  
3. **ترخيص كامل** – مطلوب للنشر التجاري. [Purchase a license](https://purchase.groupdocs.com/buy).

### الخطوة 3: التحقق من إعدادك

أنشئ فئة اختبار بسيطة للتأكد من تحميل المكتبة بشكل صحيح:

```java
import com.groupdocs.comparison.Comparer;

public class SetupTest {
    public static void main(String[] args) {
        System.out.println("GroupDocs.Comparison is ready to use!");
        // We'll add actual functionality next
    }
}
```

إذا تم تشغيل البرنامج دون استثناءات، فأنت جاهز لاستخراج البيانات الوصفية.

## دليل التنفيذ: استخراج بيانات تعريف المستند خطوة بخطوة

### java get file type – تهيئة كائن Comparer

`Comparer` هو الفئة الرئيسية التي تُحمّل المستند وتوفر الوصول إلى بياناته الوصفية.

```java
import com.groupdocs.comparison.Comparer;
import java.io.IOException;

try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    // We'll extract info here
} catch (Exception e) {
    System.err.println("Error initializing comparer: " + e.getMessage());
}
```

**ما الذي يحدث؟**  
- يضمن كتلة `try‑with‑resources` إغلاق كائن `Comparer` تلقائيًا، مما يمنع تسرب الذاكرة.  
- يمكن توسيع كائن `loadOptions` لاحقًا لملفات محمية بكلمة مرور أو إعدادات تحميل مخصصة.  

### الحصول على كائن معلومات المستند

`DocumentInfo` يوفر عرضًا للقراءة فقط للخصائص المستخرجة من المستند مثل نوع الملف، حجمه، وعدد الصفحات.

```java
import com.groupdocs.comparison.interfaces.IDocumentInfo;

try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    try (IDocumentInfo info = comparer.getSource().getDocumentInfo()) {
        // Extract metadata here
    }
} catch (Exception e) {
    System.err.println("Error retrieving document info: " + e.getMessage());
}
```

**نقاط رئيسية:**  
- `getSource()` يُعيد غلاف المستند الأصلي.  
- `getDocumentInfo()` يمنحك عرضًا للقراءة فقط لجميع البيانات الوصفية المستخرجة.  

### استخراج المعلومات المفيدة

`FileType` يمثل الصيغة المكتشفة للمستند، بينما `getSize()` يُعيد طوله بالبايت.

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    try (IDocumentInfo info = comparer.getSource().getDocumentInfo()) {
        // Extract key information
        String fileType = info.getFileType().getFileFormat();
        int pageCount = info.getPageCount();
        long fileSize = info.getSize();
        
        // Display the results
        System.out.printf("File type: %s\n", fileType);
        System.out.printf("Number of pages: %d\n", pageCount);
        System.out.printf("Document size: %d bytes (%.2f KB)\n", 
                         fileSize, fileSize / 1024.0);
    }
} catch (Exception e) {
    System.err.println("Error extracting document info: " + e.getMessage());
}
```

**ما تُعيده كل طريقة:**  
- `getFileType().getFileFormat()` → صيغة الملف مثل DOCX أو PDF أو TXT.  
- `getPageCount()` → إجمالي عدد الصفحات، أي **java pdf page count** الذي تحتاجه غالبًا.  
- `getSize()` → حجم الملف بالبايت، مفيد لفحوصات **java read file size**.

## مثال واقعي: تنفيذ كامل

فيما يلي مقتطف جاهز للإنتاج يربط كل شيء معًا. يوضح تحميل ملف، استخراج الخصائص الثلاث الأساسية، وطباعة النتائج إلى وحدة التحكم.

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.interfaces.IDocumentInfo;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;

public class DocumentMetadataExtractor {
    
    public static void extractDocumentInfo(String filePath) {
        // First, check if file exists
        Path path = Paths.get(filePath);
        if (!Files.exists(path)) {
            System.err.println("File not found: " + filePath);
            return;
        }
        
        try (Comparer comparer = new Comparer(filePath)) {
            try (IDocumentInfo info = comparer.getSource().getDocumentInfo()) {
                displayDocumentInfo(info, filePath);
            }
        } catch (Exception e) {
            System.err.println("Error processing file " + filePath + ": " + e.getMessage());
        }
    }
    
    private static void displayDocumentInfo(IDocumentInfo info, String filePath) {
        String fileName = Paths.get(filePath).getFileName().toString();
        String fileType = info.getFileType().getFileFormat();
        int pageCount = info.getPageCount();
        long fileSize = info.getSize();
        
        System.out.println("=== Document Information ===");
        System.out.printf("File name: %s\n", fileName);
        System.out.printf("File type: %s\n", fileType);
        System.out.printf("Pages: %d\n", pageCount);
        System.out.printf("Size: %d bytes (%.2f KB)\n", fileSize, fileSize / 1024.0);
        System.out.println("============================\n");
    }
    
    public static void main(String[] args) {
        // Test with different file types
        extractDocumentInfo("path/to/your/document.docx");
        extractDocumentInfo("path/to/your/document.pdf");
    }
}
```

## المشكلات الشائعة والحلول

### المشكلة 1: أخطاء “الملف غير موجود”

**الأعراض**: استثناء يُرمى عند تهيئة `Comparer`.  
**الحل**: تحقق دائمًا من صحة مسار الملف قبل إنشاء كائن `Comparer`:

```java
Path filePath = Paths.get(documentPath);
if (!Files.exists(filePath)) {
    throw new IllegalArgumentException("File does not exist: " + documentPath);
}
if (!Files.isReadable(filePath)) {
    throw new IllegalArgumentException("File is not readable: " + documentPath);
}
```

### المشكلة 2: مشاكل الذاكرة مع الملفات الكبيرة

**الأعراض**: `OutOfMemoryError` أو أداء بطيء عند معالجة ملفات PDF مئات الصفحات.  
**الحل**: عالج الملفات واحدةً تلو الأخرى، استخدم `try‑with‑resources`، وفكّر في زيادة حجم كومة JVM (`-Xmx2g` حتى 2 GB). يمكن لـ GroupDocs.Comparison معالجة ملفات تصل إلى 2 GB دون تحميل المستند بالكامل في الذاكرة.

```java
// Always use try-with-resources
try (Comparer comparer = new Comparer(filePath)) {
    // Process immediately and don't store large objects
    processDocumentInfo(comparer.getSource().getDocumentInfo());
} // Resources automatically cleaned up here
```

### المشكلة 3: صيغ ملفات غير مدعومة

**الأعراض**: استثناءات عندما تواجه المكتبة امتدادًا غير معروف.  
**الحل**: تحقق من قائمة الصيغ المدعومة قبل المعالجة. يدعم GroupDocs.Comparison **أكثر من 50 صيغة** للإدخال والإخراج، بما في ذلك DOCX، PDF، XLSX، PPTX، TXT، RTF، وHTML.

```java
public static boolean isSupportedFormat(String filePath) {
    String extension = FilenameUtils.getExtension(filePath).toLowerCase();
    return Arrays.asList("docx", "doc", "pdf", "txt", "rtf", "odt").contains(extension);
}
```

### المشكلة 4: مشاكل الترخيص في الإنتاج

**الأعراض**: ظهور علامات مائية أو تعطيل بعض الـ APIs.  
**الحل**: تأكد من تحميل ملف الترخيص بشكل صحيح عند بدء التطبيق وأن نسخة الترخيص تتطابق مع نسخة المكتبة.

```java
// Apply license at application startup
License license = new License();
license.setLicense("path/to/your/license.lic");
```

## أفضل الممارسات للاستخدام في الإنتاج

### 1. إدارة الموارد

استخدم دائمًا `try‑with‑resources` للتنظيف التلقائي لـ `Comparer` والـ streams المرتبطة:

```java
// Good - resources cleaned up automatically
try (Comparer comparer = new Comparer(filePath);
     IDocumentInfo info = comparer.getSource().getDocumentInfo()) {
    // Process info
}

// Bad - potential memory leaks
Comparer comparer = new Comparer(filePath);
IDocumentInfo info = comparer.getSource().getDocumentInfo();
// Processing code
// Resources might not be cleaned up properly
```

### 2. استراتيجية معالجة الأخطاء

غلف استخراج البيانات الوصفية في كتلة `try` واحدة وسجّل معلومات الخطأ بالتفصيل. هذا يُسهل استكشاف الأخطاء ويمنع تعطل التطبيق بشكل غير متوقع.

```java
public DocumentInfo extractSafely(String filePath) {
    try {
        return extractDocumentInfo(filePath);
    } catch (SecurityException e) {
        log.warn("Access denied for file: " + filePath, e);
        return null;
    } catch (IOException e) {
        log.error("I/O error processing file: " + filePath, e);
        return null;
    } catch (Exception e) {
        log.error("Unexpected error processing file: " + filePath, e);
        return null;
    }
}
```

### 3. تحسين الأداء

عند معالجة دفعات، أعد استخدام `ComparerFactory` محليًا لكل خيط لتجنب إنشاء كائنات متكررة، وحدّ عدد الخيوط المتزامنة إلى عدد نوى المعالج لتحقيق أقصى إنتاجية.

```java
public List<DocumentInfo> processDocumentBatch(List<String> filePaths) {
    return filePaths.parallelStream()
                   .map(this::extractSafely)
                   .filter(Objects::nonNull)
                   .collect(Collectors.toList());
}
```

## متى تستخدم هذا مقابل الأساليب الأخرى

**استخدم GroupDocs.Comparison عندما:**  
- تحتاج إلى استخراج بيانات تعريف موثوقة عبر مجموعة واسعة من صيغ Office والصور.  
- تتوقع الحاجة إلى ميزات مقارنة المستندات لاحقًا، حيث يدعم نفس فئة `Comparer` كلا الوظيفتين.  
- تتجاوز مستنداتك 100 صفحة وتحتاج إلى عدّ صفحات دقيق دون الحاجة إلى عرضها.

**فكر في البدائل عندما:**  
- تحتاج فقط إلى فحص حجم الملف أو امتداده—يمكنك الاعتماد على `java.nio.file.Files.probeContentType` و `Files.size`.  
- القيود المالية تمنع الحصول على ترخيص تجاري—المكتبات المفتوحة المصدر مثل Apache Tika توفر بيانات تعريف أساسية لكنها لا تغطي نفس نطاق الصيغ الذي تقدمه GroupDocs.

## دليل استكشاف الأخطاء وإصلاحها

### المشكلة: الشيفرة تُترجم ولكنها تُطلق استثناءات وقت التشغيل

**تحقق من التالي:**  
1. هل تم تطبيق الترخيص بشكل صحيح؟  
2. هل تستخدم مسارات مطلقة أم موارد على classpath؟  
3. هل للعملية صلاحيات قراءة على الملف؟  
4. هل الصيغة مدرجة في جدول الصيغ المدعومة؟

### المشكلة: استهلاك الذاكرة يزداد باستمرار

**الحلول:**  
1. تأكد من إنشاء كل `Comparer` داخل كتلة `try‑with‑resources`.  
2. عالج الملفات تسلسليًا بدلاً من تحميل عدة ملفات في آنٍ واحد.  
3. زد حجم كومة JVM فقط إذا كان ذلك ضروريًا؛ يفضَّل استخدام واجهات البث (streaming) عندما يكون ذلك ممكنًا.

### المشكلة: بعض حقول البيانات الوصفية تُعيد null

هذا طبيعي للملفات التي لا تحتوي على الخاصية المطلوبة (مثل ملف نصي بسيط لا يمتلك عدد صفحات). تحقق دائمًا من وجود قيمة قبل استخدامها.

## الخلاصة والخطوات التالية

أصبحت الآن تمتلك أساسًا قويًا لاستخراج بيانات تعريف المستند—بما في ذلك **java pdf page count**، نوع الملف، والحجم—باستخدام GroupDocs.Comparison لجافا. تعلمت كيفية إعداد المكتبة، استرجاع الخصائص الرئيسية، التعامل مع المشكلات الشائعة، وتطبيق أفضل الممارسات على مستوى الإنتاج.

### ما التالي؟

- استكشف واجهات **مقارنة المستندات** لاكتشاف التغييرات بين الإصدارات.  
- دمج استخراج البيانات الوصفية في خدمة **Spring Boot** REST لتوفير التحليل عند الطلب.  
- تنفيذ **معالجة دفعات** باستخدام نظام طابور (مثل RabbitMQ) للعبء العالي.  
- الغوص في **استخراج الخصائص المخصصة** لملفات Office إذا كنت بحاجة إلى بيانات تعريف خاصة بالشركة.

للمزيد من التفاصيل، اطلع على [الوثائق الرسمية لـ GroupDocs](https://docs.groupdocs.com/comparison/java/) والمرجع الكامل للـ API.

## الأسئلة المتكررة

**س: هل يمكنني استخراج بيانات تعريف من مستندات محمية بكلمة مرور؟**  
ج: نعم، قدم كلمة المرور عبر `LoadOptions` عند إنشاء كائن `Comparer`.

**س: ما صيغ الملفات المدعومة لاستخراج البيانات الوصفية؟**  
ج: يدعم GroupDocs.Comparison أكثر من 50 صيغة، بما في ذلك DOCX، PDF، XLSX، PPTX، TXT، RTF، HTML، والعديد من صيغ الصور.

**س: هل هناك طريقة لاستخراج خصائص مخصصة من مستندات Office؟**  
ج: يغطي `DocumentInfo` الخصائص المدمجة؛ لاستخراج خصائص مخصصة ستحتاج إلى دمج GroupDocs مع Office Open XML SDK أو مكتبة مشابهة.

**س: كيف أتعامل مع ملفات ضخمة دون نفاد الذاكرة؟**  
ج: استخدم `try‑with‑resources`، عالج الملفات واحدةً تلو الأخرى، وزد حجم كومة JVM إذا لزم الأمر (مثلاً `-Xmx2g`). المكتبة تقوم ببث الملفات الكبيرة، لذا نادرًا ما تحتاج إلى تحميل المستند بالكامل في الذاكرة.

**س: هل يمكن تشغيل هذا مع ملفات مخزنة في سحابة؟**  
ج: نعم، حمّل الملف إلى مسار محلي مؤقت أو بثه مباشرة إلى `ByteArrayInputStream` قبل تمريره إلى `Comparer`.

**س: ماذا أفعل إذا ظهرت أخطاء ترخيص؟**  
ج: تحقق من صحة مسار ملف الترخيص، وتأكد من توافق نسخة الترخيص مع نسخة المكتبة، وتأكد من عدم انتهاء صلاحيته. إذا استمرت المشكلة، تواصل مع دعم GroupDocs.

**س: هل هو آمن للاستخدام في تطبيقات متعددة الخيوط؟**  
ج: بالتأكيد، طالما أن كل خيط ينشئ نسخة خاصة به من `Comparer`. لا تشارك نسخة واحدة بين الخيوط.

**الموارد الإضافية**  
- **الوثائق**: [GroupDocs.Comparison Java Docs](https://docs.groupdocs.com/comparison/java/)  
- **مرجع API**: [Complete API Documentation](https://reference.groupdocs.com/comparison/java/)  
- **دعم المجتمع**: [GroupDocs Forum](https://forum.groupdocs.com/c/comparison)  
- **نسخة تجريبية**: [Download and Test](https://releases.groupdocs.com/comparison/java/)

---

**آخر تحديث:** 2026-08-25  
**تم الاختبار مع:** GroupDocs.Comparison 25.2  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [Get File Type Java – Extract Document Metadata with GroupDocs](/comparison/java/document-information/groupdocs-comparison-java-document-extraction/)
- [Set Document metadata in Java with GroupDocs.Comparison](/comparison/java/metadata-management/implement-metadata-groupdocs-comparison-java-guide/)
- [Set Custom Metadata Java with GroupDocs Comparison](/comparison/java/metadata-management/groupdocs-comparison-java-custom-metadata-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}