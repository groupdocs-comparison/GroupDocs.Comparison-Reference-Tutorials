---
categories:
- C# Development
date: '2026-05-31'
description: Pelajari cara membandingkan dokumen di C# menggunakan GroupDocs.Comparison
  .NET. Panduan langkah demi langkah dengan penyiapan, potongan kode, tips kinerja,
  dan contoh penggunaan dunia nyata.
keywords:
- how to compare documents
- compare excel files c#
- compare pdf documents c#
- document comparison best practices
lastmod: '2026-05-31'
linktitle: Tutorial Perbandingan Dokumen C#
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare documents in C# using GroupDocs.Comparison .NET.
    Step‑by‑step guide with setup, code snippets, performance tips, and real‑world
    use cases.
  headline: 'How to Compare Documents in C#: Master GroupDocs.Comparison .NET'
  type: TechArticle
- description: Learn how to compare documents in C# using GroupDocs.Comparison .NET.
    Step‑by‑step guide with setup, code snippets, performance tips, and real‑world
    use cases.
  name: 'How to Compare Documents in C#: Master GroupDocs.Comparison .NET'
  steps:
  - name: Right‑click on your project in Solution Explorer
    text: Right‑click on your project in Solution Explorer
  - name: Select “Manage NuGet Packages”
    text: Select “Manage NuGet Packages”
  - name: Search for “GroupDocs.Comparison”
    text: Search for “GroupDocs.Comparison”
  - name: Click **Install**
    text: Click **Install**
  - name: '**Document Parsing** – Reads the internal structure of both files.'
    text: '**Document Parsing** – Reads the internal structure of both files.'
  - name: '**Content Analysis** – Compares text, formatting, images, tables, and other
      elements.'
    text: '**Content Analysis** – Compares text, formatting, images, tables, and other
      elements.'
  - name: '**Difference Detection** – Identifies additions, deletions, and modifications.'
    text: '**Difference Detection** – Identifies additions, deletions, and modifications.'
  - name: '**Result Generation** – Creates a new document with changes highlighted.'
    text: '**Result Generation** – Creates a new document with changes highlighted.'
  - name: '**Batch Processing** – Reuse the output directory to minimize I/O operations
      when comparing many file pairs.'
    text: '**Batch Processing** – Reuse the output directory to minimize I/O operations
      when comparing many file pairs.'
  - name: '**Asynchronous Operations** – Use `async/await` patterns for UI applications
      to prevent freezing.'
    text: '**Asynchronous Operations** – Use `async/await` patterns for UI applications
      to prevent freezing.'
  type: HowTo
- questions:
  - answer: GroupDocs.Comparison works best when both files share the same format.
      Cross‑format comparison is possible but may lose fidelity; converting one file
      to match the other first yields the most accurate results.
    question: Can I compare documents of different formats (like Word vs PDF)?
  - answer: 'The library supports password‑protected files. Provide the password when
      initializing the `Comparer`:'
    question: How do I handle password‑protected documents?
  - answer: There’s no hard limit, but practical limits depend on available RAM. Files
      up to **100 MB** typically process without issues on a 4 GB RAM server. For
      larger files, consider chunked processing or a server with more memory.
    question: What’s the largest file size GroupDocs.Comparison can handle?
  - answer: Absolutely. The `CompareOptions` class lets you customize the appearance
      of the diff output. Use the `CompareOptions` class to set highlight colors,
      change indicators, and output formatting. The API offers granular control over
      visual diff appearance.
    question: Can I customize how changes are displayed in the output?
  - answer: Each `Comparer` instance should be used by a single thread, but you can
      create multiple instances for concurrent operations. In web scenarios, instantiate
      a new `Comparer` per request.
    question: Is GroupDocs.Comparison thread‑safe for multi‑user applications?
  type: FAQPage
tags:
- document-comparison
- groupdocs
- dotnet
- file-processing
title: 'Cara Membandingkan Dokumen di C#: Panduan Master GroupDocs.Comparison .NET'
type: docs
url: /id/net/basic-comparison/groupdocs-comparison-net-document-comparison-csharp/
weight: 1
---

# Cara Membandingkan Dokumen di C#: Menguasai GroupDocs.Comparison .NET

Pernahkah Anda secara manual membandingkan dua dokumen Word, mencoba menemukan setiap perubahan kecil? Jika Anda seorang pengembang yang bekerja dengan aplikasi yang banyak mengolah dokumen, Anda tahu betapa melelahkannya hal itu. **Mempelajari cara membandingkan dokumen** secara programatik menghemat waktu berjam‑jam, menghilangkan kesalahan manusia, dan memberikan konsistensi pada alur kerja apa pun yang menangani kontrak, spesifikasi, atau laporan.

Perbandingan dokumen bukan sekadar kemudahan—itu adalah fondasi akurasi, efisiensi, dan ketenangan dalam teknologi hukum, penerbitan teknis, dan platform penyuntingan kolaboratif. Dalam tutorial komprehensif ini kami akan membahas semua yang perlu Anda ketahui untuk mengimplementasikan perbandingan dokumen yang kuat dan berperforma tinggi menggunakan GroupDocs.Comparison untuk .NET.

**Apa yang Akan Anda Kuasai pada Akhirnya:**
- Penyiapan dan konfigurasi lengkap GroupDocs.Comparison .NET
- Memuat dan membandingkan dokumen menggunakan jalur file (skenario paling umum)
- Menangani hasil perbandingan dan menyesuaikan output
- Pola implementasi dunia nyata dan praktik terbaik
- Memecahkan masalah umum yang sebenarnya akan Anda temui

Mari kita selami transformasi alur kerja manajemen dokumen Anda.

## Jawaban Cepat
- **Apa cara paling sederhana untuk membandingkan dua file Word?** Muat kedua file dengan `Comparer` dan panggil `Compare()`.
- **Format apa yang didukung oleh GroupDocs.Comparison?** Lebih dari 50 format input dan output, termasuk DOCX, PDF, XLSX, PPTX, dan tipe gambar umum.
- **Apakah saya memerlukan lisensi berbayar untuk pengembangan?** Tidak—versi percobaan gratis dengan fungsionalitas penuh dan watermark tersedia.
- **Seberapa cepat perbandingan biasanya?** 1‑3 detik untuk dokumen standar 10‑halaman; kurang dari 5 detik untuk file 100‑halaman pada server tipikal.
- **Bisakah saya menjalankan perbandingan di Linux?** Ya—GroupDocs.Comparison bersifat lintas‑platform dan bekerja di Windows, Linux, serta macOS.

## Apa itu “cara membandingkan dokumen”?
**Cara membandingkan dokumen** mengacu pada proses otomatis mendeteksi penambahan, penghapusan, dan modifikasi antara dua versi sebuah file. GroupDocs.Comparison melakukan analisis struktural mendalam—teks, format, gambar, tabel, bahkan perubahan yang dilacak—sehingga Anda mendapatkan perbedaan visual yang tepat tanpa inspeksi manual.

## Mengapa Menggunakan GroupDocs.Comparison untuk Perbandingan Dokumen C#?
GroupDocs.Comparison memproses **lebih dari 50 format file** dan dapat menangani **dokumen ratusan halaman** tanpa memuat seluruh file ke memori, berkat arsitektur streaming-nya. Benchmark menunjukkan pengurangan penggunaan memori sebesar 30 % dibandingkan pustaka pesaing saat memproses PDF 200‑halaman, dan waktu penyelesaian tipikal 2 detik untuk file Word 100‑halaman pada VM dengan 2 core CPU.

## Sebelum Anda Memulai: Apa yang Anda Butuhkan

Menyiapkan perbandingan dokumen di C# cukup sederhana, tetapi pastikan Anda memiliki semua yang diperlukan untuk menghindari hambatan yang menjengkelkan nanti.

### Persyaratan Esensial

**Development Environment:**
- .NET Core 3.1+ atau .NET Framework 4.6.1+ (sebagian besar aplikasi modern menggunakan .NET Core)
- Visual Studio 2019+ atau Visual Studio Code (VS Community berfungsi dengan sempurna)
- Pengetahuan dasar C# (jika Anda dapat bekerja dengan kelas dan metode, Anda sudah cukup)

**GroupDocs.Comparison Library:**
- Versi 25.4.0 (stabil terbaru pada saat penulisan ini)
- Kompatibel dengan Windows, Linux, dan macOS
- Mendukung **lebih dari 50 format input dan output** secara default

**Test Documents:**  
Anda akan membutuhkan beberapa dokumen contoh untuk bereksperimen. Dokumen Word (.docx) sangat cocok untuk pengujian, tetapi pustaka ini juga menangani PDF, file Excel, presentasi PowerPoint, dan banyak lainnya.

### Pemeriksaan Lingkungan Cepat

Sebelum menginstal apa pun, verifikasi versi .NET Anda dengan menjalankan perintah berikut di command prompt:

```bash
dotnet --version
```

Jika Anda melihat nomor versi seperti 6.0.x atau 7.0.x, Anda siap. Jika tidak, unduh .NET SDK terbaru dari situs web Microsoft.

## Menyiapkan GroupDocs.Comparison untuk .NET (Cara Mudah)

Menginstal GroupDocs.Comparison mungkin merupakan bagian termudah dari seluruh tutorial ini. Anda memiliki dua opsi, dan keduanya memakan waktu kurang dari satu menit.

### Opsi 1: Menggunakan NuGet Package Manager (Disarankan)

Buka proyek Anda di Visual Studio, lalu:
1. Klik kanan pada proyek Anda di Solution Explorer  
2. Pilih “Manage NuGet Packages”  
3. Cari “GroupDocs.Comparison”  
4. Klik **Install**

Atau gunakan Package Manager Console:

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

### Opsi 2: Menggunakan .NET CLI

Jika Anda lebih suka command line (terutama berguna untuk pipeline CI/CD):

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

### Menangani Lisensi (Jangan Lewatkan Ini)

Berikut hal yang sering membuat banyak pengembang kebingungan: GroupDocs.Comparison tidak sepenuhnya gratis, tetapi mereka memberikan opsi evaluasi yang murah hati.

**Untuk Pengembangan dan Pengujian:**
- Versi percobaan gratis dengan fungsionalitas penuh
- Watermark pada output (sepenuhnya baik untuk pengujian)
- Tidak ada batas waktu pada percobaan

**Untuk Produksi:**
- Lisensi komersial diperlukan
- Lisensi sementara tersedia untuk evaluasi yang diperpanjang
- Diskon volume untuk aplikasi perusahaan

Tips profesional: Mulailah dengan percobaan gratis. Anda dapat membangun dan menguji seluruh implementasi sebelum memutuskan lisensi. Kebanyakan pengembang menemukan pustaka ini sangat berguna sehingga biaya lisensi menjadi keputusan yang mudah.

### Verifikasi Pengaturan Dasar

Pastikan semuanya berfungsi dengan tes singkat. Tambahkan pernyataan using berikut ke file C# Anda:

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
```

Jika Visual Studio tidak mengeluh tentang referensi yang hilang, Anda siap melanjutkan.

## Cara Membandingkan Dokumen Menggunakan GroupDocs.Comparison

GroupDocs.Comparison melakukan diff dokumen melalui kelas `Comparer`. Kelas `Comparer` mengatur proses perbandingan, sementara metode `Compare()`‑nya menjalankan analisis dan menghasilkan dokumen baru yang menyoroti semua perubahan. Muat file sumber Anda, tambahkan satu atau lebih file target, dan panggil `Compare()` untuk mendapatkan hasilnya.

Kelas `Comparer` adalah komponen inti yang mengatur proses perbandingan. Ia membaca kedua file sumber dan target, menganalisis struktur mereka, dan menghasilkan dokumen diff.

### Panduan Langkah‑per‑Langkah

**Langkah 1: Tentukan Jalur File Anda**  
Gunakan `Path.Combine()` untuk kompatibilitas lintas‑platform; secara otomatis menangani pemisah jalur dengan benar baik di Windows (`\`) maupun Linux/macOS (`/`). Selalu gunakan ini alih-alih menuliskan jalur secara manual dengan tanda miring.

```csharp
string YOUR_DOCUMENT_DIRECTORY = @"C:\Documents\TestFiles";
string sourcePath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "source.docx");
string targetPath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "target.docx");
```

**Langkah 2: Inisialisasi Comparer**  
Pernyataan `using` memastikan semua sumber daya dibuang setelah selesai, mencegah kebocoran memori—terutama penting saat memproses banyak dokumen dalam pekerjaan batch.

```csharp
using (Comparer comparer = new Comparer(sourcePath))
```

**Langkah 3: Tambahkan Dokumen Target**  
GroupDocs.Comparison memungkinkan Anda membandingkan satu sumber dengan beberapa target. Panggil `Add()` untuk setiap file tambahan yang ingin Anda bandingkan dengan sumber.

```csharp
comparer.Add(targetPath);
```

**Langkah 4: Jalankan dan Simpan**  
`Compare()` melakukan pekerjaan berat. Ia menganalisis kedua dokumen, mengidentifikasi perbedaan, dan membuat dokumen baru dengan perubahan yang disorot.

```csharp
string outputFileName = Path.Combine(YOUR_OUTPUT_DIRECTORY, "result.docx");
comparer.Compare(outputFileName);
```

### Apa yang Terjadi Selama Perbandingan?

Saat Anda memanggil `Compare()`, GroupDocs.Comparison melakukan beberapa operasi:

1. **Parsing Dokumen** – Membaca struktur internal kedua file.  
2. **Analisis Konten** – Membandingkan teks, format, gambar, tabel, dan elemen lainnya.  
3. **Deteksi Perbedaan** – Mengidentifikasi penambahan, penghapusan, dan modifikasi.  
4. **Pembuatan Hasil** – Membuat dokumen baru dengan perubahan yang disorot.

Seluruh proses biasanya memakan **1‑3 detik untuk dokumen bisnis standar**; file besar (100 + halaman) dapat memakan hingga **5 detik** pada server yang sederhana.

## Aplikasi Praktis: Di Mana Perbandingan Dokumen Bersinar

Memahami implementasi teknis sangat baik, tetapi mari bahas di mana hal ini benar-benar menjadi berharga dalam aplikasi nyata.

### Sistem Review Dokumen Hukum

Firma hukum dan departemen hukum terus-menerus menangani revisi kontrak. Alih-alih meninjau setiap perubahan klausul secara manual, Anda dapat menghasilkan dokumen diff yang dengan jelas menunjukkan apa yang ditambahkan, dihapus, atau diubah, secara dramatis mempercepat proses review.

```csharp
// Compare contract versions automatically
string originalContract = @"contracts\initial-agreement.docx";
string revisedContract = @"contracts\revised-agreement.docx";
string comparisonResult = @"output\contract-changes.docx";

using (Comparer comparer = new Comparer(originalContract))
{
    comparer.Add(revisedContract);
    comparer.Compare(comparisonResult);
}
```

### Manajemen Dokumentasi Teknis

Jika Anda mengelola dokumentasi API, manual pengguna, atau spesifikasi, perbandingan membantu Anda:
- Melacak perubahan antara versi dokumentasi
- Mengidentifikasi kapan screenshot atau contoh kode perlu diperbarui
- Memastikan konsistensi di berbagai format dokumen

### Pembuatan Konten Kolaboratif

Ketika banyak penulis bekerja pada whitepaper, laporan, atau proposal yang sama, perbandingan membantu Anda:
- Menggabungkan kontribusi individu
- Mendeteksi edit yang bertentangan
- Mempertahankan jejak audit perubahan yang jelas

### Jaminan Kualitas dalam Pembuatan Dokumen

Untuk aplikasi yang menghasilkan faktur, kontrak, atau laporan secara otomatis, perbandingan berfungsi sebagai gerbang kualitas:
- Memverifikasi dokumen yang dihasilkan terhadap template master
- Menangkap kesalahan pengisian data sebelum sampai ke pelanggan
- Memastikan kepatuhan format di semua tipe output

## Pertimbangan Kinerja: Membuatnya Cepat dan Efisien

Perbandingan dokumen dapat memakan banyak sumber daya, terutama dengan file besar. Berikut cara menjaga aplikasi Anda tetap responsif dan efisien.

### Praktik Terbaik Manajemen Memori

**Selalu Gunakan Pernyataan `using`**  
```csharp
// Good: Resources are automatically disposed
using (Comparer comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath);
} // Comparer is disposed here automatically

// Avoid: Manual disposal required (and often forgotten)
Comparer comparer = new Comparer(sourcePath);
comparer.Add(targetPath);
comparer.Compare(outputPath);
comparer.Dispose(); // Easy to forget, causes memory leaks
```

**Pantau Pemrosesan File Besar**  
Untuk dokumen over **50 MB** atau **500 + pages**, pertimbangkan:
- Menjalankan perbandingan pada jam off‑peak
- Menerapkan callback progres untuk umpan balik pengguna
- Membagi file sangat besar menjadi bagian logis bila memungkinkan

### Mengoptimalkan untuk Berbagai Jenis File

- **Dokumen dengan Teks Dominan (Word, PDF)** – Umumnya cepat, **1‑5 detik** untuk file bisnis tipikal.  
- **Presentasi dengan Gambar Dominan** – Lebih lambat karena algoritma diff visual, **10‑30 detik** untuk deck besar.  
- **Spreadsheet dengan Rumus Kompleks** – Kinerja bervariasi tergantung kompleksitas perhitungan; pertahankan rumus sederhana untuk kecepatan optimal.

### Tips Kinerja Dunia Nyata

1. **Pemrosesan Batch** – Gunakan kembali direktori output untuk meminimalkan operasi I/O saat membandingkan banyak pasangan file.  
2. **Operasi Asinkron** – Gunakan pola `async/await` untuk aplikasi UI agar tidak membeku.  
3. **Caching** – Simpan hasil perbandingan untuk pasangan dokumen yang identik guna menghindari pemrosesan ulang.

## Pemecahan Masalah Isu Umum (Hemat Waktu Anda)

Setiap pengembang menghadapi masalah ini. Berikut solusi yang benar‑benar Anda butuhkan.

### “File Not Found” Errors

**Masalah** – Isu paling umum saat memulai.  
```csharp
// This will fail if the path is wrong
using (Comparer comparer = new Comparer(@"C:\NonExistent\file.docx"))
```

**Solusi** – Verifikasi keberadaan file sebelum memanggil comparer:  
```csharp
if (!File.Exists(sourcePath))
{
    Console.WriteLine($"Source file not found: {sourcePath}");
    return;
}

if (!File.Exists(targetPath))
{
    Console.WriteLine($"Target file not found: {targetPath}");
    return;
}
```

### Masalah Izin dan Akses

**Masalah** – Aplikasi tidak dapat membaca atau menulis file.  

**Solusi**:
- Jalankan aplikasi dengan izin yang cukup.
- Pastikan file tidak terkunci oleh program lain (terutama Excel).
- Verifikasi izin menulis untuk direktori output.

### Format File Tidak Didukung

**Masalah** – Tidak semua tipe file didukung secara setara.

**Sepenuhnya Didukung** – Microsoft Office (Word, Excel, PowerPoint), PDF, teks biasa, sebagian besar format gambar.  
**Dukungan Terbatas** – Gambar CAD kompleks, format proprietari khusus.

### Masalah Memori dengan File Besar

**Masalah** – Crash atau perlambatan dengan dokumen sangat besar.

**Solusi**:
- Tingkatkan batas memori aplikasi.
- Proses file besar secara bertahap.
- Gunakan perbandingan streaming untuk file sangat besar (tersedia di edisi enterprise).

## Pola Penggunaan Lanjutan

Setelah Anda nyaman dengan perbandingan dasar, pola-pola ini akan membuat implementasi Anda lebih kuat.

### Membandingkan Beberapa Dokumen

```csharp
using (Comparer comparer = new Comparer(sourceDocument))
{
    // Add multiple targets
    comparer.Add(document1);
    comparer.Add(document2);
    comparer.Add(document3);
    
    // Single comparison shows differences from all targets
    comparer.Compare(outputPath);
}
```

### Praktik Terbaik Penanganan Kesalahan

```csharp
try
{
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        comparer.Compare(outputPath);
    }
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"File not found: {ex.FileName}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Access denied: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Comparison failed: {ex.Message}");
}
```

### Integrasi dengan File Watchers

Untuk perbandingan otomatis saat file berubah:  
```csharp
FileSystemWatcher watcher = new FileSystemWatcher(@"C:\Documents\Watch");
watcher.Changed += (sender, e) => {
    // Trigger comparison when files change
    CompareDocuments(e.FullPath, referenceDocument);
};
```

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya membandingkan dokumen dengan format berbeda (seperti Word vs PDF)?**  
A: GroupDocs.Comparison paling baik bekerja ketika kedua file memiliki format yang sama. Perbandingan lintas format memungkinkan tetapi dapat mengurangi akurasi; mengonversi satu file agar cocok dengan yang lain terlebih dahulu menghasilkan hasil paling akurat.

**Q: Bagaimana cara menangani dokumen yang dilindungi password?**  
A: Pustaka mendukung file yang dilindungi password. Berikan password saat menginisialisasi `Comparer`:

```csharp
LoadOptions loadOptions = new LoadOptions() { Password = "your-password" };
using (Comparer comparer = new Comparer(sourcePath, loadOptions))
```

**Q: Berapa ukuran file terbesar yang dapat ditangani oleh GroupDocs.Comparison?**  
A: Tidak ada batas keras, tetapi batas praktis tergantung pada RAM yang tersedia. File hingga **100 MB** biasanya diproses tanpa masalah pada server dengan RAM 4 GB. Untuk file yang lebih besar, pertimbangkan pemrosesan bertahap atau server dengan memori lebih besar.

**Q: Bisakah saya menyesuaikan cara perubahan ditampilkan dalam output?**  
A: Tentu saja. Kelas `CompareOptions` memungkinkan Anda menyesuaikan tampilan output diff. Gunakan kelas `CompareOptions` untuk mengatur warna sorotan, indikator perubahan, dan format output. API menyediakan kontrol granular atas tampilan visual diff.

**Q: Apakah GroupDocs.Comparison thread‑safe untuk aplikasi multi‑pengguna?**  
A: Setiap instance `Comparer` harus digunakan oleh satu thread, tetapi Anda dapat membuat beberapa instance untuk operasi bersamaan. Dalam skenario web, buat instance `Comparer` baru per permintaan.

**Q: Seberapa akurat perbandingan untuk dokumen kompleks dengan tabel dan gambar?**  
A: Sangat akurat. Mesin menganalisis struktur dokumen—bukan hanya teks biasa—sehingga tabel, gambar, format, dan bahkan perubahan yang dilacak terdeteksi dan disorot dengan benar.

**Q: Bisakah saya mengintegrasikan ini dengan layanan penyimpanan cloud seperti Azure Blob atau AWS S3?**  
A: Ya, tetapi Anda harus mengunduh file secara lokal terlebih dahulu. GroupDocs.Comparison bekerja dengan jalur file lokal, jadi ambil blob, jalankan perbandingan, kemudian unggah hasilnya kembali ke cloud.

## Sumber Daya Penting

- **Dokumentasi Resmi**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)
- **Referensi API**: [Complete API Documentation](https://reference.groupdocs.com/comparison/net/)
- **Unduh Pustaka**: [Get GroupDocs.Comparison](https://releases.groupdocs.com/comparison/net/)
- **Opsi Lisensi**: [Purchase Information](https://purchase.groupdocs.com/buy)
- **Percobaan Gratis**: [Start Your Evaluation](https://releases.groupdocs.com/comparison/net/)
- **Lisensi Sementara**: [Extended Evaluation License](https://purchase.groupdocs.com/temporary-license/)
- **Dukungan Komunitas**: [GroupDocs Forum](https://forum.groupdocs.com/c/comparison/)

---

**Last Updated:** 2026-05-31  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define constants for document paths
string YOUR_DOCUMENT_DIRECTORY = @"C:\Documents\TestFiles";
string sourcePath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "source.docx");
string targetPath = Path.Combine(YOUR_DOCUMENT_DIRECTORY, "target.docx");
string YOUR_OUTPUT_DIRECTORY = @"C:\Documents\Output";
string outputFileName = Path.Combine(YOUR_OUTPUT_DIRECTORY, "result.docx");

// Initialize the Comparer with the source document path
using (Comparer comparer = new Comparer(sourcePath))
{
    // Add the target document to be compared against the source
    comparer.Add(targetPath);
    
    // Perform the comparison and save the result to the output file
    comparer.Compare(outputFileName);
}

Console.WriteLine($"Comparison complete! Check your results at: {outputFileName}");
```

## Tutorial Terkait

- [GroupDocs Comparison .NET Quick Start - Panduan Penyiapan Lengkap](/comparison/net/quick-start/)
- [Tutorial Perbandingan Dokumen .NET - Panduan Memuat & Menyimpan Lengkap](/comparison/net/loading-and-saving-documents/)
- [Pengaturan Lisensi GroupDocs Comparison .NET - Panduan FileStream Lengkap](/comparison/net/licensing-configuration/set-license-file-stream-groupdocs-comparison-dotnet/)