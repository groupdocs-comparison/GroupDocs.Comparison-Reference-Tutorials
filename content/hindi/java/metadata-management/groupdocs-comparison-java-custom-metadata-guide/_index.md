---
categories:
- Java Development
date: '2026-09-10'
description: GroupDocs Comparison का उपयोग करके कस्टम मेटाडेटा java सेट करना सीखें
  और मजबूत Java वर्कफ़्लोज़ के लिए मेटाडेटा के साथ दस्तावेज़ों की तुलना करें।
keywords:
- set custom metadata java
- compare docs with metadata
- groupdocs comparison java
lastmod: '2026-09-10'
linktitle: GroupDocs के साथ Java दस्तावेज़ मेटाडेटा
og_description: GroupDocs Comparison का उपयोग करके कस्टम मेटाडेटा java सेट करें और
  Java में मेटाडेटा के साथ दस्तावेज़ों की तुलना करना सीखें। मजबूत वर्कफ़्लोज़ के लिए
  इस चरण‑दर‑चरण ट्यूटोरियल का पालन करें।
og_image_alt: Guide showing Java code for setting custom metadata with GroupDocs Comparison
og_title: GroupDocs Comparison के साथ कस्टम मेटाडेटा java सेट करें – Java गाइड
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to set custom metadata java using GroupDocs Comparison and
    compare documents with metadata for robust Java workflows.
  headline: Set custom metadata java with GroupDocs Comparison
  type: TechArticle
- description: Learn how to set custom metadata java using GroupDocs Comparison and
    compare documents with metadata for robust Java workflows.
  name: Set custom metadata java with GroupDocs Comparison
  steps:
  - name: set up your output path
    text: '**Pro tip:** In production you’ll usually generate these paths dynamically—consider
      using `System.getProperty("java.io.tmpdir")` or a dedicated output folder that
      your CI/CD pipeline can clean up automatically.'
  - name: initialize the comparer and add target documents
    text: If you encounter a “file not found” exception, double‑check that the paths
      are absolute during development; relative paths often resolve differently when
      the application runs from a different working directory.
  - name: configure custom metadata (the important part)
    text: '- `MetadataType.FILE_AUTHOR` tells GroupDocs which metadata bucket to touch.
      `MetadataType.FILE_AUTHOR` identifies the author metadata bucket that GroupDocs
      will modify. - The `FileAuthorMetadata.Builder` follows the classic builder
      pattern, allowing you to set author, company, and last‑modified‑by '
  - name: run the comparison and save the result
    text: When the comparison finishes, the output file will contain the exact metadata
      you defined, preserving the audit trail across revisions.
  type: HowTo
- questions:
  - answer: GroupDocs.Comparison supports metadata for Word, PDF, Excel, PowerPoint,
      and several image formats. Use the appropriate `MetadataType` enum (e.g., `FILE_AUTHOR`
      for Word, `PDF_AUTHOR` for PDFs) and test each format early in your pipeline.
    question: How do I handle metadata for different document formats?
  - answer: Yes. Call the `Metadata` API on a loaded document to retrieve current
      values, merge them with your custom fields, and then write the combined set
      back to the file.
    question: Can I read existing metadata before modifying it?
  - answer: By default GroupDocs may preserve source metadata. Using `setCloneMetadataType()`
      gives you explicit control—choose to clone, replace, or ignore metadata as required.
    question: What happens to metadata during document comparison?
  - answer: The overhead is negligible compared with the core comparison algorithm.
      In benchmarks, adding metadata to a 200‑page Word file adds less than 0.2 seconds
      to a 3‑second comparison run.
    question: Is there a performance impact from setting custom metadata?
  - answer: Hook into Git post‑commit or CI pipelines to invoke the comparison routine,
      passing the commit author and hash as metadata values. This automatically ties
      each generated document to a specific source change.
    question: How can I integrate this with version‑control systems?
  type: FAQPage
tags:
- java
- document-management
- metadata
- groupdocs
- tutorial
title: GroupDocs Comparison के साथ कस्टम मेटाडेटा java सेट करें
type: docs
url: /hi/java/metadata-management/groupdocs-comparison-java-custom-metadata-guide/
weight: 1
---

# GroupDocs Comparison के साथ कस्टम मेटाडाटा जावा सेट करें

क्या आप कभी दस्तावेज़ संस्करणों में डूबते हुए खुद को पाते हैं, यह सोचते हुए कि किसने कौन से बदलाव कब किए? आप अकेले नहीं हैं। **Set custom metadata java** आपको फ़ाइल में सीधे लेखक, कंपनी और संशोधन विवरण एम्बेड करने देता है, जिससे अदृश्य डेटा एक खोज योग्य ऑडिट ट्रेल में बदल जाता है। इस व्यापक गाइड में आप सीखेंगे कि कस्टम मेटाडाटा कैसे कॉन्फ़िगर करें, मजबूत दस्तावेज़‑तुलना जावा वर्कफ़्लो कैसे चलाएँ, और उन सामान्य समस्याओं से कैसे बचें जो कई डेवलपर्स को फँसाती हैं।

## त्वरित उत्तर
- **जावा में कस्टम मेटाडाटा सेट करने का मुख्य उद्देश्य क्या है?** यह आपको अनुपालन और ऑडिटिंग के लिए दस्तावेज़ों में सीधे लेखक, कंपनी और संशोधन विवरण एम्बेड करने देता है।  
- **कौन सी लाइब्रेरी मेटाडाटा हैंडलिंग और दस्तावेज़ तुलना का समर्थन करती है?** GroupDocs.Comparison for Java।  
- **उदाहरणों को आज़माने के लिए क्या मुझे लाइसेंस चाहिए?** एक मुफ्त ट्रायल उपलब्ध है [temporary license request form](https://purchase.groupdocs.com/temporary-license/); एक पूर्ण लाइसेंस [GroupDocs purchase site](https://purchase.groupdocs.com/buy) से खरीदा जा सकता है।  
- **क्या मैं मेटाडाटा के साथ दस्तावेज़ों की तुलना एक ही चरण में कर सकता हूँ?** हाँ—`setCloneMetadataType` को कस्टम मेटाडाटा सेटिंग्स के साथ उपयोग करें। `setCloneMetadataType` निर्धारित करता है कि सहेजने के दौरान स्रोत मेटाडाटा को कैसे क्लोन, बदल या अनदेखा किया जाए।  
- **कौन सा जावा संस्करण आवश्यक है?** Java 8 या उससे ऊपर।

## “set custom metadata java” क्या है?
`set custom metadata java` जावा कोड से फ़ाइल के भीतर दस्तावेज़ गुणों—जैसे लेखक, कंपनी, या अंतिम‑सहेजा‑गया—को जोड़ने या अपडेट करने की प्रोग्रामेटिक प्रक्रिया है। यह तकनीक अनुपालन, संस्करण नियंत्रण, और स्वचालित ऑडिट ट्रेल्स के लिए आवश्यक है।

## मेटाडाटा के साथ दस्तावेज़ों की तुलना के लिए GroupDocs Comparison का उपयोग क्यों करें?
GroupDocs.Comparison for Java न केवल सामग्री अंतर को हाइलाइट करता है बल्कि दस्तावेज़ गुणों पर सूक्ष्म नियंत्रण भी देता है। यह **50+ इनपुट और आउटपुट फ़ॉर्मेट** का समर्थन करता है और पूरे दस्तावेज़ को मेमोरी में लोड किए बिना कई‑सौ पृष्ठों वाली फ़ाइलों को प्रोसेस कर सकता है, जिससे यह बड़े‑पैमाने पर कानूनी या एंटरप्राइज़ वर्कफ़्लो के लिए आदर्श बनता है।

## पूर्वापेक्षाएँ – शुरू करने से पहले आपको क्या चाहिए
कोड की एक भी लाइन लिखने से पहले आपको एक ठोस आधार चाहिए।

- **GroupDocs.Comparison for Java** – संस्करण 25.2 या बाद का (पहले रिलीज़ में पूर्ण मेटाडाटा समर्थन नहीं है)। इसे [GroupDocs download page](https://releases.groupdocs.com/comparison/java/) से डाउनलोड करें।  
- **Java Development Kit** – Java 8 या उससे ऊपर।  
- **Maven or Gradle** – डिपेंडेंसी प्रबंधन के लिए।  
- **IDE** – IntelliJ IDEA, Eclipse, या कोई भी जावा‑संगत एडिटर।  
- **Sample documents** – परीक्षण के लिए दो Word या PDF फ़ाइलें।

आपको जावा क्लासेज़, Maven की `pom.xml`, और फ़ाइल‑पाथ हैंडलिंग की बुनियादी जानकारी भी चाहिए। यदि इनमें से कोई भी अपरिचित लग रहा है, तो आगे बढ़ने से पहले रुकें और संबंधित मूल बातें देखें।

## कस्टम मेटाडाटा जावा कैसे सेट करें?
अपने स्रोत फ़ाइलों को लोड करें, एक `Comparer` को कॉन्फ़िगर करें, और फिर कस्टम फ़ील्ड्स को इंजेक्ट करने के लिए `FileAuthorMetadata` बिल्डर लागू करें। `Comparer` वह मुख्य क्लास है जो दस्तावेज़ तुलना और मेटाडाटा हैंडलिंग करता है। `FileAuthorMetadata` एक बिल्डर क्लास है जिसका उपयोग आउटपुट दस्तावेज़ के लिए लेखक‑संबंधित मेटाडाटा फ़ील्ड्स निर्दिष्ट करने के लिए किया जाता है। यह तरीका सुनिश्चित करता है कि तुलना होने से पहले मेटाडाटा एम्बेड हो, जिससे ऑडिट ट्रेल संस्करणों में सुसंगत रहता है। आप यह भी देखेंगे कि आउटपुट पाथ कैसे प्रबंधित करें और अपवादों को कैसे संभालें। निम्नलिखित चरण एक पूर्ण, प्रोडक्शन‑रेडी इम्प्लीमेंटेशन के माध्यम से आपका मार्गदर्शन करेंगे।

### चरण 1: अपना आउटपुट पाथ सेट करें
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

**Pro tip:** प्रोडक्शन में आप आमतौर पर इन पाथ को डायनामिक रूप से जेनरेट करेंगे—`System.getProperty("java.io.tmpdir")` का उपयोग करने पर विचार करें या एक समर्पित आउटपुट फ़ोल्डर जिसका आपका CI/CD पाइपलाइन स्वचालित रूप से सफ़ाई कर सके।

### चरण 2: comparer को इनिशियलाइज़ करें और लक्ष्य दस्तावेज़ जोड़ें
```java
import com.groupdocs.comparison.Comparer;

public class MetadataBasics {
    public static void main(String[] args) throws Exception {
        // This is your starting point - simple but functional
        try (Comparer comparer = new Comparer("path/to/your/source/document.docx")) {
            System.out.println("GroupDocs.Comparison initialized successfully!");
            // We'll build on this foundation
        }
    }
}
```

यदि आपको “file not found” अपवाद मिलता है, तो विकास के दौरान पाथ को एब्सोल्यूट होने की दोबारा जाँच करें; रिलेटिव पाथ अक्सर अलग कार्य निर्देशिका से एप्लिकेशन चलने पर अलग ढंग से रिज़ॉल्व होते हैं।

### चरण 3: कस्टम मेटाडाटा कॉन्फ़िगर करें (महत्वपूर्ण भाग)
```java
String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetDocumentMetadataUserDefined.docx";
```

- `MetadataType.FILE_AUTHOR` GroupDocs को बताता है कि किस मेटाडाटा बकेट को छूना है। `MetadataType.FILE_AUTHOR` लेखक मेटाडाटा बकेट को पहचानता है जिसे GroupDocs संशोधित करेगा।  
- `FileAuthorMetadata.Builder` क्लासिक बिल्डर पैटर्न का अनुसरण करता है, जिससे आप लेखक, कंपनी, और अंतिम‑संशोधित‑द्वारा फ़ील्ड्स को टाइप‑सेफ तरीके से सेट कर सकते हैं।

### चरण 4: तुलना चलाएँ और परिणाम सहेजें
```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/SOURCE_WORD.docx")) {
    comparer.add("YOUR_DOCUMENT_DIRECTORY/TARGET1_WORD.docx");
    
    // This is where we'll add our metadata magic
}
```

जब तुलना समाप्त हो जाएगी, आउटपुट फ़ाइल में वही मेटाडाटा होगा जो आपने परिभाषित किया था, जिससे संस्करणों के बीच ऑडिट ट्रेल संरक्षित रहेगा।

## मेटाडाटा के साथ दस्तावेज़ों की तुलना कैसे करें?
दोनों स्रोत फ़ाइलों को लोड करें, एक `Comparer` बनाएं, वही `SaveOptions` पास करें जिसमें आपका कस्टम मेटाडाटा हो, और `compare` को कॉल करें। `SaveOptions` तुलना परिणाम के लिए आउटपुट फ़ॉर्मेट और मेटाडाटा हैंडलिंग को कॉन्फ़िगर करता है। परिणामी दस्तावेज़ आपके द्वारा निर्दिष्ट मेटाडाटा को विरासत में लेता है, जिससे समीक्षक फ़ाइल की सामग्री खोले बिना देख सकते हैं कि प्रत्येक संस्करण किसने लिखा है।

## सामान्य समस्याएँ और उनके समाधान
### समस्या 1: आउटपुट दस्तावेज़ों में मेटाडाटा नहीं दिख रहा है
**Solution:**  
1. पुष्टि करें कि आप GroupDocs.Comparison 25.2 या बाद का उपयोग कर रहे हैं।  
2. जाँचें कि स्रोत और लक्ष्य दोनों फ़ॉर्मेट आपके चयनित मेटाडाटा प्रकार का समर्थन करते हैं।  
3. सुनिश्चित करें कि आउटपुट डायरेक्टरी लिखने योग्य है और फ़ाइल किसी अन्य प्रक्रिया द्वारा लॉक नहीं है।  
4. डबल‑चेक करें कि `setCloneMetadataType` को सहेजने से पहले `MetadataType.FILE_AUTHOR` (या उपयुक्त enum) पर सेट किया गया है।

### समस्या 2: फ़ाइल एक्सेस अपवाद
**Solution:**  
- `Comparer` को try‑with‑resources ब्लॉक में रैप करें ताकि यह ऑटो‑क्लोज़ हो।  
- किसी भी खुले व्यूअर (Word, Acrobat) को बंद करें जो फ़ाइलों को लॉक कर सकते हैं।  
- JVM चलाने वाले उपयोगकर्ता को आउटपुट फ़ोल्डर पर लिखने की अनुमति दें।

### समस्या 3: मेटाडाटा ओवरराइटिंग समस्याएँ
**Solution:** `setCloneMetadataType()` का उपयोग करें ताकि यह नियंत्रित किया जा सके कि मौजूदा मेटाडाटा संरक्षित, मर्ज या रिप्लेस किया जाए। यदि आपको कुछ मूल फ़ील्ड्स रखना है, तो पहले `Metadata` API से उन्हें पढ़ें, अपने कस्टम मानों के साथ मर्ज करें, फिर वापस लिखें। `Metadata` API मौजूदा दस्तावेज़ गुणों जैसे लेखक, शीर्षक, और कस्टम फ़ील्ड्स को पढ़ने की अनुमति देता है।

## वास्तविक दुनिया के अनुप्रयोग और उपयोग केस
### उपयोग केस 1: कानूनी दस्तावेज़ प्रबंधन
कानूनी फर्में स्वचालित रूप से समीक्षक नाम, केस नंबर, और गोपनीयता स्तर को स्टैम्प कर सकती हैं, जिससे एक छेड़छाड़‑प्रूफ ऑडिट ट्रेल बनता है जो कोर्ट‑रूम आवश्यकताओं को पूरा करता है।

```java
final Path resultPath = comparer.compare(outputFileName,
        new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.FILE_AUTHOR)
                .setFileAuthorMetadata(
                        new FileAuthorMetadata.Builder()
                                .setAuthor("Tom")
                                .setCompany("GroupDocs")
                                .setLastSaveBy("Jack")
                                .build())
                .build());
```

### उपयोग केस 2: शैक्षणिक अनुसंधान सहयोग
अनुसंधान समूह योगदानकर्ता आईडी और अनुदान नंबर एम्बेड कर सकते हैं, जिससे फंडिंग एजेंसियों के लिए अनुपालन रिपोर्ट बनाना आसान हो जाता है।

```java
SaveOptions saveOptions = new SaveOptions.Builder()
        .setCloneMetadataType(MetadataType.FILE_AUTHOR)
        .setFileAuthorMetadata(
                new FileAuthorMetadata.Builder()
                        .setAuthor("Tom")
                        .setCompany("GroupDocs")
                        .setLastSaveBy("Jack")
                        .build())
        .build();

// Now you can reuse this configuration across multiple comparisons
```

### उपयोग केस 3: सॉफ़्टवेयर दस्तावेज़ीकरण वर्कफ़्लो
डेवलपमेंट टीमें रिलीज़ नोट्स के लिए संस्करण टैगिंग और लेखक एट्रिब्यूशन को स्वचालित कर सकती हैं, जिससे हर बदलाव को कमिट या टिकट से ट्रेस किया जा सके।

```java
public SaveOptions buildMetadataOptions(String author, String company, boolean preserveOriginal) {
    SaveOptions.Builder builder = new SaveOptions.Builder()
            .setCloneMetadataType(MetadataType.FILE_AUTHOR);
    
    if (!preserveOriginal) {
        builder.setFileAuthorMetadata(
                new FileAuthorMetadata.Builder()
                        .setAuthor(author)
                        .setCompany(company)
                        .setLastSaveBy(getCurrentUser())
                        .build());
    }
    
    return builder.build();
}
```

ये परिदृश्य SharePoint, Office 365, CI/CD पाइपलाइन्स, और कस्टम कंटेंट‑मैनेजमेंट सिस्टम्स के साथ सहजता से एकीकृत होते हैं, जिससे आप मेटाडाटा को पूरे एंटरप्राइज़ स्टैक में प्रसारित कर सकते हैं।

## प्रदर्शन अनुकूलन टिप्स
### मेमोरी प्रबंधन सर्वोत्तम अभ्यास
```java
// Automatically set reviewer and review date for legal documents
FileAuthorMetadata legalMetadata = new FileAuthorMetadata.Builder()
        .setAuthor(getCurrentReviewer())
        .setCompany("Legal Department")
        .setLastSaveBy(getCurrentReviewer())
        .build();
```

- कई फ़ाइलों को प्रोसेस करते समय एक ही `SaveOptions` इंस्टेंस को पुन: उपयोग करें।  
- हीप उपयोग को नियंत्रित रखने के लिए दस्तावेज़ों को 10‑20 के बैच में प्रोसेस करें।  
- बड़े‑पैमाने के वर्कलोड के लिए Java के G1 गार्बेज कलेक्टर को सक्षम करें।

### बैच प्रोसेसिंग सिफ़ारिशें
जब आपको हजारों फ़ाइलों को संभालना हो, तो प्रोड्यूसर‑कंज्यूमर पैटर्न पर विचार करें: वर्कर थ्रेड्स का एक छोटा पूल फ़ाइलें पढ़ता है, मेटाडाटा लागू करता है, और परिणाम को एक टेम्पररी फ़ोल्डर में लिखता है। “Too many open files” त्रुटियों से बचने के लिए फ़ाइल‑हैंडल काउंट की निगरानी करें।

### संसाधन‑उपयोग दिशानिर्देश
- **Heap:** स्थिरता के लिए उपयोग को JVM अधिकतम हीप के 75 % से नीचे रखें।  
- **Disk:** प्रोसेसिंग के दौरान टेम्पररी तुलना फ़ाइलें बनती हैं, इसलिए प्रत्येक 100 MB स्रोत सामग्री पर कम से कम 2 GB फ्री स्पेस सुनिश्चित करें।

## उन्नत टिप्स और सर्वोत्तम प्रथाएँ
### संदर्भ के आधार पर गतिशील मेटाडाटा
```java
// Track multiple contributors in research documents
FileAuthorMetadata researchMetadata = new FileAuthorMetadata.Builder()
        .setAuthor("Dr. Smith")
        .setCompany("University Research Lab")
        .setLastSaveBy("Research Assistant")
        .build();
```

### ऐसा एरर हैंडलिंग जो वास्तव में मदद करे
```java
// Integrate with version control systems
FileAuthorMetadata devMetadata = new FileAuthorMetadata.Builder()
        .setAuthor(getGitUsername())
        .setCompany("Development Team")
        .setLastSaveBy(getCurrentDeveloper())
        .build();
```

### कॉन्फ़िगरेशन प्रबंधन
अपने मेटाडाटा टेम्प्लेट्स को JSON या YAML फ़ाइलों में बाहरी रूप से रखें ताकि गैर‑डेवलपर्स लेखक फ़ील्ड्स को पुनः कम्पाइल किए बिना समायोजित कर सकें।

```java
// Good: Proper resource management
try (Comparer comparer = new Comparer("source.docx")) {
    // Do your comparison work here
    // Resources automatically cleaned up
}

// Avoid: Manual resource management
Comparer comparer = new Comparer("source.docx");
// Easy to forget cleanup, leading to memory leaks
```

## अक्सर पूछे जाने वाले प्रश्न
**Q: विभिन्न दस्तावेज़ फ़ॉर्मेट्स के लिए मेटाडाटा कैसे संभालूँ?**  
A: GroupDocs.Comparison Word, PDF, Excel, PowerPoint, और कई इमेज फ़ॉर्मेट्स के लिए मेटाडाटा का समर्थन करता है। उपयुक्त `MetadataType` enum का उपयोग करें (जैसे Word के लिए `FILE_AUTHOR`, PDFs के लिए `PDF_AUTHOR`) और अपने पाइपलाइन में प्रारंभिक चरण में प्रत्येक फ़ॉर्मेट का परीक्षण करें।

**Q: संशोधित करने से पहले मौजूदा मेटाडाटा पढ़ सकता हूँ?**  
A: हाँ। लोडेड दस्तावेज़ पर `Metadata` API को कॉल करके वर्तमान मान प्राप्त करें, उन्हें अपने कस्टम फ़ील्ड्स के साथ मर्ज करें, और फिर संयुक्त सेट को फ़ाइल में वापस लिखें।

**Q: दस्तावेज़ तुलना के दौरान मेटाडाटा क्या होता है?**  
A: डिफ़ॉल्ट रूप से GroupDocs स्रोत मेटाडाटा को संरक्षित रख सकता है। `setCloneMetadataType()` का उपयोग करने से आपको स्पष्ट नियंत्रण मिलता है—आवश्यकतानुसार मेटाडाटा को क्लोन, रिप्लेस या इग्नोर करने का चयन करें।

**Q: कस्टम मेटाडाटा सेट करने से प्रदर्शन पर कोई असर पड़ता है?**  
A: कोर तुलना एल्गोरिदम की तुलना में ओवरहेड नगण्य है। बेंचमार्क में, 200‑पृष्ठ Word फ़ाइल में मेटाडाटा जोड़ने से 3‑सेकंड की तुलना रन में 0.2 सेकंड से कम का अतिरिक्त समय लगता है।

**Q: इसे संस्करण‑नियंत्रण सिस्टम्स के साथ कैसे एकीकृत करूँ?**  
A: Git पोस्ट‑कमिट या CI पाइपलाइन्स में हुक करें ताकि तुलना रूटीन को कॉल किया जा सके, कमिट लेखक और हैश को मेटाडाटा मानों के रूप में पास करें। इससे प्रत्येक उत्पन्न दस्तावेज़ स्वचालित रूप से एक विशिष्ट स्रोत परिवर्तन से जुड़ जाता है।

**Last Updated:** 2026-09-10  
**Tested With:** GroupDocs.Comparison 25.2 for Java  
**Author:** GroupDocs

```java
public FileAuthorMetadata createContextualMetadata(DocumentContext context) {
    return new FileAuthorMetadata.Builder()
            .setAuthor(context.getCurrentUser())
            .setCompany(context.getOrganization())
            .setLastSaveBy(context.getLastModifier())
            .build();
}
```

```java
try (Comparer comparer = new Comparer(sourceFile)) {
    comparer.add(targetFile);
    comparer.compare(outputFile, saveOptions);
} catch (Exception e) {
    logger.error("Failed to process document: " + sourceFile, e);
    // Implement your error handling strategy
    throw new DocumentProcessingException("Comparison failed", e);
}
```

```java
// Load from properties file or database
Properties metadataConfig = loadMetadataConfiguration();
FileAuthorMetadata metadata = new FileAuthorMetadata.Builder()
        .setAuthor(metadataConfig.getProperty("default.author"))
        .setCompany(metadataConfig.getProperty("default.company"))
        .build();
```

## संबंधित ट्यूटोरियल

- [GroupDocs.Comparison के साथ जावा में दस्तावेज़ मेटाडाटा सेट करें](/comparison/java/metadata-management/implement-metadata-groupdocs-comparison-java-guide/)
- [compare pdf java – Word दस्तावेज़ों के लिए पूर्ण GroupDocs.Comparison गाइड](/comparison/java/basic-comparison/java-groupdocs-comparison-document-management-guide/)
- [लाइसेंस का उपयोग कैसे करें: GroupDocs Comparison Java URL कॉन्फ़िगरेशन गाइड](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)