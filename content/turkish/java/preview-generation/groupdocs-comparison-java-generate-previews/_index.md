---
categories:
- Java Development
date: '2026-02-08'
description: GroupDocs.Comparison kullanarak Java'da PDF önizleme oluşturmayı öğrenin.
  PDF, Word ve Excel önizlemeleri için kod örnekleriyle adım adım öğretici.
keywords: Java document preview generator, generate document thumbnails Java, Java
  PDF preview creation, document image conversion Java, Java library for document
  thumbnails
lastmod: '2025-01-02'
linktitle: Java Document Preview Generator
tags:
- document-processing
- java-library
- preview-generation
- pdf-thumbnails
title: PDF Önizleme Oluştur Java – Java Belge Önizleme Oluşturucu
type: docs
url: /tr/java/preview-generation/groupdocs-comparison-java-generate-previews/
weight: 1
---

# PDF Önizleme Oluşturma Java – Java Belge Önizleme Oluşturucu

## Giriş

Java uygulamanızda belge önizlemeleri oluşturmanız mı gerekiyor? İster bir belge yönetim sistemi, dosya tarayıcısı ya da iş birliği aracı oluşturuyor olun, belgelerin görsel küçük resimlerini oluşturmak daha iyi bir kullanıcı deneyimi için gereklidir. Bu rehberde **create pdf preview java** adım adım GroupDocs.Comparison ile oluşturacak, ortam kurulumundan performans ayarına kadar her şeyi kapsayacağız.

### Hızlı Yanıtlar
- **Java'da PDF önizlemeleri oluşturmak için hangi kütüphaneyi kullanabilirim?** GroupDocs.Comparison yüksek kaliteli önizlemeler için basit bir API sağlar.  
- **Hangi formatlar destekleniyor?** PDF, DOCX, XLSX, PPTX ve daha fazlası dahil olmak üzere 50'den fazla format.  
- **Sadece ilk sayfa için önizleme nasıl oluştururum?** `previewOptions.setPageNumbers(new int[]{1})` ayarlayın.  
- **Önizleme oluşturmayı asenkron olarak çalıştırabilir miyim?** Evet—`ExecutorService` veya `CompletableFuture` kullanın.  
- **Küçük resimler için en iyi görüntü formatı hangisidir?** PNG en iyi kaliteyi sunar; JPEG web kullanımı için daha küçüktür.

## “create pdf preview java” nedir?

Java'da PDF önizlemesi oluşturmak, bir PDF'in (veya başka bir belgenin) her sayfasını tarayıcılarda veya mobil uygulamalarda görüntülenebilen bir resme dönüştürmek anlamına gelir. Bu işleme genellikle **java convert document to image** denir ve tam belgeyi yüklemeden hızlı görsel indeksleme sağlar.

## Neden Java Belge Önizleme Oluşturucu Kullanmalı?

Koda geçmeden önce, belge önizleme oluşturmanın modern uygulamalar için neden hayati olduğunu anlayalım:

**Kullanıcı Deneyimi Avantajları**
- Kullanıcılar belgeleri açmadan hızlıca tanımlayabilir.
- Büyük belge koleksiyonlarında daha hızlı gezinme.
- Dosyaları indirmeden veya paylaşmadan önce görsel onay.

**Performans Avantajları**
- Tam belge render edilmesini önleyerek sunucu yükünü azaltır.
- Hafif önizleme resimleriyle daha iyi önbellekleme stratejileri.
- Optimize edilmiş küçük resimlerle mobil deneyim iyileştirilir.

**İş Uygulamaları**
- Görsel tarama özellikli belge yönetim sistemleri.
- Ürün kataloglarını gösteren e‑ticaret platformları.
- Belge paylaşım özellikli iş birliği araçları.

## Önkoşullar ve Ortam Kurulumu

Java belge önizleme oluşturucumuzu oluşturmaya başlamadan önce, şunların olduğundan emin olun:

**Gerekli Yazılım**
- **Java Development Kit (JDK)**: Sürüm 8 veya üzeri (daha iyi performans için Java 11+ önerilir)
- **Maven veya Gradle**: Bağımlılık yönetimi için
- **IDE**: IntelliJ IDEA, Eclipse veya tercih ettiğiniz Java IDE

**Temel Bilgi**
- Java programlama temelleri
- Dosya I/O işlemleri
- Görüntü işleme kavramlarına temel anlayış

**Sistem Gereksinimleri**
- Minimum 4 GB RAM (büyük belgeler için 8 GB önerilir)
- Geçici önizleme dosyaları için yeterli disk alanı

## Java için GroupDocs.Comparison Kurulumu

### Maven Kurulumu ve Yapılandırması

Java belge önizleme oluşturucunuzu oluşturmanın ilk adımı GroupDocs.Comparison bağımlılığını eklemektir. Bunu `pom.xml` dosyanıza ekleyin:

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

**İpucu:** En yeni özellikler ve hata düzeltmeleri için her zaman en son sürümü kullanın. Güncellemeler için [GroupDocs releases page](https://releases.groupdocs.com/comparison/java/) adresini kontrol edin.

### Gradle Yapılandırması (Alternatif)

Gradle kullanıyorsanız, bunu `build.gradle` dosyanıza ekleyin:

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/comparison/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

### Lisans Kurulum Seçenekleri

Belge önizleme oluşturucunuz için birkaç lisans seçeneğiniz var:

**1. Ücretsiz Deneme** (Test için mükemmel):
- GroupDocs web sitesinden indirin
- Belge başına 3 sayfa ile sınırlıdır
- Su işareti eklenmiş çıktı

**2. Geçici Lisans** (Geliştirme için):
- 30 gün tam özellik erişimi
- Su işareti ve sayfa sınırlaması yok
- Kavram kanıtı projeleri için ideal

**3. Ticari Lisans** (Üretim kullanımı):
- Sınırsız belge ve sayfa
- Öncelikli destek dahil
- Çeşitli lisans modelleri mevcut

### Temel Başlatma

Belge önizleme oluşturucunuzu nasıl başlatacağınız aşağıdadır:

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    // Your preview generation code goes here
}
```

**Önemli:** Kaynak temizliğini sağlamak ve bellek sızıntılarını önlemek için her zaman try‑with‑resources kullanın.

## pdf preview java nasıl oluşturulur – Adım Adım Uygulama

### Önizleme Oluşturma Sürecini Anlamak

Koda dalmadan önce, belge önizleme oluşturmanın nasıl çalıştığını anlayalım:

1. **Document Loading** – Kaynak belgeyi belleğe yükleyin.  
2. **Page Processing** – Her belge sayfasını bir resme dönüştürün.  
3. **Stream Management** – Oluşturulan resimler için çıktı akışlarını yönetin.  
4. **Configuration** – Önizleme seçeneklerini (format, kalite, sayfalar) uygulayın.  
5. **Cleanup** – Kaynakları ve geçici dosyaları serbest bırakın.

### Adım 1: Önizleme Seçeneklerini Yapılandırma

Java belge önizleme oluşturucunuzun temeli doğru yapılandırmadır. Önizleme seçeneklerini nasıl ayarlayacağınız aşağıdadır:

```java
import com.groupdocs.comparison.options.PreviewOptions;
import java.io.FileOutputStream;

final Delegates.CreatePageStream createPageStream = pageNumber -> {
    String pagePath = "YOUR_OUTPUT_DIRECTORY/result-GetPagePreviewsForSourceDocument_" + pageNumber + ".png";
    try {
        return new FileOutputStream(pagePath);
    } catch (FileNotFoundException e) {
        e.printStackTrace();
        return null;
    }
};
```

**Burada ne oluyor:**
- `CreatePageStream` delege, her sayfa için benzersiz bir çıktı akışı oluşturur.
- Dosya adlandırma, kolay tanımlama için sayfa numaralarını içerir.
- PNG formatı, makul dosya boyutlarıyla iyi kalite sağlar.

### Adım 2: Belge Önizlemelerini Oluşturma

Şimdi temel önizleme oluşturma mantığını uygulayalım:

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);
previewOptions.setPageNumbers(new int[]{1, 2, 3}); // Specify desired pages
comparer.getDocument().generatePreview(previewOptions);
```

**Ana Noktalar**
- `setPageNumbers()` yalnızca belirli sayfalar için önizleme oluşturmanıza olanak tanır; bu, büyük belgelerle çalışırken performans için kritiktir.
- Tüm sayfalar için önizleme oluşturma çağrısını atlayın.

### Gelişmiş Yapılandırma Seçenekleri

Üretim uygulamaları için belge küçük resmi oluşturma üzerinde daha fazla kontrol isteyeceksiniz:

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);

// Generate previews for first 5 pages only
previewOptions.setPageNumbers(new int[]{1, 2, 3, 4, 5});

// Set image dimensions (if supported by the format)
// Note: Specific dimension control depends on the output format

// Configure preview format
// PNG: Better quality, larger files
// JPEG: Smaller files, slight quality loss
```

## Yaygın Uygulama Zorlukları ve Çözümler

### Zorluk 1: Büyük Belgelerde Bellek Yönetimi

**Problem:** Çok sayfa içeren büyük PDF'ler veya belgeler `OutOfMemoryError` hatasına neden olabilir.

**Çözüm:** Belgeleri partiler halinde işleyin ve uygun temizlik uygulayın:

```java
// Process in smaller batches
int batchSize = 5;
int totalPages = getTotalPages(document); // Your method to get page count

for (int i = 1; i <= totalPages; i += batchSize) {
    int endPage = Math.min(i + batchSize - 1, totalPages);
    
    // Generate previews for current batch
    int[] pageNumbers = IntStream.rangeClosed(i, endPage).toArray();
    previewOptions.setPageNumbers(pageNumbers);
    
    comparer.getDocument().generatePreview(previewOptions);
    
    // Optional: Force garbage collection between batches
    System.gc();
}
```

### Zorluk 2: Dosya Yolu ve Dizin Yönetimi

**Problem:** Önizleme dosyaları dizinler arasında dağınık, ad çakışmaları.

**Çözüm:** Yapılandırılmış bir dosya yönetim sistemi uygulayın:

```java
public class PreviewFileManager {
    private final String baseDirectory;
    private final String documentId;
    
    public PreviewFileManager(String baseDirectory, String documentId) {
        this.baseDirectory = baseDirectory;
        this.documentId = documentId;
        
        // Create directory structure
        Path previewDir = Paths.get(baseDirectory, "previews", documentId);
        try {
            Files.createDirectories(previewDir);
        } catch (IOException e) {
            throw new RuntimeException("Failed to create preview directory", e);
        }
    }
    
    public String getPreviewPath(int pageNumber) {
        return Paths.get(baseDirectory, "previews", documentId, 
                        String.format("page_%03d.png", pageNumber)).toString();
    }
}
```

### Zorluk 3: Farklı Belge Formatlarını İşleme

**Problem:** Farklı belge türleri farklı işleme yaklaşımları gerektirir.

**Çözüm:** Format‑özel işleyiciler oluşturun:

```java
public class DocumentPreviewGenerator {
    
    public void generatePreviews(String filePath) {
        String extension = getFileExtension(filePath).toLowerCase();
        
        switch (extension) {
            case "pdf":
                generatePdfPreviews(filePath);
                break;
            case "docx":
            case "doc":
                generateWordPreviews(filePath);
                break;
            case "xlsx":
            case "xls":
                generateExcelPreviews(filePath);
                break;
            default:
                generateGenericPreviews(filePath);
        }
    }
    
    private void generatePdfPreviews(String filePath) {
        // PDF-specific optimization
        try (Comparer comparer = new Comparer(filePath)) {
            // PDF documents often have many pages
            // Generate previews for first 10 pages only by default
            PreviewOptions options = createPreviewOptions();
            options.setPageNumbers(new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9, 10});
            comparer.getDocument().generatePreview(options);
        }
    }
}
```

## Performans Optimizasyon Stratejileri

### CPU ve Bellek Optimizasyonu

Üretim için bir Java belge önizleme oluşturucu oluştururken performans hayati önemdedir:

**1. Eşzamanlı İşleme**

```java
ExecutorService executor = Executors.newFixedThreadPool(4);

List<Future<Void>> futures = new ArrayList<>();
for (String documentPath : documentPaths) {
    futures.add(executor.submit(() -> {
        generatePreviewsForDocument(documentPath);
        return null;
    }));
}

// Wait for all tasks to complete
for (Future<Void> future : futures) {
    future.get();
}

executor.shutdown();
```

**2. Önbellekleme Stratejisi**

```java
public class PreviewCache {
    private final Map<String, List<String>> cache = new ConcurrentHashMap<>();
    
    public List<String> getPreviewPaths(String documentHash) {
        return cache.get(documentHash);
    }
    
    public void cachePreviewPaths(String documentHash, List<String> previewPaths) {
        cache.put(documentHash, previewPaths);
    }
}
```

### Görüntü Kalitesi ve Dosya Boyutu Dengesi

Görüntü kalitesi ile dosya boyutu arasındaki doğru dengeyi bulmak kritiktir:

- **Yüksek Kalite (PNG)** – Teknik belgeler, diyagramlar için idealdir.  
- **Optimum Boyut (JPEG, %80‑85 kalite)** – Web küçük resimleri için daha iyidir.  
- Farklı cihazlara hizmet vermek için birden fazla boyut varyantı (küçük, orta, büyük) oluşturmayı düşünün.

## Pratik Uygulamalar ve Kullanım Durumları

### Belge Yönetim Sistemi Entegrasyonu

Java belge önizleme oluşturucunuzu bir belge yönetim sistemine nasıl entegre edeceğiniz aşağıdadır:

```java
@Service
public class DocumentService {
    
    @Autowired
    private PreviewGenerator previewGenerator;
    
    public DocumentPreview uploadDocument(MultipartFile file) {
        // Save document
        String documentPath = saveDocument(file);
        
        // Generate previews asynchronously
        CompletableFuture.runAsync(() -> {
            try {
                previewGenerator.generatePreviews(documentPath);
            } catch (Exception e) {
                log.error("Failed to generate previews for: " + documentPath, e);
            }
        });
        
        return new DocumentPreview(documentPath);
    }
}
```

### E‑ticaret Ürün Kataloğu

Ürün belgelerini gösteren e‑ticaret platformları için:

```java
public class ProductDocumentHandler {
    
    public void processProductDocument(String productId, String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            // Generate thumbnail (first page only for product display)
            PreviewOptions thumbnailOptions = new PreviewOptions(pageNumber -> {
                String thumbnailPath = String.format("products/%s/thumbnail.png", productId);
                return createOutputStream(thumbnailPath);
            });
            thumbnailOptions.setPageNumbers(new int[]{1});
            
            comparer.getDocument().generatePreview(thumbnailOptions);
            
            // Generate detailed previews for product page
            PreviewOptions detailOptions = new PreviewOptions(pageNumber -> {
                String detailPath = String.format("products/%s/page_%d.png", productId, pageNumber);
                return createOutputStream(detailPath);
            });
            
            comparer.getDocument().generatePreview(detailOptions);
        }
    }
}
```

## Üretim Dağıtımı için En İyi Uygulamalar

### Hata Yönetimi ve Günlükleme

Belge önizleme oluşturucunuz için kapsamlı hata yönetimi uygulayın:

```java
public class RobustPreviewGenerator {
    private static final Logger logger = LoggerFactory.getLogger(RobustPreviewGenerator.class);
    
    public boolean generatePreview(String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            logger.info("Starting preview generation for: {}", documentPath);
            
            PreviewOptions options = createPreviewOptions();
            comparer.getDocument().generatePreview(options);
            
            logger.info("Successfully generated previews for: {}", documentPath);
            return true;
            
        } catch (Exception e) {
            logger.error("Failed to generate previews for: " + documentPath, e);
            return false;
        }
    }
}
```

### Kaynak Yönetimi

Her zaman uygun kaynak temizliği uygulayın:

```java
public class ResourceManagedPreviewGenerator implements AutoCloseable {
    private final ExecutorService executor;
    private final PreviewCache cache;
    
    public ResourceManagedPreviewGenerator() {
        this.executor = Executors.newFixedThreadPool(4);
        this.cache = new PreviewCache();
    }
    
    @Override
    public void close() {
        executor.shutdown();
        try {
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                executor.shutdownNow();
            }
        } catch (InterruptedException e) {
            executor.shutdownNow();
            Thread.currentThread().interrupt();
        }
        
        cache.clear();
    }
}
```

## Yaygın Sorunları Giderme

### Sorun 1: “Belge yüklenemedi” Hatası

**Belirtiler:** Belirli belge türlerini yüklemeye çalışırken istisna.

**Çözümler**
1. Belgenin bozuk olmadığını doğrulayın.  
2. Dosya formatının desteklenip desteklenmediğini kontrol edin.  
3. Dosya izinlerinin doğru olduğundan emin olun.  
4. Dosya yolunun var olduğunu doğrulayın.

```java
private boolean isDocumentValid(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        logger.error("Document file does not exist: {}", filePath);
        return false;
    }
    
    if (!file.canRead()) {
        logger.error("Cannot read document file: {}", filePath);
        return false;
    }
    
    return true;
}
```

### Sorun 2: Zayıf Önizleme Kalitesi

**Belirtiler:** Oluşturulan önizlemeler bulanık veya pikselli.

**Çözümler**
- Kaynak belgenin kalitesini kontrol edin.  
- Çıktı formatı ayarlarını düzenleyin (kayıpsız kalite için PNG kullanın).  
- Dönüştürme sırasında yeterli sistem kaynaklarının bulunduğundan emin olun.

### Sorun 3: Yavaş Önizleme Oluşturma

**Belirtiler:** Büyük belgeler için önizleme oluşturma çok uzun sürüyor.

**Çözümler**
- İlk önizlemeler için sayfa sınırlamaları uygulayın.  
- Asenkron işleme kullanın (`ExecutorService` örneğine bakın).  
- Kullanıcı geri bildirimi için ilerleme göstergeleri ekleyin.  
- Sık erişilen önizlemeleri önbelleğe alın.

## GroupDocs.Comparison'a Alternatifler

GroupDocs.Comparison belge önizleme oluşturma için mükemmel olsa da, alternatifleri değerlendirmek isteyebilirsiniz:

- **Apache PDFBox** (PDF‑only, open source)  
- **iText** (Commercial, extensive PDF features)  
- **ImageIO with Office libraries** (More control, higher setup complexity)

## Sonuç

Artık GroupDocs.Comparison kullanarak **create pdf preview java** nasıl yapılacağını öğrendiniz. Bu çözüm şunları sağlar:

- PDF, Word, Excel, PowerPoint gibi birden fazla belge formatı desteği  
- Yapılandırılabilir seçeneklerle yüksek kalite önizleme oluşturma  
- Üretim ortamına hazır hata yönetimi ve kaynak yönetimi  
- Kurumsal uygulamalara uygun ölçeklenebilir mimari  

### Sonraki Adımlar
1. **Önbellekleme Uygulayın** – Sık erişilen önizlemeler için Redis veya dosya tabanlı önbellek ekleyin.  
2. **İlerleme İzleme Ekleyin** – Büyük belgeler için önizleme oluşturma ilerlemesini kullanıcılara gösterin.  
3. **Mobil İçin Optimize Edin** – Mobil uygulamalar için duyarlı önizleme ekranları oluşturun.  
4. **Performansı İzleyin** – Sistem performansını izlemek için metrikler ve izleme ekleyin.

Java uygulamanızda belge önizleme oluşturmayı uygulamaya hazır mısınız? Küçük bir kavram kanıtı ile başlayın ve işlevselliği belirli gereksinimlerinize göre yavaş yavaş genişletin.

## Sıkça Sorulan Sorular

**Q1:** Bu Java belge önizleme oluşturucu hangi belge formatlarını destekliyor?  
**A:** GroupDocs.Comparison PDF, DOCX, XLSX, PPTX, TXT, HTML ve daha fazlası dahil olmak üzere 50'den fazla belge formatını destekler. Tam liste için [documentation](https://docs.groupdocs.com/comparison/java/) adresine bakın.

**Q2:** Sadece ilk sayfa için belge küçük resimleri nasıl oluştururum?  
**A:** `previewOptions.setPageNumbers(new int[]{1})` kullanarak yalnızca ilk sayfa için önizleme oluşturun. Bu, belge tarayıcılarında küçük resim oluşturmak için mükemmeldir.

**Q3:** Çıktı görüntü formatını ve kalitesini özelleştirebilir miyim?  
**A:** Evet, `CreatePageStream` delege aracılığıyla çıktı formatını yapılandırabilirsiniz. Kütüphane temel olarak PNG formatını destekler; bu, belge önizlemeleri için mükemmel kalite sağlar.

**Q4:** Çok büyük PDF dosyalarını bellek tükenmeden nasıl yönetirim?  
**A:** Sayfa aralıkları belirleyerek büyük belgeleri partiler halinde işleyin, try‑with‑resources ile uygun kaynak temizliği yapın ve JVM yığın boyutunu `-Xmx` parametresiyle artırmayı düşünün.

**Q5:** Önizlemeleri asenkron olarak oluşturmanın bir yolu var mı?  
**A:** Kesinlikle! `CompletableFuture.runAsync()` veya `ExecutorService` kullanarak önizlemeleri arka plan iş parçacıklarında oluşturun. Bu, ana uygulama iş parçacığının engellenmesini önler.

**Q6:** “License not found” hatalarını nasıl gideririm?  
**A:** Lisans dosyanızın sınıf yolunda (classpath) olduğundan emin olun, lisansın süresinin dolmadığını doğrulayın ve GroupDocs.Comparison sürümünüz için doğru lisans tipini kullandığınızı kontrol edin.

**Ek Kaynaklar**

- **Documentation:** [GroupDocs.Comparison Java Documentation](https://docs.groupdocs.com/comparison/java/)  
- **API Reference:** [Complete API Reference](https://reference.groupdocs.com/comparison/java/)  
- **Download Latest:** [GroupDocs.Comparison Downloads](https://releases.groupdocs.com/comparison/java/)  
- **Purchase License:** [Buy GroupDocs.Comparison License](https://purchase.groupdocs.com/buy)  
- **Try Free:** [Download Free Trial](https://releases.groupdocs.com/comparison/java/)  
- **Get Support:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison)  
- **Temporary License:** [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Son Güncelleme:** 2026-02-08  
**Test Edilen Versiyon:** GroupDocs.Comparison 25.2  
**Yazar:** GroupDocs  

---  
