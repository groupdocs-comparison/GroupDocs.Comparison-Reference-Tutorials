---
title: .NET の GroupDocs 比較における変更の承認と拒否
linktitle: .NET の GroupDocs 比較における変更の承認と拒否
second_title: GroupDocs.Comparison .NET API
description: GroupDocs Comparison for .NET を使用してドキュメントの変更を承認および拒否する方法を学びます。ドキュメントのワークフローを簡単に合理化します。
weight: 10
url: /ja/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# .NET の GroupDocs 比較における変更の承認と拒否

## 導入
ドキュメント管理とコラボレーションの領域では、ファイルの正確性と整合性を確保することが最も重要です。 GroupDocs Comparison for .NET は堅牢なソリューションとして登場し、開発者がドキュメント内の変更を簡単に承認および拒否できるようにすることで、ワークフローを合理化し、生産性を向上させます。このチュートリアルでは、GroupDocs Comparison for .NET を使用して変更を承認および拒否するプロセスを説明し、明確さと実装の容易さのために各ステップに分けて説明します。
## 前提条件
チュートリアルに入る前に、次の前提条件が満たされていることを確認してください。
### 環境設定
1. .NET SDK をインストールする: まだ行っていない場合は、.NET Web サイトからオペレーティング システムに適した .NET SDK をダウンロードしてインストールします。
2.  GroupDocs Comparison for .NET をインストールする: 提供されている最新バージョンの GroupDocs Comparison for .NET を入手します。[ダウンロードリンク](https://releases.groupdocs.com/comparison/net/)インストール手順に従ってください。
3. C# プログラミングに精通していること: このチュートリアルは、C# プログラミング言語とその構文の基本を理解していることを前提としています。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートします。これらの名前空間は、ドキュメントの比較と操作に必要な機能へのアクセスを提供します。

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## ステップ 1: 出力ディレクトリとファイル名を指定する
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
必ず交換してください`"Your Document Directory"`目的の出力ディレクトリへのパスを置き換えます。
## ステップ 2: 比較機能を初期化してドキュメントを比較する
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
このコードは、Comparer オブジェクトをソース ドキュメントで初期化し、比較対象のターゲット ドキュメントを追加します。そして、比較処理を実行する。
## ステップ 3: 変更の取得と操作
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
比較から変更を取得し、必要に応じて操作します。この例では、変更は最初に拒否され、次に受け入れられます。結果として得られるドキュメントは、それに応じて保存されます。

## 結論
結論として、GroupDocs Comparison for .NET は、ドキュメント内の変更を承認および拒否するためのシームレスなソリューションを提供します。このチュートリアルで概説されている手順に従うことで、開発者はこの機能をアプリケーションに効率的に統合し、ドキュメントの正確性を確保し、コラボレーションを強化できます。
## よくある質問
### GroupDocs Comparison for .NET は、異なる形式のドキュメントを比較できますか?
はい、GroupDocs Comparison for .NET は、DOCX、PDF、PPTX などのさまざまな形式のドキュメント間の比較をサポートしています。
### GroupDocs Comparison for .NET は .NET Core と互換性がありますか?
はい、GroupDocs Comparison for .NET は .NET Framework と .NET Core の両方と互換性があります。
### 比較したドキュメントの変更の外観をカスタマイズできますか?
もちろん、GroupDocs Comparison for .NET には、色やスタイルなど、変更の外観をカスタマイズするための広範なオプションが用意されています。
### GroupDocs Comparison for .NET は複数ページのドキュメント比較をサポートしていますか?
はい。GroupDocs Comparison for .NET は、複数ページのドキュメントの正確な比較をサポートします。
### GroupDocs Comparison for .NET で利用できる試用版はありますか?
はい、提供されているから GroupDocs Comparison for .NET の無料トライアルを利用できます。[リンク](https://releases.groupdocs.com/).