---
categories:
- Image Processing
date: '2026-05-31'
description: 了解如何在 .NET 中使用 GroupDocs.Comparison 比較圖像，同時停用摘要頁面。本教學涵蓋設定、程式碼、效能技巧以及實務案例。
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: 比較圖像 .NET（無摘要）
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: 如何在 .NET 中比較圖像 – 跳過摘要頁面
type: docs
url: /zh-hant/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# 如何在 .NET 中比較圖像 – 跳過摘要頁面

當您需要在 .NET 應用程式中以程式方式 **how to compare images**（比較圖像）時，最不想要的就是浪費時間和儲存空間的額外摘要頁面。無論您是在構建品質控制線、內容管理管道，或是自動化視覺回歸測試套件，跳過摘要頁面都能為每次執行節省數秒，並保持磁碟佔用量精簡。

在本教學中，您將學習如何使用 **GroupDocs.Comparison for .NET** 來高效比較兩張圖像、設定庫以抑制摘要產生，並套用最佳實踐的效能技巧。我們還會探討此做法的重要性、何時使用以及如何避免常見陷阱。

## 快速解答
- **What is the fastest way to compare images without a summary page?** 使用 `Comparer` 搭配 `CompareOptions`，並將 `GenerateSummaryPage = false` 設定為關閉。  
- **Which library supports this out of the box?** GroupDocs.Comparison for .NET (v25.4.0+)。  
- **Do I need a license?** 是的，商業授權在正式環境中是必需的；免費試用可用於開發。  
- **Can I compare more than two images at once?** 當然可以 – 在 `Compare()` 之前多次呼叫 `Add()`。  
- **Is this approach suitable for large‑scale batch jobs?** 是的，結合批次處理與適當的記憶體管理即可。  

## 什麼是 GroupDocs.Comparison？
`GroupDocs.Comparison` 是一個 .NET 函式庫，可偵測文件與圖像之間的視覺差異，產生並排或疊加的結果。它支援 **50+ 輸入與輸出格式**，包括 JPEG、PNG、BMP、TIFF 與 GIF，且能在不將整個檔案載入記憶體的情況下處理數百頁的檔案。  

## 為何跳過摘要頁面？
根據函式庫的基準測試，停用摘要頁面可將僅圖像比較的 I/O 減少高達 **70 %**，並平均縮短約 **30 %** 的處理時間。當您只需要差異圖像（用於自動化測試或品質檢驗通過/失敗判斷）時，額外的 HTML 報告並無實質價值，只會佔用磁碟空間。  

## 前置條件與環境設定

### 您需要的項目
- **GroupDocs.Comparison for .NET** 版本 **25.4.0** 或更新版本  
- Visual Studio 2019 + 或任何相容 .NET 的 IDE  
- .NET Framework 4.6.1 + **或** .NET Core 2.0 +  
- 基本的 C# 知識與檔案 I/O 的熟悉度  

### 推薦的額外項目
- 包含一對範例圖像（例如 `source.png` 與 `target.png`）的小型測試專案。  
- 可選：如果您偏好服務導向架構，可設定依賴注入。  

### 為何這些前置條件很重要
指定的函式庫版本包含 `GenerateSummaryPage` 旗標與性能改進，而舊版缺乏這些功能。使用現代化的 IDE 可確保您能善用 NuGet 套件管理，並及早看到編譯時警告。  

## 如何安裝 GroupDocs.Comparison
GroupDocs.Comparison 可透過 NuGet 加入任何 .NET 專案，NuGet 會處理二進位檔的下載與專案檔的更新。選擇符合您工作流程的方法：Visual Studio 使用者可使用套件管理員主控台，或在命令列環境使用 .NET CLI。兩種指令皆會自動解析相依性並確保引用正確版本。  

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(將 `25.4.0` 替換為您計畫鎖定的確切版本。)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
兩個指令皆會將函式庫加入您的專案檔，並還原必要的二進位檔。  

**Pro Tip:** 在 `.csproj` 中釘住版本，以避免意外升級導致 API 行為變更。  

## 授權考量
GroupDocs.Comparison 在任何正式部署皆需授權。您可以先使用提供完整功能的 **free trial**，再升級為 **temporary license** 以進行延伸測試，最後取得 **full commercial license** 以供正式環境使用。請記得將 `GroupDocs.Comparison.lic` 檔案放置於應用程式根目錄，或以程式方式指定其路徑。  

## 基本專案設定
建立一個新的主控台應用程式（或整合至現有服務），並加入以下樣板程式碼。此片段示範在進入比較邏輯前所需的最小設定。  

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Important:** 總是使用 `Path.Combine()` 來處理檔案路徑。它會自動處理作業系統特定的路徑分隔符，避免在 Windows 與 Linux 容器之間移動時產生微妙的錯誤。  

## 步驟式實作指南

### 如何在不產生摘要頁面的情況下比較圖像？
`Comparer` 是 GroupDocs.Comparison 中的主要類別，負責協調文件與圖像的比較作業。`CompareOptions` 包含控制比較執行方式的設定，例如是否產生摘要頁面。載入來源圖像、設定 `CompareOptions` 以停用摘要、加入目標圖像，然後呼叫 `Compare()`。此方法會回傳包含差異圖像串流的 `ComparisonResult`，您可以將其寫入磁碟、透過網路傳送，或嵌入 UI 元件。此做法確保僅產生必要的差異圖，省去任何額外的 HTML 或 PDF 報告。  

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

上述程式碼以 **四個邏輯步驟** 完成整個比較，且僅寫入差異圖像，省略任何 HTML 或 PDF 摘要。  

### 步驟 1：初始化 Comparer 物件
`Comparer` 類別是所有比較作業的入口。它實作 `IDisposable`，因此將其包在 `using` 區塊中，可確保即使拋出例外，檔案句柄與非受管理記憶體也會及時釋放。  

### 步驟 2：設定 CompareOptions 以不產生摘要
在 `CompareOptions` 實例上設定 `GenerateSummaryPage = false`。此旗標告訴引擎跳過預設 HTML 報告的產生，這是圖像僅比較情境中額外 I/O 的主要來源。  

### 步驟 3：加入目標圖像以進行比較
您可以多次呼叫 `Add()`，在單一批次中將一個來源與多個目標進行比較。若需要針對每張圖像的自訂設定，每次呼叫皆可傳入各自的 `CompareOptions`。  

### 步驟 4：執行比較並儲存結果
`Comparer.Compare()` 承擔主要運算，並回傳 `ComparisonResult`。結果包含差異圖像的 `Stream`，您可以直接儲存至磁碟、透過網路傳送，或嵌入 UI 元件。  

## 完整的生產就緒方法
以下是一個可直接放入任何 .NET 服務的即用方法，內含路徑驗證、例外處理與可選的日誌掛鉤。  

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## 常見實作陷阱（以及如何避免）
- **Path Issues:** 總是使用 `File.Exists()` 驗證來源與目標檔案是否存在。缺少的檔案會拋出 `FileNotFoundException`，可於早期捕獲。  
- **Memory Pressure:** 大型圖像（10 MB +）可能佔用大量記憶體。請分批處理，若不需要精確像素比較，可考慮縮小尺寸。  
- **File Locks:** 確保沒有其他程序對圖像檔案持有排他鎖定。這在多執行緒或容器化環境中特別重要。  

## 實務應用與使用案例

### 製造業品質控制
生產線會捕捉每件產品的圖像，並與金標參考圖進行比較。跳過摘要頁面使系統能在毫秒內決定「通過」或「失敗」，保持高速流水線運作。  

### 內容管理系統
當使用者上傳資產時，CMS 可即時偵測重複或近似重複，防止儲存空間膨脹並提升搜尋相關性。差異圖像可作為縮圖儲存，以便快速視覺檢查。  

### 自動化 UI 測試（視覺回歸）
Selenium 或 Playwright 可捕捉網頁截圖，然後將其傳入此比較例程。差異圖像會突顯 UI 變更，且因未產生摘要，CI 流程保持快速且輕量。  

### 醫學影像（含稽核）
放射科工作流程有時需要標記連續掃描之間的變化。雖然仍可能產生詳細稽核日誌，但差異圖像本身可在不產生摘要頁面的情況下產出，減少大型 DICOM 轉換 PNG 的處理時間。  

## 效能考量與最佳化

### 記憶體管理最佳實踐
根據伺服器記憶體，將圖像以 **20–50** 張為一批處理。及時釋放每個 `Comparer` 實例，僅在長時間執行的工作中觀察到記憶體尖峰時才呼叫 `GC.Collect()`。  

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### 磁碟 I/O 最佳化
將輸入、輸出與暫存目錄放在同一快速 SSD 磁碟區。差異圖像儲存後立即刪除暫存檔，以避免不必要的磁碟使用。  

### 執行緒與非同步考量
GroupDocs.Comparison 在唯讀操作下是執行緒安全的，但避免在多執行緒間共享單一 `Comparer` 實例。相反地，請啟動獨立的任務：  

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## 常見問題排除

### 檔案路徑與權限錯誤
- **Symptom:** `FileNotFoundException` 或 `UnauthorizedAccessException`。  
- **Solution:** 使用 `Path.GetFullPath()` 來偵錯解析後的路徑，確保應用程式池身分（或 Docker 容器使用者）具有讀寫權限，並再次確認路徑未被環境變數截斷。  

### 記憶體與效能瓶頸
- **Symptom:** 執行緩慢或 `OutOfMemoryException`。  
- **Solution:** 在不需要精確像素比較時，將圖像調整為統一解析度（例如 1024 × 768）。使用 dotMemory 或內建效能分析器等工具監控記憶體。  

### 授權問題
- **Symptom:** 差異圖像帶有浮水印或 `LicenseException`。  
- **Solution:** 確認 `GroupDocs.Comparison.lic` 位於可執行檔目錄，或透過 `License license = new License(); license.SetLicense("path/to/license.file");` 明確載入。  

## 進階設定選項

### 自訂比較靈敏度
您可以透過調整 `CompareOptions` 上的 `Sensitivity` 屬性，微調引擎對細微像素變化（例如壓縮雜訊）的處理方式。較低的數值會使比較更嚴格。  

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### 輸出格式最佳化
若需要特定格式的差異圖像（PNG 與 JPEG），請設定 `OutputFormat` 屬性：  

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## 與流行 .NET 框架的整合

### ASP.NET Core 服務範例
公開一個輕量級的 HTTP 端點，接受兩個圖像串流，執行比較，並以 `FileResult` 回傳差異圖像。  

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### 依賴注入註冊
在 `Program.cs` 或 `Startup.cs` 中將 comparer 註冊為 scoped 服務：  

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## 常見問答

**Q: 跳過摘要頁面的主要優勢是什麼？**  
A: 它可將處理時間縮短最多 30 %，並將僅圖像比較的磁碟使用量降低約 70 %，對高吞吐量的管線至關重要。  

**Q: 在不產生摘要頁面的情況下，我仍能取得詳細的變更中繼資料嗎？**  
A: 可以。`ComparisonResult` 物件會公開 `Changes` 集合，內含每個偵測到的差異的程式化資訊。  

**Q: 支援哪些圖像格式？**  
A: JPEG、PNG、BMP、TIFF、GIF 以及其他多種格式——總計超過 50 種。  

**Q: 如何處理非常大的圖像（例如 >20 MB）？**  
A: 將它們分成較小的批次處理，必要時縮小尺寸，並監控記憶體使用。將 `Comparer` 放在 `using` 區塊中使用，可確保資源及時釋放。  

**Q: 此方法對多執行緒應用程式安全嗎？**  
A: 是的，只要每個執行緒自行建立 `Comparer` 實例。共享單一實例可能導致競爭條件。  

## 其他資源
- [GroupDocs.Comparison 文件](https://docs.groupdocs.com/comparison/net/)  
- [API 參考](https://reference.groupdocs.com/comparison/net/)  
- [下載](https://releases.groupdocs.com/comparison/net/)  
- [購買](https://purchase.groupdocs.com/buy)  
- [免費試用](https://releases.groupdocs.com/comparison/net/)  
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)  
- [支援論壇](https://forum.groupdocs.com/c/comparison/)  

---

**最後更新：** 2026-05-31  
**測試環境：** GroupDocs.Comparison 25.4.0 for .NET  
**作者：** GroupDocs  

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## 相關教學
- [圖像比較 .NET - 以程式方式比較圖像](/comparison/net/image-comparison/compare-images-from-path/)  
- [圖像比較 .NET - 從串流比較圖像](/comparison/net/image-comparison/compare-images-from-stream/)  
- [GroupDocs Comparison .NET 教學 - 完整基礎使用指南](/comparison/net/basic-usage/)