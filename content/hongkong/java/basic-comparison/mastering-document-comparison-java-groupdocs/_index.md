---
"date": "2025-05-05"
"description": "了解如何使用 GroupDocs.Comparison for Java 實現精確的自動化文件比較。輕鬆自訂樣式、調整敏感度以及忽略頁首/頁尾。"
"title": "使用 GroupDocs.Comparison API 在 Java 中掌握文件比較"
"url": "/zh-hant/java/basic-comparison/mastering-document-comparison-java-groupdocs/"
"weight": 1
type: docs
---
# 使用 GroupDocs.Comparison API 掌握 Java 中的文件比較

## 介紹

厭倦了手動比較文件？無論是識別頁首、頁尾或內容的變更，文件比較都可能是一項艱鉅的任務。 GroupDocs.Comparison for Java 程式庫可以自動化並增強此過程，精準便捷。

本教學將指導您如何利用 Java 中的 GroupDocs.Comparison 自訂文件比較樣式、調整敏感度設定、忽略頁首/頁尾比較、設定輸出紙張尺寸等。完成本教程後，您將能夠有效地簡化工作流程。

**您將學到什麼：**
- 在文件比較期間忽略頁首和頁尾。
- 透過樣式調整來自訂變更。
- 調整比較敏感度以進行詳細分析。
- 在 Java 應用程式中設定輸出紙張尺寸。
- 在現實場景中實現這些功能。

在深入實際操作之前，請確保您已具備必要的先決條件。

## 先決條件

若要開始使用 GroupDocs.Comparison for Java，請確保您具備以下條件：
1. **Java 開發工具包 (JDK)：** 確保你的機器上安裝了 JDK。 JDK 8 以上版本即可。
2. **Maven：** 本教學假設您使用 Maven 來管理專案依賴項。
3. **GroupDocs.Comparison 庫：**
   - 將以下相依性新增至您的 `pom.xml`：

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/comparison/java/</url>
    </repository>
</repositories>
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-comparison</artifactId>
        <version>25.2</version>
    </dependency>
</dependencies>
```
4. **執照：** 從 GroupDocs 取得免費試用版、臨時授權或購買完整版。

完成這些設定後，您就可以開始在 Java 應用程式中實作文件比較功能了。

## 為 Java 設定 GroupDocs.Comparison

確保我們的環境配置正確：

### 透過 Maven 安裝

將上述 XML 程式碼片段加入你的項目 `pom.xml`。此步驟可確保 Maven 識別必要的儲存庫和相依性。 

### 許可證獲取
- **免費試用：** 從下載試用版 [GroupDocs 下載](https://releases。groupdocs.com/comparison/java/).
- **臨時執照：** 透過申請臨時許可證 [GroupDocs 支持](https://purchase.groupdocs.com/temporary-license/) 評估全部特徵。
- **購買：** 如需長期使用，請透過以下方式購買許可證 [GroupDocs 購買](https://purchase。groupdocs.com/buy).

根據 GroupDocs 文件取得並設定許可證文件後，請依下列方式初始化 GroupDocs.Comparison：

```java
// 基本初始化範例
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

## 實施指南

### 功能 1：忽略頁首/頁尾比較

**概述：** 頁首和頁尾通常包含頁碼或文件標題等訊息，這些訊息可能與內容變化比較無關。

#### 設定選項

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import java.io.FileOutputStream;

public class IgnoreHeaderFooterExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/IgnoreHeaderFooter_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_with_footer.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target_with_footer.docx");

            // 設定比較選項以忽略頁首和頁尾
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

#### 解釋
- **`CompareOptions.Builder().setHeaderFootersComparison(false)`**：此設定指示庫跳過頁首和頁尾比較。
- **`try-with-resources`：** 確保所有串流在使用後都正確關閉。

### 功能2：設定輸出紙張尺寸

**概述：** 自訂輸出紙張尺寸對於建立易於列印的文件至關重要。以下是如何在文件比較過程中進行調整。

#### 實施步驟

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.PaperSize;

public class SetOutputPaperSizeExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetOutputPaperSize_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // 將紙張尺寸設定為A6
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### 解釋
- **`CompareOptions.Builder().setPaperSize(PaperSize.A6)`**：將輸出紙張尺寸設定為 A6。

### 功能 3：調整比較敏感度

**概述：** 微調比較敏感度有助於辨識哪怕是細微的變化。調整方法如下：

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // 將靈敏度設定為 100
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### 解釋
- **`CompareOptions.Builder().setSensitivityOfComparison(100)`**：調整檢測變化的靈敏度等級。

### 功能 4：自訂變更樣式（使用 Streams）

**概述：** 區分插入、刪除和更改的文本，使比較更加直觀。以下是使用流自訂樣式的方法：

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.save.SaveOptions;
import com.groupdocs.comparison.options.style.StyleSettings;

import java.awt.Color;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class CustomizeChangesStylesStreamExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/CustomizeChangesStylesStream_result.docx";

        try (InputStream sourceFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/source_word.docx");
             InputStream targetFile = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");
             OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer(sourceFile)) {

            comparer.add(targetFile);

            // 自訂更改樣式
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // 綠色表示插入
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // 紅色表示刪除
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // 藍色表示更改

            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setInsertedItemStyle(insertedStyle)
                    .setDeletedItemStyle(deletedStyle)
                    .setChangedItemStyle(changedStyle)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

#### 解釋
- **自訂樣式設定**： 使用 `StyleSettings` 定義插入（綠色）、刪除（紅色）和更改（藍色）的突出顯示顏色。
- **`CompareOptions.Builder()`：** 在比較過程中套用這些樣式。

## 結論

利用 GroupDocs.Comparison for Java，您可以精確地自動執行文件比較。本教學介紹如何忽略頁首/頁尾、設定輸出紙張大小、調整靈敏度以及自訂變更樣式。實作這些功能將簡化您的工作流程並增強 Java 應用程式中的文件分析功能。

## 常見問題解答

### 1. 在 GroupDocs for Java 中比較時可以忽略頁首和頁尾嗎？  

是的，使用 `setHeaderFootersComparison(false)` 在 `CompareOptions` 從比較中排除頁首和頁尾。

### 2. 如何使用 GroupDocs 在 Java 中設定輸出紙張大小？  

申請 `setPaperSize(PaperSize.A6)` 或其他尺寸 `CompareOptions` 自訂最終文件的紙張尺寸。

### 3. 是否可以微調比較敏感度？  

是的，使用 `setSensitivityOfComparison()` 在 `CompareOptions` 調整靈敏度，相應地檢測微小或重大變化。

### 4. 我可以在比較過程中設定插入、刪除和更改文字的樣式嗎？  

當然，可以透過以下方式自訂樣式 `StyleSettings` 針對不同的變更類型並應用它們 `CompareOptions`。

### 5. 使用 Java 中的 GroupDocs 比較的先決條件是什麼？  

安裝 JDK，使用 Maven 管理依賴項，取得許可證，並將 GroupDocs.Comparison 庫新增至您的專案。