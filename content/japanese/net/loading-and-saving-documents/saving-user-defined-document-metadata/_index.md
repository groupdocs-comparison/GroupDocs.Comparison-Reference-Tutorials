---
title: GroupDocs でのユーザー定義ドキュメントのメタデータの保存 .NET の比較
linktitle: GroupDocs でのユーザー定義ドキュメントのメタデータの保存 .NET の比較
second_title: GroupDocs.Comparison .NET API
description: GroupDocs Comparison for .NET を使用してユーザー定義のドキュメント メタデータを保存する方法を学びます。ステップバイステップの指示に従って、メタデータを簡単に比較および操作できます。
weight: 16
url: /ja/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## 導入
このチュートリアルでは、GroupDocs Comparison for .NET を使用してユーザー定義のドキュメント メタデータを保存する方法を検討します。メタデータは、ドキュメントを効率的に整理および管理するために不可欠です。 GroupDocs Comparison を使用すると、特定の要件を満たすようにメタデータを簡単に比較および操作できます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs Comparison for .NET: GroupDocs Comparison for .NET を次の場所からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/comparison/net/).
2. 開発環境: Visual Studio などの適切な開発環境がシステムにインストールされていることを確認してください。
3. ソース ドキュメントとターゲット ドキュメント: メタデータを比較および操作するソース ドキュメントとターゲット ドキュメントを準備します。

## 名前空間のインポート
まず、GroupDocs Comparison for .NET が提供する機能にアクセスするために必要な名前空間をインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ステップ 1: 出力ディレクトリとファイル名を定義する
比較ドキュメントを保存するディレクトリを定義し、出力ファイル名を指定します。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## ステップ 2: コンペアラーを初期化してドキュメントを追加する
を初期化します`Comparer`オブジェクトをソース ドキュメントと比較し、比較のためにターゲット ドキュメントを追加します。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## ステップ 3: メタデータ オプションを指定する
比較するドキュメントに保存するためのメタデータ オプションを指定します。この例では、`CloneMetadataType`に`MetadataType.FileAuthor`の詳細を提供します`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## ステップ 4: ドキュメントを比較し、メタデータを保存する
指定されたメタデータ オプションを使用してドキュメントを比較し、比較したドキュメントを保存します。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## ステップ 5: 成功メッセージを表示する
ドキュメントが正常に比較されたことを示す成功メッセージと出力場所を表示します。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 結論
このチュートリアルでは、GroupDocs Comparison for .NET を使用してユーザー定義のドキュメント メタデータを保存する方法を学習しました。これらの手順に従うことで、要件に応じてメタデータを保存および操作しながら、ドキュメントを効率的に比較できます。
## よくある質問
### GroupDocs Comparison for .NET はさまざまなドキュメント形式を処理できますか?
はい。GroupDocs Comparison は、DOCX、PDF、PPTX、XLSX などの幅広いドキュメント形式をサポートしています。
### GroupDocs Comparison for .NET に利用できる無料トライアルはありますか?
はい、無料トライアルにアクセスできます[ここ](https://releases.groupdocs.com/).
### ニーズに応じてメタデータ オプションをカスタマイズできますか?
確かに、GroupDocs Comparison は、ドキュメント比較中のメタデータ処理をカスタマイズするための柔軟なオプションを提供します。
### GroupDocs Comparison では技術サポートを提供していますか?
はい、GroupDocs 比較フォーラムから技術サポートを受けることができます。[ここ](https://forum.groupdocs.com/c/comparison/12).
### GroupDocs Comparison for .NET のライセンスはどこで購入できますか?
 GroupDocs Web サイトからライセンスを購入できます。[ここ](https://purchase.groupdocs.com/buy).