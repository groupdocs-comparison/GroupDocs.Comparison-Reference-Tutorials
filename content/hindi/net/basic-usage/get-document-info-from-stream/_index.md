---
categories:
- Document Processing
date: '2026-07-01'
description: GroupDocs.Comparison का उपयोग करके फ़ाइल मेटाडेटा पढ़ना C# में सीखें,
  फ़ाइल आकार स्ट्रीम निकालें और दस्तावेज़ गुणों की स्ट्रीम को कुशलतापूर्वक प्राप्त
  करें।
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: दस्तावेज़ जानकारी निकालें .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: फ़ाइल मेटाडेटा पढ़ें C# – स्ट्रीम से दस्तावेज़ जानकारी निकालें
type: docs
url: /hi/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# फ़ाइल मेटाडेटा पढ़ें C# – स्ट्रीम से दस्तावेज़ जानकारी निकालें

## परिचय

Reading file metadata in C# without loading the whole document is a common requirement for modern .NET applications. **Read file metadata C#** lets you validate uploads, display document details, and make processing decisions while keeping memory usage low. GroupDocs.Comparison for .NET provides a fast, stream‑based API that extracts file type, page count, size, and other properties directly from a `Stream`. In the next sections you’ll see why this matters, how to set it up, and step‑by‑step code you can drop into any .NET project.

## त्वरित उत्तर
- **“read file metadata C#” क्या है?** यह .NET स्ट्रीम के माध्यम से दस्तावेज़ की गुणधर्म (प्रकार, पृष्ठ, आकार) प्राप्त करने का अर्थ है, बिना पूरी सामग्री लोड किए।  
- **यह कौन सी लाइब्रेरी संभालती है?** GroupDocs.Comparison for .NET तेज़ मेटाडेटा निष्कर्षण के लिए `GetDocumentInfo()` मेथड प्रदान करता है।  
- **क्या मुझे लाइसेंस की आवश्यकता है?** विकास के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए एक व्यावसायिक लाइसेंस आवश्यक है।  
- **क्या मैं इसे बड़े PDF के साथ उपयोग कर सकता हूँ?** हां – स्ट्रीम दृष्टिकोण कई सौ पृष्ठों वाली फ़ाइलों को उच्च मेमोरी उपयोग के बिना प्रोसेस करता है।  
- **क्या यह .NET 6+ के साथ संगत है?** बिल्कुल, लाइब्रेरी .NET Standard 2.0 को लक्षित करती है और .NET 6, .NET 7, तथा .NET Core पर काम करती है।

## read file metadata C# क्या है?
`Read file metadata C#` दस्तावेज़ की वर्णनात्मक जानकारी—जैसे फ़ॉर्मेट, पृष्ठ संख्या, और बाइट आकार—प्राप्त करने को दर्शाता है, जो C# कोड द्वारा स्ट्रीम के साथ काम करता है। यह तकनीक पूरी फ़ाइल को मेमोरी में लोड करने से बचती है, जो बड़े PDF, DOCX फ़ाइलों, या बैच ऑपरेशनों के लिए विशेष रूप से उपयोगी है।

## स्ट्रीम से GroupDocs मेटाडेटा निष्कर्षण का उपयोग क्यों करें?
GroupDocs.Comparison **50+ इनपुट और आउटपुट फ़ॉर्मेट** का समर्थन करता है और **2 GB** तक के फ़ाइलों से मेटाडेटा निकाल सकता है जबकि मेमोरी उपयोग **10 MB** से कम रहता है। लाइब्रेरी केवल आवश्यक हेडर सेक्शन पढ़ती है, जिससे मानक सर्वर पर सामान्य 100‑पृष्ठ PDF के लिए **150 ms** से कम समय में परिणाम मिलते हैं। ये मापनीय लाभ तेज़ अपलोड वैधता, कम क्लाउड लागत, और बेहतर उपयोगकर्ता अनुभव में परिवर्तित होते हैं।

## पूर्वापेक्षाएँ और सेटअप

### 1. GroupDocs.Comparison for .NET स्थापित करें
नवीनतम पैकेज [आधिकारिक डाउनलोड पेज](https://releases.groupdocs.com/comparison/net/) से डाउनलोड करें। यदि आप NuGet पसंद करते हैं, तो चलाएँ:

```
Install-Package GroupDocs.Comparison
```

### 2. बुनियादी .NET विकास ज्ञान
आपको C# और .NET I/O मॉडल में सहज होना चाहिए। नीचे दिए गए उदाहरणों के लिए `Stream`, `FileStream`, और `MemoryStream` के साथ काम करना आवश्यक है।

### 3. विकास वातावरण
Visual Studio, VS Code, या JetBrains Rider सभी समर्थित हैं। सर्वोत्तम प्रदर्शन के लिए सुनिश्चित करें कि आपका प्रोजेक्ट .NET 6 या बाद के संस्करण को लक्षित करता हो।

## स्ट्रीम से फ़ाइल मेटाडेटा पढ़ना C# कैसे करें?
दस्तावेज़ को `FileStream` से लोड करें, एक `Comparer` बनाएं, और `GetDocumentInfo()` को कॉल करें। पूरी प्रक्रिया केवल दो कोड लाइनों में पूरी होती है और एक `IDocumentInfo` ऑब्जेक्ट लौटाती है जिसमें फ़ाइल प्रकार, पृष्ठ संख्या, और आकार शामिल होते हैं। आंतरिक रूप से लाइब्रेरी केवल आवश्यक हेडर बाइट्स पढ़ती है, इसलिए बड़े PDF भी जल्दी प्रोसेस होते हैं बिना अधिक मेमोरी उपयोग के।  
`Comparer` मुख्य GroupDocs.Comparison क्लास है जो दस्तावेज़ विश्लेषण को समन्वयित करता है।  
`GetDocumentInfo()` बुनियादी मेटाडेटा के साथ एक `IDocumentInfo` ऑब्जेक्ट लौटाता है।

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### चरण 1: स्ट्रीम के साथ Comparer ऑब्जेक्ट को प्रारंभ करें
निम्नलिखित स्निपेट एक पढ़ने‑के‑लिए‑केवल `FileStream` से `Comparer` इंस्टेंस बनाता है। `using` ब्लॉक का उपयोग यह सुनिश्चित करता है कि स्ट्रीम बंद हो और comparer डिस्पोज़ हो, जिससे फ़ाइल लॉक नहीं होते।

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### चरण 2: दस्तावेज़ जानकारी निकालें
`GetDocumentInfo()` को कॉल करने से एक `IDocumentInfo` ऑब्जेक्ट मिलता है जिसमें आपको आवश्यक सभी मेटाडेटा होते हैं। मेथड फ़ाइल हेडर के केवल आवश्यक भाग पढ़ता है, इसलिए 500‑पृष्ठ PDF भी एक सेकंड के अंश में प्रोसेस हो जाता है।

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### चरण 3: दस्तावेज़ जानकारी प्रदर्शित करें और उपयोग करें
अब आप `FileType`, `PageCount`, और `Size` प्रॉपर्टीज़ तक पहुँच सकते हैं। उत्पादन में आप इन मानों को डेटाबेस में संग्रहीत कर सकते हैं, API के माध्यम से एक्सपोज़ कर सकते हैं, या अपलोड स्वीकार करने का निर्णय लेने के लिए उपयोग कर सकते हैं।

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## सामान्य उपयोग केस और कार्यान्वयन पैटर्न

### फ़ाइल अपलोड वैधता
जब उपयोगकर्ता कोई दस्तावेज़ अपलोड करता है, तो आप इसे स्टोरेज में कमिट करने से पहले तुरंत उसका प्रकार और पृष्ठ संख्या सत्यापित कर सकते हैं। यह अनचाहे फ़ॉर्मेट और बड़े फ़ाइलों को आपके सिस्टम में प्रवेश करने से रोकता है।

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### बैच दस्तावेज़ विश्लेषण
दस्तावेज़ों के फ़ोल्डर को प्रोसेस कर रहे हैं? पहले मेटाडेटा निकालें ताकि फ़ाइलों को विभिन्न पाइपलाइन में रूट किया जा सके—जैसे, बड़े PDF असिंक्रोनस वर्कर को भेजे जाएँ, जबकि सिंगल‑पेज फ़ाइलें इनलाइन संभाली जाएँ।

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## सामान्य समस्याएँ और समाधान

### फ़ाइल एक्सेस और लॉकिंग समस्याएँ
**Issue**: “फ़ाइल किसी अन्य प्रक्रिया द्वारा उपयोग की जा रही है।”  
**Solution**: स्ट्रीम को `using` स्टेटमेंट में रैप करें और आवश्यकता होने पर एक्सपोनेंशियल बैक‑ऑफ़ के साथ रीट्राई पॉलिसी लागू करें।

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### असमर्थित फ़ाइल फ़ॉर्मेट हैंडलिंग
**Issue**: अज्ञात फ़ॉर्मेट के लिए API एक एक्सेप्शन फेंकता है।  
**Solution**: `FileType` प्रॉपर्टी की जाँच करें; यदि यह `Unknown` लौटाता है, तो कॉलर को एक मित्रवत त्रुटि लौटाएँ और घटना को लॉग करें।

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### बड़ी फ़ाइलों के साथ मेमोरी प्रबंधन
**Issue**: बहुत बड़ी दस्तावेज़ों को प्रोसेस करते समय मेमोरी स्पाइक होती है।  
**Solution**: स्ट्रीम‑आधारित दृष्टिकोण पहले से ही मेमोरी उपयोग को न्यूनतम करता है, लेकिन आपको काम समाप्त होते ही `Comparer` पर `Dispose()` कॉल करना चाहिए और `IDocumentInfo` के रेफ़रेंस को आवश्यक से अधिक समय तक नहीं रखना चाहिए।

## प्रदर्शन विचार और सर्वोत्तम प्रथाएँ

### स्ट्रीम प्रबंधन सर्वोत्तम प्रथाएँ
1. **हमेशा `using` स्टेटमेंट्स का उपयोग करें** – यह डिस्पोज़ की गारंटी देता है और संसाधनों को तुरंत मुक्त करता है।  
2. **पुन: उपयोग करते समय स्ट्रीम पोज़िशन रीसेट करें** – यदि आपको वही स्ट्रीम दो बार पढ़नी है, तो `stream.Seek(0, SeekOrigin.Begin)` कॉल करें।  
3. **सही स्ट्रीम प्रकार चुनें** – डिस्क फ़ाइलों के लिए `FileStream`, इन‑मेमोरी डेटा के लिए `MemoryStream`, रिमोट स्रोतों के लिए `NetworkStream`।

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### कब इस दृष्टिकोण को पूर्ण दस्तावेज़ लोडिंग के बजाय प्राथमिकता दें
**जब आप स्ट्रीम‑आधारित मेटाडेटा निष्कर्षण को प्राथमिकता देना चाहते हैं**:
- आप केवल उच्च‑स्तरीय विवरण (प्रकार, पृष्ठ, आकार) चाहिए।  
- आप अपलोड वैधता कर रहे हैं या दस्तावेज़ कैटलॉग बना रहे हैं।  
- प्रदर्शन और कम मेमोरी फुटप्रिंट महत्वपूर्ण हैं।  

**पूर्ण दस्तावेज़ प्रोसेसिंग पर स्विच करें जब**:
- आपको सामग्री की तुलना, टेक्स्ट निकालना, या पृष्ठ रेंडर करना आवश्यक है।  
- गहरी विश्लेषण (जैसे OCR, वॉटरमार्क डिटेक्शन) की आवश्यकता है।  

## उत्पादन उपयोग के लिए उन्नत टिप्स

### मजबूत त्रुटि हैंडलिंग रणनीतियाँ
सभी ऑपरेशन्स को एक try‑catch ब्लॉक में रैप करें जो `GroupDocs.Comparison.Exceptions.ComparisonException` को कैप्चर करता है। `ComparisonException` लाइब्रेरी द्वारा तब फेंका जाता है जब दस्तावेज़ प्रोसेसिंग के दौरान कोई त्रुटि होती है। त्रुटि विवरण को लॉग करें, एक मानकीकृत त्रुटि प्रतिक्रिया लौटाएँ, और `finally` क्लॉज़ में `Comparer` को डिस्पोज़ करना सुनिश्चित करें।

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### लॉगिंग और मॉनिटरिंग के साथ एकीकरण
एक लॉगिंग फ्रेमवर्क (जैसे Serilog या NLog) इन्जेक्ट करें और प्रोसेसिंग समय, फ़ाइल आकार, और सफलता/विफलता काउंट जैसी मीट्रिक्स इमिट करें। यह डेटा आपको प्रदर्शन गिरावट को जल्दी पहचानने में मदद करता है।

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या GroupDocs.Comparison for .NET विभिन्न दस्तावेज़ फ़ॉर्मेट्स के साथ संगत है?**  
A: हाँ। लाइब्रेरी **50 से अधिक फ़ाइल फ़ॉर्मेट्स** का समर्थन करती है, जिसमें DOCX, PDF, XLSX, PPTX, और कई इमेज टाइप्स शामिल हैं, जिससे यह लगभग सभी दस्तावेज़ वर्कफ़्लो के लिए उपयुक्त है।

**Q: क्या मैं GroupDocs.Comparison for .NET को खरीदने से पहले आज़मा सकता हूँ?**  
A: बिल्कुल। एक मुफ्त ट्रायल [वेबसाइट](https://releases.groupdocs.com/) पर उपलब्ध है, जिससे आप बिना लाइसेंस के सभी फीचर्स का मूल्यांकन कर सकते हैं।

**Q: GroupDocs.Comparison for .NET के लिए समर्थन कहाँ मिल सकता है?**  
A: आप [GroupDocs.Comparison फ़ोरम](https://forum.groupdocs.com/c/comparison/12) में मदद प्राप्त कर सकते हैं, जहाँ समुदाय और प्रोडक्ट टीम प्रश्नों का शीघ्र उत्तर देती है।

**Q: क्या परीक्षण के लिए अस्थायी लाइसेंस उपलब्ध हैं?**  
A: हाँ। अस्थायी लाइसेंस [लाइसेंसिंग पेज](https://purchase.groupdocs.com/temporary-license/) से प्राप्त किए जा सकते हैं, जो विकास और QA वातावरण के लिए उपयुक्त हैं।

**Q: क्या GroupDocs.Comparison for .NET एंटरप्राइज़ डिप्लॉयमेंट्स के लिए उपयुक्त है?**  
A: निश्चित रूप से। यह एंटरप्राइज़‑ग्रेड प्रदर्शन, व्यापक फ़ॉर्मेट समर्थन, और मजबूत त्रुटि हैंडलिंग प्रदान करता है, जो बड़े‑पैमाने पर उत्पादन सिस्टम के लिए आवश्यक हैं।

---

**अंतिम अपडेट:** 2026-07-01  
**परीक्षण किया गया:** GroupDocs.Comparison 23.10 for .NET  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल्स

- [डॉक्यूमेंट प्रॉपर्टीज़ प्राप्त करें C# .NET - फ़ाइल मेटाडेटा निकालें](/comparison/net/basic-usage/get-document-info-from-path/)
- [डॉक्यूमेंट मेटाडेटा मैनेजमेंट .NET - GroupDocs.Comparison के लिए पूर्ण गाइड](/comparison/net/metadata-management/)
- [डॉक्यूमेंट तुलना .NET ट्यूटोरियल - GroupDocs के साथ मेटाडेटा संरक्षित करें](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)