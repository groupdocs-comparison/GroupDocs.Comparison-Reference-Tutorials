---
title: .NET के लिए GroupDocs Compare में उपयोगकर्ता परिभाषित दस्तावेज़ मेटाडेटा सहेजना
linktitle: .NET के लिए GroupDocs Compare में उपयोगकर्ता परिभाषित दस्तावेज़ मेटाडेटा सहेजना
second_title: GroupDocs.Comparison .NET API
description: .NET के लिए GroupDocs Compare का उपयोग करके उपयोगकर्ता-परिभाषित दस्तावेज़ मेटाडेटा को सहेजना सीखें। चरण-दर-चरण निर्देशों के साथ मेटाडेटा की आसानी से तुलना और हेरफेर करें।
weight: 16
url: /hi/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# .NET के लिए GroupDocs Compare में उपयोगकर्ता परिभाषित दस्तावेज़ मेटाडेटा सहेजना

## परिचय
इस ट्यूटोरियल में, हम यह पता लगाएंगे कि .NET के लिए GroupDocs Compare का उपयोग करके उपयोगकर्ता-परिभाषित दस्तावेज़ मेटाडेटा को कैसे सहेजा जाए। दस्तावेज़ों को कुशलतापूर्वक व्यवस्थित और प्रबंधित करने के लिए मेटाडेटा महत्वपूर्ण है। GroupDocs Compare के साथ, आप अपनी विशिष्ट आवश्यकताओं को पूरा करने के लिए मेटाडेटा की आसानी से तुलना और हेरफेर कर सकते हैं।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यकताएँ हैं:
1.  .NET के लिए GroupDocs Compare: .NET के लिए GroupDocs Compare को डाउनलोड और इंस्टॉल करें[यहाँ](https://releases.groupdocs.com/comparison/net/).
2. विकास परिवेश: सुनिश्चित करें कि आपके सिस्टम पर विज़ुअल स्टूडियो जैसा उपयुक्त विकास परिवेश स्थापित है।
3. स्रोत और लक्ष्य दस्तावेज़: वह स्रोत और लक्ष्य दस्तावेज़ तैयार करें जिनके लिए आप मेटाडेटा की तुलना और हेरफेर करना चाहते हैं।

## नामस्थान आयात करें
सबसे पहले, .NET के लिए GroupDocs Compare द्वारा प्रदान की गई कार्यक्षमताओं तक पहुँचने के लिए आवश्यक नामस्थान आयात करें।
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## चरण 1: आउटपुट निर्देशिका और फ़ाइल नाम को परिभाषित करें
उस निर्देशिका को परिभाषित करें जहां आप तुलना किए गए दस्तावेज़ को सहेजना चाहते हैं और आउटपुट फ़ाइल नाम निर्दिष्ट करें।
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## चरण 2: तुलनाकर्ता प्रारंभ करें और दस्तावेज़ जोड़ें
 को आरंभ करें`Comparer` स्रोत दस्तावेज़ के साथ ऑब्जेक्ट करें और तुलना के लिए लक्ष्य दस्तावेज़ जोड़ें।
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## चरण 3: मेटाडेटा विकल्प निर्दिष्ट करें
 तुलना किए गए दस्तावेज़ में सहेजने के लिए मेटाडेटा विकल्प निर्दिष्ट करें। इस उदाहरण में, हम सेट करते हैं`CloneMetadataType` को`MetadataType.FileAuthor` और इसके लिए विवरण प्रदान करें`FileAuthorMetadata`.
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
## चरण 4: दस्तावेज़ों की तुलना करें और मेटाडेटा सहेजें
निर्दिष्ट मेटाडेटा विकल्पों के साथ दस्तावेज़ों की तुलना करें और तुलना किए गए दस्तावेज़ को सहेजें।
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## चरण 5: सफलता संदेश प्रदर्शित करें
एक सफलता संदेश प्रदर्शित करें जो दर्शाता है कि दस्तावेज़ों और आउटपुट स्थान की सफलतापूर्वक तुलना की गई है।
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने सीखा कि .NET के लिए GroupDocs Compare का उपयोग करके उपयोगकर्ता-परिभाषित दस्तावेज़ मेटाडेटा को कैसे सहेजा जाए। इन चरणों का पालन करके, आप अपनी आवश्यकताओं के अनुसार मेटाडेटा को संरक्षित और हेरफेर करते हुए दस्तावेजों की कुशलतापूर्वक तुलना कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs Compare विभिन्न दस्तावेज़ प्रारूपों को संभाल सकता है?
हाँ, GroupDocs Compare DOCX, PDF, PPTX, XLSX और अन्य सहित दस्तावेज़ प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या .NET के लिए GroupDocs Compare के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप नि:शुल्क परीक्षण का उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### क्या मैं अपनी आवश्यकताओं के अनुसार मेटाडेटा विकल्पों को अनुकूलित कर सकता हूँ?
बिल्कुल, GroupDocs Compare दस्तावेज़ तुलना के दौरान मेटाडेटा हैंडलिंग को अनुकूलित करने के लिए लचीले विकल्प प्रदान करता है।
### क्या GroupDocs Compare तकनीकी सहायता प्रदान करता है?
हाँ, आप GroupDocs Compare मंच से तकनीकी सहायता प्राप्त कर सकते हैं[यहाँ](https://forum.groupdocs.com/c/comparison/12).
### मैं .NET के लिए GroupDocs Compare के लिए लाइसेंस कहां से खरीद सकता हूं?
 आप GroupDocs वेबसाइट से लाइसेंस खरीद सकते हैं[यहाँ](https://purchase.groupdocs.com/buy).