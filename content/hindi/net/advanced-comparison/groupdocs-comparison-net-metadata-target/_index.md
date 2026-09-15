---
categories:
- Document Comparison
date: '2026-09-15'
description: GroupDocs.Comparison for .NET का उपयोग करके दस्तावेज़ तुलना के दौरान
  मेटाडेटा को कैसे संरक्षित किया जाए, जानें। C# उदाहरणों, सर्वोत्तम प्रथाओं और वास्तविक
  उपयोग मामलों के साथ चरण-दर-चरण मार्गदर्शिका।
keywords:
- how to preserve metadata
- GroupDocs.Comparison metadata preservation
- .NET document comparison
- metadata handling in .NET
lastmod: '2026-09-15'
linktitle: मेटाडेटा संरक्षण ट्यूटोरियल
og_description: GroupDocs.Comparison का उपयोग करके .NET में दस्तावेज़ तुलना के दौरान
  मेटाडेटा को कैसे संरक्षित किया जाए, जानें। सर्वोत्तम प्रथाओं, समस्या निवारण सुझावों
  और वास्तविक उदाहरणों के साथ विस्तृत ट्यूटोरियल का पालन करें।
og_image_alt: Developer guide showing metadata preservation with GroupDocs.Comparison
  in a .NET application
og_title: GroupDocs.Comparison के साथ .NET में मेटाडेटा कैसे संरक्षित करें
schemas:
- author: GroupDocs
  dateModified: '2026-09-15'
  description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  headline: How to preserve metadata with GroupDocs.Comparison in .NET
  type: TechArticle
- description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  name: How to preserve metadata with GroupDocs.Comparison in .NET
  steps:
  - name: Initialize your comparer object
    text: '`Comparer` is the core class that orchestrates the comparison process.
      It loads the source file, tracks changes, and generates the output. **Why use
      `using` statements?** They automatically dispose of resources, preventing memory
      leaks when processing large documents. Trust me, you’ll thank yourself'
  - name: Add the target document
    text: '`Comparer.Add` registers the file that contains the modifications you want
      to compare against. **Common mistake**: Confusing source and target. Think of
      it this way—source is your “original,” target is your “updated version.”'
  - name: Set the metadata type (the magic happens here)
    text: '`CloneMetadataType` is a property of `ComparisonOptions` that determines
      which document’s metadata is cloned into the result. **What’s happening?** `CloneMetadataType
      = MetadataType.Target` tells GroupDocs.Comparison: “Hey, I want to keep the
      target document’s metadata in my final result.”'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'LoadOptions specifies settings such as passwords for opening protected
      documents. Use a `LoadOptions` object with the password, then pass it to the
      `Comparer` constructor: ```csharp var loadOptions = new LoadOptions() { Password
      = "your_password" }; using (var comparer = new Comparer(sourceFile, loadOptions))
      { // comparison logic here } ```'
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
- metadata preservation
- GroupDocs.Comparison
- .NET tutorial
- document management
- C# comparison
title: GroupDocs.Comparison के साथ .NET में मेटाडेटा कैसे संरक्षित करें
type: docs
url: /hi/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# GroupDocs.Comparison के साथ .NET में मेटाडेटा को संरक्षित कैसे करें

इस ट्यूटोरियल में आप **मेटाडेटा को संरक्षित करने** का तरीका सीखेंगे जब आप GroupDocs.Comparison for .NET के साथ दो दस्तावेज़ों की तुलना करते हैं। मेटाडेटा को संरक्षित करना कानूनी अनुपालन, ऑडिट ट्रेल और सहयोगी वर्कफ़्लो के लिए आवश्यक है, और लाइब्रेरी आपको यह नियंत्रित करने की सूक्ष्म क्षमता देती है कि तुलना परिणाम में किस दस्तावेज़ का मेटाडेटा बना रहता है।

## परिचय

क्या आपने कभी दो दस्तावेज़ों की तुलना की है और प्रक्रिया में महत्वपूर्ण मेटाडेटा खो दिया? आप अकेले नहीं हैं। जब आपको .NET एप्लिकेशन में दस्तावेज़ों की तुलना करते समय **लक्ष्य मेटाडेटा को संरक्षित** करने की आवश्यकता होती है, तो यह काम जटिल लग सकता है—लेकिन ऐसा नहीं होना चाहिए।

GroupDocs.Comparison for .NET आपको यह तय करने देता है कि तुलना परिणाम में किस दस्तावेज़ का मेटाडेटा बना रहेगा। चाहे आप दस्तावेज़‑प्रबंधन प्रणाली बना रहे हों, कानूनी अनुबंध संभाल रहे हों, या सहयोगी सामग्री प्रबंधित कर रहे हों, आपको हर बार सही स्रोत दस्तावेज़ से मेटाडेटा चाहिए होगा।

## त्वरित उत्तर
- **“लक्ष्य मेटाडेटा को संरक्षित” का क्या मतलब है?** यह तुलना परिणाम उत्पन्न करते समय उस दस्तावेज़ (लक्ष्य) से मेटाडेटा (लेखक, निर्माण तिथि, कस्टम प्रॉपर्टीज़ आदि) को रखता है जिसे आप लक्ष्य के रूप में निर्दिष्ट करते हैं।  
- **कौन सा GroupDocs.Comparison संस्करण आवश्यक है?** संस्करण 25.4.0 या बाद का।  
- **क्या मैं इसे .NET Core के साथ उपयोग कर सकता हूँ?** हाँ – .NET Core 2.0+ या .NET Framework 4.6.1+।  
- **उत्पादन के लिए लाइसेंस आवश्यक है?** उत्पादन के लिए एक व्यावसायिक लाइसेंस आवश्यक है; सीखने के लिए एक मुफ्त ट्रायल काम करता है।  
- **क्या यह फीचर PDF और DOCX के साथ काम करेगा?** हाँ – सभी प्रमुख Office और PDF फ़ॉर्मेट मेटाडेटा संरक्षण का समर्थन करते हैं।

## मेटाडेटा संरक्षण क्यों महत्वपूर्ण है

कोड में कूदने से पहले, चलिए समझते हैं कि लक्ष्य मेटाडेटा को संरक्षित करना क्यों ज़रूरी है। दस्तावेज़ मेटाडेटा सिर्फ “अच्छा है” नहीं है—यह अक्सर कानूनी रूप से आवश्यक या व्यवसाय‑क्रिटिकल होता है:

- **कानूनी दस्तावेज़** – वकील‑ग्राहक विशेषाधिकार चिह्नों को बनाए रखें।  
- **कॉर्पोरेट फ़ाइलें** – अनुपालन टैग और अनुमोदन श्रृंखलाओं को रखें।  
- **शैक्षणिक पेपर** – लेखक का उल्लेख और संशोधन इतिहास आवश्यक है।  
- **तकनीकी दस्तावेज़ीकरण** – संस्करण नियंत्रण और समीक्षा स्थिति महत्वपूर्ण है।

यदि सही ढंग से नहीं संभाला गया, तो आप अनजाने में वह जानकारी हटा सकते हैं जो महीनों में स्थापित हुई थी। यहीं पर **लक्ष्य मेटाडेटा को संरक्षित** विकल्प काम आता है।

## पूर्वापेक्षाएँ

### आवश्यक लाइब्रेरी और संस्करण
- **GroupDocs.Comparison for .NET**: संस्करण 25.4.0 या बाद का (पहले संस्करणों में मेटाडेटा विकल्प सीमित हैं)।  
- **.NET Framework**: 4.6.1 या उससे ऊपर, या .NET Core 2.0+।

### पर्यावरण सेटअप
- Visual Studio (या कोई भी C# IDE जो आप पसंद करते हैं)।  
- बेसिक C# ज्ञान (बहुत उन्नत नहीं, वादा!).  
- परीक्षण के लिए दो नमूना दस्तावेज़ (Word *.docx* बहुत अच्छा काम करता है)।

### ज्ञान पूर्वापेक्षाएँ
आपको GroupDocs विशेषज्ञ होने की ज़रूरत नहीं है, लेकिन आपको इन चीज़ों में सहज होना चाहिए:
- C# `using` स्टेटमेंट्स और फ़ाइल हैंडलिंग।  
- बेसिक दस्तावेज़‑प्रोसेसिंग अवधारणाएँ।  
- मेटाडेटा वास्तव में क्या है (लेखक, शीर्षक, कस्टम प्रॉपर्टीज़ आदि)।

तैयार हैं? चलिए सेटअप करते हैं।

## GroupDocs.Comparison for .NET की सेटअप

GroupDocs.Comparison को इंस्टॉल करना सीधा है, लेकिन कुछ छोटी‑छोटी बातों का ध्यान रखना पड़ता है।

### स्थापना विकल्प

**NuGet Package Manager Console** (सबसे आसान तरीका):  
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```  

**.NET CLI** (यदि आप कमांड लाइन पसंद करते हैं):  
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```  

**प्रो टिप**: अनपेक्षित ब्रेकिंग चेंजेज़ से बचने के लिए हमेशा संस्करण निर्दिष्ट करें।

### लाइसेंस प्राप्ति

यहाँ कई डेवलपर्स शुरुआती में अटक जाते हैं। GroupDocs.Comparison मुफ्त नहीं है, लेकिन आपके पास विकल्प हैं:

- **फ्री ट्रायल** – 30 दिनों के लिए पूरी कार्यक्षमता, मूल्यांकन के लिए परफेक्ट।  
- **टेम्पररी लाइसेंस** – यदि आपको अधिक समय चाहिए तो विस्तारित मूल्यांकन अवधि।  
- **कमर्शियल लाइसेंस** – उत्पादन उपयोग के लिए (विभिन्न प्राइसिंग टियर्स उपलब्ध)।

यदि आप अभी सीख रहे हैं तो लाइसेंस की चिंता न करें—ट्रायल संस्करण में सभी **लक्ष्य मेटाडेटा को संरक्षित** फीचर शामिल हैं।

### बेसिक सेटअप सत्यापन

आइए एक सरल टेस्ट से सुनिश्चित करें कि सब कुछ काम कर रहा है:  
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

यदि यह बिना त्रुटियों के कंपाइल हो जाता है, तो आप तैयार हैं। यदि नहीं, तो अपने पैकेज इंस्टॉलेशन और `using` स्टेटमेंट्स को दोबारा जांचें।

## लक्ष्य मेटाडेटा को कैसे संरक्षित करें

अपने स्रोत और लक्ष्य फ़ाइलें लोड करें, फिर API को बताएं कि अंतिम आउटपुट में लक्ष्य का मेटाडेटा रखें।

**सीधा उत्तर (40‑70 शब्द):**  
लक्ष्य मेटाडेटा को संरक्षित करने के लिए, `Comparer` को स्रोत दस्तावेज़ के साथ इंस्टैंशिएट करें, `Add` के माध्यम से लक्ष्य दस्तावेज़ जोड़ें, `ComparisonOptions` पर `CloneMetadataType = MetadataType.Target` सेट करें, और अंत में `Compare` कॉल करें। यह GroupDocs.Comparison को लक्ष्य फ़ाइल से लेखक, निर्माण तिथि, कस्टम प्रॉपर्टीज़ और सभी अन्य मेटाडेटा को उत्पन्न परिणाम में कॉपी करने को कहता है।

### मेटाडेटा प्रवाह को समझना

एक सामान्य तुलना के दौरान:

1. **स्रोत दस्तावेज़** बेस कंटेंट प्रदान करता है।  
2. **लक्ष्य दस्तावेज़** तुलना के लिए परिवर्तन प्रदान करता है।  
3. **आउटपुट दस्तावेज़** दोनों को मिलाता है, लेकिन किसका मेटाडेटा जीतता है?

डिफ़ॉल्ट रूप से, GroupDocs.Comparison स्रोत दस्तावेज़ का मेटाडेटा उपयोग करता है। **लक्ष्य मेटाडेटा को संरक्षित** करने के लिए आपको API को स्पष्ट रूप से बताना होगा।

### स्टेप‑बाय‑स्टेप इम्प्लीमेंटेशन

#### स्टेप 1: अपने comparer ऑब्जेक्ट को इनिशियलाइज़ करें

`Comparer` वह कोर क्लास है जो तुलना प्रक्रिया को ऑर्केस्ट्रेट करता है। यह स्रोत फ़ाइल लोड करता है, बदलाव ट्रैक करता है, और आउटपुट जनरेट करता है।  

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```  

**`using` स्टेटमेंट्स क्यों उपयोग करें?** वे स्वचालित रूप से रिसोर्सेज़ को डिस्पोज़ कर देते हैं, जिससे बड़े दस्तावेज़ों को प्रोसेस करते समय मेमोरी लीक नहीं होती। बाद में 50 MB Word फ़ाइलों से निपटते समय आप खुद का धन्यवाद करेंगे।

#### स्टेप 2: लक्ष्य दस्तावेज़ जोड़ें

`Comparer.Add` वह फ़ाइल रजिस्टर करता है जिसमें वह संशोधन होते हैं जिनसे आप तुलना करना चाहते हैं।  

```csharp
comparer.Add(targetFilePath);
```  

**आम गलती**: स्रोत और लक्ष्य को उलट देना। इसे इस तरह सोचें—स्रोत आपका “ऑरिजिनल” है, लक्ष्य आपका “अपडेटेड वर्ज़न” है।

#### स्टेप 3: मेटाडेटा प्रकार सेट करें (यहाँ जादू होता है)

`CloneMetadataType` `ComparisonOptions` की एक प्रॉपर्टी है जो निर्धारित करती है कि परिणाम में किस दस्तावेज़ का मेटाडेटा क्लोन किया जाएगा।  

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```  

**क्या हो रहा है?** `CloneMetadataType = MetadataType.Target` GroupDocs.Comparison को बताता है: “हे, मैं अंतिम परिणाम में लक्ष्य दस्तावेज़ का मेटाडेटा रखना चाहता हूँ।”

## पूरा कार्यशील उदाहरण

यहाँ सब कुछ एक रन करने योग्य प्रोग्राम में एक साथ है:  
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

## से बचने के लिए सामान्य जाल

**फ़ाइल पाथ समस्याएँ** – हमेशा पूर्ण पाथ उपयोग करें या सुनिश्चित करें कि फ़ाइलें कार्यशील डायरेक्टरी में हों:  
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```  

**मेमोरी प्रबंधन** – बड़े दस्तावेज़ों के लिए हमेशा `Comparer` ऑब्जेक्ट्स को `using` स्टेटमेंट्स में रैप करें।

**वर्ज़न संगतता** – विभिन्न GroupDocs.Comparison रिलीज़ अलग‑अलग मेटाडेटा विकल्प उजागर करती हैं—सबसे अच्छे परिणामों के लिए 25.4.0 या नया उपयोग करें।

## उन्नत मेटाडेटा परिदृश्य

### लक्ष्य बनाम स्रोत मेटाडेटा कब उपयोग करें

| परिदृश्य | **लक्ष्य** मेटाडेटा को प्राथमिकता दें | **स्रोत** मेटाडेटा को प्राथमिकता दें |
|----------|----------------------------|----------------------------|
| अपडेटेड लेखक जानकारी चाहिए | ✅ | ❌ |
| मूल दस्तावेज़ का कानूनी प्राधान्य है | ❌ | ✅ |
| कस्टम प्रॉपर्टीज़ केवल नए फ़ाइल में जोड़ी गई हैं | ✅ | ❌ |
| “मास्टर” दस्तावेज़ का इतिहास रखना चाहते हैं | ❌ | ✅ |

### कई लक्ष्य दस्तावेज़ों को संभालना

आप कई लक्ष्यों के खिलाफ तुलना कर सकते हैं जबकि पहले जोड़े गए लक्ष्य से मेटाडेटा संरक्षित रहता है:  
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

## व्यावहारिक अनुपयोग और उपयोग केस

### कानूनी दस्तावेज़ प्रबंधन

कानूनी फर्मों को अक्सर अनुबंध संस्करणों की तुलना करनी पड़ती है जबकि विशिष्ट मेटाडेटा मार्कर संरक्षित रखने होते हैं:  
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

### शैक्षणिक और अनुसंधान सहयोग

जब कई शोधकर्ता सहयोग करते हैं, तो आप सबसे हालिया लेखक जानकारी को संरक्षित करना चाहते हैं:  
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

### कॉर्पोरेट अनुपालन कार्यप्रवाह

नियामक उद्योगों में, अनुपालन मेटाडेटा को बनाए रखना अत्यंत महत्वपूर्ण है:  
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

## सामान्य समस्याओं का निवारण

### “फ़ाइल नहीं मिली” त्रुटियाँ

सबसे आम समस्या। स्पष्ट चेक के साथ डिबग करें:  
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

### बड़े दस्तावेज़ों के साथ मेमोरी समस्याएँ

10 MB से बड़े दस्तावेज़ों के लिए ये ऑप्टिमाइज़ेशन देखें:  
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

### अनुमति और एक्सेस समस्याएँ

सुरक्षित फ़ाइलों या नेटवर्क शेयरों के साथ काम करते समय:  
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

## प्रदर्शन विचार और सर्वोत्तम प्रथाएँ

### मेमोरी प्रबंधन

GroupDocs.Comparison 100‑पेज PDF प्रोसेस करते समय **300 MB RAM** तक उपयोग कर सकता है। `using` स्टेटमेंट्स का उपयोग करके डिस्पोज़ सुनिश्चित करें और मेमोरी तुरंत मुक्त करें।  

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

**बैच में दस्तावेज़ प्रोसेस करें** – यदि आप कई फ़ाइलों की तुलना कर रहे हैं, तो उन्हें छोटे समूहों में संभालें ताकि मेमोरी उपयोग कम रहे।

### बेहतर प्रतिक्रिया के लिए असिंक्रोनस ऑपरेशन्स

डेस्कटॉप या वेब ऐप्स के लिए, तुलना को एक async मेथड में रैप करें:  
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

### फ़ाइल आकार दिशानिर्देश

- **छोटा (< 1 MB)** – सीधे प्रोसेस करें।  
- **मध्यम (1‑10 MB)** – UI को रिस्पॉन्सिव रखने के लिए प्रोग्रेस दिखाएँ।  
- **बड़ा (> 10 MB)** – हमेशा async प्रोसेसिंग उपयोग करें और ऊपर दिखाए अनुसार स्पष्ट GC पर विचार करें।

## बड़े सिस्टम के साथ एकीकरण

### ASP.NET Core एकीकरण

नीचे एक तैयार‑करने‑योग्य कंट्रोलर है जो दो अपलोडेड फ़ाइलें लेता है, तुलना चलाता है, और **लक्ष्य मेटाडेटा को संरक्षित** करते हुए परिणाम लौटाता है:  
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

## अक्सर पूछे जाने वाले प्रश्न

**प्रश्न: क्या मैं कई लक्ष्य दस्तावेज़ों से मेटाडेटा संरक्षित कर सकता हूँ?**  
उत्तर: जब आप कई लक्ष्य फ़ाइलें जोड़ते हैं, तो GroupDocs.Comparison **पहली** जोड़ी गई लक्ष्य फ़ाइल का मेटाडेटा उपयोग करता है। वह दस्तावेज़ पहले जोड़ें जिसका मेटाडेटा आप रखना चाहते हैं।

**प्रश्न: यदि लक्ष्य दस्तावेज़ में कुछ मेटाडेटा फ़ील्ड नहीं हैं तो क्या होगा?**  
उत्तर: केवल वही मेटाडेटा जो लक्ष्य में मौजूद है, आउटपुट में कॉपी किया जाएगा। अनुपलब्ध फ़ील्ड बस छोड़ दी जाएँगी; तुलना फिर भी सफल होगी।

**प्रश्न: पासवर्ड‑प्रोटेक्टेड दस्तावेज़ों को कैसे संभालें?**  
उत्तर: `LoadOptions` पासवर्ड जैसी सेटिंग्स निर्दिष्ट करता है।  
पासवर्ड के साथ `LoadOptions` ऑब्जेक्ट बनाएं, फिर उसे `Comparer` कन्स्ट्रक्टर में पास करें:  
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```  

**प्रश्न: क्या केवल चयनित मेटाडेटा प्रॉपर्टीज़ को ही संरक्षित किया जा सकता है?**  
उत्तर: वर्तमान API चुने हुए स्रोत (Target या Source) से **सभी** मेटाडेटा संरक्षित करता है। ग्रैन्युलर कंट्रोल के लिए आपको तुलना के बाद प्रॉपर्टीज़ निकालकर मैन्युअली पुनः लागू करनी होंगी।

**प्रश्न: कौन से दस्तावेज़ फ़ॉर्मेट मेटाडेटा संरक्षण का समर्थन करते हैं?**  
उत्तर: अधिकांश सामान्य व्यापार फ़ॉर्मेट—DOCX, PDF, PPTX, XLSX, और कई अन्य—मेटाडेटा संरक्षण का समर्थन करते हैं। पूरी सूची के लिए आधिकारिक दस्तावेज़ देखें।

**प्रश्न: यदि समस्या आए तो मदद कहाँ मिलेगी?**  
उत्तर: समुदाय सहायता के लिए [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) देखें, या यदि आपके पास व्यावसायिक लाइसेंस है तो सीधे GroupDocs सपोर्ट से संपर्क करें।

## अतिरिक्त संसाधन

- **आधिकारिक दस्तावेज़**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **API रेफ़रेंस**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **नवीनतम संस्करण डाउनलोड**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **फ्री ट्रायल**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **खरीद विकल्प**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**अंतिम अपडेट:** 2026-09-15  
**परीक्षण किया गया:** GroupDocs.Comparison 25.4.0 for .NET  
**लेखक:** GroupDocs  

---

## संबंधित ट्यूटोरियल

- [GroupDocs Comparison NET Tutorial - Complete Guide to Document Comparison with Metadata](/comparison/net/metadata-management/guide-groupdocs-comparison-net-metadata-setting/)
- [How to Extract Metadata from .NET Comparison Results – Complete Guide](/comparison/net/basic-usage/get-document-info-from-result-document/)
- [Document Comparison .NET - How to Save Metadata Target](/comparison/net/loading-and-saving-documents/saving-documents-metadata-target/)