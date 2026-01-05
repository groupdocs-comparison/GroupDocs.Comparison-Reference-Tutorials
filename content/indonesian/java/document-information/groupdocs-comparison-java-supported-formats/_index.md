---
categories:
- Java Development
date: '2026-01-05'
description: Pelajari cara mendeteksi format Java yang didukung dan melakukan validasi
  format file Java dengan GroupDocs.Comparison. Panduan langkah demi langkah serta
  solusi praktis.
keywords: java supported file formats, GroupDocs comparison tutorial, java document
  formats list, retrieve file types java, document management system file format checking
lastmod: '2026-01-05'
linktitle: Java File Formats Detection
tags:
- java
- file-formats
- document-processing
- groupdocs
title: deteksi format yang didukung java – Panduan Deteksi Lengkap
type: docs
url: /id/java/document-information/groupdocs-comparison-java-supported-formats/
weight: 1
---

# deteksi format yang didukung java – Panduan Deteksi Lengkap

## Pendahuluan

Pernah mencoba memproses sebuah dokumen di Java hanya untuk menemui kegagalan karena pustaka Anda tidak mendukung format tertentu itu? Anda tidak sendirian. Kompatibilitas format file adalah salah satu momen “gotcha” yang dapat menggagalkan proyek lebih cepat daripada Anda dapat mengucapkan *UnsupportedFileException*.

Mengetahui **cara mendeteksi format yang didukung java** sangat penting untuk membangun sistem pemrosesan dokumen yang tangguh. Baik Anda sedang membangun platform manajemen dokumen, layanan konversi file, atau hanya perlu memvalidasi unggahan sebelum diproses, deteksi format secara programatik menyelamatkan Anda dari kejutan runtime dan pengguna yang tidak puas.

**Dalam panduan ini, Anda akan menemukan:**
- Cara mendeteksi format file yang didukung secara programatik di Java
- Implementasi praktis menggunakan GroupDocs.Comparison untuk Java
- Pola integrasi dunia nyata untuk aplikasi perusahaan
- Solusi pemecahan masalah untuk isu pengaturan umum
- Tips optimalisasi performa untuk lingkungan produksi

## Jawaban Cepat
- **Apa metode utama untuk mencantumkan format?** `FileType.getSupportedFileTypes()` mengembalikan semua tipe yang didukung.  
- **Apakah saya memerlukan lisensi untuk menggunakan API?** Ya, lisensi percobaan gratis atau lisensi sementara diperlukan untuk pengembangan.  
- **Bisakah saya menyimpan daftar format dalam cache?** Tentu—caching meningkatkan performa dan mengurangi beban.  
- **Apakah deteksi format thread‑safe?** Ya, API GroupDocs thread‑safe, tetapi cache Anda sendiri harus menangani konkurensi.  
- **Apakah daftar akan berubah dengan pembaruan pustaka?** Versi baru mungkin menambah format; selalu refresh cache setelah upgrade.

## Mengapa Deteksi Format File Penting dalam Aplikasi Java

### Biaya Tersembunyi dari Asumsi Format

Bayangkan ini: aplikasi Anda dengan percaya diri menerima unggahan file, memprosesnya melalui pipeline dokumen, dan kemudian—crash. Format file tidak didukung, tetapi Anda baru mengetahuinya setelah membuang sumber daya pemrosesan dan menciptakan pengalaman pengguna yang buruk.

**Skenario umum di mana deteksi format menyelamatkan situasi:**
- **Validasi unggahan**: Periksa kompatibilitas sebelum menyimpan file  
- **Pemrosesan batch**: Lewati file yang tidak didukung alih‑alih gagal total  
- **Integrasi API**: Berikan pesan error yang jelas tentang batasan format  
- **Perencanaan sumber daya**: Perkirakan kebutuhan pemrosesan berdasarkan tipe file  
- **Pengalaman pengguna**: Tampilkan format yang didukung di pemilih file  

### Dampak Bisnis

Deteksi format yang cerdas bukan sekadar keindahan teknis—itu langsung memengaruhi profitabilitas Anda:
- **Pengurangan tiket dukungan**: Pengguna tahu sebelumnya apa yang berfungsi  
- **Pemanfaatan sumber daya yang lebih baik**: Proses hanya file yang kompatibel  
- **Peningkatan kepuasan pengguna**: Umpan balik yang jelas tentang kompatibilitas format  
- **Siklus pengembangan lebih cepat**: Temukan masalah format lebih awal dalam pengujian  

## Prasyarat dan Persyaratan Pengaturan

Sebelum kita melompat ke implementasi, pastikan Anda memiliki semua yang diperlukan.

### Apa yang Anda Butuhkan

**Lingkungan Pengembangan:**
- Java Development Kit (JDK) 8 atau lebih tinggi  
- Maven atau Gradle untuk manajemen dependensi  
- IDE pilihan Anda (IntelliJ IDEA, Eclipse, VS Code)

**Prasyarat Pengetahuan:**
- Konsep dasar pemrograman Java  
- Familiaritas dengan struktur proyek Maven/Gradle  
- Pemahaman tentang penanganan exception di Java  

**Dependensi Pustaka:**
- GroupDocs.Comparison untuk Java (kami akan menunjukkan cara menambahkannya)

Jangan khawatir jika Anda belum familiar dengan GroupDocs secara khusus—kami akan membimbing Anda langkah demi langkah.

## Menyiapkan GroupDocs.Comparison untuk Java

### Mengapa GroupDocs.Comparison?

Di antara pustaka pemrosesan dokumen Java, GroupDocs.Comparison menonjol karena dukungan format yang komprehensif dan API yang mudah dipahami. Ia menangani segala hal mulai dari dokumen kantor umum hingga format khusus seperti gambar CAD dan file email.

### Instalasi Maven

Tambahkan repositori dan dependensi ini ke `pom.xml` Anda:

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

### Pengaturan Gradle

Untuk pengguna Gradle, tambahkan ini ke `build.gradle` Anda:

```gradle
repositories {
    maven {
        url 'https://releases.groupdocs.com/comparison/java/'
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

### Opsi Konfigurasi Lisensi

**Untuk Pengembangan:**
- **Free Trial**: Sempurna untuk pengujian dan evaluasi  
- **Temporary License**: Dapatkan akses penuh selama fase pengembangan  

**Untuk Produksi:**
- **Commercial License**: Diperlukan untuk penyebaran ke lingkungan produksi  

**Tip pro**: Mulailah dengan free trial untuk memvalidasi bahwa pustaka memenuhi kebutuhan Anda, kemudian upgrade ke lisensi sementara untuk akses pengembangan penuh.

## Panduan Implementasi: Mengambil Format File yang Didukung

### Implementasi Inti

Berikut cara mengambil semua format file yang didukung secara programatik menggunakan GroupDocs.Comparison:

```java
import com.groupdocs.comparison.result.FileType;

// Retrieve the iterable collection of supported file types
Iterable<FileType> fileTypes = FileType.getSupportedFileTypes();

// Iterate over each file type in the collection
for (FileType fileType : fileTypes) {
    // Print out the file type to demonstrate retrieval
    System.out.println(fileType);
}

// Indicate successful retrieval of supported file types
System.out.println("\nSupported file types retrieved successfully.");
```

### Memahami Kode

**Apa yang terjadi di sini:**
1. `FileType.getSupportedFileTypes()` mengembalikan koleksi iterable dari semua format yang didukung.  
2. Setiap objek `FileType` berisi metadata tentang kemampuan format.  
3. Loop sederhana menunjukkan cara mengakses informasi ini secara programatik.

**Manfaat utama pendekatan ini:**
- **Penemuan runtime** – Tidak ada daftar format hard‑coded yang harus dipelihara.  
- **Kompatibilitas versi** – Selalu mencerminkan kemampuan versi pustaka Anda.  
- **Validasi dinamis** – Bangun pemeriksaan format langsung ke dalam logika aplikasi Anda.  

### Implementasi Tingkat Lanjut dengan Penyaringan

Untuk aplikasi dunia nyata, Anda sering ingin menyaring atau mengkategorikan format:

```java
import com.groupdocs.comparison.result.FileType;
import java.util.*;

public class FormatDetector {
    
    public static Map<String, List<String>> categorizeFormats() {
        Map<String, List<String>> categories = new HashMap<>();
        categories.put("Documents", new ArrayList<>());
        categories.put("Spreadsheets", new ArrayList<>());
        categories.put("Presentations", new ArrayList<>());
        categories.put("Images", new ArrayList<>());
        categories.put("Other", new ArrayList<>());
        
        Iterable<FileType> fileTypes = FileType.getSupportedFileTypes();
        
        for (FileType fileType : fileTypes) {
            String extension = fileType.getExtension().toLowerCase();
            String category = determineCategory(extension);
            categories.get(category).add(extension);
        }
        
        return categories;
    }
    
    private static String determineCategory(String extension) {
        if (extension.matches("\\.(doc|docx|pdf|txt|rtf)")) {
            return "Documents";
        } else if (extension.matches("\\.(xls|xlsx|csv)")) {
            return "Spreadsheets";
        } else if (extension.matches("\\.(ppt|pptx)")) {
            return "Presentations";
        } else if (extension.matches("\\.(jpg|jpeg|png|gif|bmp)")) {
            return "Images";
        }
        return "Other";
    }
}
```

## Masalah Pengaturan Umum dan Solusinya

### Masalah 1: Masalah Resolusi Dependensi

**Gejala**: Maven/Gradle tidak dapat menemukan repositori atau artefak GroupDocs.

**Solusi**:
- Pastikan koneksi internet Anda memungkinkan akses ke repositori eksternal.  
- Periksa bahwa URL repositori persis seperti yang ditentukan.  
- Untuk lingkungan korporat, Anda mungkin perlu menambahkan repositori ke Nexus/Artifactory Anda.

**Perbaikan cepat**:

```xml
<!-- Add to Maven settings.xml if repository access is restricted -->
<mirrors>
    <mirror>
        <id>central-proxy</id>
        <mirrorOf>*</mirrorOf>
        <url>http://your-corporate-nexus/repository/maven-public/</url>
    </mirror>
</mirrors>
```

### Masalah 2: Kesalahan Validasi Lisensi

**Gejala**: Aplikasi berjalan tetapi menampilkan peringatan atau batasan lisensi.

**Solusi**:
- Pastikan file lisensi berada di classpath Anda.  
- Verifikasi lisensi belum kedaluwarsa.  
- Periksa bahwa lisensi mencakup lingkungan penyebaran Anda (dev/staging/prod).

**Contoh kode untuk memuat lisensi**:

```java
// Load license at application startup
License license = new License();
license.setLicense("path/to/GroupDocs.Comparison.lic");
```

### Masalah 3: ClassNotFoundException saat Runtime

**Gejala**: Kode berhasil dikompilasi tetapi gagal saat runtime dengan error kelas yang hilang.

**Penyebab umum**:
- Konflik dependensi dengan pustaka lain.  
- Dependensi transitif yang hilang.  
- Ketidakcocokan versi Java.

**Langkah debugging**:
1. Periksa pohon dependensi Anda: `mvn dependency:tree`.  
2. Verifikasi kompatibilitas versi Java.  
3. Kecualikan dependensi transitif yang konflik bila diperlukan.

### Masalah 4: Masalah Performa dengan Daftar Format Besar

**Gejala**: Pemanggilan `getSupportedFileTypes()` memakan waktu lebih lama dari yang diharapkan.

**Solusi**: Cache hasilnya karena format yang didukung tidak berubah selama runtime:

```java
public class FormatCache {
    private static volatile List<FileType> cachedFormats;
    
    public static List<FileType> getSupportedFormats() {
        if (cachedFormats == null) {
            synchronized (FormatCache.class) {
                if (cachedFormats == null) {
                    cachedFormats = new ArrayList<>();
                    FileType.getSupportedFileTypes().forEach(cachedFormats::add);
                }
            }
        }
        return cachedFormats;
    }
}
```

## Pola Integrasi untuk Aplikasi Dunia Nyata

### Pola 1: Validasi Pra‑Unggah

Ideal untuk aplikasi web yang ingin memvalidasi file sebelum diunggah:

```java
public class FileUploadValidator {
    
    private static final Set<String> SUPPORTED_EXTENSIONS = 
        getSupportedExtensions();
    
    public boolean isSupported(String filename) {
        String extension = getExtension(filename).toLowerCase();
        return SUPPORTED_EXTENSIONS.contains(extension);
    }
    
    private static Set<String> getSupportedExtensions() {
        Set<String> extensions = new HashSet<>();
        FileType.getSupportedFileTypes().forEach(
            type -> extensions.add(type.getExtension().toLowerCase())
        );
        return extensions;
    }
    
    private String getExtension(String filename) {
        int lastDot = filename.lastIndexOf('.');
        return lastDot > 0 ? filename.substring(lastDot) : "";
    }
}
```

### Pola 2: Pemrosesan Batch dengan Penyaringan Format

Untuk aplikasi yang memproses banyak file dan perlu menangani format yang tidak didukung secara elegan:

```java
public class BatchProcessor {
    
    public ProcessingResult processBatch(List<File> files) {
        Map<String, List<File>> categorized = categorizeFiles(files);
        
        ProcessingResult result = new ProcessingResult();
        result.setProcessedFiles(processSupported(categorized.get("supported")));
        result.setSkippedFiles(categorized.get("unsupported"));
        
        return result;
    }
    
    private Map<String, List<File>> categorizeFiles(List<File> files) {
        Set<String> supportedExts = getSupportedExtensions();
        
        return files.stream().collect(
            Collectors.groupingBy(file -> 
                supportedExts.contains(getExtension(file.getName())) 
                    ? "supported" : "unsupported"
            )
        );
    }
}
```

### Pola 3: API REST Informasi Format

Ekspose kemampuan format melalui API Anda:

```java
@RestController
@RequestMapping("/api/formats")
public class FormatController {
    
    @GetMapping("/supported")
    public ResponseEntity<List<FormatInfo>> getSupportedFormats() {
        List<FormatInfo> formats = new ArrayList<>();
        
        FileType.getSupportedFileTypes().forEach(type -> {
            formats.add(new FormatInfo(
                type.getExtension(),
                type.getFileFormat(),
                determineDescription(type)
            ));
        });
        
        return ResponseEntity.ok(formats);
    }
    
    @GetMapping("/check/{extension}")
    public ResponseEntity<SupportInfo> checkFormat(@PathVariable String extension) {
        boolean supported = isFormatSupported(extension);
        return ResponseEntity.ok(new SupportInfo(extension, supported));
    }
}
```

## Praktik Terbaik untuk Penggunaan Produksi

### Manajemen Memori

**Cache dengan bijak**: Daftar format tidak berubah selama runtime, jadi cachelah mereka:

```java
// Good: Initialize once, use many times
private static final List<FileType> SUPPORTED_FORMATS = 
    StreamSupport.stream(FileType.getSupportedFileTypes().spliterator(), false)
                 .collect(Collectors.toList());

// Avoid: Calling getSupportedFileTypes() repeatedly
```

### Penanganan Error

**Degradasi yang elegan**: Selalu sediakan fallback ketika deteksi format gagal:

```java
public boolean isFormatSupported(String filename) {
    try {
        String extension = getExtension(filename);
        return SUPPORTED_FORMATS.stream()
            .anyMatch(type -> type.getExtension().equalsIgnoreCase(extension));
    } catch (Exception e) {
        // Log the error but don't fail the operation
        logger.warn("Format check failed for: " + filename, e);
        return false; // Conservative approach
    }
}
```

### Optimasi Performa

**Inisialisasi lazy**: Jangan muat informasi format sampai diperlukan:

```java
public class LazyFormatChecker {
    private volatile boolean initialized = false;
    private Set<String> supportedExtensions;
    
    public boolean isSupported(String extension) {
        ensureInitialized();
        return supportedExtensions.contains(extension.toLowerCase());
    }
    
    private void ensureInitialized() {
        if (!initialized) {
            synchronized (this) {
                if (!initialized) {
                    loadSupportedExtensions();
                    initialized = true;
                }
            }
        }
    }
}
```

### Manajemen Konfigurasi

**Eksternalisasi pembatasan format**: Gunakan file konfigurasi untuk kebijakan format:

```yaml
# application.yml
document-processing:
  allowed-formats:
    - pdf
    - docx
    - xlsx
  max-file-size: 10MB
  validation-mode: strict
```

## Kasus Penggunaan Lanjutan dan Aplikasi

### Manajemen Dokumen Perusahaan

**Skenario**: Organisasi besar perlu memvalidasi ribuan dokumen di berbagai departemen dengan persyaratan format yang berbeda.

**Pendekatan implementasi**:
- Daftar putih format khusus departemen  
- Pelaporan format otomatis dan pemeriksaan kepatuhan  
- Integrasi dengan sistem manajemen siklus hidup dokumen  

### Integrasi Penyimpanan Cloud

**Skenario**: Aplikasi SaaS yang menyinkronkan file dari berbagai penyedia penyimpanan cloud.

**Pertimbangan utama**:
- Kompatibilitas format antar sistem penyimpanan yang berbeda  
- Optimasi bandwidth dengan menyaring format yang tidak didukung lebih awal  
- Notifikasi pengguna tentang file yang tidak didukung selama sinkronisasi  

### Sistem Workflow Otomatis

**Skenario**: Otomatisasi proses bisnis yang mengarahkan dokumen berdasarkan format dan konten.

**Manfaat implementasi**:
- Routing cerdas berdasarkan kemampuan format  
- Konversi format otomatis bila memungkinkan  
- Optimasi workflow melalui pemrosesan yang sadar format  

## Pertimbangan Performa dan Optimasi

### Optimasi Penggunaan Memori

**Tantangan**: Memuat semua informasi format yang didukung dapat mengonsumsi memori yang tidak perlu pada lingkungan dengan sumber daya terbatas.

**Solusi**:
1. **Lazy loading** – Muat informasi format hanya saat dibutuhkan.  
2. **Selective caching** – Cache hanya format yang relevan dengan kasus penggunaan Anda.  
3. **Weak references** – Izinkan garbage collection saat memori ketat.  

### Tips Performa CPU

**Pemeriksaan format yang efisien**:
- Gunakan `HashSet` untuk lookup O(1) alih‑alih pencarian linear.  
- Pre‑compile pola regex untuk validasi format.  
- Pertimbangkan penggunaan parallel streams untuk operasi batch besar.

```java
// Efficient format validation
private static final Set<String> SUPPORTED_EXTENSIONS = 
    Collections.unmodifiableSet(loadSupportedExtensions());

public boolean isSupported(String extension) {
    return SUPPORTED_EXTENSIONS.contains(extension.toLowerCase());
}
```

### Pertimbangan Skalabilitas

**Untuk aplikasi throughput tinggi**:
- Inisialisasi informasi format saat aplikasi mulai.  
- Gunakan connection pooling bila berintegrasi dengan layanan deteksi format eksternal.  
- Pertimbangkan cache terdistribusi (Redis, Hazelcast) untuk lingkungan cluster.  

## Pemecahan Masalah Isu Runtime Umum

### Masalah: Hasil Deteksi Format Tidak Konsisten

**Gejala**: Ekstensi file yang sama kadang‑kadang mengembalikan status dukungan yang berbeda.

**Penyebab utama**:
- Perbedaan versi antara instance pustaka.  
- Batasan lisensi yang memengaruhi format yang tersedia.  
- Konflik classpath dengan pustaka pemrosesan dokumen lain.

**Pendekatan debugging**:
1. Log versi pustaka yang tepat digunakan.  
2. Verifikasi status dan cakupan lisensi.  
3. Periksa adanya JAR duplikat di classpath.  

### Masalah: Penurunan Performa Seiring Waktu

**Gejala**: Deteksi format menjadi lebih lambat seiring aplikasi berjalan lama.

**Penyebab umum**:
- Memory leak pada mekanisme caching format.  
- Cache internal yang terus tumbuh tanpa pembersihan.  
- Kontensi sumber daya dengan komponen aplikasi lain.

**Solusi**:
- Terapkan kebijakan eviksi cache yang tepat.  
- Pantau pola penggunaan memori.  
- Gunakan alat profiling untuk mengidentifikasi bottleneck.  

### Masalah: Deteksi Format Gagal Tanpa Error

**Gejala**: Tidak ada exception yang dilempar, tetapi dukungan format tampak tidak lengkap.

**Langkah investigasi**:
1. Aktifkan debug logging untuk komponen GroupDocs.  
2. Pastikan inisialisasi pustaka selesai dengan sukses.  
3. Periksa batasan lisensi pada format tertentu.  

## Kesimpulan dan Langkah Selanjutnya

Memahami dan mengimplementasikan **deteksi format yang didukung java** bukan sekadar menulis kode—itu tentang membangun aplikasi yang tahan banting dan ramah pengguna yang mampu menangani lanskap format file dunia nyata dengan elegan.

**Poin penting dari panduan ini**:
- **Deteksi format programatik** mencegah kejutan runtime dan meningkatkan pengalaman pengguna.  
- **Pengaturan dan konfigurasi yang tepat** menghemat jam debugging pada isu umum.  
- **Caching pintar dan optimasi performa** memastikan aplikasi Anda dapat diskalakan secara efektif.  
- **Penanganan error yang kuat** menjaga aplikasi tetap berjalan mulus meski terjadi masalah.  

**Langkah selanjutnya untuk Anda**:
1. Implementasikan deteksi format dasar di proyek Anda menggunakan contoh kode inti.  
2. Tambahkan penanganan error yang komprehensif untuk menangkap kasus tepi secara elegan.  
3. Optimalkan untuk kasus penggunaan spesifik Anda dengan pola caching yang dibahas.  
4. Pilih pola integrasi (validasi pra‑unggah, pemrosesan batch, atau API REST) yang sesuai dengan arsitektur Anda.  

Siap melangkah lebih jauh? Jelajahi fitur lanjutan GroupDocs.Comparison seperti opsi perbandingan spesifik format, ekstraksi metadata, dan kemampuan pemrosesan batch untuk membangun alur kerja pemrosesan dokumen yang lebih kuat.

## Pertanyaan yang Sering Diajukan

**T: Apa yang terjadi jika saya mencoba memproses format file yang tidak didukung?**  
J: GroupDocs.Comparison akan melempar exception. Pra‑validasi menggunakan `getSupportedFileTypes()` memungkinkan Anda menangkap masalah kompatibilitas sebelum proses dimulai.

**T: Apakah daftar format yang didukung berubah antar versi pustaka?**  
J: Ya, versi yang lebih baru biasanya menambah dukungan untuk format tambahan. Selalu periksa catatan rilis saat melakukan upgrade, dan pertimbangkan untuk meng‑cache ulang daftar format yang didukung setelah pembaruan.

**T: Bisakah saya memperluas pustaka untuk mendukung format tambahan?**  
J: GroupDocs.Comparison memiliki set format yang tetap. Jika Anda memerlukan format ekstra, pertimbangkan menggunakannya bersama pustaka khusus lain atau hubungi GroupDocs untuk dukungan format kustom.

**T: Berapa banyak memori yang digunakan deteksi format?**  
J: Jejak memori minimal—biasanya hanya beberapa KB untuk metadata format. Pertimbangan yang lebih besar adalah bagaimana Anda meng‑cache dan menggunakan informasi ini dalam aplikasi Anda.

**T: Apakah deteksi format thread‑safe?**  
J: Ya, `FileType.getSupportedFileTypes()` thread‑safe. Namun, jika Anda mengimplementasikan mekanisme caching sendiri, pastikan menangani akses bersamaan dengan benar.

**T: Apa dampak performa dari memeriksa dukungan format?**  
J: Dengan caching yang tepat, pemeriksaan format pada dasarnya adalah operasi lookup O(1). Panggilan awal ke `getSupportedFileTypes()` memiliki overhead tertentu, tetapi pemeriksaan selanjutnya sangat cepat.

## Sumber Daya Tambahan

**Dokumentasi:**  
- [GroupDocs.Comparison for Java Documentation](https://docs.groupdocs.com/comparison/java/)  
- [API Reference Guide](https://reference.groupdocs.com/comparison/java/)

**Panduan Memulai:**  
- [Download and Installation Guide](https://releases.groupdocs.com/comparison/java/)  
- [Free Trial Access](https://releases.groupdocs.com/comparison/java/)  
- [Temporary License for Development](https://purchase.groupdocs.com/temporary-license/)

**Komunitas dan Dukungan:**  
- [Developer Support Forum](https://forum.groupdocs.com/c/comparison)  
- [Purchase and Licensing Information](https://purchase.groupdocs.com/buy)

---

**Terakhir Diperbarui:** 2026-01-05  
**Diuji Dengan:** GroupDocs.Comparison 25.2 untuk Java  
**Penulis:** GroupDocs  

---