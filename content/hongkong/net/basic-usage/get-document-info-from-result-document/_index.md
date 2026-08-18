---
categories:
- Document Comparison
date: '2026-06-15'
description: 了解如何使用 GroupDocs.Comparison 從 .NET 比較結果中提取元資料。一步一步的指南，附有程式碼範例與實用技巧。
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: 從比較結果提取文件資訊
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: 如何從 .NET 比較結果中提取元資料 – 完整指南
type: docs
url: /zh-hant/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# 如何從 .NET 比較結果中提取元資料 – 完整指南

當你在 .NET 應用程式中處理文件比較時，可能會想知道 **如何提取元資料** 從比較結果中。像是檔案類型、頁數以及文件大小等元資料對於稽核記錄、效能調校，或僅僅是向最終使用者顯示有用資訊都相當重要。本教學將引導你使用 GroupDocs.Comparison for .NET 高效取得這些資料。

## 快速答案
- **比較的主要類別是什麼？** `Comparer` 會載入來源文件並執行比較引擎。  
- **哪個方法會返回元資料？** 目標文件上的 `GetDocumentInfo()` 會返回 `IDocumentInfo` 物件。  
- **我可以在 .NET 中取得文件大小嗎？** 可以 – `IDocumentInfo` 的 `Size` 屬性會返回以位元組為單位的大小。  
- **提取元資料需要授權嗎？** 生產環境必須擁有有效的 GroupDocs.Comparison 授權；免費試用版支援所有元資料功能。  
- **API 是否相容於 .NET 6？** 完全相容 – GroupDocs.Comparison 支援 .NET Framework 4.6.1+、.NET Core 2.0+ 以及 .NET 5/6+。

`GetDocumentInfo()` 方法會返回包含文件元資料的 `IDocumentInfo` 物件。

## 什麼是文件比較中的元資料提取？
元資料提取是從參與比較操作的文件中取得描述性資訊（例如檔案類型、頁數與檔案大小）的過程。GroupDocs.Comparison 透過統一的 API 釋出這些資料，讓記錄、顯示或條件處理變得簡單。

## 為何要從比較結果中提取元資料？
提取元資料可讓你建立詳細的稽核日誌、依類型路由檔案，並針對大型文件調整處理策略。了解檔案類型、頁數與大小後，你可以執行合規規則、估算處理時間，並在使用者開始比較前提供清晰資訊。

## 前置條件

1. **GroupDocs.Comparison for .NET** – 從 [官方發佈頁面](https://releases.groupdocs.com/comparison/net/) 安裝此函式庫。  
   你也可以在 [GroupDocs 發佈頁面](https://releases.groupdocs.com/) 瀏覽所有版本。  
2. **開發環境** – Visual Studio、VS Code，或任何支援 .NET 6+ 的 IDE。  
3. **範例文件** – 兩個檔案（例如 `SOURCE.docx` 與 `TARGET.docx`）用於測試。API 支援超過 **50 種文件格式**。

## 匯入命名空間

以下的 `using` 指令讓你存取核心比較引擎、檔案處理工具與元資料介面。

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

在實例化任何 GroupDocs 物件之前，需要先加入這些匯入。

## 如何從比較結果中提取元資料？

`Comparer` 類別會載入來源文件並協調比較流程。

要取得元資料，首先使用 `Comparer` 實例載入來源文件，接著加入目標文件（可多個）。在比較引擎初始化後，對每個目標呼叫 `GetDocumentInfo()`，即可取得包含檔案類型、頁數與大小等屬性的 `IDocumentInfo` 物件。此方法在所有支援的格式上皆可一致運作。

### 步驟 1：以來源文件初始化 Comparer

`Comparer` 是 GroupDocs.Comparison 的核心類別，負責載入來源文件並協調比較操作。使用 `using` 區塊可自動釋放所有非受管理資源。

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **專業提示：** 你可以將任何 `Stream`（檔案、記憶體、雲端）傳入 `Comparer` 建構子，而不僅限於檔案路徑。

### 步驟 2：加入目標文件進行比較

`Add()` 方法接受額外的串流或檔案路徑，支援一對多的比較。

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **重要提示：** 新增文件的順序會影響最終報告中變更的標示方式。

### 步驟 3：從結果文件取得文件資訊

`IDocumentInfo` 在所有支援的格式中提供統一的文件元資料檢視，如檔案類型、頁數與大小。

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **了解資料：** 返回的物件在 DOCX、PDF、XLSX 與 PPTX 上的行為相同，因而可撰寫與格式無關的程式碼。

### 步驟 4：顯示文件資訊

取得 `IDocumentInfo` 實例後，你可以記錄、儲存或呈現其屬性。

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

最常使用的三個屬性為：

- **FileType** – 例如 `DOCX`、`PDF`、`XLSX`。  
- **PageCount** – 總頁數或投影片數。  
- **Size** – 以位元組為單位的檔案大小（對儲存計算很有用）。

## 如何在 .NET 中取得文件大小？

`Size` 屬性會返回檔案的位元組大小。

可直接透過 `IDocumentInfo` 實例的 `Size` 屬性取得文件大小。此屬性返回原始檔案的精確位元組數，讓你可轉換為千位元組或兆位元組以供顯示或儲存計算。它反映的是來源檔案大小，而非任何處理後的版本。

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **注意：** `Size` 值反映的是原始檔案大小，而非任何內部處理或壓縮後的大小。

## 常見使用情境與實務應用

- **批次處理：** 使用檔案類型將 DOCX 檔案導向 Word 專屬工作流程，PDF 檔案導向 PDF 最佳化管線。  
- **儲存管理：** 自動將大於 10 MB 的文件歸檔至冷儲存桶。  
- **使用者回饋：** 在比較前顯示頁數與大小，以設定合理的處理時間預期。  
- **品質保證：** 透過比較預期與實際頁數，驗證上傳檔案是否完整。

## 疑難排解常見問題

- **檔案存取錯誤：** 確認讀取權限，開發時使用絕對路徑。  
- **大型檔案記憶體壓力：** 優先使用串流 (`File.OpenRead`) 而非將整個檔案載入記憶體。  
- **空參考例外：** 若未加入目標，`FirstOrDefault()` 可能返回 `null`；在存取 `GetDocumentInfo()` 前務必檢查。  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **純文字格式的元資料有限制：** 如 `.txt` 可能不提供有意義的 `PageCount`。需防範缺失值。

## 效能考量

- **串流管理：** 總是將串流包在 `using` 陳述式中，以即時釋放檔案句柄。  
- **快取：** 將常用的元資料儲存於快取，以避免重複提取。  
- **批次操作：** 以群組方式處理文件，以減少開銷並提升吞吐量。

## 生產環境最佳實踐

- **健全的錯誤處理：** 將元資料提取包在 try‑catch 區塊中，以優雅處理損毀或不支援的檔案。  
- **完整的日誌記錄：** 為每次比較記錄文件類型、大小與頁數，以協助疑難排解與稽核合規。  
- **安全衛生：** 避免在 UI 訊息中暴露完整檔案路徑或內部伺服器資訊。  
- **資源釋放：** 及時釋放 `Comparer` 實例，特別是在處理大量同時請求的 Web 服務中。

## 進階情境

### 多目標文件

若將單一來源與多個目標比較，可遍歷 `Targets` 集合，並從每個目標提取元資料。

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### 基於元資料的條件處理

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### 將元資料儲存於資料庫

將 `FileType`、`PageCount` 與 `Size` 持久化於關聯式資料表，以支援數千次比較的報表與分析。

## 常見問與答

**Q: GroupDocs.Comparison for .NET 是否相容於各種文件格式？**  
A: 是的，它支援 **50+ 種格式**，包括 DOCX、PDF、PPTX、XLSX、TXT 等等，提供一致的元資料提取。

**Q: 我可以自訂比較設定而不影響元資料提取嗎？**  
A: 當然可以。敏感度、變更類型與輸出格式等設定與 `GetDocumentInfo()` 呼叫互不相干。

**Q: 有可供評估的試用版嗎？**  
A: 有，請從 [GroupDocs 發佈頁面](https://releases.groupdocs.com/) 下載免費試用版。試用版包含完整的元資料提取功能。

**Q: 我可以在哪裡取得實作問題的支援？**  
A: 可使用 [GroupDocs.Comparison 論壇](https://forum.groupdocs.com/c/comparison/12) 獲得社群協助與 GroupDocs 團隊的官方支援。

**Q: 生產部署有哪些授權選項？**  
A: GroupDocs 提供開發者、站點與 OEM 授權。購買選項列於 [GroupDocs 購買頁面](https://purchase.groupdocs.com/buy)。

---

**最後更新：** 2026-06-15  
**測試環境：** GroupDocs.Comparison 6.0 for .NET  
**作者：** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## 相關教學

- [文件元資料管理 .NET - GroupDocs.Comparison 完整指南](/comparison/net/metadata-management/)
- [取得文件屬性 C# .NET - 提取檔案元資料](/comparison/net/basic-usage/get-document-info-from-path/)
- [使用 GroupDocs.Comparison 保留目標元資料 – .NET 教學](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)