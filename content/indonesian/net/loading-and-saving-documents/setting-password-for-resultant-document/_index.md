---
title: Menetapkan Kata Sandi untuk Dokumen yang Dihasilkan dalam Perbandingan GroupDocs untuk .NET
linktitle: Menetapkan Kata Sandi untuk Dokumen yang Dihasilkan dalam Perbandingan GroupDocs untuk .NET
second_title: GroupDocs.Perbandingan .NET API
description: Pelajari cara mengatur kata sandi untuk dokumen yang dihasilkan di Perbandingan GroupDocs untuk .NET. Tingkatkan keamanan dan lindungi file Anda yang dibandingkan.
type: docs
weight: 17
url: /id/net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## Perkenalan
Dalam tutorial ini, kami akan memandu Anda melalui proses pengaturan kata sandi untuk dokumen yang dihasilkan menggunakan Perbandingan GroupDocs untuk .NET. Fitur ini menambahkan lapisan keamanan ekstra pada dokumen Anda yang dibandingkan, memastikan bahwa hanya individu yang berwenang yang dapat mengaksesnya.
## Prasyarat
Sebelum melanjutkan, pastikan Anda memiliki hal berikut:
1.  Perbandingan GroupDocs untuk .NET: Pastikan Anda telah menginstal perpustakaan Perbandingan GroupDocs di lingkungan .NET Anda. Anda dapat mengunduhnya dari[Di Sini](https://releases.groupdocs.com/comparison/net/).
2. Dokumen Sumber dan Sasaran: Siapkan dokumen sumber (`SOURCE.docx`) dan dokumen target (`TARGET.docx`) yang ingin Anda bandingkan dan atur kata sandi untuk dokumen yang dihasilkan.

## Impor Namespace
Pertama, Anda perlu mengimpor namespace yang diperlukan ke proyek C# Anda untuk menggunakan fungsionalitas Perbandingan GroupDocs:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Langkah 1: Tentukan Direktori Output dan Nama File
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
Tentukan direktori tempat Anda ingin menyimpan dokumen yang dihasilkan dan tentukan nama untuk file keluaran.
## Langkah 2: Bandingkan Dokumen dengan Pengaturan Kata Sandi
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
 Di sini, kami menginisialisasi a`Comparer` objek dengan dokumen sumber. Kemudian kita tambahkan dokumen target yang akan dibandingkan. Kami mengatur`PasswordSaveOption` ke`User` untuk menentukan bahwa kata sandi akan diterapkan pada dokumen yang dihasilkan. Berikan kata sandi yang diinginkan di`Password` properti dari`SaveOptions` obyek.
## Langkah 3: Tampilkan Pesan Sukses
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Terakhir, kami menampilkan pesan sukses yang menunjukkan bahwa dokumen telah berhasil dibandingkan, dan dokumen yang dihasilkan dengan kata sandi yang ditetapkan telah disimpan ke direktori yang ditentukan.

## Kesimpulan
Menetapkan kata sandi untuk dokumen yang dihasilkan di Perbandingan GroupDocs untuk .NET menambahkan lapisan keamanan ekstra pada dokumen yang Anda bandingkan, memastikan kerahasiaan dan integritas. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat dengan mudah mengimplementasikan fitur ini di aplikasi .NET Anda.
## FAQ
### Bisakah saya membandingkan dokumen dalam format berbeda?
Ya, Perbandingan GroupDocs untuk .NET mendukung perbandingan dokumen dalam berbagai format seperti DOCX, PDF, PPTX, XLSX, dan banyak lagi.
### Apakah ada versi uji coba yang tersedia?
 Ya, Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana saya bisa mendapatkan dukungan jika saya menemui masalah?
 Anda dapat mencari bantuan dari forum komunitas Perbandingan GroupDocs[Di Sini](https://forum.groupdocs.com/c/comparison/12).
### Apakah saya memerlukan lisensi untuk menggunakan Perbandingan GroupDocs untuk .NET?
 Ya, Anda dapat membeli lisensi dari[Di Sini](https://purchase.groupdocs.com/buy) atau mendapatkan izin sementara[Di Sini](https://purchase.groupdocs.com/temporary-license/).
### Apakah ada dokumentasi yang tersedia untuk Perbandingan GroupDocs untuk .NET?
 Ya, Anda dapat mengakses dokumentasinya[Di Sini](https://reference.groupdocs.com/comparison/net/).