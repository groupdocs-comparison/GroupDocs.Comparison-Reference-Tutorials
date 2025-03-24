---
title: .NET için GroupDocs Karşılaştırmasındaki Değişiklikleri Kabul Etme ve Reddetme
linktitle: .NET için GroupDocs Karşılaştırmasındaki Değişiklikleri Kabul Etme ve Reddetme
second_title: GroupDocs.Comparison .NET API'si
description: GroupDocs Comparison for .NET'i kullanarak belgelerdeki değişiklikleri nasıl kabul edeceğinizi ve reddedeceğinizi öğrenin. Belge iş akışlarınızı zahmetsizce kolaylaştırın.
weight: 10
url: /tr/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## giriiş
Belge yönetimi ve işbirliği alanında, dosyaların doğruluğunun ve bütünlüğünün sağlanması çok önemlidir. GroupDocs Comparison for .NET, geliştiricilere belgelerdeki değişiklikleri zahmetsizce kabul etme ve reddetme yetkisi veren, böylece iş akışlarını kolaylaştıran ve üretkenliği artıran güçlü bir çözüm olarak ortaya çıkıyor. Bu eğitim, GroupDocs Comparison for .NET'i kullanarak değişiklikleri kabul etme ve reddetme süreci boyunca size rehberlik edecek ve netlik ve uygulama kolaylığı için her adımı parçalara ayıracaktır.
## Önkoşullar
Eğiticiye dalmadan önce aşağıdaki önkoşulların mevcut olduğundan emin olun:
### Ortam Kurulumu
1. .NET SDK'yı yükleyin: Henüz yapmadıysanız, işletim sisteminize uygun .NET SDK'yı .NET web sitesinden indirip yükleyin.
2.  GroupDocs Comparison for .NET'i yükleyin: GroupDocs Comparison for .NET'in en son sürümünü sağlanan kaynaktan edinin.[İndirme: {link](https://releases.groupdocs.com/comparison/net/) ve kurulum talimatlarını takip edin.
3. C# Programlamaya Aşinalık: Bu eğitimde C# programlama dili ve sözdiziminin temel olarak anlaşıldığı varsayılmaktadır.

## Ad Alanlarını İçe Aktar
Başlangıç olarak gerekli ad alanlarını projenize aktarın. Bu ad alanları, belge karşılaştırması ve manipülasyonu için gereken işlevselliklere erişim sağlayacaktır.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Adım 1: Çıktı Dizinini ve Dosya Adlarını Belirleyin
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Değiştirildiğinden emin olun`"Your Document Directory"` İstediğiniz çıktı dizininin yolu ile.
## Adım 2: Karşılaştırıcıyı Başlatın ve Belgeleri Karşılaştırın
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Bu kod, Comparer nesnesini kaynak belgeyle başlatır ve karşılaştırma için hedef belgeyi ekler. Daha sonra karşılaştırma işlemini yürütür.
## 3. Adım: Değişiklikleri Alın ve Yönetin
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Karşılaştırmadaki değişiklikleri alın ve bunları gerektiği gibi değiştirin. Bu örnekte, değişiklikler önce reddedilir, sonra kabul edilir. Ortaya çıkan belgeler buna göre kaydedilir.

## Çözüm
Sonuç olarak GroupDocs Comparison for .NET, belgelerdeki değişiklikleri kabul etmek ve reddetmek için kusursuz bir çözüm sunar. Geliştiriciler, bu eğitimde özetlenen adımları izleyerek bu işlevselliği uygulamalarına verimli bir şekilde entegre edebilir, belge doğruluğunu sağlayabilir ve işbirliğini geliştirebilir.
## SSS'ler
### GroupDocs Comparison for .NET farklı formatlardaki belgeleri karşılaştırabilir mi?
Evet, GroupDocs Comparison for .NET, DOCX, PDF, PPTX ve daha fazlası gibi çeşitli formatlardaki belgeler arasında karşılaştırmayı destekler.
### .NET için GroupDocs Karşılaştırması .NET Core ile uyumlu mu?
Evet, GroupDocs Comparison for .NET, hem .NET Framework hem de .NET Core ile uyumludur.
### Karşılaştırılan belgelerdeki değişikliklerin görünümünü özelleştirebilir miyim?
Kesinlikle, GroupDocs Comparison for .NET renk, stil ve daha fazlasını içeren değişikliklerin görünümünü özelleştirmek için kapsamlı seçenekler sunar.
### GroupDocs Comparison for .NET çok sayfalı belge karşılaştırmasını destekliyor mu?
Evet, GroupDocs Comparison for .NET, çok sayfalı belgelerin kesinlik ve doğrulukla karşılaştırılmasını destekler.
### GroupDocs Comparison for .NET'in deneme sürümü mevcut mu?
 Evet, sağlanan ücretsiz GroupDocs Comparison for .NET denemesinden yararlanabilirsiniz.[bağlantı](https://releases.groupdocs.com/).