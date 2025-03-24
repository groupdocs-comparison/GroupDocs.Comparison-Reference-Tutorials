---
title: Menyimpan Metadata Dokumen Buatan Pengguna dalam Perbandingan GroupDocs untuk .NET
linktitle: Menyimpan Metadata Dokumen Buatan Pengguna dalam Perbandingan GroupDocs untuk .NET
second_title: GroupDocs.Perbandingan .NET API
description: Pelajari cara menyimpan metadata dokumen yang ditentukan pengguna menggunakan Perbandingan GroupDocs untuk .NET. Bandingkan dan manipulasi metadata dengan mudah menggunakan petunjuk langkah demi langkah.
weight: 16
url: /id/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menyimpan metadata dokumen yang ditentukan pengguna menggunakan Perbandingan GroupDocs untuk .NET. Metadata sangat penting untuk mengatur dan mengelola dokumen secara efisien. Dengan Perbandingan GroupDocs, Anda dapat dengan mudah membandingkan dan memanipulasi metadata untuk memenuhi kebutuhan spesifik Anda.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1.  Perbandingan GroupDocs untuk .NET: Unduh dan instal Perbandingan GroupDocs untuk .NET dari[Di Sini](https://releases.groupdocs.com/comparison/net/).
2. Lingkungan Pengembangan: Pastikan Anda memiliki lingkungan pengembangan yang sesuai seperti Visual Studio yang terinstal di sistem Anda.
3. Dokumen Sumber dan Target: Siapkan dokumen sumber dan target yang metadatanya ingin Anda bandingkan dan manipulasi.

## Impor Namespace
Pertama, impor namespace yang diperlukan untuk mengakses fungsionalitas yang disediakan oleh GroupDocs Comparison untuk .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Langkah 1: Tentukan Direktori Output dan Nama File
Tentukan direktori tempat Anda ingin menyimpan dokumen yang dibandingkan dan tentukan nama file keluaran.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Langkah 2: Inisialisasi Pembanding dan Tambahkan Dokumen
 Inisialisasi`Comparer` objek dengan dokumen sumber dan tambahkan dokumen target untuk perbandingan.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Langkah 3: Tentukan Opsi Metadata
 Tentukan opsi metadata untuk disimpan dalam dokumen yang dibandingkan. Dalam contoh ini, kami menetapkan`CloneMetadataType` ke`MetadataType.FileAuthor` dan memberikan rincian untuk`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## Langkah 4: Bandingkan Dokumen dan Simpan Metadata
Bandingkan dokumen dengan opsi metadata tertentu dan simpan dokumen yang dibandingkan.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Langkah 5: Tampilkan Pesan Sukses
Menampilkan pesan sukses yang menunjukkan bahwa dokumen telah berhasil dibandingkan dan lokasi keluarannya.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menyimpan metadata dokumen yang ditentukan pengguna menggunakan Perbandingan GroupDocs untuk .NET. Dengan mengikuti langkah-langkah ini, Anda dapat membandingkan dokumen secara efisien sambil menjaga dan memanipulasi metadata sesuai kebutuhan Anda.
## FAQ
### Bisakah Perbandingan GroupDocs untuk .NET menangani berbagai format dokumen?
Ya, Perbandingan GroupDocs mendukung berbagai format dokumen termasuk DOCX, PDF, PPTX, XLSX, dan banyak lagi.
### Apakah ada uji coba gratis yang tersedia untuk Perbandingan GroupDocs untuk .NET?
 Ya, Anda dapat mengakses uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### Bisakah saya menyesuaikan opsi metadata sesuai kebutuhan saya?
Tentu saja, Perbandingan GroupDocs memberikan opsi fleksibel untuk menyesuaikan penanganan metadata selama perbandingan dokumen.
### Apakah Perbandingan GroupDocs menawarkan dukungan teknis?
Ya, Anda bisa mendapatkan dukungan teknis dari forum Perbandingan GroupDocs[Di Sini](https://forum.groupdocs.com/c/comparison/12).
### Di mana saya dapat membeli lisensi Perbandingan GroupDocs untuk .NET?
 Anda dapat membeli lisensi dari situs web GroupDocs[Di Sini](https://purchase.groupdocs.com/buy).