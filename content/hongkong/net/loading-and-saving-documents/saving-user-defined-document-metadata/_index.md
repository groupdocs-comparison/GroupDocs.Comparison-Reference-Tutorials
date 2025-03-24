---
title: 在 .NET 的 GroupDocs Comparison 中儲存使用者定義的文檔元數據
linktitle: 在 .NET 的 GroupDocs Comparison 中儲存使用者定義的文檔元數據
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs Comparison for .NET 儲存使用者定義的文件元資料。透過逐步說明輕鬆比較和操作元資料。
weight: 16
url: /zh-hant/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## 介紹
在本教學中，我們將探討如何使用 GroupDocs Comparison for .NET 儲存使用者定義的文件元資料。元資料對於有效組織和管理文件至關重要。透過 GroupDocs Comparison，您可以輕鬆比較和操作元資料以滿足您的特定要求。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1. 適用於 .NET 的 GroupDocs Comparison：從以下位置下載並安裝適用於 .NET 的 GroupDocs Comparison[這裡](https://releases.groupdocs.com/comparison/net/).
2. 開發環境：確保您的系統上安裝了合適的開發環境，例如 Visual Studio。
3. 來源文件和目標文件：準備要比較和操作元資料的來源文件和目標文件。

## 導入命名空間
首先，匯入必要的命名空間以存取 GroupDocs Comparison for .NET 提供的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 第 1 步：定義輸出目錄和檔名
定義要儲存比較文件的目錄並指定輸出檔名。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 第 2 步：初始化比較器並新增文檔
初始化`Comparer`物件與來源文件並新增目標文件進行比較。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 步驟 3：指定元資料選項
指定用於保存在比較文件中的元資料選項。在這個例子中，我們設定`CloneMetadataType`到`MetadataType.FileAuthor`並提供詳細信息`FileAuthorMetadata`.
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
## 第 4 步：比較文件並儲存元數據
將文件與指定的元資料選項進行比較並儲存比較的文件。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 步驟5：顯示成功訊息
顯示成功訊息，指示文件已成功比較以及輸出位置。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs Comparison for .NET 來儲存使用者定義的文件元資料。透過執行這些步驟，您可以有效地比較文檔，同時根據您的要求保留和操作元資料。
## 常見問題解答
### GroupDocs Comparison for .NET 可以處理各種文件格式嗎？
是的，GroupDocs Comparison 支援多種文件格式，包括 DOCX、PDF、PPTX、XLSX 等。
### GroupDocs Comparison for .NET 是否有免費試用版？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).
### 我可以根據需要自訂元資料選項嗎？
當然，GroupDocs Comparison 提供了靈活的選項來自訂文件比較期間的元資料處理。
### GroupDocs Comparison 是否提供技術支援？
是的，您可以從 GroupDocs Comparison 論壇獲得技術支持[這裡](https://forum.groupdocs.com/c/comparison/12).
### 哪裡可以購買 GroupDocs Comparison for .NET 的授權？
您可以從 GroupDocs 網站購買許可證[這裡](https://purchase.groupdocs.com/buy).