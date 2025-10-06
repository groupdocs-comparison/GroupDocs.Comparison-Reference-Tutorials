---
"date": "2025-05-05"
"description": "了解如何使用 GroupDocs.Comparison for .NET 高效比較資料夾，並將結果儲存為 TXT 或 HTML 格式。使用詳細的 C# 程式碼範例來增強您的工作流程。"
"title": "如何使用 GroupDocs.Comparison .NET 比較資料夾並將結果儲存為 TXT/HTML"
"url": "/zh-hant/net/advanced-comparison/groupdocs-comparison-net-folder-comparison-tutorial/"
"weight": 1
type: docs
---
# 如何使用 GroupDocs.Comparison .NET 實作資料夾比較並將結果儲存為 TXT/HTML

## 介紹

有效地比較資料夾中的大量文件對於開發人員來說可能是一項艱鉅的任務，尤其是在複雜的專案中。 **適用於 .NET 的 GroupDocs.Comparison** 提供了一個強大的解決方案，簡化了資料夾比較並將結果儲存為 TXT 或 HTML 檔案。

本教學將指導您使用 GroupDocs.Comparison 自動執行資料夾內的文件比較，從而提高開發工作流程的效率和可靠性。完成本指南後，您將能夠：
- 了解使用 GroupDocs.Comparison for .NET 進行資料夾比較的基礎知識。
- 配置選項以將結果儲存為 TXT 或 HTML 檔案。
- 編寫C#程式碼實現資料夾比較。
- 使用 GroupDocs.Comparison 功能優化效能。

讓我們先來了解必要的先決條件！

## 先決條件

在開始之前，請確保您具備以下條件：

### 所需的庫和版本
- **適用於 .NET 的 GroupDocs.Comparison**：建議使用 25.4.0 版本。
- **.NET 框架/SDK**：相容.NET Core及更高版本。

### 環境設定要求
- Visual Studio 或任何相容的 C# 開發環境。
- 透過 NuGet 或 .NET CLI 存取終端以安裝套件。

### 知識前提
- 對 C# 程式設計有基本的了解。
- 熟悉.NET中的檔案系統操作。

滿足這些先決條件後，讓我們為您的專案設定 GroupDocs.Comparison！

## 為 .NET 設定 GroupDocs.Comparison

要將 GroupDocs.Comparison 整合到您的專案中，您需要安裝該程式庫。操作方法如下：

**NuGet 套件管理器控制台**
```shell
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI**
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

### 許可證取得步驟

要開始使用 GroupDocs.Comparison，您可以選擇免費試用或購買許可證：
- **免費試用**：使用有限的所有功能。
- **臨時執照**：取得臨時許可證來評估全部功能。
- **購買**：購買許可證以供長期使用。

您可以透過在程式碼中套用許可證來管理許可證，確保可以存取所有功能。

### 基本初始化和設定

以下是在 C# 應用程式中初始化 GroupDocs.Comparison 的方法：

```csharp
using System;
using GroupDocs.Comparison;

class Program
{
    static void Main()
    {
        // 如果可用，則初始化許可證
        License license = new License();
        license.SetLicense("Path to your license file");

        Console.WriteLine("GroupDocs.Comparison for .NET is ready to use.");
    }
}
```

## 實施指南

讓我們使用 GroupDocs.Comparison 實作資料夾比較並將結果儲存為 TXT 或 HTML 檔案。

### 比較資料夾並將結果儲存為 TXT

#### 概述
此功能可讓您比較兩個資料夾並在文字檔案中輸出差異，從而可以輕鬆地逐行查看變更。

#### 步驟 1：配置比較選項

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

string sourceFolder = "YOUR_DOCUMENT_DIRECTORY/SOURCE_FOLDER";
string targetFolder = "YOUR_DOCUMENT_DIRECTORY/TARGET_FOLDER";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// 設定 TXT 輸出的比較選項
Options.CompareOptions compareOptionsTxt = new Options.CompareOptions
{
    DirectoryCompare = true,
    FolderComparisonExtension = GroupDocs.Comparison.Options.FolderComparisonExtension.Txt
};
```

#### 步驟2：初始化比較器對象

```csharp
Comparer comparerTxt = new Comparer(sourceFolder, compareOptionsTxt);
// 新增用於比較的目標資料夾
comparerTxt.Add(targetFolder, compareOptionsTxt);
```

#### 步驟3：進行比較並儲存結果

```csharp
string txtOutputFileName = Path.Combine(outputDirectory, "ComparisonResult.txt");
comparerTxt.Compare(txtOutputFileName, compareOptionsTxt);

Console.WriteLine("TXT file with comparison results saved successfully.");
```

### 比較資料夾並將結果儲存為 HTML

#### 概述
此功能可產生突出顯示變更的 HTML 報告，幫助您直觀地看到差異。

#### 步驟 1：配置 HTML 輸出的比較選項

```csharp
// 設定 HTML 輸出的比較選項
Options.CompareOptions compareOptionsHtml = new Options.CompareOptions
{
    DirectoryCompare = true,
    FolderComparisonExtension = GroupDocs.Comparison.Options.FolderComparisonExtension.Html
};
```

#### 步驟 2：初始化 HTML 的 Comparer 對象

```csharp
Comparer comparerHtml = new Comparer(sourceFolder, compareOptionsHtml);
// 將目標資料夾加入比較中
comparerHtml.Add(targetFolder, compareOptionsHtml);
```

#### 步驟 3：進行比較並將結果儲存為 HTML

```csharp
string htmlOutputFileName = Path.Combine(outputDirectory, "ComparisonResult.html");
comparerHtml.Compare(htmlOutputFileName, compareOptionsHtml);

Console.WriteLine("HTML file with comparison results saved successfully.");
```

### 故障排除提示
- 確保正確指定目錄路徑。
- 檢查輸出目錄中的寫入權限。
- 驗證所有必要的文件和依賴項是否存在。

## 實際應用

以下是一些資料夾比較可能有益的實際用例：
1. **程式碼審查**：比較程式碼庫的不同版本以識別變化。
2. **資料備份驗證**：確保備份與原始資料資料夾相符。
3. **配置管理**：追蹤跨環境的設定檔的變化。
4. **文件版本控制**：保持文件更新和修訂的一致性。
5. **與 CI/CD 管道集成**：作為部署過程的一部分，自動進行比較檢查。

## 性能考慮

為確保使用 GroupDocs.Comparison 時獲得最佳效能：
- 如果可能的話，盡量減少每個資料夾中的檔案數量以減少處理時間。
- 使用高效的資料結構進行文件儲存和存取。
- 監控記憶體使用情況並在 .NET 應用程式中有效管理資源。

## 結論

恭喜！您已經學習如何使用 GroupDocs.Comparison for .NET 實作資料夾比較，並將結果儲存為 TXT 或 HTML 格式。這些技能將提升您高效管理和比較大型資料集的能力。

接下來，考慮探索 GroupDocs.Comparison 的更多高級功能，例如比較特定文件類型或將該工具整合到更大的應用程式中。

準備好將這些知識付諸實踐了嗎？立即在您的專案中實施這些解決方案！

## 常見問題部分

**問題 1：我可以在 Linux 上使用 GroupDocs.Comparison for .NET 嗎？**
- 是的，它透過 .NET Core 支援 Linux 等跨平台環境。

**Q2：比較時如何處理大檔案？**
- 使用高效的記憶體管理方法，並考慮在必要時將檔案分解為較小的區塊。

**問題 3：我可以比較的文件數量有限制嗎？**
- 雖然從技術上來說沒有嚴格的限制，但效能可能會根據系統資源而有所不同。

**Q4：GroupDocs.Comparison 可以處理加密檔案嗎？**
- 目前不支援直接比較加密檔案。如有必要，您需要先解密。

**Q5：如何解決資料夾比較過程中的錯誤？**
- 檢查控制台輸出的特定錯誤訊息並確保滿足所有先決條件。

## 資源

進一步探索：
- **文件**： [GroupDocs.Comparison .NET 文檔](https://docs.groupdocs.com/comparison/net/)
- **API 參考**： [GroupDocs API 參考](https://reference.groupdocs.com/comparison/net/)
- **下載**： [GroupDocs 發布](https://releases.groupdocs.com/comparison/net/)
- **購買**： [購買 GroupDocs 比較](https://purchase.groupdocs.com/buy)
- **免費試用**： [免費試用](https://releases.groupdocs.com/comparison/net/)
- **臨時執照**： [申請臨時許可證](https://purchase.groupdocs.com/temporary-license)