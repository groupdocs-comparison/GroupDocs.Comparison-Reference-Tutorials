---
"description": "GroupDocs Comparison for .NET を使用して、ドキュメントの変更を承認または拒否する方法を学びます。ドキュメントワークフローを簡単に効率化できます。"
"linktitle": "GroupDocs Comparison for .NET における変更の承認と拒否"
"second_title": "GroupDocs.Comparison .NET API"
"title": "GroupDocs Comparison for .NET における変更の承認と拒否"
"url": "/ja/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# GroupDocs Comparison for .NET における変更の承認と拒否

## 導入
ドキュメント管理とコラボレーションの分野では、ファイルの正確性と整合性を確保することが最も重要です。GroupDocs Comparison for .NETは、開発者がドキュメント内の変更を簡単に承認または拒否できるようにする堅牢なソリューションとして登場しました。これにより、ワークフローが効率化され、生産性が向上します。このチュートリアルでは、GroupDocs Comparison for .NETを使用して変更を承認および拒否するプロセスを、各ステップをわかりやすく分解して解説し、実装を容易にします。
## 前提条件
チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。
### 環境設定
1. .NET SDK をインストールします。まだインストールしていない場合は、.NET Web サイトから、ご使用のオペレーティング システムに適した .NET SDK をダウンロードしてインストールします。
2. GroupDocs Comparison for .NETのインストール: 提供されているサイトからGroupDocs Comparison for .NETの最新バージョンを入手します。 [ダウンロードリンク](https://releases.groupdocs.com/comparison/net/) インストール手順に従います。
3. C# プログラミングに関する知識: このチュートリアルでは、C# プログラミング言語とその構文の基本的な理解を前提としています。

## 名前空間のインポート
まず、プロジェクトに必要な名前空間をインポートします。これらの名前空間は、ドキュメントの比較と操作に必要な機能へのアクセスを提供します。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## ステップ1: 出力ディレクトリとファイル名を指定する
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
必ず交換してください `"Your Document Directory"` 希望する出力ディレクトリへのパスを入力します。
## ステップ2: Comparer を初期化してドキュメントを比較する
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
このコードは、ソースドキュメントでComparerオブジェクトを初期化し、比較対象となるターゲットドキュメントを追加します。そして、比較処理を実行します。
## ステップ3: 変更を取得して操作する
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
比較から変更を取得し、必要に応じて操作します。この例では、変更は最初に拒否され、その後承認されます。結果のドキュメントはそれに応じて保存されます。

## 結論
結論として、GroupDocs Comparison for .NETは、ドキュメント内の変更を承認または拒否するためのシームレスなソリューションを提供します。このチュートリアルで概説されている手順に従うことで、開発者はこの機能をアプリケーションに効率的に統合し、ドキュメントの正確性を確保し、コラボレーションを強化できます。
## よくある質問
### GroupDocs Comparison for .NET は異なる形式のドキュメントを比較できますか?
はい、GroupDocs Comparison for .NET は、DOCX、PDF、PPTX など、さまざまな形式のドキュメント間の比較をサポートしています。
### GroupDocs Comparison for .NET は .NET Core と互換性がありますか?
はい、GroupDocs Comparison for .NET は .NET Framework と .NET Core の両方と互換性があります。
### 比較したドキュメントの変更の外観をカスタマイズできますか?
はい、GroupDocs Comparison for .NET には、色やスタイルなど、変更の外観をカスタマイズするための幅広いオプションが用意されています。
### GroupDocs Comparison for .NET は複数ページのドキュメントの比較をサポートしていますか?
はい、GroupDocs Comparison for .NET は、複数ページのドキュメントを正確かつ正確に比較することをサポートします。
### GroupDocs Comparison for .NET の試用版はありますか?
はい、GroupDocs Comparison for .NETの無料トライアルをご利用いただけます。 [リンク](https://releases。groupdocs.com/).