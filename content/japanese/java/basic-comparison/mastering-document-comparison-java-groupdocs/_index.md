---
categories:
- Java Development
date: '2026-05-16'
description: GroupDocs.Comparison for Java を使用して Java の Excel ファイルを比較する方法を学び、PDF、
  大容量ドキュメント、 暗号化ファイルの例をご紹介します。
keywords:
- compare excel files java
- compare pdf documents java
- groupdocs comparison java
- excel file diff java
- document comparison api
lastmod: '2026-05-16'
linktitle: Java Excel ファイル比較ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-05-16'
  description: Learn how to compare excel files java using GroupDocs.Comparison for
    Java, with examples for PDF, large documents, and encrypted files.
  headline: Compare Excel Files Java with GroupDocs Document Comparison API
  type: TechArticle
- description: Learn how to compare excel files java using GroupDocs.Comparison for
    Java, with examples for PDF, large documents, and encrypted files.
  name: Compare Excel Files Java with GroupDocs Document Comparison API
  steps:
  - name: '**Java Development Kit (JDK):** 8 or higher (JDK 11+ recommended)'
    text: '**Java Development Kit (JDK):** 8 or higher (JDK 11+ recommended)'
  - name: '**Build Tool:** Maven 3.6+ or Gradle 6.0+'
    text: '**Build Tool:** Maven 3.6+ or Gradle 6.0+'
  - name: '**Memory:** Minimum **4 GB RAM** for large files'
    text: '**Memory:** Minimum **4 GB RAM** for large files'
  - name: '**Storage:** At least **500 MB** free for temporary comparison data'
    text: '**Storage:** At least **500 MB** free for temporary comparison data'
  type: HowTo
- questions:
  - answer: Yes, call `setHeaderFootersComparison(false)` on `CompareOptions`. This
      removes dynamic header/footer noise from the diff.
    question: Can I ignore headers and footers during comparison in GroupDocs for
      Java?
  - answer: Use `setPaperSize(PaperSize.A6)` (or any other enum value) in `CompareOptions`.
      This generates a print‑ready PDF in the chosen size.
    question: How do I set output paper size in Java using GroupDocs?
  - answer: Absolutely. Invoke `setSensitivityOfComparison(85)` for legal contracts
      or `setSensitivityOfComparison(45)` for marketing drafts to control granularity.
    question: Is it possible to fine‑tune comparison sensitivity for different document
      types?
  - answer: Yes. Create a `StyleSettings` instance for each change type and assign
      colors, fonts, or borders before passing it to `CompareOptions`.
    question: Can I customize the styling of inserted, deleted, and changed text during
      comparison?
  - answer: You need JDK 8+ (JDK 11+ recommended), Maven 3.6+ or Gradle 6.0+, at least
      4 GB RAM, and a valid GroupDocs license (free trial available).
    question: What are the prerequisites to get started with GroupDocs Comparison
      in Java?
  type: FAQPage
tags:
- document-comparison
- java-api
- automation
- groupdocs
title: GroupDocs Document Comparison API を使用した Java の Excel ファイル比較
type: docs
url: /ja/java/basic-comparison/mastering-document-comparison-java-groupdocs/
weight: 1
---

# Excel ファイルの比較 Java と GroupDocs Document Comparison API

手作業で文書を何時間も比較し、行ごとに変更点を探したことはありませんか？契約書の改訂を追跡したり、コードドキュメントをレビューしたり、財務レポートのために **compare excel files java** が必要だったりする場合でも、手動の文書比較は時間がかかり、エラーが起きやすいです。このガイドでは、GroupDocs.Comparison for Java を使用して Excel ワークブック（および他の多くの形式）を高速かつ信頼性のある方法で比較する方法を学びます。

## クイック回答

`Comparer` クラスは、ソース文書を読み込み比較を実行するコアコンポーネントです。  
`CompareOptions` は、比較の実行方法を制御する設定可能なパラメータのセットを提供します。  
`StyleSettings` を使用すると、出力レポート内の挿入、削除、変更された要素の視覚的外観をカスタマイズできます。

- **Can GroupDocs compare Excel files in Java?** はい、`.xlsx` ファイルを `Comparer` クラスで読み込み `compare` を呼び出すだけです。  
- **How to ignore headers/footers?** `CompareOptions` で `setHeaderFootersComparison(false)` を設定します。  
- **What about large PDFs?** JVM ヒープを増やし、メモリ最適化を有効にし、ストリーミングモードを使用します。  
- **Can I compare password‑protected PDFs?** `Comparer` 作成時にパスワードを提供します。  
- **Is there a way to change highlight colors?** 挿入、削除、変更項目に対して `StyleSettings` を使用します。

## compare excel files java とは？

`compare excel files java` は、Java を使用して 2 つの Excel ワークブック間のセルレベルの差分をプログラムで検出するプロセスです。GroupDocs.Comparison API は各スプレッドシートを読み込み、すべてのセル、行、数式を評価し、追加、削除、変更を明確なビジュアル形式でハイライトした差分レポートを生成します。

## Java ドキュメント比較 API を使用する理由

### 自動化のビジネスケース

手動の文書比較は面倒なだけでなく、リスクも伴います。調査によると、人間は手動で文書をレビューする際に重要な変更の約 **20 %** を見逃すことが示されています。API を使用すればこのリスクを排除し、測定可能な生産性向上を実現できます。

- **99.9 % Accuracy** – 文字レベルの変更すべてが捕捉されます。  
- **Speed** – 標準サーバー上で 100 ページの PDF を **30 秒** 未満で比較できます。  
- **Consistency** – すべての文書タイプでハイライトとレポートが統一されます。  
- **Scalability** – 手作業なしで数千ファイルをバッチ処理できます。

### ドキュメント比較 API を使用すべき時

以下のようなケースで最大の効果が得られます。

- **Review legal contracts** – 条項の改訂を自動的にフラグ付けします。  
- **Track technical documentation** – API 仕様リリース間で何が変更されたか正確に把握します。  
- **Manage content assets** – マーケティングコピー、ユーザーマニュアル、ブログドラフトを比較します。  
- **Audit compliance** – ポリシー更新が確実に記録・追跡されます。  
- **Supplement version control** – コード以外のアーティファクトに対して人間が読める差分を提供します。

## サポートされているファイル形式と機能

GroupDocs.Comparison for Java は **50+** の入力・出力形式をサポートしており、以下が含まれます。

- **ドキュメント**: DOCX, DOC, PDF, RTF, ODT  
- **スプレッドシート**: XLSX, XLS, CSV, ODS  
- **プレゼンテーション**: PPTX, PPT, ODP  
- **テキスト**: TXT, HTML, XML, MD  
- **画像**: PNG, JPEG, BMP, GIF (ビジュアル比較)

### 高度な機能

- パスワード保護された文書の比較  
- 多言語検出と比較  
- 文書タイプごとのカスタム感度設定  
- 複数文書ペアのバッチ処理  
- クラウドネイティブおよびオンプレミスのデプロイオプション  

## 前提条件とセットアップ

### システム要件

1. **Java Development Kit (JDK):** 8 以上 (JDK 11+ 推奨)  
2. **Build Tool:** Maven 3.6+ または Gradle 6.0+  
3. **Memory:** 大きなファイル用に最低 **4 GB RAM**  
4. **Storage:** 一時比較データ用に少なくとも **500 MB** の空き容量  

### Maven 設定

`pom.xml` に GroupDocs リポジトリと依存関係を追加します。これにより公式リリースが取得されます。

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

### ライセンス設定

**開発・テスト用:**  
- **Free Trial:** [GroupDocs Downloads](https://releases.groupdocs.com/comparison/java/) からダウンロード – ウォーターマーク付き出力が含まれます。  
- **Temporary License:** [GroupDocs Support](https://purchase.groupdocs.com/temporary-license/) で 30 日間のフルアクセスを取得します。  

**本番環境用:**  
- **Full License:** 無制限の商用利用のために [GroupDocs Purchase](https://purchase.groupdocs.com/buy) で購入します。  

アプリケーション起動時にライセンスを初期化します。

```java
// License initialization - do this once at application startup
com.groupdocs.comparison.License license = new com.groupdocs.comparison.License();
license.setLicense("path/to/your/license/file.lic");
```

**Pro Tip:** ライセンスファイルを resources フォルダーに保存し、`getClass().getResourceAsStream()` でロードするとポータブルに展開できます。

## コア実装ガイド

### 機能 1: ヘッダーとフッターの比較を無視する

`setHeaderFootersComparison` メソッドはヘッダーとフッターの内容の比較を無効にし、差分に無関係な違いが表示されないようにします。  

**Why This Matters:** ヘッダーとフッターにはタイムスタンプやページ番号など動的データが含まれ、バージョン間で変わりますが、コンテンツレビューには関係ありません。無視することでノイズが減り、処理が高速化します。  

**Real‑World Scenario:** フッターに新しい日付スタンプが追加された 2 つの契約ドラフトを比較する場合、条項の変更だけが重要です。

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

            // Set comparison options to ignore headers and footers
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setHeaderFootersComparison(false)
                    .build();

            final Path resultPath = comparer.compare(resultStream, new SaveOptions(), compareOptions);
        }
    }
}
```

**Key Benefits:**  
- 差分結果がクリーンになる  
- 誤検出が減少する  
- それらのセクションをスキップするため比較が高速になる  

### 機能 2: プロフェッショナルレポート用の出力用紙サイズを設定する

`PaperSize` 列挙型は生成される PDF が使用する標準ページ寸法を定義します。  

**Business Context:** 法務チームは裁判所への提出やクライアントへの納品のため、特定の用紙サイズの印刷可能な比較レポートを頻繁に必要とします。  

**How to Apply:** `CompareOptions` で `PaperSize` 列挙型を使用して目的のサイズを指定します。

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

            // Set the paper size to A6
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setPaperSize(PaperSize.A6)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

サポートされるサイズには A0‑A10、Letter、Legal、Tabloid、カスタム寸法が含まれます。欧州クライアントには A4、米国パートナーには Letter を選択してください。

### 機能 3: 比較感度の微調整

`setSensitivityOfComparison` メソッドは、比較エンジンが変更を評価する粒度を調整します。大きな構造的編集から単一文字の差分まで幅広く設定可能です。  

**The Challenge:** 文書カテゴリにより必要な粒度は異なります。法務契約は文字レベルの精度が必要ですが、マーケティングコピーは段落レベルで十分な場合があります。  

**Sensitivity Scale (0‑100):**  
- **0‑25:** 大きな変更のみ（段落の追加/削除）  
- **26‑50:** 中程度の変更（文の編集）  
- **51‑75:** 詳細な変更（単語レベル）  
- **76‑100:** 粒度の高い変更（文字レベル）  

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.CompareOptions;

public class AdjustComparisonSensitivityExample {
    public static void main(String[] args) throws Exception {
        String outputFileName = "YOUR_OUTPUT_DIRECTORY/AdjustComparisonSensitivity_result.docx";

        try (OutputStream resultStream = new FileOutputStream(outputFileName);
             Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_word.docx")) {

            comparer.add("YOUR_DOCUMENT_DIRECTORY/target1_word.docx");

            // Set sensitivity to 100 for maximum detail
            CompareOptions compareOptions = new CompareOptions.Builder()
                    .setSensitivityOfComparison(100)
                    .build();

            final Path resultPath = comparer.compare(resultStream, compareOptions);
        }
    }
}
```

**Best‑Practice Settings:**  
- **Legal Docs:** 90‑100  
- **Marketing Content:** 40‑60  
- **Technical Specs:** 70‑80  

### 機能 4: 変更スタイルをカスタマイズして視覚的コミュニケーションを向上させる

`StyleSettings` オブジェクトを使用すると、挿入、削除、変更されたコンテンツの色、フォント、枠線、その他の視覚的手がかりを定義できます。  

**Why Custom Styles Matter:** デフォルトのハイライトは企業のブランディングやアクセシビリティガイドラインと衝突することがあります。色・フォント・枠線を調整することで、差分が即座に理解しやすくなります。  

**Example:** 削除は赤背景、挿入は緑、変更は青で表示します。

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

            // Customize change styles for professional appearance
            StyleSettings insertedStyle = new StyleSettings();
            insertedStyle.setHighlightColor(Color.GREEN); // Green for additions
            StyleSettings deletedStyle = new StyleSettings();
            deletedStyle.setHighlightColor(Color.RED); // Red for deletions
            StyleSettings changedStyle = new StyleSettings();
            changedStyle.setHighlightColor(Color.BLUE); // Blue for modifications

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

`StyleSettings` の高度なオプションでは、フォントの太さ、サイズ、背景の不透明度、枠線スタイル、取り消し線の挙動なども変更できます。

## 比較レポートで Java の用紙サイズを設定する方法

`CompareOptions` の `PaperSize` 列挙型を直接使用して用紙サイズを設定します。`PaperSize.A6` を任意のサポート定数（例: `PaperSize.LETTER`）に置き換えて地域の印刷基準に合わせます。これにより生成された PDF レポートが手動でスケーリングすることなく正しく印刷されます。さらに、カスタム余白や向きフラグと組み合わせて、組織の文書提出ガイドラインに合致したレイアウトを作成でき、常にプロフェッショナルな外観が保証されます。

## よくある問題とトラブルシューティング

### 大規模文書のメモリ管理

**Problem:** 50 MB を超えるファイルを比較すると `OutOfMemoryError` が発生します。  
**Solution:** JVM ヒープを増やす（例: `-Xmx8g`）とストリーミングモードを有効にします。

```bash
# Increase heap size for large document processing
java -Xmx4g -XX:MaxMetaspaceSize=512m YourComparisonApp
```

### 破損またはパスワード保護されたファイルの処理

`PasswordRequiredException` は、パスワードが提供されていない暗号化文書に API が遭遇したときにスローされます。  

**Issue:** ロックされた文書の比較が失敗します。  
**Prevention:** `Comparer` を構築する際にパスワードを提供し、`PasswordRequiredException` をキャッチします。

```java
// Check document accessibility before comparison
try {
    Comparer comparer = new Comparer(sourceFile, "password123");
    // Document loaded successfully, proceed with comparison
} catch (PasswordRequiredException ex) {
    // Handle password‑protected documents
    log.error("Document requires password: " + sourceFile);
} catch (CorruptedFileException ex) {
    // Handle corrupted files gracefully
    log.error("File corruption detected: " + sourceFile);
}
```

### バッチ処理のパフォーマンス最適化

**Challenge:** 100 件以上の文書ペアを効率的に処理すること。  
**Solution:** 固定サイズのスレッドプールを使用し、各比較を個別タスクとして送信します。

```java
ExecutorService executor = Executors.newFixedThreadPool(4);
List<Future<ComparisonResult>> futures = new ArrayList<>();

for (DocumentPair pair : documentPairs) {
    futures.add(executor.submit(() -> compareDocuments(pair)));
}

// Wait for all comparisons to complete
for (Future<ComparisonResult> future : futures) {
    ComparisonResult result = future.get();
    // Process results
}
executor.shutdown();
```

### フォーマット固有の問題

- **Scanned PDFs:** 比較前に OCR 前処理を適用します。  
- **Word Documents:** 誤検出を防ぐために既存の “Track Changes” を無効にします。  
- **Embedded Objects:** 正確性を保つためにオブジェクトを抽出し、個別に比較します。  

## ベストプラクティスとパフォーマンスのヒント

### 1. 文書の前処理

比較前に不要なメタデータを除去し、フォントを標準化すると速度と精度が向上します。

```java
// Example preprocessing workflow
public void preprocessDocument(String filePath) {
    // Remove comments and tracked changes
    // Standardize formatting
    // Extract text‑only version for pure content comparison
}
```

### 2. 最適な構成プロファイル

各文書タイプ（法務、マーケティング、技術）用に再利用可能な `CompareOptions` プリセットを作成し、パイプライン全体で再利用します。

```java
public class ComparisonProfiles {
    public static CompareOptions getLegalDocumentProfile() {
        return new CompareOptions.Builder()
                .setSensitivityOfComparison(95)
                .setHeaderFootersComparison(false)
                .setShowRevisions(true)
                .build();
    }
    
    public static CompareOptions getMarketingContentProfile() {
        return new CompareOptions.Builder()
                .setSensitivityOfComparison(45)
                .setIgnoreFormatting(true)
                .setFocusOnContent(true)
                .build();
    }
}
```

### 3. 堅牢なエラーハンドリングとロギング

`ComparisonException` は比較プロセス中の失敗を示し、詳細な診断情報を提供します。比較呼び出しを try‑catch ブロックでラップし、`ComparisonException` の詳細をログに記録し、必要に応じて安全なデフォルトにフォールバックします。

```java
public ComparisonResult safeCompareDocuments(String source, String target) {
    try {
        return performComparison(source, target);
    } catch (Exception ex) {
        logger.error("Comparison failed for {} vs {}: {}", source, target, ex.getMessage());
        return ComparisonResult.failure(ex.getMessage());
    }
}
```

### 4. キャッシュとスマートリユース

- 同一ファイルペアの差分結果をキャッシュする。  
- 文書の指紋（ハッシュ）を保存して変更のないファイルをスキップする。  
- 非クリティカルな比較は非同期キューで処理し、UI の応答性を保つ。  

## 実際の統合シナリオ

### シナリオ 1: 自動契約レビュー パイプライン

```java
@Service
public class ContractReviewService {
    
    public void processContractRevision(String originalContract, String revisedContract) {
        CompareOptions legalOptions = ComparisonProfiles.getLegalDocumentProfile();
        
        try (Comparer comparer = new Comparer(originalContract)) {
            comparer.add(revisedContract);
            Path result = comparer.compare(generateOutputPath(), legalOptions);
            
            // Send comparison report to legal team
            emailService.sendComparisonReport(result, legalTeamEmails);
            
            // Log changes for audit trail
            auditService.logDocumentChanges(extractChanges(result));
        }
    }
}
```

### シナリオ 2: コンテンツ管理システム統合

```java
@RestController
public class DocumentComparisonController {
    
    @PostMapping("/api/documents/compare")
    public ResponseEntity<ComparisonReport> compareDocuments(
            @RequestParam("source") MultipartFile source,
            @RequestParam("target") MultipartFile target,
            @RequestParam(value = "sensitivity", defaultValue = "75") int sensitivity) {
        
        CompareOptions options = new CompareOptions.Builder()
                .setSensitivityOfComparison(sensitivity)
                .build();
                
        ComparisonReport report = documentComparisonService.compare(source, target, options);
        return ResponseEntity.ok(report);
    }
}
```

## よくある質問

**Q: Can I ignore headers and footers during comparison in GroupDocs for Java?**  
A: はい、`CompareOptions` で `setHeaderFootersComparison(false)` を呼び出します。これにより動的なヘッダー/フッターノイズが差分から除外されます。

**Q: How do I set output paper size in Java using GroupDocs?**  
A: `CompareOptions` の `setPaperSize(PaperSize.A6)`（または他の列挙値）を使用します。これにより選択したサイズの印刷対応 PDF が生成されます。

**Q: Is it possible to fine‑tune comparison sensitivity for different document types?**  
A: もちろんです。法務契約には `setSensitivityOfComparison(85)`、マーケティングドラフトには `setSensitivityOfComparison(45)` を呼び出して粒度を制御します。

**Q: Can I customize the styling of inserted, deleted, and changed text during comparison?**  
A: はい。各変更タイプ用に `StyleSettings` インスタンスを作成し、色、フォント、枠線を設定してから `CompareOptions` に渡します。

**Q: What are the prerequisites to get started with GroupDocs Comparison in Java?**  
A: JDK 8+（JDK 11+ 推奨）、Maven 3.6+ または Gradle 6.0+、最低 4 GB RAM、そして有効な GroupDocs ライセンス（無料トライアル利用可）が必要です。

**Q: How do I handle password‑protected documents in GroupDocs.Comparison?**  
A: `Comparer` を構築する際にパスワードを第2引数として渡します（例: `new Comparer(sourceFile, "myPassword")`）。`PasswordRequiredException` をキャッチしてエラーを適切に処理します。

**Q: What file formats does GroupDocs.Comparison for Java support?**  
A: DOCX、PDF、XLSX、PPTX、TXT、HTML、XML、PNG、JPEG など、**50** 以上の形式をサポートします。API は自動で形式を検出しますが、バッチ処理のパフォーマンス向上のために明示的に指定することも可能です。

## 結論

GroupDocs.Comparison for Java を活用すれば、Excel ワークブックやその他のサポート形式の比較という手間のかかる作業を、正確さ・速度・一貫性をもって自動化できます。本ガイドのコードスニペットとベストプラクティスを CI/CD パイプライン、文書管理システム、またはカスタム監査ツールに組み込むことで、測定可能な生産性向上を実現できます。

---

**Last Updated:** 2026-05-16  
**Tested With:** GroupDocs.Comparison 25.2 for Java  
**Author:** GroupDocs

```java
// Use streaming for memory efficiency
try (Comparer comparer = new Comparer(sourceStream)) {
    // Process in chunks for very large documents
    CompareOptions options = new CompareOptions.Builder()
            .setMemoryOptimization(true) // Enable memory optimization
            .build();
}
```

## 関連チュートリアル

- [compare pdf java – Java Document Comparison Tutorial – Complete Guide to Loading & Comparing Documents](/comparison/java/document-loading/)  
- [GroupDocs Comparison Java License Setup - Complete URL Configuration Guide](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)  
- [How to Use GroupDocs - Java Document Comparison Streams – Complete Guide](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)