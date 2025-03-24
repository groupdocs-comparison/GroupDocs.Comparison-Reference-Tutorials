---
title: 在 .NET 的 GroupDocs Comparison 中儲存文件元資料來源
linktitle: 在 .NET 的 GroupDocs Comparison 中儲存文件元資料來源
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 儲存文件元資料來源。請按照我們的逐步指南在 .NET 中進行無縫文件比較。
weight: 14
url: /zh-hant/net/loading-and-saving-documents/saving-documents-metadata-source/
---

# 在 .NET 的 GroupDocs Comparison 中儲存文件元資料來源

## 介紹
在軟體開發領域，有效的文件比較對於各個行業（包括法律、金融和教育）至關重要。 GroupDocs Comparison for .NET 提供了一個強大的解決方案，用於無縫比較 .NET 應用程式中的文件。本教學將引導您完成使用 GroupDocs Comparison for .NET 儲存文件元資料來源的過程。透過執行這些步驟，您將能夠充分利用該程式庫的潛力來增強您的文件比較任務。
## 先決條件
在深入學習本教學之前，請確保您已設定以下先決條件：
1. 環境設定：在您的電腦上準備好 .NET 開發環境。
2.  GroupDocs Comparison 安裝：從下列位置下載並安裝 GroupDocs Comparison for .NET[下載連結](https://releases.groupdocs.com/comparison/net/).
3. 文件文件：準備要比較的來源文件文件和目標文件文件。
4. 基本 C# 知識：熟悉 C# 程式語言基礎知識，以理解提供的程式碼片段。

## 導入命名空間
在繼續進行比較過程之前，請確保導入必要的命名空間：
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```

## 第 1 步：定義輸出目錄和檔名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
在此步驟中，我們定義儲存比較文件的目錄並指定輸出檔名。
## 第 2 步：初始化比較器對象
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
```
在這裡，我們初始化一個`Comparer`透過提供來源文檔的路徑來取得物件。該物件將用於文件比較。
## 第三步：新增目標文檔
```csharp
comparer.Add("TARGET.docx");
```
我們將目標文件新增到比較器物件中。這是將與來源文件進行比較的文件。
## 步驟 4：比較文件並儲存元資料來源
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Source });
```
在此步驟中，我們使用以下方法比較來源文檔和目標文檔`Compare`比較器物件的方法。此外，我們指定輸出檔案名稱並設置`CloneMetadataType`到`MetadataType.Source`儲存文檔元資料來源。
## 步驟5：顯示輸出目錄
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
最後，我們顯示一則訊息，指示文件比較成功，並提供保存比較文檔的輸出目錄。

## 結論
總之，GroupDocs Comparison for .NET 為 .NET 應用程式中的文件比較任務提供了全面的解決方案。透過學習本教學課程，您已了解如何有效保存文件元資料來源，從而增強文件比較流程。
## 常見問題解答
### GroupDocs Comparison for .NET 可以比較不同格式的文件嗎？
是的，GroupDocs Comparison 支援比較各種格式的文檔，包括 DOCX、PDF、PPTX 等。
### GroupDocs Comparison for .NET 是否有試用版？
是的，您可以存取試用版[這裡](https://releases.groupdocs.com/).
### 我可以自訂比較文件的輸出格式嗎？
當然，GroupDocs Comparison 提供了根據您的要求自訂輸出格式的選項。
### .NET 使用者的 GroupDocs Comparison 是否可以獲得技術支援？
是的，您可以向以下機構尋求技術協助[支援論壇](https://forum.groupdocs.com/c/comparison/12).
### 哪裡可以購買 GroupDocs Comparison for .NET 的授權？
您可以從 GroupDocs 網站購買許可證[這裡](https://purchase.groupdocs.com/buy).