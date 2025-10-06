---
"description": "Pelajari cara membandingkan dokumen menggunakan GroupDocs.Comparison untuk .NET langkah demi langkah. Tingkatkan aplikasi .NET Anda dengan manajemen dokumen yang efisien."
"linktitle": "Bersihkan Sumber Daya Setelah Pratinjau Halaman"
"second_title": "API Perbandingan GroupDocs.NET"
"title": "Bersihkan Sumber Daya Setelah Pratinjau Halaman"
"url": "/id/net/document-comparison/clean-resources-after-page-previews/"
"weight": 13
type: docs
---
# Bersihkan Sumber Daya Setelah Pratinjau Halaman

## Perkenalan
Dalam dunia pengembangan .NET, mengelola dan membandingkan dokumen secara efisien sangat penting untuk berbagai aplikasi, mulai dari firma hukum hingga lembaga pendidikan. Untungnya, dengan alat seperti GroupDocs.Comparison for .NET, pengembang dapat menyederhanakan proses membandingkan dokumen dengan mudah. Dalam tutorial ini, kita akan membahas cara memanfaatkan GroupDocs.Comparison for .NET untuk membandingkan dokumen langkah demi langkah.
## Prasyarat
Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:
1. GroupDocs.Comparison untuk .NET: Unduh dan instal pustaka dari [Di Sini](https://releases.groupdocs.com/comparison/net/).
2. Lingkungan Pengembangan .NET: Pastikan Anda memiliki lingkungan pengembangan .NET yang berfungsi di komputer Anda.
3. Contoh Dokumen: Siapkan dokumen sumber dan target yang ingin Anda bandingkan.

## Mengimpor Ruang Nama
Dalam proyek .NET Anda, mulailah dengan mengimpor namespace yang diperlukan untuk mengakses fungsionalitas GroupDocs.Comparison untuk .NET.

```csharp
using System;
using System.IO;
```

## Langkah 1: Tentukan Direktori Output dan Nama File
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## Langkah 2: Inisialisasi Pembanding dan Tambahkan Dokumen
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```
## Langkah 3: Lakukan Perbandingan dan Hasilkan Output
```csharp
    comparer.Compare(File.Create(outputFileName));
```
## Langkah 4: Hasilkan Pratinjau Dokumen
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    document.GeneratePreview(previewOptions);
}
```
## Langkah 5: Menampilkan Pesan Sukses
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## Kesimpulan
Sebagai kesimpulan, GroupDocs.Comparison untuk .NET menyediakan solusi yang kuat untuk membandingkan dokumen dengan mudah dalam aplikasi .NET. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, pengembang dapat dengan mudah mengintegrasikan fungsionalitas perbandingan dokumen ke dalam proyek mereka, meningkatkan produktivitas dan efisiensi.
## Pertanyaan yang Sering Diajukan
### Apakah GroupDocs.Comparison untuk .NET kompatibel dengan berbagai format dokumen?
Ya, GroupDocs.Comparison untuk .NET mendukung berbagai format dokumen, termasuk DOCX, PPTX, XLSX, PDF, dan banyak lagi.
### Dapatkah saya menyesuaikan format keluaran dari dokumen yang dibandingkan?
Tentu saja, GroupDocs.Comparison untuk .NET menawarkan fleksibilitas dalam memilih format keluaran sesuai dengan kebutuhan Anda.
### Apakah ada versi uji coba yang tersedia untuk tujuan pengujian?
Ya, Anda dapat menjelajahi fitur GroupDocs.Comparison untuk .NET dengan uji coba gratis yang tersedia [Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan untuk masalah atau pertanyaan apa pun yang terkait dengan GroupDocs.Comparison untuk .NET?
Anda dapat mencari bantuan dari forum komunitas GroupDocs.Comparison [Di Sini](https://forum.groupdocs.com/c/comparison/12).
### Di mana saya dapat membeli lisensi untuk GroupDocs.Comparison untuk .NET?
Anda dapat membeli lisensi untuk GroupDocs.Comparison untuk .NET dari [tautan ini](https://purchase.groupdocs.com/buy).