---
"description": "了解如何使用 GroupDocs.Comparison for .NET 比較來自資料流的映像。無縫整合到 .NET 應用程式的逐步指南。"
"linktitle": "比較來自流的圖像 - GroupDocs.Comparison for .NET"
"second_title": "GroupDocs.Comparison .NET API"
"title": "比較來自流的圖像 - GroupDocs.Comparison for .NET"
"url": "/zh-hant/net/image-comparison/compare-images-from-stream/"
"weight": 11
type: docs
---
# 比較來自流的圖像 - GroupDocs.Comparison for .NET

## 介紹
在 .NET 開發領域，確保文件或影像的準確性和一致性至關重要。 GroupDocs.Comparison for .NET 為開發人員提供了一個強大的解決方案，可以有效地比較映像。本教學將指導您使用 GroupDocs.Comparison for .NET 比較來自資料流的圖像。請按照以下步驟操作，您將能夠將影像比較功能無縫整合到您的 .NET 應用程式中。
## 先決條件
在深入學習本教程之前，請確保您已滿足以下先決條件：
### 1. 安裝 GroupDocs.Comparison for .NET
確保您的開發環境中已安裝 GroupDocs.Comparison for .NET。您可以從 [下載連結](https://releases。groupdocs.com/comparison/net/).
### 2. 取得許可證
要使用 GroupDocs.Comparison for .NET，您需要一個有效的授權。您可以從以下方式購買許可證： [群組文檔](https://purchase.groupdocs.com/buy) 或從以下網站取得臨時許可證以進行評估 [這裡](https://purchase。groupdocs.com/temporary-license/).
### 3.熟悉.NET開發
學習本教程需要具備 .NET 程式設計的基本知識。

## 導入命名空間
在繼續比較過程之前，請確保將必要的命名空間匯入到您的 .NET 專案中。 
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 步驟 1：定義輸出目錄和檔名
首先，指定要儲存比較結果的目錄和輸出檔案的名稱。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.png");
```
## 步驟2：初始化比較器
接下來，初始化 `Comparer` 透過提供來源影像流來物件。
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.png")))
{
```
## 步驟3：新增目標影像
透過提供目標影像的串流將其添加到比較過程中。
```csharp
comparer.Add(File.OpenRead("TARGET.png"));
```
## 步驟 4：配置比較選項
配置影像比較的選項。在本例中，我們設定 `GenerateSummaryPage` 為 false 以防止產生摘要頁面。
```csharp
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```
## 步驟5：進行比較
透過呼叫執行比較過程 `Compare` 方法並提供輸出檔名和比較選項。
```csharp
comparer.Compare(outputFileName, options);
```
## 步驟6：顯示結果
最後，顯示一則訊息確認比較成功以及輸出檔案的位置。
```csharp
Console.WriteLine($"\nImages compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```

## 結論
總而言之，GroupDocs.Comparison for .NET 為在 .NET 應用程式中比較映像提供了強大的解決方案。透過遵循本教程中概述的逐步指南，開發人員可以將圖像比較功能無縫整合到他們的專案中，從而確保跨文件的準確性和一致性。
## 常見問題解答
### GroupDocs.Comparison for .NET 可以比較不同格式的圖片嗎？
是的，GroupDocs.Comparison for .NET 支援比較各種格式的圖片，包括 PNG、JPEG、GIF、BMP 等。
### 可以自訂比較設定嗎？
當然，開發人員可以根據自己的需求自訂比較設置，例如忽略細微的格式差異或設定容忍度等級。
### 我可以比較儲存在記憶體流中的圖像嗎？
是的，您可以比較來自記憶體流的圖像，如本教學所示。
### .NET 的 GroupDocs.Comparison 是否也提供文件比較支援？
是的，GroupDocs.Comparison for .NET 不僅支援比較圖像，還支援比較各種格式的文檔，例如 Word、Excel、PDF 等。
### 是否有可供測試的試用版？
是的，您可以從以下位置取得免費試用版 [這裡](https://releases。groupdocs.com/).