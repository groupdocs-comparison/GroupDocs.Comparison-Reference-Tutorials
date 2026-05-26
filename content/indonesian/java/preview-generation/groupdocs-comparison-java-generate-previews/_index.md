---
categories:
- Java Development
date: '2026-05-26'
description: Pelajari cara membuat pratinjau pdf java menggunakan GroupDocs.Comparison.
  Tutorial langkah demi langkah dengan contoh kode untuk pratinjau PDF, Word, Excel.
keywords:
- create pdf preview java
- java document preview generator
- pdf thumbnail generation java
- document image conversion java
lastmod: '2025-01-02'
linktitle: Generator Pratinjau Dokumen Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create pdf preview java using GroupDocs.Comparison. Step-by-step
    tutorial with code examples for PDF, Word, Excel previews.
  headline: Create PDF Preview Java – Java Document Preview Generator
  type: TechArticle
- questions:
  - answer: GroupDocs.Comparison provides a simple API for high‑quality previews.
    question: What library can I use to create PDF previews in Java?
  - answer: Over 50 formats including PDF, DOCX, XLSX, PPTX, and more.
    question: Which formats are supported?
  - answer: Set `previewOptions.setPageNumbers(new int[]{1})`.
    question: How do I generate a preview for only the first page?
  - answer: Yes—use `ExecutorService` or `CompletableFuture`.
    question: Can I run preview generation asynchronously?
  - answer: PNG offers the best quality; JPEG is smaller for web use.
    question: What’s the best image format for thumbnails?
  type: FAQPage
tags:
- document-processing
- java-library
- preview-generation
- pdf-thumbnails
title: Buat Pratinjau PDF Java – Generator Pratinjau Dokumen Java
type: docs
url: /id/java/preview-generation/groupdocs-comparison-java-generate-previews/
weight: 1
---

# Membuat Pratinjau PDF Java – Generator Pratinjau Dokumen Java

Membuat thumbnail visual dokumen secara dramatis meningkatkan kegunaan aplikasi penanganan file berbasis Java. Dalam tutorial ini Anda akan **create pdf preview java** dengan GroupDocs.Comparison, mulai dari persiapan lingkungan hingga penyetelan kinerja lanjutan. Pada akhir tutorial Anda akan memiliki generator pratinjau siap produksi yang mendukung lebih dari 50 format file dan dapat berjalan aman pada PDF besar.

## Jawaban Cepat
- **Library apa yang dapat saya gunakan untuk membuat pratinjau PDF di Java?** GroupDocs.Comparison menyediakan API sederhana untuk pratinjau berkualitas tinggi.  
- **Format apa yang didukung?** Lebih dari 50 format termasuk PDF, DOCX, XLSX, PPTX, dan lainnya.  
- **Bagaimana cara menghasilkan pratinjau hanya untuk halaman pertama?** Atur `previewOptions.setPageNumbers(new int[]{1})`.  
- **Bisakah saya menjalankan pembuatan pratinjau secara asynchronous?** Ya—gunakan `ExecutorService` atau `CompletableFuture`.  
- **Format gambar apa yang terbaik untuk thumbnail?** PNG menawarkan kualitas terbaik; JPEG lebih kecil untuk penggunaan web.

## Apa itu “create pdf preview java”

Membuat pratinjau PDF di Java berarti mengonversi setiap halaman PDF (atau dokumen yang didukung) menjadi gambar yang dapat ditampilkan di peramban atau aplikasi seluler. Konversi ini—sering disebut **java convert document to image**—memungkinkan pengguna menelusuri koleksi besar tanpa membuka file lengkap, menghemat bandwidth dan meningkatkan waktu respons.

## Mengapa Menggunakan Generator Pratinjau Dokumen Java?

Membuat pratinjau di sisi server menghilangkan kebutuhan akan perpustakaan rendering PDF di sisi klien dan memastikan pengalaman visual yang seragam di semua perangkat. Ini mempercepat penelusuran dokumen, mengurangi konsumsi bandwidth, dan menyederhanakan integrasi, menjadikannya ideal untuk manajemen dokumen, e‑commerce, dan platform kolaborasi.

- **Kecepatan:** Pembuatan thumbnail biasanya 5‑10× lebih cepat daripada memuat PDF lengkap.  
- **Skalabilitas:** GroupDocs.Comparison dapat memproses dokumen 200‑halaman tanpa memuat seluruh file ke memori, berkat arsitektur streamingnya.  
- **Keandalan:** Mendukung lebih dari 50 format input dan output, menjamin bahwa sebagian besar dokumen perusahaan tercakup secara langsung.

## Prasyarat dan Penyiapan Lingkungan

Sebelum kita mulai membangun generator pratinjau dokumen Java, pastikan Anda memiliki:

**Required Software**
- **Java Development Kit (JDK)**: Versi 8 atau lebih tinggi (Java 11+ disarankan untuk kinerja lebih baik)
- **Maven atau Gradle**: Untuk manajemen dependensi
- **IDE**: IntelliJ IDEA, Eclipse, atau IDE Java pilihan Anda

**Basic Knowledge**
- Dasar-dasar pemrograman Java
- Operasi File I/O
- Pemahaman dasar konsep pemrosesan gambar

**System Requirements**
- Minimum 4 GB RAM (8 GB disarankan untuk memproses dokumen besar)
- Ruang disk yang cukup untuk file pratinjau sementara

## Menyiapkan GroupDocs.Comparison untuk Java

### Instalasi dan Konfigurasi Maven

The `Comparison` package is delivered via Maven Central. Add this dependency to your `pom.xml`:

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

**Pro Tip:** Selalu gunakan versi terbaru untuk mendapatkan fitur terbaru dan perbaikan bug. Periksa [GroupDocs releases page](https://releases.groupdocs.com/comparison/java/) untuk pembaruan.

### Konfigurasi Gradle (Alternatif)

If you prefer Gradle, include the following in your `build.gradle` file:

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

### Opsi Penyiapan Lisensi

Anda memiliki beberapa opsi lisensi untuk generator pratinjau dokumen Anda:

**1. Free Trial** (Sempurna untuk pengujian):
- Unduh dari situs web GroupDocs
- Terbatas pada 3 halaman per dokumen
- Output berwatermark

**2. Temporary License** (Untuk pengembangan):
- Akses penuh fitur selama 30 hari
- Tanpa watermark atau batasan halaman
- Ideal untuk proyek proof‑of‑concept

**3. Commercial License** (Penggunaan produksi):
- Dokumen dan halaman tak terbatas
- Dukungan prioritas termasuk
- Berbagai model lisensi tersedia

### Inisialisasi Dasar

The `Comparison` object is the entry point for all preview operations. Initializing it correctly ensures thread‑safety and optimal memory usage.

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    // Your preview generation code goes here
}
```

**Important:** Selalu gunakan try‑with‑resources untuk memastikan pembersihan sumber daya yang tepat dan menghindari kebocoran memori.

## Cara membuat pdf preview java – Implementasi Langkah‑per‑Langkah

Muat file sumber Anda dengan `Comparison comparison = new Comparison("license.txt");` dan panggil `comparison.generatePreview(inputPath, previewOptions);` — panggilan tunggal ini menangani pemuatan dokumen, rendering halaman, dan pembuatan aliran gambar. API menyembunyikan parsing PDF tingkat rendah, memungkinkan Anda fokus pada logika bisnis sambil menghasilkan thumbnail PNG atau JPEG berkualitas tinggi.

### Memahami Proses Pembuatan Pratinjau

Sebelum menyelam ke kode, mari pahami cara kerja pembuatan pratinjau dokumen:

1. **Document Loading** – Muat dokumen sumber ke memori.  
2. **Page Processing** – Konversi setiap halaman dokumen menjadi gambar.  
3. **Stream Management** – Tangani aliran output untuk gambar yang dihasilkan.  
4. **Configuration** – Terapkan opsi pratinjau (format, kualitas, halaman).  
5. **Cleanup** – Lepaskan sumber daya dan file sementara.

### Langkah 1: Konfigurasikan Opsi Pratinjau

The `CreatePageStream` delegate creates a unique output stream for each page. The `previewOptions` object lets you specify image format, resolution, and which pages to render.

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

**Apa yang terjadi di sini:**  
- Delegate menulis setiap halaman ke file PNG terpisah dengan nama `preview_page_{pageNumber}.png`.  
- Format PNG memberikan kualitas lossless, sementara resolusi 150 dpi menyeimbangkan kejernihan dan ukuran file untuk sebagian besar skenario web.

### Langkah 2: Hasilkan Pratinjau Dokumen

`previewOptions` is an object that specifies output format, resolution, and page selection for the preview generation process.  
Invoke the preview engine with the configured options. The API will iterate over the requested pages, render them, and write the results to the streams you supplied.

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);
previewOptions.setPageNumbers(new int[]{1, 2, 3}); // Specify desired pages
comparer.getDocument().generatePreview(previewOptions);
```

**Poin Penting**  
- `setPageNumbers()` memungkinkan Anda menghasilkan pratinjau hanya untuk halaman tertentu, yang penting untuk kinerja saat menangani dokumen besar.  
- Lewati pemanggilan untuk menghasilkan pratinjau semua halaman.

## Opsi Konfigurasi Lanjutan

Production environments often need tighter control over output size, color depth, and caching. The following snippet demonstrates how to tweak these settings:

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

## Tantangan Implementasi Umum dan Solusinya

### Tantangan 1: Manajemen Memori dengan Dokumen Besar

Large PDFs can exhaust the JVM heap if every page is kept in memory. Process documents in batches and dispose of each page stream immediately after writing.

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

### Tantangan 2: Manajemen Jalur File dan Direktori

Scattered preview files cause maintenance headaches. Use a deterministic folder hierarchy based on document ID and timestamp.

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

### Tantangan 3: Menangani Berbagai Format Dokumen

Not all formats render identically. GroupDocs.Comparison provides format‑specific optimizations; for example, DOCX files benefit from vector‑based rendering while images use raster conversion.

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

## Strategi Optimasi Kinerja

### Optimasi CPU dan Memori

`ExecutorService` is a Java concurrency utility that manages a pool of worker threads for parallel task execution.  
Concurrent processing can dramatically reduce total preview time on multi‑core servers. The following example spins up a fixed thread pool and processes pages in parallel.

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

### Strategi Caching

`Redis` is an in‑memory data store commonly used for fast caching of objects such as generated thumbnails.  
Cache previously generated thumbnails in Redis or a local file store. The cache key should combine document hash, page number, and requested image size.

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

### Keseimbangan Kualitas Gambar vs Ukuran File

Finding the right balance between image quality and file size is crucial:

- **High Quality (PNG)** – Ideal untuk dokumen teknis, diagram.  
- **Optimized Size (JPEG, 80‑85 % quality)** – Lebih baik untuk thumbnail web.  
- Pertimbangkan menghasilkan beberapa varian ukuran (thumbnail, medium, large) untuk melayani berbagai perangkat.

## Aplikasi Praktis dan Kasus Penggunaan

### Integrasi Sistem Manajemen Dokumen

Integrate the preview generator into a DMS workflow so that every uploaded file automatically receives a PNG thumbnail stored alongside the original.

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

### Katalog Produk E‑commerce

For e‑commerce platforms that sell downloadable product manuals, generate a preview image for each manual to display on product pages, improving conversion rates.

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

## Praktik Terbaik untuk Penyebaran Produksi

### Penanganan Kesalahan dan Logging

Implement comprehensive error handling to capture licensing issues, unsupported formats, and I/O failures. Log each exception with a unique correlation ID for easier troubleshooting.

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

### Manajemen Sumber Daya

Always close streams in a finally block or use try‑with‑resources. This prevents file descriptor leaks that can crash long‑running services.

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

## Memecahkan Masalah Umum

### Masalah 1: Kesalahan “Could not load document”

**Symptoms:** Exception when trying to load certain document types.

**Solutions**
1. Verifikasi bahwa dokumen tidak rusak.  
2. Periksa apakah format file didukung.  
3. Pastikan izin file yang tepat.  
4. Validasi bahwa jalur file ada.

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

### Masalah 2: Kualitas Pratinjau Buruk

**Symptoms:** Generated previews are blurry or pixelated.

**Solutions**
- Periksa kualitas dokumen sumber.  
- Sesuaikan pengaturan format output (gunakan PNG untuk kualitas lossless).  
- Pastikan sumber daya sistem memadai selama konversi.

### Masalah 3: Pembuatan Pratinjau Lambat

**Symptoms:** Preview generation takes too long for large documents.

**Solutions**
- Terapkan batas halaman untuk pratinjau awal.  
- Gunakan pemrosesan asynchronous (lihat contoh `ExecutorService`).  
- Tambahkan indikator kemajuan untuk umpan balik pengguna.  
- Cache pratinjau yang sering diakses.

## Alternatif untuk GroupDocs.Comparison

Meskipun GroupDocs.Comparison sangat baik untuk pembuatan pratinjau dokumen, Anda mungkin ingin mempertimbangkan alternatif:

- **Apache PDFBox** (hanya PDF, sumber terbuka)  
- **iText** (Komersial, fitur PDF yang luas)  
- **ImageIO with Office libraries** (Kontrol lebih, kompleksitas pengaturan lebih tinggi)

## Kesimpulan

Anda kini telah mempelajari cara **create pdf preview java** menggunakan GroupDocs.Comparison. Solusi ini menyediakan:

- Dukungan untuk berbagai format dokumen (PDF, Word, Excel, PowerPoint)  
- Pembuatan pratinjau berkualitas tinggi dengan opsi yang dapat dikonfigurasi  
- Penanganan kesalahan dan manajemen sumber daya siap produksi  
- Arsitektur skalabel yang cocok untuk aplikasi perusahaan  

### Langkah Selanjutnya

1. **Implement Caching** – Tambahkan caching Redis atau berbasis file untuk pratinjau yang sering diakses.  
2. **Add Progress Tracking** – Tampilkan kepada pengguna progres pembuatan pratinjau untuk dokumen besar.  
3. **Optimize for Mobile** – Buat tampilan pratinjau responsif untuk aplikasi seluler.  
4. **Monitor Performance** – Tambahkan metrik dan pemantauan untuk melacak kinerja sistem.

Siap menerapkan pembuatan pratinjau dokumen dalam aplikasi Java Anda? Mulailah dengan proof‑of‑concept kecil dan secara bertahap kembangkan fungsionalitas berdasarkan kebutuhan spesifik Anda.

## Pertanyaan yang Sering Diajukan

**Q:** Format dokumen apa yang didukung oleh generator pratinjau dokumen Java ini?  
**A:** GroupDocs.Comparison mendukung lebih dari 50 format dokumen termasuk PDF, DOCX, XLSX, PPTX, TXT, HTML, dan banyak lagi. Periksa [documentation](https://docs.groupdocs.com/comparison/java/) untuk daftar lengkap.

**Q:** Bagaimana cara menghasilkan thumbnail dokumen hanya untuk halaman pertama?  
**A:** Gunakan `previewOptions.setPageNumbers(new int[]{1})` untuk menghasilkan pratinjau hanya untuk halaman pertama. Ini sempurna untuk pembuatan thumbnail di penjelajah dokumen.

**Q:** Bisakah saya menyesuaikan format gambar output dan kualitasnya?  
**A:** Ya, Anda dapat mengonfigurasi format output melalui delegate `CreatePageStream`. Perpustakaan ini terutama mendukung format PNG, yang memberikan kualitas luar biasa untuk pratinjau dokumen.

**Q:** Bagaimana cara menangani file PDF sangat besar tanpa kehabisan memori?  
**A:** Proses dokumen besar dalam batch dengan menentukan rentang halaman, terapkan pembersihan sumber daya yang tepat dengan try‑with‑resources, dan pertimbangkan meningkatkan ukuran heap JVM dengan parameter `-Xmx`.

**Q:** Apakah ada cara untuk menghasilkan pratinjau secara asynchronous?  
**A:** Tentu saja! Gunakan `CompletableFuture.runAsync()` atau `ExecutorService` untuk menghasilkan pratinjau di thread latar belakang. Ini mencegah pemblokiran thread utama aplikasi Anda.

**Q:** Bagaimana cara memecahkan kesalahan “License not found”?  
**A:** Pastikan file lisensi Anda berada di classpath, verifikasi lisensi belum kedaluwarsa, dan periksa bahwa Anda menggunakan tipe lisensi yang tepat untuk versi GroupDocs.Comparison Anda.

**Sumber Daya Tambahan**
- **Documentation**: [GroupDocs.Comparison Java Documentation](https://docs.groupdocs.com/comparison/java/)  
- **API Reference**: [Complete API Reference](https://reference.groupdocs.com/comparison/java/)  
- **Download Latest**: [GroupDocs.Comparison Downloads](https://releases.groupdocs.com/comparison/java/)  
- **Purchase License**: [Buy GroupDocs.Comparison License](https://purchase.groupdocs.com/buy)  
- **Try Free**: [Download Free Trial](https://releases.groupdocs.com/comparison/java/)  
- **Get Support**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison)  
- **Temporary License**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Terakhir Diperbarui:** 2026-05-26  
**Diuji Dengan:** GroupDocs.Comparison 25.2  
**Penulis:** GroupDocs  

## Tutorial Terkait

- [Generasi Pratinjau Dokumen Java - Tutorial Lengkap GroupDocs.Comparison](/comparison/java/preview-generation/)
- [compare pdf java – Tutorial Perbandingan Dokumen Java – Panduan Lengkap Memuat & Membandingkan Dokumen](/comparison/java/document-loading/)
- [Panduan Penyiapan Lisensi Java GroupDocs.Comparison - Tutorial Konfigurasi Lengkap](/comparison/java/licensing-configuration/)