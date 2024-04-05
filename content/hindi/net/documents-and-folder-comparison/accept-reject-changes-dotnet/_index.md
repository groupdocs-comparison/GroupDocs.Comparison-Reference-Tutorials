---
title: .NET के लिए GroupDocs तुलना में परिवर्तन स्वीकार करें और अस्वीकार करें
linktitle: .NET के लिए GroupDocs तुलना में परिवर्तन स्वीकार करें और अस्वीकार करें
second_title: GroupDocs.Comparison .NET API
description: .NET के लिए GroupDocs Compare का उपयोग करके दस्तावेज़ों में परिवर्तनों को स्वीकार और अस्वीकार करना सीखें। अपने दस्तावेज़ वर्कफ़्लो को सहजता से सुव्यवस्थित करें।
type: docs
weight: 10
url: /hi/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## परिचय
दस्तावेज़ प्रबंधन और सहयोग के क्षेत्र में, फ़ाइलों की सटीकता और अखंडता सुनिश्चित करना सर्वोपरि है। .NET के लिए GroupDocs Compare एक मजबूत समाधान के रूप में उभरता है, जो डेवलपर्स को दस्तावेज़ों में परिवर्तनों को सहजता से स्वीकार करने और अस्वीकार करने के लिए सशक्त बनाता है, जिससे वर्कफ़्लो सुव्यवस्थित होता है और उत्पादकता बढ़ती है। यह ट्यूटोरियल आपको .NET के लिए GroupDocs Compare का उपयोग करके परिवर्तनों को स्वीकार करने और अस्वीकार करने की प्रक्रिया में मार्गदर्शन करेगा, स्पष्टता और कार्यान्वयन में आसानी के लिए प्रत्येक चरण को तोड़ देगा।
## आवश्यक शर्तें
ट्यूटोरियल में जाने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित आवश्यक शर्तें हैं:
### पर्यावरण सेटअप
1. .NET SDK इंस्टॉल करें: यदि आपने पहले से नहीं किया है, तो .NET वेबसाइट से अपने ऑपरेटिंग सिस्टम के लिए उपयुक्त .NET SDK डाउनलोड और इंस्टॉल करें।
2.  .NET के लिए GroupDocs Compare स्थापित करें: दिए गए लिंक से .NET के लिए GroupDocs Compare का नवीनतम संस्करण प्राप्त करें।[लिंक को डाउनलोड करें](https://releases.groupdocs.com/comparison/net/) और स्थापना निर्देशों का पालन करें.
3. C# प्रोग्रामिंग से परिचित: यह ट्यूटोरियल C# प्रोग्रामिंग भाषा और उसके सिंटैक्स की बुनियादी समझ पर आधारित है।

## नामस्थान आयात करें
आरंभ करने के लिए, अपने प्रोजेक्ट में आवश्यक नामस्थान आयात करें। ये नामस्थान दस्तावेज़ तुलना और हेरफेर के लिए आवश्यक कार्यात्मकताओं तक पहुंच प्रदान करेंगे।

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## चरण 1: आउटपुट निर्देशिका और फ़ाइल नाम निर्दिष्ट करें
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 प्रतिस्थापित करना सुनिश्चित करें`"Your Document Directory"` आपकी इच्छित आउटपुट निर्देशिका के पथ के साथ।
## चरण 2: तुलनाकर्ता प्रारंभ करें और दस्तावेज़ों की तुलना करें
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
यह कोड तुलनाकर्ता ऑब्जेक्ट को स्रोत दस्तावेज़ के साथ प्रारंभ करता है और तुलना के लिए लक्ष्य दस्तावेज़ जोड़ता है। फिर, यह तुलना प्रक्रिया को क्रियान्वित करता है।
## चरण 3: परिवर्तनों को पुनः प्राप्त करें और उनमें हेरफेर करें
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
तुलना से परिवर्तन पुनः प्राप्त करें और आवश्यकतानुसार उनमें हेरफेर करें। इस उदाहरण में, परिवर्तनों को पहले अस्वीकार कर दिया जाता है और फिर स्वीकार कर लिया जाता है। परिणामी दस्तावेज़ तदनुसार सहेजे जाते हैं।

## निष्कर्ष
अंत में, .NET के लिए GroupDocs Compare दस्तावेज़ों में परिवर्तनों को स्वीकार करने और अस्वीकार करने के लिए एक सहज समाधान प्रदान करता है। इस ट्यूटोरियल में उल्लिखित चरणों का पालन करके, डेवलपर्स इस कार्यक्षमता को अपने अनुप्रयोगों में कुशलतापूर्वक एकीकृत कर सकते हैं, दस्तावेज़ सटीकता सुनिश्चित कर सकते हैं और सहयोग बढ़ा सकते हैं।
## अक्सर पूछे जाने वाले प्रश्न
### क्या .NET के लिए GroupDocs Compare विभिन्न प्रारूपों के दस्तावेज़ों की तुलना कर सकता है?
हाँ, .NET के लिए GroupDocs Compare DOCX, PDF, PPTX और अन्य जैसे विभिन्न प्रारूपों के दस्तावेज़ों के बीच तुलना का समर्थन करता है।
### क्या .NET के लिए ग्रुपडॉक्स तुलना .NET कोर के साथ संगत है?
हाँ, .NET के लिए GroupDocs Compare .NET Framework और .NET Core दोनों के साथ संगत है।
### क्या मैं तुलना किए गए दस्तावेज़ों में परिवर्तनों की उपस्थिति को अनुकूलित कर सकता हूँ?
बिल्कुल, .NET के लिए GroupDocs Compare रंग, शैली और अन्य सहित परिवर्तनों की उपस्थिति को अनुकूलित करने के लिए व्यापक विकल्प प्रदान करता है।
### क्या .NET के लिए GroupDocs Compare मल्टी-पेज दस्तावेज़ तुलना का समर्थन करता है?
हाँ, .NET के लिए GroupDocs Compare परिशुद्धता और सटीकता के साथ बहु-पृष्ठ दस्तावेज़ों की तुलना का समर्थन करता है।
### क्या .NET के लिए GroupDocs Compare के लिए कोई परीक्षण संस्करण उपलब्ध है?
 हाँ, आप दिए गए लिंक से .NET के लिए GroupDocs Compare का निःशुल्क परीक्षण प्राप्त कर सकते हैं[जोड़ना](https://releases.groupdocs.com/).