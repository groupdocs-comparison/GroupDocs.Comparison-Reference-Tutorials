---
categories:
- Document Processing
date: '2026-07-01'
description: 了解如何使用 GroupDocs.Comparison 以 C# 讀取檔案中繼資料、擷取檔案大小串流，並有效取得文件屬性串流。
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: 擷取文件資訊 .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: 讀取檔案中繼資料 C# – 從串流中擷取文件資訊
type: docs
url: /zh-hant/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# 讀取檔案中繼資料 C# – 從串流提取文件資訊

## 簡介

在 C# 中讀取檔案中繼資料而不載入整個文件，是現代 .NET 應用程式的常見需求。**Read file metadata C#** 讓您能驗證上傳、顯示文件詳細資訊，並在保持低記憶體使用量的同時做出處理決策。GroupDocs.Comparison for .NET 提供快速的串流式 API，直接從 `Stream` 提取檔案類型、頁數、大小及其他屬性。接下來的章節將說明此功能的重要性、如何設定，以及可直接放入任何 .NET 專案的逐步程式碼。

## 快速答覆
- **“read file metadata C#” 是什麼意思？** 它表示透過 .NET 串流取得文件的屬性（類型、頁數、大小），而不載入完整內容。  
- **哪個函式庫負責此功能？** GroupDocs.Comparison for .NET 提供 `GetDocumentInfo()` 方法以快速提取中繼資料。  
- **我需要授權嗎？** 免費試用可用於開發；正式環境需要商業授權。  
- **我可以在大型 PDF 上使用嗎？** 可以 — 串流方式可處理數百頁的檔案而不會消耗大量記憶體。  
- **它相容於 .NET 6+ 嗎？** 完全相容，函式庫以 .NET Standard 2.0 為目標，並可在 .NET 6、.NET 7 以及 .NET Core 上執行。

## 什麼是 read file metadata C#？
`Read file metadata C#` 指透過使用串流的 C# 程式碼取得文件的描述性資訊——例如格式、頁數與位元組大小。此技術避免將整個檔案載入記憶體，對於大型 PDF、DOCX 檔或批次作業尤為有價值。

## 為什麼使用 GroupDocs 從串流提取中繼資料？
GroupDocs.Comparison 支援 **50+ 種輸入與輸出格式**，且能從最高 **2 GB** 大小的檔案提取中繼資料，同時將記憶體使用量控制在 **10 MB** 以下。函式庫僅讀取必要的標頭區段，對於一般 100 頁的 PDF，在標準伺服器上可於 **150 毫秒** 內完成。這些具體效益轉化為更快的上傳驗證、更低的雲端成本，以及更順暢的使用者體驗。

## 前置條件與設定

### 1. 安裝 GroupDocs.Comparison for .NET
從 [official download page](https://releases.groupdocs.com/comparison/net/) 下載最新套件。如果偏好使用 NuGet，執行以下指令：

```
Install-Package GroupDocs.Comparison
```

### 2. 基本 .NET 開發知識
您應該熟悉 C# 與 .NET I/O 模型。使用 `Stream`、`FileStream` 與 `MemoryStream` 是以下範例的必要前置。

### 3. 開發環境
支援 Visual Studio、VS Code 或 JetBrains Rider。請確保您的專案目標為 .NET 6 或更新版本，以獲得最佳效能。

## 如何從串流讀取檔案中繼資料 C#？
使用 `FileStream` 載入文件，建立 `Comparer` 實例，並呼叫 `GetDocumentInfo()`。整個操作僅需兩行程式碼，即可回傳包含檔案類型、頁數與大小的 `IDocumentInfo` 物件。函式庫在內部僅讀取必要的標頭位元組，因此即使是大型 PDF 也能快速處理且不會佔用過多記憶體。  
`Comparer` 是負責協調文件分析的主要 GroupDocs.Comparison 類別。  
`GetDocumentInfo()` 回傳包含基本中繼資料的 `IDocumentInfo` 物件。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### 步驟 1：使用串流初始化 Comparer 物件
以下程式碼片段從唯讀的 `FileStream` 建立 `Comparer` 實例。使用 `using` 區塊可確保串流關閉且 Comparer 釋放，防止檔案被鎖定。

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### 步驟 2：提取文件資訊
呼叫 `GetDocumentInfo()` 會回傳包含所有所需中繼資料的 `IDocumentInfo` 物件。此方法僅讀取檔案標頭的必要部分，因此即使是 500 頁的 PDF 也能在瞬間完成處理。

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### 步驟 3：顯示與使用文件資訊
現在您可以存取 `FileType`、`PageCount` 與 `Size` 屬性。在正式環境中，您可能會將這些值儲存至資料庫、透過 API 暴露，或用於判斷是否接受上傳。

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## 常見使用情境與實作模式

### 檔案上傳驗證
當使用者上傳文件時，您可以即時驗證其類型與頁數，然後再寫入儲存空間。此舉可防止不允許的格式與過大檔案進入系統。

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### 批次文件分析
要處理一個文件資料夾嗎？先提取中繼資料，以將檔案導向不同的管線——例如，大型 PDF 交給非同步工作者處理，而單頁檔案則直接在流程中處理。

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## 常見問題與解決方案

### 檔案存取與鎖定問題
**問題**： “The file is being used by another process.”  
**解決方案**：將串流包在 `using` 陳述式中，必要時實作指數退避的重試策略。

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### 不支援的檔案格式處理
**問題**： API 對未知格式拋出例外。  
**解決方案**：檢查 `FileType` 屬性；若回傳 `Unknown`，則向呼叫端回傳友善錯誤並記錄此事件。

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### 大檔案的記憶體管理
**問題**： 處理極大文件時記憶體激增。  
**解決方案**：串流式方法已盡量減少記憶體使用，但仍應在完成後立即呼叫 `Comparer` 的 `Dispose()`，並避免長時間保留 `IDocumentInfo` 的參考。

## 效能考量與最佳實踐

### 串流管理最佳實踐
1. **始終使用 `using` 陳述式** – 可確保及時釋放資源。  
2. **重新設定串流位置以便重複使用** – 若需兩次讀取同一串流，請呼叫 `stream.Seek(0, SeekOrigin.Begin)`。  
3. **選擇正確的串流類型** – `FileStream` 用於磁碟檔案，`MemoryStream` 用於記憶體資料，`NetworkStream` 用於遠端來源。

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### 何時偏好此方法而非完整文件載入
**當需要使用串流式中繼資料提取時**：
- 您只需要高層次的資訊（類型、頁數、大小）。  
- 您正在驗證上傳或建立文件目錄。  
- 效能與低記憶體佔用至關重要。

**當需要完整文件處理時**：
- 您需要比較內容、抽取文字或渲染頁面。  
- 需要深度分析（例如 OCR、浮水印偵測）。

## 生產環境的進階技巧

### 強韌的錯誤處理策略
將所有操作包在 try‑catch 區塊中，捕獲 `GroupDocs.Comparison.Exceptions.ComparisonException`。當文件處理發生錯誤時，函式庫會拋出 `ComparisonException`。記錄錯誤細節，回傳標準化的錯誤回應，並確保在 `finally` 區塊中釋放 `Comparer`。

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### 與日誌與監控的整合
注入日誌框架（例如 Serilog 或 NLog），並發送處理時間、檔案大小、成功/失敗次數等指標。此資料有助於及早發現效能退化。

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## 常見問題

**Q: GroupDocs.Comparison for .NET 是否相容於不同的文件格式？**  
A: 是的。函式庫支援 **超過 50 種檔案格式**，包括 DOCX、PDF、XLSX、PPTX 以及多種影像類型，適用於幾乎所有文件工作流程。

**Q: 我可以在購買前試用 GroupDocs.Comparison for .NET 嗎？**  
A: 當然可以。免費試用可於 [the website](https://releases.groupdocs.com/) 取得，讓您在未取得授權前評估所有功能。

**Q: 我可以在哪裡取得 GroupDocs.Comparison for .NET 的支援？**  
A: 您可於 [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12) 獲得協助，社群與產品團隊會即時回覆問題。

**Q: 是否提供測試用的臨時授權？**  
A: 有。可從 [the licensing page](https://purchase.groupdocs.com/temporary-license/) 取得臨時授權，適合開發與 QA 環境。

**Q: GroupDocs.Comparison for .NET 是否適合企業部署？**  
A: 絕對適合。它提供企業級效能、廣泛的格式支援與強韌的錯誤處理，這些都是大型生產系統所必需的。

**最後更新：** 2026-07-01  
**測試環境：** GroupDocs.Comparison 23.10 for .NET  
**作者：** GroupDocs

## 相關教學

- [取得文件屬性 C# .NET - 提取檔案中繼資料](/comparison/net/basic-usage/get-document-info-from-path/)
- [文件中繼資料管理 .NET - GroupDocs.Comparison 完整指南](/comparison/net/metadata-management/)
- [文件比較 .NET 教學 - 使用 GroupDocs 保留中繼資料](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)