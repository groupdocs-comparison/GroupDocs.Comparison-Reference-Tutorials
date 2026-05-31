---
categories:
- Image Processing
date: '2026-05-31'
description: Pelajari cara membandingkan gambar di .NET menggunakan GroupDocs.Comparison
  sambil menonaktifkan halaman ringkasan. Tutorial ini mencakup penyiapan, kode, tips
  kinerja, dan contoh penggunaan dunia nyata.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Bandingkan Gambar .NET Tanpa Ringkasan
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Cara Membandingkan Gambar di .NET – Lewati Halaman Ringkasan
type: docs
url: /id/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Cara Membandingkan Gambar di .NET – Lewati Halaman Ringkasan

Ketika Anda perlu **cara membandingkan gambar** secara programatis dalam aplikasi .NET, hal terakhir yang Anda inginkan adalah halaman ringkasan tambahan yang membuang waktu dan penyimpanan. Baik Anda membangun jalur kontrol kualitas, pipeline manajemen konten, atau suite pengujian regresi visual otomatis, melewatkan halaman ringkasan dapat mengurangi beberapa detik dari setiap run dan menjaga jejak disk Anda tetap ramping.

Dalam tutorial ini Anda akan belajar cara menggunakan **GroupDocs.Comparison for .NET** untuk membandingkan dua gambar secara efisien, mengonfigurasi perpustakaan untuk menekan pembuatan ringkasan, dan menerapkan trik kinerja praktik terbaik. Kami juga akan mengeksplorasi mengapa hal ini penting, kapan menggunakannya, dan cara menghindari jebakan umum.

## Jawaban Cepat
- **Apa cara tercepat untuk membandingkan gambar tanpa halaman ringkasan?** Gunakan `Comparer` dengan `CompareOptions` dan set `GenerateSummaryPage = false`.  
- **Perpustakaan mana yang mendukung ini secara langsung?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Apakah saya memerlukan lisensi?** Ya, lisensi komersial diperlukan untuk produksi; percobaan gratis dapat digunakan untuk pengembangan.  
- **Bisakah saya membandingkan lebih dari dua gambar sekaligus?** Tentu – panggil `Add()` beberapa kali sebelum `Compare()`.  
- **Apakah pendekatan ini cocok untuk pekerjaan batch berskala besar?** Ya, ketika digabungkan dengan pemrosesan batch dan penanganan memori yang tepat.

## Apa itu GroupDocs.Comparison?
`GroupDocs.Comparison` adalah perpustakaan .NET yang mendeteksi perbedaan visual antara dokumen dan gambar, menghasilkan hasil berdampingan atau overlay. Ia mendukung **lebih dari 50 format input dan output**, termasuk JPEG, PNG, BMP, TIFF, dan GIF, serta dapat memproses file ratusan halaman tanpa memuat seluruh file ke memori.

## Mengapa Melewatkan Halaman Ringkasan?
Menonaktifkan halaman ringkasan mengurangi I/O hingga **70 %** untuk perbandingan hanya gambar dan memotong waktu pemrosesan sekitar **30 %** rata‑rata, menurut suite benchmark perpustakaan. Ketika Anda hanya membutuhkan gambar diff (untuk pengujian otomatis atau keputusan lulus/gagal QC), laporan HTML tambahan tidak memberikan nilai dan hanya mengonsumsi ruang disk.

## Prasyarat dan Penyiapan Lingkungan

### Apa yang Anda Butuhkan
- **GroupDocs.Comparison for .NET** versi **25.4.0** atau lebih baru  
- Visual Studio 2019 + atau IDE kompatibel .NET apa pun  
- .NET Framework 4.6.1 + **atau** .NET Core 2.0 +  
- Pengetahuan dasar C# dan familiaritas dengan file I/O  

### Rekomendasi Tambahan
- Proyek uji kecil yang berisi sepasang gambar contoh (misalnya `source.png` dan `target.png`).  
- Opsional: Pengaturan dependency injection jika Anda lebih suka arsitektur berbasis layanan.  

### Mengapa Prasyarat Ini Penting
Versi perpustakaan yang ditentukan mencakup flag `GenerateSummaryPage` dan peningkatan kinerja yang tidak dimiliki rilis lama. Menggunakan IDE modern memastikan Anda dapat memanfaatkan manajemen paket NuGet dan melihat peringatan waktu kompilasi lebih awal.

## Cara Menginstal GroupDocs.Comparison
GroupDocs.Comparison dapat ditambahkan ke proyek .NET apa pun melalui NuGet, yang menangani pengunduhan binari dan memperbarui file proyek. Pilih metode yang sesuai dengan alur kerja Anda: Package Manager Console untuk pengguna Visual Studio atau .NET CLI untuk lingkungan baris perintah. Kedua perintah secara otomatis menyelesaikan dependensi dan memastikan versi yang tepat direferensikan.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Ganti `25.4.0` dengan versi tepat yang ingin Anda kunci.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Kedua perintah menambahkan perpustakaan ke file proyek Anda dan memulihkan binari yang diperlukan.

**Pro Tip:** Pin versi di `.csproj` Anda untuk menghindari upgrade tidak sengaja yang dapat mengubah perilaku API.

## Pertimbangan Lisensi
GroupDocs.Comparison memerlukan lisensi untuk setiap penyebaran produksi. Anda dapat memulai dengan **percobaan gratis** yang menyediakan fungsionalitas penuh, kemudian upgrade ke **lisensi sementara** untuk pengujian lanjutan, dan akhirnya ke **lisensi komersial penuh** untuk produksi. Ingat untuk menempatkan file `GroupDocs.Comparison.lic` di root aplikasi atau menentukan jalurnya secara programatis.

## Penyiapan Proyek Dasar
Buat aplikasi console baru (atau integrasikan ke layanan yang ada) dan tambahkan kode boilerplate berikut. Potongan ini menunjukkan penyiapan minimal yang diperlukan sebelum Anda menyelam ke logika perbandingan.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Penting:** Selalu gunakan `Path.Combine()` untuk jalur file. Ini secara otomatis menangani pemisah jalur spesifik OS dan menghindari bug halus saat berpindah antara kontainer Windows dan Linux.

## Panduan Implementasi Langkah‑per‑Langkah

### Bagaimana cara membandingkan gambar tanpa halaman ringkasan?
`Comparer` adalah kelas utama di GroupDocs.Comparison yang mengatur operasi perbandingan dokumen dan gambar. `CompareOptions` menyimpan pengaturan konfigurasi yang mengontrol bagaimana perbandingan dilakukan, seperti apakah menghasilkan halaman ringkasan. Muat gambar sumber, konfigurasikan `CompareOptions` untuk menonaktifkan ringkasan, tambahkan gambar target, dan panggil `Compare()`. Metode ini mengembalikan `ComparisonResult` yang berisi aliran gambar diff, yang dapat Anda tulis ke disk, kirim melalui jaringan, atau sematkan dalam komponen UI. Pendekatan ini memastikan hanya diff penting yang dihasilkan, menghilangkan laporan HTML atau PDF tambahan.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

Kode di atas melakukan seluruh perbandingan dalam **empat langkah logis** dan menulis hanya gambar diff, meninggalkan semua ringkasan HTML atau PDF.

### Langkah 1: Inisialisasi Objek Comparer
`Comparer` adalah pintu gerbang ke semua operasi perbandingan. Ia mengimplementasikan `IDisposable`, sehingga membungkusnya dalam blok `using` menjamin bahwa handle file dan memori tak terkelola dibebaskan segera, bahkan jika terjadi pengecualian.

### Langkah 2: Konfigurasikan CompareOptions untuk Tanpa Ringkasan
Setel `GenerateSummaryPage = false` pada instance `CompareOptions`. Flag ini memberi tahu engine untuk melewatkan pembuatan laporan HTML default, yang merupakan sumber I/O tambahan utama dalam skenario hanya gambar.

### Langkah 3: Tambahkan Gambar Target untuk Perbandingan
Anda dapat memanggil `Add()` beberapa kali untuk membandingkan satu sumber dengan beberapa target dalam satu batch. Setiap panggilan dapat menerima `CompareOptions` masing‑masing jika Anda memerlukan kustomisasi per‑gambar.

### Langkah 4: Jalankan Perbandingan dan Simpan Hasil
`Comparer.Compare()` melakukan pekerjaan berat dan mengembalikan `ComparisonResult`. Hasilnya berisi `Stream` dengan gambar diff, yang dapat Anda simpan langsung ke disk, kirim melalui jaringan, atau sematkan dalam komponen UI.

## Metode Siap‑Produksi Lengkap
Berikut adalah metode siap‑pakai yang dapat Anda sisipkan ke layanan .NET apa pun. Ia mencakup validasi jalur, penanganan pengecualian, dan kait log opsional.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Jebakan Implementasi Umum (Dan Cara Menghindarinya)

- **Masalah Jalur:** Selalu verifikasi bahwa kedua file sumber dan target ada dengan `File.Exists()`. File yang hilang akan melempar `FileNotFoundException` yang dapat ditangkap lebih awal.  
- **Tekanan Memori:** Gambar besar (10 MB +) dapat mengonsumsi RAM signifikan. Proses dalam batch dan pertimbangkan down‑scaling jika akurasi pixel‑perfect tidak diperlukan.  
- **Kunci File:** Pastikan tidak ada proses lain yang memegang kunci eksklusif pada file gambar. Ini terutama penting dalam lingkungan multi‑threaded atau containerized.  

## Aplikasi Praktis dan Kasus Penggunaan

### Kontrol Kualitas dalam Manufaktur
Jalur produksi menangkap gambar setiap item dan membandingkannya dengan referensi emas. Melewatkan halaman ringkasan memungkinkan sistem memutuskan “lulus” atau “gagal” dalam milidetik, menjaga jalur tetap bergerak cepat.

### Sistem Manajemen Konten
Ketika pengguna mengunggah aset, CMS dapat langsung mendeteksi duplikat atau hampir duplikat, mencegah pembengkakan penyimpanan dan meningkatkan relevansi pencarian. Gambar diff dapat disimpan sebagai thumbnail untuk inspeksi visual cepat.

### Pengujian UI Otomatis (Regresi Visual)
Selenium atau Playwright dapat menangkap screenshot halaman web, lalu memberi mereka ke rutinitas perbandingan ini. Gambar diff menyoroti perubahan UI, dan karena tidak ada ringkasan yang dihasilkan, pipeline CI tetap cepat dan ringan.

### Imaging Medis (Dengan Audit)
Alur kerja radiologi kadang perlu menandai perubahan antara pemindaian berurutan. Meskipun Anda mungkin masih menghasilkan log audit detail, gambar diff itu sendiri dapat diproduksi tanpa halaman ringkasan, mengurangi waktu pemrosesan untuk PNG yang dikonversi dari DICOM besar.

## Pertimbangan Kinerja dan Optimasi

### Praktik Terbaik Manajemen Memori
Proses gambar dalam **batch 20–50** tergantung pada RAM server. Lepaskan setiap instance `Comparer` segera dan panggil `GC.Collect()` hanya jika Anda melihat lonjakan memori selama pekerjaan panjang.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Optimasi I/O Disk
Letakkan direktori input, output, dan sementara Anda pada volume SSD cepat yang sama. Hapus file sementara segera setelah gambar diff disimpan untuk menghindari penggunaan disk yang tidak perlu.

### Pertimbangan Threading dan Async
`GroupDocs.Comparison` aman untuk thread pada operasi read‑only, tetapi hindari berbagi satu instance `Comparer` antar thread. Sebagai gantinya, buat tugas independen:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Memecahkan Masalah Umum

### Kesalahan Jalur File dan Izin
- **Gejala:** `FileNotFoundException` atau `UnauthorizedAccessException`.  
- **Solusi:** Gunakan `Path.GetFullPath()` untuk men-debug jalur yang diresolusikan, pastikan identitas pool aplikasi (atau pengguna container Docker) memiliki hak baca/tulis, dan periksa kembali bahwa jalur tidak terpotong oleh variabel lingkungan.

### Bottleneck Memori dan Kinerja
- **Gejala:** Eksekusi lambat atau `OutOfMemoryException`.  
- **Solusi:** Ubah ukuran gambar ke resolusi umum (misalnya 1024 × 768) ketika perbandingan pixel‑perfect tidak diperlukan. Pantau memori dengan alat seperti dotMemory atau Performance Profiler bawaan.

### Masalah Lisensi
- **Gejala:** Gambar diff ber watermark atau `LicenseException`.  
- **Solusi:** Pastikan `GroupDocs.Comparison.lic` berada di direktori eksekusi atau muat secara eksplisit via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Opsi Konfigurasi Lanjutan

### Menyesuaikan Sensitivitas Perbandingan
Anda dapat menyesuaikan bagaimana engine memperlakukan variasi pixel kecil (misalnya artefak kompresi) dengan mengatur properti `Sensitivity` pada `CompareOptions`. Nilai lebih rendah membuat perbandingan lebih ketat.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Optimasi Format Output
Jika Anda memerlukan gambar diff dalam format tertentu (PNG vs JPEG), set properti `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```
```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Integrasi dengan .NET Framework Populer

### Contoh Layanan ASP.NET Core
Ekspose endpoint HTTP ringan yang menerima dua aliran gambar, menjalankan perbandingan, dan mengembalikan gambar diff sebagai `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Registrasi Dependency Injection
Tambahkan comparer sebagai layanan scoped di `Program.cs` atau `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Pertanyaan yang Sering Diajukan

**T: Apa keuntungan utama melewatkan halaman ringkasan?**  
J: Ini memotong waktu pemrosesan hingga 30 % dan mengurangi penggunaan disk sekitar 70 % untuk perbandingan hanya gambar, yang penting untuk pipeline berkecepatan tinggi.

**T: Bisakah saya tetap mengambil metadata perubahan detail tanpa halaman ringkasan?**  
J: Ya. Objek `ComparisonResult` mengekspos koleksi `Changes` yang berisi informasi programatik tentang setiap perbedaan yang terdeteksi.

**T: Format gambar apa yang didukung?**  
J: JPEG, PNG, BMP, TIFF, GIF, dan beberapa lainnya—lebih dari 50 format secara total.

**T: Bagaimana cara menangani gambar sangat besar (mis., >20 MB)?**  
J: Proses dalam batch lebih kecil, opsional down‑scale, dan pantau penggunaan memori. Menggunakan `Comparer` dalam blok `using` memastikan sumber daya dilepaskan segera.

**T: Apakah pendekatan ini aman untuk aplikasi multi‑threaded?**  
J: Ya, selama setiap thread membuat instance `Comparer` masing‑masing. Membagikan satu instance dapat menyebabkan kondisi balapan.

## Sumber Daya Tambahan

- [Dokumentasi GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Referensi API](https://reference.groupdocs.com/comparison/net/)
- [Unduh](https://releases.groupdocs.com/comparison/net/)
- [Beli](https://purchase.groupdocs.com/buy)
- [Percobaan Gratis](https://releases.groupdocs.com/comparison/net/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)
- [Forum Dukungan](https://forum.groupdocs.com/c/comparison/)

---

**Terakhir Diperbarui:** 2026-05-31  
**Diuji Dengan:** GroupDocs.Comparison 25.4.0 untuk .NET  
**Penulis:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Tutorial Terkait

- [Perbandingan Gambar .NET - Membandingkan Gambar Secara Programatis](/comparison/net/image-comparison/compare-images-from-path/)
- [Perbandingan Gambar .NET - Membandingkan Gambar dari Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [Tutorial GroupDocs Comparison .NET - Panduan Penggunaan Dasar Lengkap](/comparison/net/basic-usage/)