---
"description": "了解如何使用 GroupDocs .NET 比較工具接受和拒絕文件中的變更。輕鬆簡化您的文件工作流程。"
"linktitle": "接受與拒絕 .NET GroupDocs 比較中的更改"
"second_title": "GroupDocs.Comparison .NET API"
"title": "接受與拒絕 .NET GroupDocs 比較中的更改"
"url": "/zh-hant/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
---

# 接受與拒絕 .NET GroupDocs 比較中的更改

## 介紹
在文件管理和協作領域，確保文件的準確性和完整性至關重要。 GroupDocs .NET 比較工具是一款強大的解決方案，可讓開發人員輕鬆接受和拒絕文件中的更改，從而簡化工作流程並提高生產力。本教學將指導您使用 GroupDocs .NET 比較工具接受和拒絕變更的流程，並將每個步驟分解，以便清晰易懂地實施。
## 先決條件
在深入學習本教程之前，請確保您已滿足以下先決條件：
### 環境設定
1. 安裝 .NET SDK：如果您還沒有安裝，請從 .NET 網站下載並安裝適合您的作業系統的 .NET SDK。
2. 安裝 GroupDocs .NET 比較：從提供的 [下載連結](https://releases.groupdocs.com/comparison/net/) 並按照安裝說明進行操作。
3. 熟悉 C# 程式設計：本教學假設您對 C# 程式語言及其語法有基本的了解。

## 導入命名空間
首先，將必要的命名空間匯入到您的專案中。這些命名空間將提供對文件比較和操作所需功能的存取。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## 步驟 1：指定輸出目錄和檔案名
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
確保更換 `"Your Document Directory"` 使用所需輸出目錄的路徑。
## 步驟 2：初始化比較器並比較文檔
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
此程式碼使用來源文件初始化 Comparer 對象，並新增目標文件進行比較。然後，執行比較過程。
## 步驟 3：檢索和操作更改
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
從比較中檢索變更並根據需要進行操作。在此範例中，更改先被拒絕，然後被接受。生成的文檔將相應地保存。

## 結論
總而言之，GroupDocs .NET 比較工具提供了一個無縫的解決方案，用於接受和拒絕文件中的變更。透過遵循本教程中概述的步驟，開發人員可以有效地將此功能整合到他們的應用程式中，從而確保文件的準確性並增強協作。
## 常見問題解答
### GroupDocs Compare for .NET 可以比較不同格式的文件嗎？
是的，GroupDocs Compare for .NET 支援各種格式的文件比較，例如 DOCX、PDF、PPTX 等。
### .NET 的 GroupDocs 比較是否與 .NET Core 相容？
是的，GroupDocs Compare for .NET 與 .NET Framework 和 .NET Core 也相容。
### 我可以自訂比較文件中更改的外觀嗎？
當然，GroupDocs Compare for .NET 提供了廣泛的選項來自訂變更的外觀，包括顏色、樣式等。
### GroupDocs Compare for .NET 是否支援多頁文件比較？
是的，GroupDocs Compare for .NET 支援精確、準確的多頁文件比較。
### GroupDocs Compare for .NET 有試用版嗎？
是的，您可以從提供的 GroupDocs 比較中免費試用 .NET [關聯](https://releases。groupdocs.com/).