---
"description": "GroupDocs Comparison for .NET を使用して、ユーザー定義のドキュメントメタデータを保存する方法を学びます。ステップバイステップの指示に従って、メタデータを簡単に比較および操作できます。"
"linktitle": "GroupDocs Comparison for .NET でユーザー定義のドキュメント メタデータを保存する"
"second_title": "GroupDocs.Comparison .NET API"
"title": "GroupDocs Comparison for .NET でユーザー定義のドキュメント メタデータを保存する"
"url": "/ja/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
type: docs
---
# GroupDocs Comparison for .NET でユーザー定義のドキュメント メタデータを保存する

## 導入
このチュートリアルでは、GroupDocs Comparison for .NET を使用してユーザー定義のドキュメントメタデータを保存する方法を説明します。メタデータは、ドキュメントを効率的に整理・管理するために不可欠です。GroupDocs Comparison を使用すると、特定の要件に合わせてメタデータを簡単に比較・操作できます。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs Comparison for .NET: GroupDocs Comparison for .NET をダウンロードしてインストールします。 [ここ](https://releases。groupdocs.com/comparison/net/).
2. 開発環境: システムに Visual Studio などの適切な開発環境がインストールされていることを確認してください。
3. ソース ドキュメントとターゲット ドキュメント: メタデータを比較および操作するソース ドキュメントとターゲット ドキュメントを準備します。

## 名前空間のインポート
まず、GroupDocs Comparison for .NET によって提供される機能にアクセスするために必要な名前空間をインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ステップ1: 出力ディレクトリとファイル名を定義する
比較したドキュメントを保存するディレクトリを定義し、出力ファイル名を指定します。
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## ステップ2: Comparer を初期化し、ドキュメントを追加する
初期化する `Comparer` オブジェクトをソース ドキュメントと比較し、比較のためにターゲット ドキュメントを追加します。
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## ステップ3: メタデータオプションを指定する
比較対象文書に保存するメタデータオプションを指定します。この例では、 `CloneMetadataType` に `MetadataType.FileAuthor` 詳細を記入してください `FileAuthorMetadata`。
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
## ステップ4: ドキュメントを比較してメタデータを保存する
指定されたメタデータ オプションを使用してドキュメントを比較し、比較したドキュメントを保存します。
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## ステップ5: 成功メッセージを表示する
ドキュメントの比較が正常に完了したことを示す成功メッセージと出力場所を表示します。
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## 結論
このチュートリアルでは、GroupDocs Comparison for .NET を使用してユーザー定義のドキュメントメタデータを保存する方法を学習しました。これらの手順に従うことで、要件に応じてメタデータを保存および操作しながら、効率的にドキュメントを比較できます。
## よくある質問
### GroupDocs Comparison for .NET はさまざまなドキュメント形式を処理できますか?
はい、GroupDocs Comparison は、DOCX、PDF、PPTX、XLSX など、幅広いドキュメント形式をサポートしています。
### GroupDocs Comparison for .NET の無料試用版はありますか?
はい、無料トライアルにアクセスできます [ここ](https://releases。groupdocs.com/).
### ニーズに応じてメタデータ オプションをカスタマイズできますか?
はい、GroupDocs Comparison は、ドキュメントの比較中にメタデータの処理をカスタマイズするための柔軟なオプションを提供します。
### GroupDocs Comparison は技術サポートを提供していますか?
はい、GroupDocs比較フォーラムからテクニカルサポートを受けることができます。 [ここ](https://forum。groupdocs.com/c/comparison/12).
### GroupDocs Comparison for .NET のライセンスはどこで購入できますか?
GroupDocsのウェブサイトからライセンスを購入できます [ここ](https://purchase。groupdocs.com/buy).