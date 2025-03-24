---
title: Terima dan Tolak Perubahan dalam Perbandingan GroupDocs untuk .NET
linktitle: Terima dan Tolak Perubahan dalam Perbandingan GroupDocs untuk .NET
second_title: GroupDocs.Perbandingan .NET API
description: Pelajari cara menerima dan menolak perubahan dalam dokumen menggunakan Perbandingan GroupDocs untuk .NET. Sederhanakan alur kerja dokumen Anda dengan mudah.
weight: 10
url: /id/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# Terima dan Tolak Perubahan dalam Perbandingan GroupDocs untuk .NET

## Perkenalan
Dalam bidang manajemen dokumen dan kolaborasi, memastikan keakuratan dan integritas file adalah hal yang terpenting. Perbandingan GroupDocs untuk .NET muncul sebagai solusi tangguh, memberdayakan pengembang untuk dengan mudah menerima dan menolak perubahan dalam dokumen, sehingga menyederhanakan alur kerja dan meningkatkan produktivitas. Tutorial ini akan memandu Anda melalui proses menerima dan menolak perubahan menggunakan Perbandingan GroupDocs untuk .NET, menguraikan setiap langkah untuk kejelasan dan kemudahan penerapan.
## Prasyarat
Sebelum masuk ke tutorial, pastikan Anda memiliki prasyarat berikut:
### Pengaturan Lingkungan
1. Instal .NET SDK: Jika Anda belum melakukannya, unduh dan instal .NET SDK yang sesuai untuk sistem operasi Anda dari situs web .NET.
2.  Instal Perbandingan GroupDocs untuk .NET: Dapatkan versi terbaru Perbandingan GroupDocs untuk .NET dari yang disediakan[tautan unduhan](https://releases.groupdocs.com/comparison/net/) dan ikuti petunjuk instalasi.
3. Keakraban dengan Pemrograman C#: Tutorial ini mengasumsikan pemahaman dasar bahasa pemrograman C# dan sintaksisnya.

## Impor Namespace
Untuk memulainya, impor namespace yang diperlukan ke dalam proyek Anda. Namespace ini akan memberikan akses ke fungsionalitas yang diperlukan untuk perbandingan dan manipulasi dokumen.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Langkah 1: Tentukan Direktori Output dan Nama File
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Pastikan untuk mengganti`"Your Document Directory"` dengan jalur ke direktori keluaran yang Anda inginkan.
## Langkah 2: Inisialisasi Pembanding dan Bandingkan Dokumen
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Kode ini menginisialisasi objek Pembanding dengan dokumen sumber dan menambahkan dokumen target untuk perbandingan. Kemudian, ia menjalankan proses perbandingan.
## Langkah 3: Ambil dan Manipulasi Perubahan
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Ambil perubahan dari perbandingan dan manipulasi sesuai kebutuhan. Dalam contoh ini, perubahan ditolak terlebih dahulu, lalu diterima. Dokumen yang dihasilkan disimpan sebagaimana mestinya.

## Kesimpulan
Kesimpulannya, Perbandingan GroupDocs untuk .NET menawarkan solusi yang lancar untuk menerima dan menolak perubahan dalam dokumen. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, pengembang dapat secara efisien mengintegrasikan fungsi ini ke dalam aplikasi mereka, memastikan keakuratan dokumen dan meningkatkan kolaborasi.
## FAQ
### Bisakah Perbandingan GroupDocs untuk .NET membandingkan dokumen dengan format berbeda?
Ya, Perbandingan GroupDocs untuk .NET mendukung perbandingan antara dokumen berbagai format seperti DOCX, PDF, PPTX, dan lainnya.
### Apakah Perbandingan GroupDocs untuk .NET kompatibel dengan .NET Core?
Ya, Perbandingan GroupDocs untuk .NET kompatibel dengan .NET Framework dan .NET Core.
### Bisakah saya menyesuaikan tampilan perubahan pada dokumen yang dibandingkan?
Tentu saja, Perbandingan GroupDocs untuk .NET menyediakan opsi luas untuk menyesuaikan tampilan perubahan termasuk warna, gaya, dan banyak lagi.
### Apakah Perbandingan GroupDocs untuk .NET mendukung perbandingan dokumen multi-halaman?
Ya, Perbandingan GroupDocs untuk .NET mendukung perbandingan dokumen multi-halaman dengan presisi dan akurat.
### Apakah ada versi uji coba yang tersedia untuk Perbandingan GroupDocs untuk .NET?
 Ya, Anda dapat memanfaatkan uji coba gratis Perbandingan GroupDocs untuk .NET dari yang disediakan[tautan](https://releases.groupdocs.com/).