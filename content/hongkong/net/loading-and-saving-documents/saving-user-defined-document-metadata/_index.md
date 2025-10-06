---
"description": "了解如何使用 GroupDocs Compare for .NET 儲存使用者定義的文件元資料。透過逐步說明輕鬆比較和操作元資料。"
"linktitle": "在 GroupDocs 比較中保存 .NET 的使用者定義文檔元數據"
"second_title": "GroupDocs.Comparison .NET API"
"title": "在 GroupDocs 比較中保存 .NET 的使用者定義文檔元數據"
"url": "/zh-hant/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
type: docs
---
# 在 GroupDocs 比較中保存 .NET 的使用者定義文檔元數據

## 介紹
在本教學中，我們將探索如何使用 GroupDocs Compare for .NET 儲存使用者定義的文件元資料。元資料對於有效率地組織和管理文件至關重要。使用 GroupDocs Compare，您可以輕鬆比較和操作元數據，以滿足您的特定需求。
## 先決條件
在開始之前，請確保您符合以下先決條件：
1. GroupDocs .NET 比較：從下列位置下載並安裝 GroupDocs .NET 比較 [這裡](https://releases。groupdocs.com/comparison/net/).
2. 開發環境：確保您的系統上安裝了合適的開發環境，例如 Visual Studio。
3. 來源文件和目標文件：準備要比較和操作元資料的來源文件和目標文件。

## 導入命名空間
首先，匯入必要的命名空間以存取 GroupDocs Compare for .NET 提供的功能。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 步驟 1：定義輸出目錄和檔名
定義要儲存比較文件的目錄並指定輸出檔名。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 步驟 2：初始化比較器並新增文檔
初始化 `Comparer` 物件與來源文件並新增目標文件進行比較。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 步驟 3：指定元資料選項
指定比較文件中儲存的元資料選項。在本例中，我們設定 `CloneMetadataType` 到 `MetadataType.FileAuthor` 並提供詳細信息 `FileAuthorMetadata`。
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
## 步驟 4：比較文件並儲存元數據
將文件與指定的元資料選項進行比較並儲存比較的文件。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 步驟5：顯示成功訊息
顯示成功訊息，表示文件已成功比較以及輸出位置。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 結論
在本教學中，我們學習如何使用 GroupDocs Compare for .NET 儲存使用者定義的文件元資料。請依照以下步驟，您可以有效率地比較文檔，同時根據需要儲存和操作元資料。
## 常見問題解答
### GroupDocs Compare for .NET 能處理各種文件格式嗎？
是的，GroupDocs Compare 支援多種文件格式，包括 DOCX、PDF、PPTX、XLSX 等。
### GroupDocs Compare for .NET 有免費試用版嗎？
是的，您可以免費試用 [這裡](https://releases。groupdocs.com/).
### 我可以根據需要自訂元資料選項嗎？
當然，GroupDocsComparison 提供了一個靈活的選項來客製化文件比較期間的元資料處理。
### GroupDocs Compare 是否提供技術支援？
是的，您可以從 GroupDocs 比較論壇獲得技術支持 [這裡](https://forum。groupdocs.com/c/comparison/12).
### 我可以在哪裡購買 GroupDocs Compare for .NET 的授權？
您可以從 GroupDocs 網站購買許可證 [這裡](https://purchase。groupdocs.com/buy).