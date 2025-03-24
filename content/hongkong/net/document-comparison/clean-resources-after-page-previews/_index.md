---
title: 頁面預覽後清理資源
linktitle: 頁面預覽後清理資源
second_title: GroupDocs.Comparison .NET API
description: 了解如何使用 GroupDocs.Comparison for .NET 逐步比較文件。透過高效的文件管理增強您的 .NET 應用程式。
weight: 13
url: /zh-hant/net/document-comparison/clean-resources-after-page-previews/
---

# 頁面預覽後清理資源

## 介紹
在 .NET 開發領域，有效管理和比較文件對於從律師事務所到教育機構的各種應用程式至關重要。幸運的是，透過 GroupDocs.Comparison for .NET 等工具，開發人員可以輕鬆簡化比較文件的流程。在本教學中，我們將逐步探索如何利用 GroupDocs.Comparison for .NET 來比較文件。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
1.  GroupDocs.Comparison for .NET：從以下位置下載並安裝此程式庫[這裡](https://releases.groupdocs.com/comparison/net/).
2. .NET 開發環境：確保您的電腦上設定了有效的 .NET 開發環境。
3. 文件樣本：準備要比較的來源文件和目標文件。

## 導入命名空間
在您的 .NET 專案中，首先匯入必要的命名空間以存取 GroupDocs.Comparison for .NET 的功能。

```csharp
using System;
using System.IO;
```

## 第 1 步：定義輸出目錄和檔名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## 第 2 步：初始化比較器並新增文檔
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```
## 第 3 步：執行比較並產生輸出
```csharp
    comparer.Compare(File.Create(outputFileName));
```
## 第 4 步：產生文件預覽
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    document.GeneratePreview(previewOptions);
}
```
## 步驟5：顯示成功訊息
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## 結論
總之，GroupDocs.Comparison for .NET 提供了一個強大的解決方案，可以在 .NET 應用程式中輕鬆比較文件。透過遵循本教程中概述的步驟，開發人員可以將文件比較功能無縫整合到他們的專案中，從而提高生產力和效率。
## 常見問題解答
### GroupDocs.Comparison for .NET 是否與不同的文件格式相容？
是的，GroupDocs.Comparison for .NET 支援多種文件格式，包括 DOCX、PPTX、XLSX、PDF 等。
### 我可以自訂比較文件的輸出格式嗎？
當然，GroupDocs.Comparison for .NET 可以根據您的要求靈活地選擇輸出格式。
### 是否有可用於測試目的的試用版？
是的，您可以透過免費試用版探索 GroupDocs.Comparison for .NET 的功能[這裡](https://releases.groupdocs.com/).
### 對於與 GroupDocs.Comparison for .NET 相關的任何問題或查詢，如何獲得支援？
您可以從 GroupDocs.Comparison 社群論壇尋求協助[這裡](https://forum.groupdocs.com/c/comparison/12).
### 哪裡可以購買 GroupDocs.Comparison for .NET 的授權？
您可以從以下位置購買 GroupDocs.Comparison for .NET 的授權：[這個連結](https://purchase.groupdocs.com/buy).