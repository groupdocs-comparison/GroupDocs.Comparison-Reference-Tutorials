---
title: .NET için GroupDocs Karşılaştırmasında Kullanıcı Tanımlı Belge Meta Verilerini Kaydetme
linktitle: .NET için GroupDocs Karşılaştırmasında Kullanıcı Tanımlı Belge Meta Verilerini Kaydetme
second_title: GroupDocs.Comparison .NET API'si
description: GroupDocs Comparison for .NET'i kullanarak kullanıcı tanımlı belge meta verilerini nasıl kaydedeceğinizi öğrenin. Adım adım talimatlarla meta verileri kolayca karşılaştırın ve değiştirin.
weight: 16
url: /tr/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# .NET için GroupDocs Karşılaştırmasında Kullanıcı Tanımlı Belge Meta Verilerini Kaydetme

## giriiş
Bu öğreticide, GroupDocs Comparison for .NET'i kullanarak kullanıcı tanımlı belge meta verilerinin nasıl kaydedileceğini inceleyeceğiz. Meta veriler, belgeleri verimli bir şekilde düzenlemek ve yönetmek için çok önemlidir. GroupDocs Karşılaştırması ile, özel gereksinimlerinizi karşılamak için meta verileri kolayca karşılaştırabilir ve değiştirebilirsiniz.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1.  .NET için GroupDocs Karşılaştırması: .NET için GroupDocs Karşılaştırmasını indirip yükleyin.[Burada](https://releases.groupdocs.com/comparison/net/).
2. Geliştirme Ortamı: Sisteminizde Visual Studio gibi uygun bir geliştirme ortamının kurulu olduğundan emin olun.
3. Kaynak ve Hedef Belgeler: Karşılaştırmak ve meta verilerini değiştirmek istediğiniz kaynak ve hedef belgeleri hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle GroupDocs Comparison for .NET tarafından sağlanan işlevlere erişmek için gerekli ad alanlarını içe aktarın.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Adım 1: Çıktı Dizinini ve Dosya Adını Tanımlayın
Karşılaştırılan belgeyi kaydetmek istediğiniz dizini tanımlayın ve çıktı dosyasının adını belirtin.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Adım 2: Karşılaştırıcıyı Başlatın ve Belgeleri Ekleyin
 Başlat`Comparer` Kaynak belgeyle nesneyi eşleştirin ve karşılaştırma için hedef belgeyi ekleyin.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 3. Adım: Meta Veri Seçeneklerini Belirleyin
 Karşılaştırılan belgeye kaydedilecek meta veri seçeneklerini belirtin. Bu örnekte, ayarladık`CloneMetadataType` ile`MetadataType.FileAuthor` ve ayrıntıları sağlayın`FileAuthorMetadata`.
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
## 4. Adım: Belgeleri Karşılaştırın ve Meta Verileri Kaydedin
Belgeleri belirtilen meta veri seçenekleriyle karşılaştırın ve karşılaştırılan belgeyi kaydedin.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Adım 5: Başarı Mesajını Görüntüleyin
Belgelerin başarıyla karşılaştırıldığını ve çıktı konumunu belirten bir başarı mesajı görüntüler.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Çözüm
Bu öğreticide, GroupDocs Comparison for .NET'i kullanarak kullanıcı tanımlı belge meta verilerinin nasıl kaydedileceğini öğrendik. Bu adımları izleyerek, meta verileri korurken ve gereksinimlerinize göre değiştirirken belgeleri verimli bir şekilde karşılaştırabilirsiniz.
## SSS'ler
### GroupDocs Comparison for .NET çeşitli belge formatlarını işleyebilir mi?
Evet, GroupDocs Karşılaştırması, DOCX, PDF, PPTX, XLSX ve daha fazlasını içeren çok çeşitli belge formatlarını destekler.
### GroupDocs Comparison for .NET'in ücretsiz deneme sürümü var mı?
 Evet, ücretsiz deneme sürümüne erişebilirsiniz[Burada](https://releases.groupdocs.com/).
### Meta veri seçeneklerini ihtiyaçlarıma göre özelleştirebilir miyim?
GroupDocs Comparison kesinlikle belge karşılaştırması sırasında meta veri işlemeyi özelleştirmek için esnek seçenekler sunar.
### GroupDocs Karşılaştırması teknik destek sunuyor mu?
Evet, GroupDocs Karşılaştırma forumundan teknik destek alabilirsiniz[Burada](https://forum.groupdocs.com/c/comparison/12).
### GroupDocs Comparison for .NET lisansını nereden satın alabilirim?
 GroupDocs web sitesinden lisans satın alabilirsiniz.[Burada](https://purchase.groupdocs.com/buy).