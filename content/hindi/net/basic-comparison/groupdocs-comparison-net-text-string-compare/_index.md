---
categories:
- String Manipulation
date: '2026-06-10'
description: GroupDocs.Comparison का उपयोग करके C# में स्ट्रिंग्स की तुलना करना सीखें,
  फ़ाइल ऑपरेशनों के बिना तेज़ स्ट्रिंग तुलना प्रदर्शन प्रदान करता है – .NET डेवलपर्स
  के लिए उपयुक्त।
keywords:
- how to compare strings
- string comparison performance
- compare strings c#
- groupdocs comparison .net
- direct string comparison
lastmod: '2026-06-10'
linktitle: C# स्ट्रिंग तुलना ट्यूटोरियल
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
title: फ़ाइलों के बिना C# में स्ट्रिंग्स की तुलना कैसे करें - GroupDocs ट्यूटोरियल
type: docs
url: /hi/net/basic-comparison/groupdocs-comparison-net-text-string-compare/
weight: 1
---

# फ़ाइलों के बिना C# में स्ट्रिंग्स की तुलना कैसे करें - GroupDocs ट्यूटोरियल

क्या आपने कभी अपने .NET ऐप में दो टेक्स्ट स्ट्रिंग्स की तुलना करने की ज़रूरत महसूस की है, लेकिन पारंपरिक तुलना विधियों की जटिलता से डरते रहे हैं? आप अकेले नहीं हैं। चाहे आप एक वर्ज़न कंट्रोल सिस्टम बना रहे हों, यूज़र इनपुट वैलिडेट कर रहे हों, या बस दो टेक्स्ट ब्लॉक्स के बीच अंतर देखना चाहते हों, स्ट्रिंग तुलना जल्दी ही सिरदर्द बन सकती है। **इस गाइड में आप स्ट्रिंग्स की प्रभावी तुलना करना सीखेंगे**, GroupDocs.Comparison का उपयोग करके ताकि आपको फ़ाइल सिस्टम को छूना न पड़े।

## त्वरित उत्तर
- **सीधे स्ट्रिंग तुलना को संभालने वाली लाइब्रेरी कौन सी है?** GroupDocs.Comparison for .NET.  
- **क्या मुझे पहले फ़ाइलें लिखनी पड़ेंगी?** नहीं – API सीधे स्ट्रिंग वेरिएबल्स के साथ काम करता है।  
- **कौन से .NET संस्करण समर्थित हैं?** .NET Framework 4.6.1+, .NET Core 2.0+, .NET 5/6/7.  
- **क्या प्रोडक्शन के लिए लाइसेंस आवश्यक है?** हाँ, प्रोडक्शन उपयोग के लिए पूर्ण या अस्थायी लाइसेंस की आवश्यकता होती है।  
- **तुलना कितनी तेज़ है?** यह इन‑मेमोरी चलती है और छोटे‑से‑मध्यम टेक्स्ट के लिए फ़ाइल‑आधारित तरीकों से आमतौर पर 3‑5× तेज़ होती है।

## सीधे स्ट्रिंग तुलना क्यों चुनें?

सीधे स्ट्रिंग तुलना डिस्क I/O के ओवरहेड को समाप्त करती है, जिससे सामान्य 500 KB से कम टेक्स्ट स्निपेट्स के लिए **5× तक तेज़ निष्पादन** मिलता है। यह अस्थायी फ़ाइलों के निर्माण से मेमोरी दबाव भी कम करती है, और चैट या लाइव डॉक्यूमेंट एडिटिंग जैसे इंटरैक्टिव एप्लिकेशन्स में रियल‑टाइम फीडबैक सक्षम करती है।

## शुरू करने के लिए आपको क्या चाहिए

- **डेवलपमेंट एनवायरनमेंट** – Visual Studio 2022 (या कोई भी .NET‑कम्पैटिबल IDE) जिसमें .NET Framework 4.6.1+ या .NET Core 2.0+ इंस्टॉल हो।  
- **बेसिक C# स्किल्स** – कंसोल या वेब प्रोजेक्ट बनाने, `using` स्टेटमेंट्स जोड़ने, और ऑब्जेक्ट्स को इंस्टैंशिएट करने की क्षमता।  
- **GroupDocs.Comparison NuGet पैकेज** – हम इसे अगले सेक्शन में इंस्टॉल करेंगे।

## अपने प्रोजेक्ट में GroupDocs.Comparison सेट अप करना

आपके पास लाइब्रेरी को सॉल्यूशन में लाने के दो सरल तरीके हैं।

### विकल्प 1: NuGet पैकेज मैनेजर कंसोल

Visual Studio में पैकेज मैनेजर कंसोल खोलें और चलाएँ:

```shell
Install-Package GroupDocs.Comparison -Version 25.4.0
```

### विकल्प 2: .NET CLI

यदि आप कमांड लाइन पसंद करते हैं (या VS Code उपयोग कर रहे हैं), तो निष्पादित करें:

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**Pro Tip**: अनपेक्षित ब्रेकिंग चेंजेज़ से बचने के लिए संस्करण को `25.4.0` (या नया) पर पिन करें।

### अपना लाइसेंस व्यवस्थित करना

GroupDocs आपकी जरूरतों के अनुसार कई लाइसेंस विकल्प प्रदान करता है:

- **Free Trial** – परीक्षण और छोटे प्रोजेक्ट्स के लिए परफेक्ट।  
- **Temporary License** – बड़े इवैल्यूएशन डिप्लॉयमेंट्स के लिए आदर्श।  
- **Full License** – प्रोडक्शन वर्कलोड्स के लिए आवश्यक।

उनके [खरीद पृष्ठ](https://purchase.groupdocs.com/buy) पर जाकर इन विकल्पों का पता लगाएँ। सीखने के उद्देश्य से, फ़्री ट्रायल बहुत अच्छा काम करता है।

## C# में सीधे स्ट्रिंग्स की तुलना कैसे करें

GroupDocs.Comparison एक इन‑मेमोरी API प्रदान करता है जो आपको दो टेक्स्ट स्ट्रिंग्स फीड करने और फ़ाइल सिस्टम को छुए बिना तुरंत विस्तृत डिफ़ प्राप्त करने देता है। `Comparer` इंस्टेंस बनाकर, टार्गेट स्ट्रिंग जोड़कर, और `Compare` को कॉल करके, आप एक `ComparisonResult` प्राप्त करते हैं जिसे HTML, प्लेन टेक्स्ट, या PDF के रूप में रेंडर किया जा सकता है, जिससे यह रियल‑टाइम एप्लिकेशन्स के लिए आदर्श बनता है।

### चरण 1: अपने Comparer ऑब्जेक्ट को सेट अप करें

`Comparer` क्लास वह कोर इंजन है जो दो टेक्स्ट भागों के बीच अंतर का मूल्यांकन करता है।

`LoadOptions` यह निर्धारित करता है कि इनपुट कैसे इंटरप्रेट किया जाए, जिससे आप रॉ टेक्स्ट सीधे लोड कर सकते हैं।

```csharp
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

अपने सोर्स स्ट्रिंग के साथ comparer बनाएं और लाइब्रेरी को बताएं कि आप रॉ टेक्स्ट लोड कर रहे हैं:

```csharp
using (Comparer comparer = new Comparer("source text", new LoadOptions() { LoadText = true }))
{
    // Your comparison logic goes here
}
```

**`using` ब्लॉक क्यों?** `Comparer` `IDisposable` को इम्प्लीमेंट करता है; इसे रैप करने से सभी अनमैनेज्ड रिसोर्सेज़ तुरंत रिलीज़ हो जाते हैं, जो लूप में कई तुलना चलाते समय बहुत ज़रूरी है।

### चरण 2: अपना लक्ष्य टेक्स्ट जोड़ें

`Add` स्रोत के साथ तुलना करने के लिए नया डॉक्यूमेंट या स्ट्रिंग रजिस्टर करता है।

अब वह टेक्स्ट फीड करें जिससे आप तुलना करना चाहते हैं। आवश्यकता पड़ने पर आप कई टार्गेट जोड़ सकते हैं।

`Add` मेथड मूल स्रोत के साथ तुलना करने के लिए नया डॉक्यूमेंट (या स्ट्रिंग) रजिस्टर करता है।  
```csharp
comparer.Add(targetString, new LoadOptions() { LoadText = true });
```

आप कई संस्करणों के खिलाफ स्रोत की तुलना करने के लिए `Add` को बार‑बार कॉल कर सकते हैं।

### चरण 3: तुलना निष्पादित करें

`Compare` डिफ़ इंजन चलाता है और परिवर्तन डेटा वाला `ComparisonResult` रिटर्न करता है।

डिफ़ एल्गोरिद्म को ट्रिगर करें।

`Compare` मेथड वास्तविक विश्लेषण करता है, एक `ComparisonResult` ऑब्जेक्ट बनाता है जिसमें सभी परिवर्तन मेटाडेटा होता है।  
```csharp
var result = comparer.Compare();
```

अंतर्निहित एल्गोरिद्म कैरेक्टर लेवल पर काम करता है, इन्सर्शन, डिलीशन, और मोडिफिकेशन का पता लगाता है, और एक पेटेंटेड सिमिलैरिटी इंजन के साथ गति और सटीकता को संतुलित करता है।

### चरण 4: अपने परिणाम प्राप्त करें

`GetResultString()` इन्सर्शन, डिलीशन, और मोडिफिकेशन को हाईलाइट करने वाला HTML स्ट्रिंग जनरेट करता है।

अंत में, एक मानव‑पठनीय डिफ़ निकालें।

`GetResultString()` मेथड एक HTML‑स्टाइल्ड स्ट्रिंग रिटर्न करता है जहाँ एडिशन हरे रंग में, डिलीशन लाल में, और मोडिफिकेशन पीले में हाईलाइट होते हैं।  
```csharp
string diffHtml = result.GetResultString();
```

आप `diffHtml` को वेब व्यू में रेंडर कर सकते हैं, ईमेल में भेज सकते हैं, या ऑडिट उद्देश्यों के लिए लॉग कर सकते हैं।

## आपको इस दृष्टिकोण का उपयोग कब करना चाहिए?

जब आपको इन‑मेमोरी डेटा का तुरंत, कम‑ओवरहेड डिफ़ चाहिए, तब सीधे स्ट्रिंग तुलना चमकती है। यह API रिस्पॉन्स वैलिडेशन, लाइव कोलैबोरेटिव एडिटिंग, कॉन्फ़िगरेशन चेंज डिटेक्शन, डेटा‑माइग्रेशन वेरिफिकेशन, और चैट‑एप्लिकेशन मेसेज डिफ़ के लिए आदर्श है। बड़े डॉक्यूमेंट्स (> 10 MB) या जब आपको जटिल लेआउट को संरक्षित रखना हो, तो फ़ाइल‑आधारित तुलना अधिक उपयुक्त हो सकती है।

## सामान्य गड़बड़ियों और उन्हें कैसे टालें

### LoadOptions पैरामीटर भूल जाना

**समस्या:** आप एक “फ़ाइल नहीं मिली” एक्सेप्शन प्राप्त करते हैं जबकि आपने स्ट्रिंग पास की है।  
**समाधान:** `Comparer` बनाते समय या `Add` कॉल करते समय हमेशा `new LoadOptions() { LoadText = true }` शामिल करें।  
```csharp
// Wrong - will look for files named "source text"
using (Comparer comparer = new Comparer("source text"))

// Right - tells GroupDocs this is raw text
using (Comparer comparer = new Comparer("source text", new LoadOptions() { LoadText = true }))
```

### बड़े पैमाने की तुलना में मेमोरी लीक

**समस्या:** बैच प्रोसेसिंग के दौरान मेमोरी उपयोग लगातार बढ़ता है।  
**समाधान:** प्रत्येक `Comparer` को `using` स्टेटमेंट में रैप करें और तुरंत डिस्पोज़ करें।  
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

### नल या खाली स्ट्रिंग हैंडलिंग

**समस्या:** नल इनपुट `ArgumentNullException` का कारण बनते हैं।  
**रोकथाम:** लाइब्रेरी को कॉल करने से पहले इनपुट्स को वैलिडेट करें।  
```csharp
if (string.IsNullOrEmpty(sourceText) || string.IsNullOrEmpty(targetText))
{
    // Handle the edge case appropriately for your application
    return "Cannot compare null or empty strings";
}
```

## प्रदर्शन टिप्स और सर्वोत्तम प्रथाएँ

### उच्च-आयतन अनुप्रयोगों के लिए मेमोरी प्रबंधन

यदि आप प्रति मिनट हजारों स्ट्रिंग्स की तुलना कर रहे हैं, तो एक ही `Comparer` इंस्टेंस को `Reset()` के साथ पुन: उपयोग करने पर विचार करें, या कई तुलना को एक कॉल में बैच करें ताकि ऑब्जेक्ट निर्माण कम हो।

### असिंक्रोनस प्रोसेसिंग

वेब APIs के लिए, तुलना को बैकग्राउंड टास्क में ऑफ‑लोड करें ताकि अनुरोध थ्रेड रिस्पॉन्सिव बना रहे।  
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

### फ़ाइलों बनाम सीधे स्ट्रिंग तुलना कब चुनें

| परिदृश्य | सिफारिश किया गया दृष्टिकोण |
|----------|----------------------|
| टेक्स्ट पहले से मेमोरी में है, < 500 KB | सीधे स्ट्रिंग तुलना (इन‑मेमोरी) |
| दस्तावेज़ > 10 MB या सटीक लेआउट संरक्षण की आवश्यकता | फ़ाइल‑आधारित तुलना |
| मूल फ़ॉर्मेटिंग (फ़ॉन्ट, इमेज) को संरक्षित रखना आवश्यक | फ़ाइल‑आधारित तुलना |
| रियल‑टाइम फीडबैक (जैसे चैट, लाइव एडिटिंग) | सीधे स्ट्रिंग तुलना |

## लोकप्रिय .NET फ्रेमवर्क्स के साथ एकीकरण

### ASP.NET Core वेब API एकीकरण

दो JSON स्ट्रिंग्स को स्वीकार करने और डिफ़ रिटर्न करने वाला REST एंडपॉइंट एक्सपोज़ करें।  
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

### यूनिट टेस्टिंग एकीकरण

अपने टेस्ट सूट के भीतर लाइब्रेरी का उपयोग करके यह सत्यापित करें कि ट्रांसफ़ॉर्मेशन अपेक्षित आउटपुट उत्पन्न करते हैं।  
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

## सामान्य समस्याओं का निवारण

### “फ़ाइल नहीं मिली” त्रुटियाँ

**कारण** – `LoadOptions` गायब है या `LoadText = false` है।  
**समाधान** – कंस्ट्रक्टर और `Add` कॉल दोनों में `new LoadOptions() { LoadText = true }` शामिल है या नहीं, यह जांचें।

### बड़ी स्ट्रिंग्स के साथ खराब प्रदर्शन

**कारण** – बहुत बड़े इनपुट (> 1 MB) या UI थ्रेड पर चलाना।  
**समाधान** – बड़े पेलोड्स के लिए फ़ाइल‑आधारित तुलना पर स्विच करें, मेमोरी प्रोफ़ाइल करें, और काम को बैकग्राउंड थ्रेड में ले जाएँ।

### अनपेक्षित परिणाम या फ़ॉर्मेटिंग समस्याएँ

**कारण** – एन्कोडिंग मिसमैच, छिपे हुए कैरेक्टर्स (टैब, CR/LF)।  
**समाधान** – तुलना से पहले स्ट्रिंग्स को नॉर्मलाइज़ करें (`string.Normalize(NormalizationForm.FormC)`) और अदृश्य व्हाइटस्पेस को ट्रिम करें।

## समापन

अब आपके पास C# में GroupDocs.Comparison के साथ सीधे स्ट्रिंग्स की तुलना के लिए एक पूर्ण, प्रोडक्शन‑रेडी रेसिपी है। याद रखें:

- हमेशा `LoadOptions.LoadText = true` सेट करें।  
- `Comparer` ऑब्जेक्ट्स को तुरंत डिस्पोज़ करें।  
- जब डेटा पहले से वेरिएबल्स में हो तो गति के लिए इन‑मेमोरी दृष्टिकोण चुनें।  
- बहुत बड़े या लेआउट‑संवेदनशील डॉक्यूमेंट्स के लिए फ़ाइल‑आधारित तुलना पर वापस जाएँ।  
- नल और खाली स्ट्रिंग्स से बचाव के लिए इनपुट्स को वैलिडेट करें।

केवल कुछ लाइनों के कोड से आप किसी भी .NET एप्लिकेशन—बैकएंड सर्विसेज से लेकर इंटरैक्टिव वेब ऐप्स तक—में शक्तिशाली डिफ़ फ़ंक्शनैलिटी प्रदान कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं बहुत अलग लंबाई की स्ट्रिंग्स की तुलना प्रभावी ढंग से कर सकता हूँ?**  
A: हाँ, एल्गोरिद्म रैखिक रूप से स्केल करता है और कई मेगाबाइट तक की स्ट्रिंग्स के लिए तेज़ रहता है; > 10 MB के लिए, इष्टतम प्रदर्शन के लिए फ़ाइल‑आधारित तुलना पर विचार करें।

**Q: यदि मैं नल या खाली स्ट्रिंग्स की तुलना करने की कोशिश करूँ तो क्या होता है?**  
A: लाइब्रेरी एक खाली डिफ़ रिटर्न करती है, लेकिन स्पष्ट यूज़र मैसेज देने के लिए `string.IsNullOrEmpty` की पहले जाँच करना बेस्ट प्रैक्टिस है।

**Q: क्या यह थ्रेड‑सेफ़ है जब कई तुलना एक साथ की जाएँ?**  
A: प्रत्येक `Comparer` इंस्टेंस सिंगल‑थ्रेडेड है; प्रत्येक थ्रेड के लिए अलग इंस्टेंस बनाएँ या हाई कॉन्करेंसी के लिए थ्रेड‑लोकल पूल उपयोग करें।

**Q: यह `string.Equals()` की तुलना में कैसे प्रदर्शन करता है?**  
A: `string.Equals()` केवल यह बताता है कि टेक्स्ट समान हैं या नहीं। GroupDocs.Comparison डिफ़ डिटेक्शन जोड़ता है, जिसमें मामूली ओवरहेड होता है—आमतौर पर 100 KB स्ट्रिंग्स के लिए 3‑5 ms, जबकि साधारण इक्वैलिटी चेक < 1 ms लेता है।

**Q: क्या मैं डिफ़ आउटपुट फ़ॉर्मेट को कस्टमाइज़ कर सकता हूँ?**  
A: हाँ, `ComparisonOptions` आपको HTML मार्कअप, CSS क्लासेज़ बदलने और यहाँ तक कि प्लेन टेक्स्ट या PDF में एक्सपोर्ट करने की अनुमति देता है।

**Q: क्या स्ट्रिंग्स की तुलना के लिए कोई आकार सीमा है?**  
A: कोई हार्ड लिमिट नहीं है, लेकिन ~5 MB से आगे प्रदर्शन घटता है; बहुत बड़े डॉक्यूमेंट्स के लिए फ़ाइल‑आधारित तुलना पर स्विच करना अनुशंसित है।

## अतिरिक्त संसाधन

- [GroupDocs.Comparison .NET दस्तावेज़](https://docs.groupdocs.com/comparison/net/)  
- [पूरा API रेफ़रेंस](https://reference.groupdocs.com/comparison/net/)  
- [रिलीज़ पेज](https://releases.groupdocs.com/comparison/net/)  
- [खरीद विकल्प](https://purchase.groupdocs.com/buy)  
- [फ़्री ट्रायल डाउनलोड](https://releases.groupdocs.com/comparison/net/)  
- [सपोर्ट फ़ोरम](https://forum.groupdocs.com/c/comparison/)

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

## संबंधित ट्यूटोरियल

- [GroupDocs Comparison .NET ट्यूटोरियल - पूर्ण बेसिक उपयोग गाइड](/comparison/net/basic-usage/)  
- [GroupDocs Comparison .NET मीटर्ड लाइसेंस सेटअप - पूर्ण ट्यूटोरियल](/comparison/net/quick-start/set-metered-license/)  
- [डॉक्यूमेंट तुलना .NET - पूर्ण C# ट्यूटोरियल](/comparison/net/document-comparison/compare-documents-from-path/)