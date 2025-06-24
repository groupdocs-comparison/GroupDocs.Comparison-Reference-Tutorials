---
"description": "GroupDocs.Comparison for .NET के साथ अपने .NET अनुप्रयोगों में दस्तावेज़ तुलना कार्यक्षमता को सहजता से एकीकृत करें।"
"linktitle": "पूर्वावलोकन के लिए विशिष्ट छवि आकार सेट करें"
"second_title": "GroupDocs.तुलना .NET एपीआई"
"title": "पूर्वावलोकन के लिए विशिष्ट छवि आकार सेट करें"
"url": "/hi/net/document-comparison/set-specific-image-sizes-for-previews/"
"weight": 14
---

# पूर्वावलोकन के लिए विशिष्ट छवि आकार सेट करें

## परिचय
सॉफ़्टवेयर विकास के क्षेत्र में, सूचना की अखंडता और स्थिरता सुनिश्चित करने के लिए कुशल और सटीक दस्तावेज़ तुलना महत्वपूर्ण है। GroupDocs.Comparison for .NET उन डेवलपर्स के लिए एक मजबूत समाधान प्रदान करता है जो अपने .NET अनुप्रयोगों में दस्तावेज़ तुलना कार्यक्षमता को सहजता से शामिल करना चाहते हैं।
## आवश्यक शर्तें
GroupDocs.Comparison for .NET का उपयोग करके दस्तावेज़ तुलना के कार्यान्वयन में गोता लगाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:
### 1. .NET के लिए GroupDocs.तुलना स्थापित करें
आरंभ करने के लिए, आपको अपने विकास परिवेश में GroupDocs.Comparison for .NET स्थापित करना होगा। आप आवश्यक फ़ाइलें यहाँ से डाउनलोड कर सकते हैं। [लिंक को डाउनलोड करें](https://releases.groupdocs.com/comparison/net/).
### 2. अपना विकास वातावरण स्थापित करें
सुनिश्चित करें कि आपके पास Visual Studio या किसी पसंदीदा .NET विकास IDE सहित उपयुक्त विकास वातावरण कॉन्फ़िगर किया गया है।
### 3. .NET फ्रेमवर्क से परिचित होना
.NET ढांचे और सी # प्रोग्रामिंग भाषा की एक बुनियादी समझ प्रभावी रूप से GroupDocs.तुलना के लिए .NET का उपयोग करने के लिए आवश्यक है।

## नामस्थान आयात करें
दस्तावेज़ तुलना कार्यक्षमता को कार्यान्वित करने से पहले, आपको आवश्यक वर्गों और विधियों तक पहुँचने के लिए आवश्यक नामस्थानों को आयात करना होगा।
```csharp
using System;
using System.IO;
```
## चरण 1: आउटपुट निर्देशिका और फ़ाइल नाम सेट करें
सबसे पहले, आउटपुट निर्देशिका और फ़ाइल नाम निर्धारित करें जहां तुलना किए गए दस्तावेज़ को सहेजा जाएगा।
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## चरण 2: तुलनित्र को आरंभ करें
एक उदाहरण बनाना `Comparer` स्रोत दस्तावेज़ पथ को पैरामीटर के रूप में पास करके ऑब्जेक्ट का चयन करें।
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
```
## चरण 3: लक्ष्य दस्तावेज़ जोड़ें
वह लक्ष्य दस्तावेज़(दस्तावेज़) जोड़ें जिसकी आप स्रोत दस्तावेज़ से तुलना करना चाहते हैं।
```csharp
comparer.Add("TARGET.pptx");
```
## चरण 4: तुलना करें
आह्वान करें `Compare` दस्तावेज़ तुलना करने और परिणाम को सहेजने की विधि।
```csharp
comparer.Compare(File.Create(outputFileName));
```
## चरण 5: दस्तावेज़ पूर्वावलोकन उत्पन्न करें
दृश्य निरीक्षण के लिए तुलना किए गए दस्तावेज़ का पूर्वावलोकन तैयार करें।
```csharp
Document document = new Document(File.OpenRead(outputFileName));
PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
{
    var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
    return File.Create(pagePath);
});
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new int[] { 1, 2 };
previewOptions.Height = 1000;
previewOptions.Width = 1000;
document.GeneratePreview(previewOptions);
```
## चरण 6: आउटपुट प्रदर्शित करें
उत्पन्न दस्तावेज़ पूर्वावलोकन के पथ के साथ एक सफलता संदेश प्रदर्शित करें।
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## निष्कर्ष
अपने .NET अनुप्रयोगों में दस्तावेज़ तुलना कार्यक्षमता को शामिल करना GroupDocs.Comparison for .NET के साथ सरल है। उल्लिखित चरणों का पालन करके, डेवलपर्स दस्तावेज़ प्रबंधन प्रक्रियाओं में सटीकता और स्थिरता सुनिश्चित करने के लिए इस शक्तिशाली उपकरण को सहजता से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Comparison for .NET सभी दस्तावेज़ प्रारूपों के साथ संगत है?
GroupDocs.तुलना के लिए .NET DOCX, पीडीएफ, पीपीटीएक्स, एक्सएलएसएक्स, और अधिक सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं अपनी आवश्यकताओं के आधार पर तुलना विकल्पों को अनुकूलित कर सकता हूँ?
हां, GroupDocs.Comparison for .NET विशिष्ट आवश्यकताओं के अनुसार तुलना प्रक्रिया को अनुकूलित करने के लिए व्यापक विकल्प प्रदान करता है।
### क्या GroupDocs.Comparison for .NET दस्तावेज़ संस्करण के लिए समर्थन प्रदान करता है?
जबकि GroupDocs.Comparison for .NET मुख्य रूप से दस्तावेज़ तुलना पर केंद्रित है, इसे व्यापक दस्तावेज़ प्रबंधन समाधानों के लिए संस्करण नियंत्रण प्रणालियों के साथ एकीकृत किया जा सकता है।
### क्या .NET के लिए GroupDocs.Comparison के लिए एक निःशुल्क परीक्षण उपलब्ध है?
हां, आप .NET के लिए GroupDocs.Comparison के नि:शुल्क परीक्षण का लाभ उठा सकते हैं [वेबसाइट](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Comparison के लिए अतिरिक्त समर्थन और सहायता कहां पा सकता हूं?
आप समर्पित का पता लगा सकते हैं [सहयता मंच](https://forum.groupdocs.com/c/comparison/12) .NET के लिए ग्रुपडॉक्स.तुलना के लिए मदद प्राप्त करने, अनुभव साझा करने और समुदाय के साथ जुड़ने के लिए।