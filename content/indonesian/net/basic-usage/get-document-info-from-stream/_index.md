---
categories:
- Document Processing
date: '2026-07-01'
description: Pelajari cara membaca metadata file C# menggunakan GroupDocs.Comparison,
  mengekstrak ukuran file dari stream dan mendapatkan properti dokumen dari stream
  secara efisien.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Ekstrak Informasi Dokumen .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: Baca Metadata File C# – Ekstrak Informasi Dokumen dari Stream
type: docs
url: /id/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Baca Metadata File C# – Ekstrak Informasi Dokumen dari Stream

## Pendahuluan

Membaca metadata file dalam C# tanpa memuat seluruh dokumen adalah kebutuhan umum untuk aplikasi .NET modern. **Read file metadata C#** memungkinkan Anda memvalidasi unggahan, menampilkan detail dokumen, dan membuat keputusan pemrosesan sambil menjaga penggunaan memori tetap rendah. GroupDocs.Comparison untuk .NET menyediakan API berbasis stream yang cepat yang mengekstrak tipe file, jumlah halaman, ukuran, dan properti lainnya langsung dari `Stream`. Pada bagian berikut Anda akan melihat mengapa ini penting, cara menyiapkannya, dan kode langkah‑demi‑langkah yang dapat Anda masukkan ke proyek .NET apa pun.

## Jawaban Cepat
- **Apa arti “read file metadata C#”?** Itu berarti mengambil properti dokumen (tipe, halaman, ukuran) melalui stream .NET tanpa memuat konten penuh.  
- **Perpustakaan mana yang menangani ini?** GroupDocs.Comparison untuk .NET menawarkan metode `GetDocumentInfo()` untuk ekstraksi metadata cepat.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengembangan; lisensi komersial diperlukan untuk produksi.  
- **Bisakah saya menggunakan ini dengan PDF besar?** Ya – pendekatan stream memproses file ratusan halaman tanpa konsumsi memori tinggi.  
- **Apakah kompatibel dengan .NET 6+?** Tentu saja, perpustakaan menargetkan .NET Standard 2.0 dan bekerja pada .NET 6, .NET 7, dan .NET Core.

## Apa itu read file metadata C#?
`Read file metadata C#` mengacu pada memperoleh informasi deskriptif dokumen—seperti format, jumlah halaman, dan ukuran byte—menggunakan kode C# yang bekerja dengan stream. Teknik ini menghindari memuat seluruh file ke memori, yang sangat berharga untuk PDF besar, file DOCX, atau operasi batch.

## Mengapa menggunakan ekstraksi metadata GroupDocs dari stream?
GroupDocs.Comparison mendukung **50+ format input dan output** dan dapat mengekstrak metadata dari file hingga **2 GB** sambil menjaga penggunaan memori di bawah **10 MB**. Perpustakaan hanya membaca bagian header yang diperlukan, memberikan hasil dalam **kurang dari 150 ms** untuk PDF 100‑halaman tipikal pada server standar. Manfaat terkuantifikasi ini diterjemahkan menjadi validasi unggahan yang lebih cepat, biaya cloud yang lebih rendah, dan pengalaman pengguna yang lebih mulus.

## Prasyarat dan Penyiapan

### 1. Instal GroupDocs.Comparison untuk .NET
Unduh paket terbaru dari [halaman unduhan resmi](https://releases.groupdocs.com/comparison/net/). Jika Anda lebih suka NuGet, jalankan:

```
Install-Package GroupDocs.Comparison
```

### 2. Pengetahuan Dasar Pengembangan .NET  
Anda harus nyaman dengan C# dan model I/O .NET. Bekerja dengan `Stream`, `FileStream`, dan `MemoryStream` sangat penting untuk contoh di bawah ini.

### 3. Lingkungan Pengembangan  
Visual Studio, VS Code, atau JetBrains Rider semuanya didukung. Pastikan proyek Anda menargetkan .NET 6 atau yang lebih baru untuk kinerja terbaik.

## Cara membaca metadata file C# dari stream?

Muat dokumen dengan `FileStream`, buat instance `Comparer`, dan panggil `GetDocumentInfo()`. Seluruh operasi hanya memerlukan dua baris kode dan mengembalikan objek `IDocumentInfo` yang berisi tipe file, jumlah halaman, dan ukuran. Secara internal perpustakaan hanya membaca byte header yang diperlukan, sehingga bahkan PDF besar diproses dengan cepat tanpa mengonsumsi memori signifikan.  
`Comparer` adalah kelas utama GroupDocs.Comparison yang mengatur analisis dokumen.  
`GetDocumentInfo()` mengembalikan objek `IDocumentInfo` dengan metadata dasar.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Langkah 1: Inisialisasi Objek Comparer dengan Stream

Potongan kode berikut membuat instance `Comparer` dari `FileStream` yang hanya-baca. Menggunakan blok `using` menjamin stream ditutup dan comparer dibuang, mencegah penguncian file.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Langkah 2: Ekstrak Informasi Dokumen

Memanggil `GetDocumentInfo()` mengembalikan objek `IDocumentInfo` yang memuat semua metadata yang Anda butuhkan. Metode ini hanya membaca bagian header file yang diperlukan, sehingga bahkan PDF 500‑halaman diproses dalam sepersekian detik.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Langkah 3: Tampilkan dan Gunakan Informasi Dokumen

Sekarang Anda dapat mengakses properti `FileType`, `PageCount`, dan `Size`. Pada produksi Anda mungkin menyimpan nilai ini di basis data, menampilkannya melalui API, atau menggunakannya untuk memutuskan apakah menerima unggahan.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Kasus Penggunaan Umum dan Pola Implementasi

### Validasi Unggahan File

Saat pengguna mengunggah dokumen, Anda dapat langsung memverifikasi tipe dan jumlah halaman sebelum menyimpannya. Ini mencegah format yang tidak diinginkan dan file berukuran besar masuk ke sistem Anda.

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### Analisis Dokumen Batch

Memproses folder dokumen? Ekstrak metadata terlebih dahulu untuk mengarahkan file ke pipeline berbeda—misalnya, PDF besar dikirim ke pekerja asinkron, sementara file satu‑halaman diproses secara inline.

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## Masalah Umum dan Solusinya

### Masalah Akses dan Penguncian File

**Issue**: “The file is being used by another process.”  
**Solution**: Bungkus stream dalam pernyataan `using` dan, bila perlu, terapkan kebijakan retry dengan back‑off eksponensial.

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### Penanganan Format File yang Tidak Didukung

**Issue**: API melempar pengecualian untuk format yang tidak dikenal.  
**Solution**: Periksa properti `FileType`; jika mengembalikan `Unknown`, kembalikan kesalahan yang ramah kepada pemanggil dan catat insiden tersebut.

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### Manajemen Memori dengan File Besar

**Issue**: Lonjakan memori saat memproses dokumen sangat besar.  
**Solution**: Pendekatan berbasis stream sudah meminimalkan penggunaan memori, tetapi Anda juga harus memanggil `Dispose()` pada `Comparer` segera setelah selesai dan menghindari menyimpan referensi ke `IDocumentInfo` lebih lama dari yang diperlukan.

## Pertimbangan Kinerja dan Praktik Terbaik

### Praktik Terbaik Manajemen Stream

1. **Always use `using` statements** – Guarantees disposal and frees resources promptly.  
2. **Reset stream position when reusing** – If you need to read the same stream twice, call `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Choose the right stream type** – `FileStream` for disk files, `MemoryStream` for in‑memory data, `NetworkStream` for remote sources.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Kapan Memilih Pendekatan Ini vs. Memuat Dokumen Sepenuhnya

**Prefer stream‑based metadata extraction when**:

- Anda hanya membutuhkan detail tingkat tinggi (tipe, halaman, ukuran).  
- Anda memvalidasi unggahan atau membangun katalog dokumen.  
- Kinerja dan jejak memori rendah sangat penting.

**Switch to full document processing when**:

- Anda perlu membandingkan konten, mengekstrak teks, atau merender halaman.  
- Analisis mendalam (mis., OCR, deteksi watermark) diperlukan.  

## Tips Lanjutan untuk Penggunaan Produksi

### Strategi Penanganan Kesalahan yang Kuat

Bungkus semua operasi dalam blok try‑catch yang menangkap `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` dilempar oleh perpustakaan ketika terjadi kesalahan selama pemrosesan dokumen. Catat detail kesalahan, kembalikan respons kesalahan standar, dan pastikan `Comparer` dibuang dalam klausa `finally`.

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### Integrasi dengan Logging dan Monitoring

Sisipkan kerangka kerja logging (mis., Serilog atau NLog) dan kirim metrik seperti waktu pemrosesan, ukuran file, serta hitungan sukses/gagal. Data ini membantu Anda mengidentifikasi regresi kinerja lebih awal.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Pertanyaan yang Sering Diajukan

**Q: Apakah GroupDocs.Comparison untuk .NET kompatibel dengan berbagai format dokumen?**  
A: Ya. Perpustakaan mendukung **lebih dari 50 format file**, termasuk DOCX, PDF, XLSX, PPTX, dan banyak tipe gambar, menjadikannya cocok untuk hampir semua alur kerja dokumen.

**Q: Bisakah saya mencoba GroupDocs.Comparison untuk .NET sebelum membeli?**  
A: Tentu saja. Versi percobaan gratis tersedia di [the website](https://releases.groupdocs.com/), memungkinkan Anda mengevaluasi semua fitur tanpa lisensi.

**Q: Di mana saya dapat menemukan dukungan untuk GroupDocs.Comparison untuk .NET?**  
A: Anda dapat mendapatkan bantuan di [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12), tempat komunitas dan tim produk merespons pertanyaan dengan cepat.

**Q: Apakah lisensi sementara tersedia untuk pengujian?**  
A: Ya. Lisensi sementara dapat diperoleh dari [the licensing page](https://purchase.groupdocs.com/temporary-license/), ideal untuk lingkungan pengembangan dan QA.

**Q: Apakah GroupDocs.Comparison untuk .NET cocok untuk penerapan perusahaan?**  
A: Tentu. Ia menawarkan kinerja tingkat perusahaan, dukungan format yang luas, dan penanganan kesalahan yang kuat, semua hal yang penting untuk sistem produksi berskala besar.

---

**Terakhir Diperbarui:** 2026-07-01  
**Diuji Dengan:** GroupDocs.Comparison 23.10 untuk .NET  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Dapatkan Properti Dokumen C# .NET - Ekstrak Metadata File](/comparison/net/basic-usage/get-document-info-from-path/)
- [Manajemen Metadata Dokumen .NET - Panduan Lengkap untuk GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Tutorial Perbandingan Dokumen .NET - Pertahankan Metadata dengan GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)