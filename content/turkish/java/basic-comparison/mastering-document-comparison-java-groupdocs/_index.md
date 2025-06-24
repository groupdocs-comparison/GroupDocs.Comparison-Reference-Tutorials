---
"date": "2025-05-05"
"description": "GroupDocs.Comparison for Java'yı kullanarak belge karşılaştırmasını hassasiyetle nasıl otomatikleştireceğinizi öğrenin. Stilleri özelleştirin, hassasiyeti ayarlayın ve başlıkları/altbilgileri zahmetsizce yok sayın."
"title": "GroupDocs.Comparison API'sini Kullanarak Java'da Ana Belge Karşılaştırması"
"url": "/tr/java/basic-comparison/mastering-document-comparison-java-groupdocs/"
"weight": 1
---

# GroupDocs.Comparison API'sini Kullanarak Java'da Belge Karşılaştırmasında Ustalaşma

## giriiş

Belgeleri manuel olarak karşılaştırmaktan yoruldunuz mu? İster başlıklarda, ister altbilgilerde veya içerikte değişiklikleri belirlemek olsun, belge karşılaştırması zorlu bir görev olabilir. GroupDocs.Comparison for Java kitaplığı bu süreci hassasiyet ve kolaylıkla otomatikleştirir ve geliştirir.

Bu kapsamlı eğitim, belge karşılaştırma stillerini özelleştirmek, hassasiyet ayarlarını düzenlemek, başlık/altbilgi karşılaştırmalarını yoksaymak, çıktı kağıt boyutunu ayarlamak ve daha fazlası için Java'da GroupDocs.Comparison'ı kullanma konusunda size rehberlik edecektir. Bu kılavuzun sonunda, iş akışınızı verimli bir şekilde düzene koyabileceksiniz.

**Ne Öğreneceksiniz:**
- Belge karşılaştırmaları sırasında üstbilgileri ve altbilgileri dikkate almayın.
- Stil ayarlamalarıyla değişiklikleri özelleştirin.
- Ayrıntılı analiz için karşılaştırma hassasiyetini ayarlayın.
- Java uygulamalarında çıktı kağıt boyutlarını ayarlayın.
- Bu özellikleri gerçek dünya senaryolarına uygulayın.

Pratik konulara dalmadan önce gerekli ön koşullara sahip olduğunuzdan emin olun.

## Ön koşullar

GroupDocs.Comparison for Java'yı kullanmaya başlamak için aşağıdakilere sahip olduğunuzdan emin olun:
1. **Java Geliştirme Kiti (JDK):** Makinenizde JDK'nın yüklü olduğundan emin olun. 8'in üzerindeki herhangi bir sürüm yeterli olacaktır.
2. **Usta:** Bu eğitimde proje bağımlılıklarını yönetmek için Maven kullandığınızı varsayıyoruz.
3. **GroupDocs.Karşılaştırma Kütüphanesi:**
   - Aşağıdaki bağımlılığı ekleyin `pom.xml`:

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
4. **Lisans:** GroupDocs'tan ücretsiz deneme sürümünü, geçici lisansı edinin veya tam sürümü satın alın.

Bunları ayarladıktan sonra Java uygulamalarınızda belge karşılaştırma özelliklerini uygulamaya başlamaya hazırsınız.

## Java için GroupDocs.Comparison Kurulumu

Ortamımızın doğru şekilde yapılandırıldığından emin olun:

### Maven üzerinden kurulum

Yukarıdaki XML kod parçacığını projenize ekleyin `pom.xml`Bu adım, gerekli deponun ve bağımlılığın Maven tarafından tanınmasını sağlar. 

### Lisans Edinimi
- **Ücretsiz Deneme:** Deneme sürümünü şuradan indirin: [GroupDocs İndirmeleri](https://releases.groupdocs.com/comparison/java/).
- **Geçici Lisans:** Geçici bir lisans talebinde bulunun [GroupDocs Desteği](https://purchase.groupdocs.com/temporary-license/) tüm özelliklerini değerlendirmek için.
- **Satın almak:** Uzun vadeli kullanım için, şu adresten lisans satın alın: [GroupDocs Satın Alma](https://purchase.groupdocs.com/buy).

GroupDocs dokümantasyonuna göre lisans dosyanızı edinip ayarladıktan sonra GroupDocs.Comparison'ı şu şekilde başlatın:

```java
// Temel başlatma örneği
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

## Uygulama Kılavuzu

### Özellik 1: Başlık/Altbilgi Karşılaştırmasını Yoksay

**Genel Bakış:** Üstbilgiler ve altbilgiler genellikle sayfa numaraları veya belge başlıkları gibi içerik değişikliği karşılaştırmaları için önemli olmayabilecek bilgiler içerir.

#### Seçenekleri Ayarlama

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import java.io.FileOutputStream;

public class IgnoreHeaderFooterExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/IgnoreHeaderFooter_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_with_footer.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target_with_footer.docx");

            // Karşılaştırma seçeneklerini üstbilgileri ve altbilgileri yoksayacak şekilde ayarlayın
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

#### Açıklama
- **`CompareOptions.Builder().setHeaderFootersComparison(false)`**: Bu ayar, kütüphaneye üstbilgi ve altbilgi karşılaştırmalarını atlamasını söyler.
- **`try-with-resources`:** Kullanımdan sonra tüm akışların düzgün bir şekilde kapatılmasını sağlar.

### Özellik 2: Çıktı Kağıt Boyutunu Ayarla

**Genel Bakış:** Çıktı kağıt boyutunu özelleştirmek, baskıya uygun belgeler oluşturmak için çok önemlidir. İşte belge karşılaştırması sırasında bunu nasıl ayarlayabileceğiniz.

#### Uygulama Adımları

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.PaperSize;

public class SetOutputPaperSizeExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetOutputPaperSize_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Kağıt boyutunu A6 olarak ayarlayın
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Açıklama
- **`CompareOptions.Builder().setPaperSize(PaperSize.A6)`**: Çıktı kağıt boyutunu A6 olarak ayarlar.

### Özellik 3: Karşılaştırma Hassasiyetini Ayarla

**Genel Bakış:** Karşılaştırma hassasiyetini ince ayarlamak, küçük değişiklikleri bile belirlemeye yardımcı olur. İşte bunu nasıl ayarlayabileceğiniz:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Hassasiyeti 100'e ayarlayın
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Açıklama
- **`CompareOptions.Builder().setSensitivityOfComparison(100)`**: Değişiklikleri algılamak için hassasiyet seviyesini ayarlar.

### Özellik 4: Değişiklik Stillerini Özelleştirme (Akışları Kullanarak)

**Genel Bakış:** Eklenen, silinen ve değiştirilen metinler arasında ayrım yapmak, karşılaştırmaları daha sezgisel hale getirir. Akışları kullanarak stilleri nasıl özelleştireceğiniz aşağıda açıklanmıştır:

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.save.SaveOptions;
import com.groupdocs.comparison.options.style.StyleSettings;

import java.awt.Color;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class CustomizeChangesStylesStreamExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CustomizeChangesStylesStream_result.docx";

        try (InputStream sourceFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source_word.docx");
             InputStream targetFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer(sourceFile)) {

            comparer.add(targetFile);

            // Değişiklik stillerini özelleştir
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // Eklemeler için yeşil
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // Silinmeler için kırmızı
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // Değişiklikler için mavi

            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setInsertedItemStyle(insertedStyle)
                    .setDeletedItemStyle(deletedStyle)
                    .setChangedItemStyle(changedStyle)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### Açıklama
- **Özel Stil Ayarları**: Kullanmak `StyleSettings` eklemeler (yeşil), silmeler (kırmızı) ve değişiklikler (mavi) için vurgu renklerini tanımlamak.
- **`CompareOptions.Builder()`:** Karşılaştırma sürecinde bu stilleri uygulayın.

## Çözüm

GroupDocs.Comparison for Java'dan yararlanarak, belge karşılaştırmasını hassasiyetle otomatikleştirebilirsiniz. Bu eğitimde, başlıklar/altbilgilerin nasıl göz ardı edileceği, çıktı kağıt boyutlarının nasıl ayarlanacağı, hassasiyetin nasıl ayarlanacağı ve değişiklik stillerinin nasıl özelleştirileceği ele alındı. Bu özelliklerin uygulanması, iş akışınızı kolaylaştıracak ve Java uygulamalarında belge analizini geliştirecektir.

## SSS

### 1. GroupDocs for Java'da karşılaştırma sırasında üstbilgileri ve altbilgileri göz ardı edebilir miyim?  

Evet, kullan `setHeaderFootersComparison(false)` içinde `CompareOptions` Başlık ve altbilgileri karşılaştırmadan hariç tutmak için.

### 2. GroupDocs kullanarak Java'da çıktı kağıt boyutunu nasıl ayarlarım?  

Uygula `setPaperSize(PaperSize.A6)` veya diğer boyutlarda `CompareOptions` Son belgenin kağıt boyutunu özelleştirmek için.

### 3. Karşılaştırma hassasiyetini ince ayarlamak mümkün müdür?  

Evet, kullan `setSensitivityOfComparison()` içinde `CompareOptions` hassasiyeti ayarlamak, buna göre küçük veya büyük değişiklikleri algılamak.

### 4. Karşılaştırma sırasında eklenen, silinen ve değiştirilen metinleri biçimlendirebilir miyim?  

Kesinlikle, stilleri şu şekilde özelleştirin: `StyleSettings` farklı değişiklik türleri için bunları uygulayın ve `CompareOptions`.

### 5. Java'da GroupDocs Comparison'ı kullanmaya başlamak için ön koşullar nelerdir?  

JDK'yı kurun, Maven ile bağımlılıkları yönetin, bir lisans edinin ve GroupDocs.Comparison kütüphanesini projenize ekleyin.