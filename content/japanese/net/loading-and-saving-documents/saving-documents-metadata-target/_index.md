---
title: GroupDocs でのドキュメント メタデータ ターゲットの保存 .NET の比較
linktitle: GroupDocs でのドキュメント メタデータ ターゲットの保存 .NET の比較
second_title: GroupDocs.Comparison .NET API
description: GroupDocs Comparison for .NET を使用してドキュメントのメタデータ ターゲットを保存する方法を学びます。 .NET アプリケーションでドキュメントを効率的に比較するための簡単な手順。
type: docs
weight: 15
url: /ja/net/loading-and-saving-documents/saving-documents-metadata-target/
---
## 導入
このチュートリアルでは、GroupDocs Comparison for .NET を使用してドキュメント メタデータ ターゲットを保存するプロセスを説明します。 GroupDocs Comparison for .NET は、.NET アプリケーションでドキュメントを比較およびマージできる強力なライブラリです。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs Comparison for .NET: GroupDocs Comparison for .NET をダウンロードしてインストールしていることを確認します。からダウンロードできます[ここ](https://releases.groupdocs.com/comparison/net/).
2. .NET 開発環境: システム上に .NET 開発環境がセットアップされている必要があります。

## 名前空間のインポート
コーディングを開始する前に、必要な名前空間をインポートしましょう。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ステップ 1: 出力ディレクトリとファイル名を定義する
まず、比較したドキュメントを保存する出力ディレクトリと出力ファイルの名前を指定します。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## ステップ 2: ドキュメントを比較し、メタデータ ターゲットを保存する
ここで、を初期化します`Comparer`オブジェクトをソース ドキュメントに追加し、比較するターゲット ドキュメントを追加します。次に、`Compare`メソッドを使用し、メタデータ タイプをターゲットとして複製するための保存オプションとともに出力ファイル名を指定します。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
}
```
## ステップ 3: 成功メッセージを表示する
最後に、ドキュメントが正常に比較されたことを示す成功メッセージを表示し、出力ファイルが保存されるパスを指定します。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
おめでとう！ GroupDocs Comparison for .NET を使用してドキュメント メタデータ ターゲットを正常に保存しました。

## 結論
このチュートリアルでは、GroupDocs Comparison for .NET を使用してドキュメント メタデータ ターゲットを保存するプロセスについて説明しました。上記の手順に従うことで、.NET アプリケーションでドキュメントを効率的に比較して保存できます。
## よくある質問
### 異なる形式のドキュメントを比較できますか?
はい、GroupDocs Comparison for .NET は、DOCX、PDF、PPTX、XLSX などのさまざまな形式のドキュメントの比較をサポートしています。
### 試用版はありますか?
はい、次のサイトから無料トライアルを利用できます。[ここ](https://releases.groupdocs.com/).
### 問題が発生した場合、どうすればサポートを受けられますか?
 GroupDocs Comparison コミュニティ フォーラムから支援を求めることができます。[ここ](https://forum.groupdocs.com/c/comparison/12).
### 比較したドキュメントの出力形式をカスタマイズできますか?
はい、要件に応じて出力形式やその他のオプションをカスタマイズできます。
### GroupDocs Comparison for .NET は大規模なドキュメント比較タスクに適していますか?
はい。GroupDocs Comparison for .NET は、大規模なドキュメント比較タスクを効率的に処理できるように設計されています。