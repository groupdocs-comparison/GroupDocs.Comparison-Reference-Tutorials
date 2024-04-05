---
title: GroupDocs Comparison for .NET での結果ドキュメントのパスワードの設定
linktitle: GroupDocs Comparison for .NET での結果ドキュメントのパスワードの設定
second_title: GroupDocs.Comparison .NET API
description: GroupDocs Comparison for .NET で結果のドキュメントにパスワードを設定する方法を学習します。セキュリティを強化し、比較したファイルを保護します。
type: docs
weight: 17
url: /ja/net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## 導入
このチュートリアルでは、GroupDocs Comparison for .NET を使用して、結果のドキュメントにパスワードを設定するプロセスを説明します。この機能により、比較対象のドキュメントにセキュリティ層が追加され、許可された個人のみがドキュメントにアクセスできるようになります。
## 前提条件
続行する前に、次のものが揃っていることを確認してください。
1.  GroupDocs Comparison for .NET: GroupDocs Comparison ライブラリが .NET 環境にインストールされていることを確認します。からダウンロードできます[ここ](https://releases.groupdocs.com/comparison/net/).
2. ソース文書とターゲット文書: ソース文書を準備します (`SOURCE.docx`) と対象ドキュメント (`TARGET.docx`) を比較して、結果のドキュメントにパスワードを設定したいとします。

## 名前空間のインポート
まず、GroupDocs 比較機能を使用するには、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## ステップ 1: 出力ディレクトリとファイル名を定義する
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
結果のドキュメントを保存するディレクトリを指定し、出力ファイルの名前を定義します。
## ステップ 2: パスワード設定のある文書を比較する
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
ここでは、`Comparer`オブジェクトをソースドキュメントに追加します。次に、比較対象のドキュメントを追加します。私たちは、`PasswordSaveOption`に`User`結果のドキュメントにパスワードを適用することを指定します。希望のパスワードを入力します。`Password`の財産`SaveOptions`物体。
## ステップ 3: 成功メッセージを表示する
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
最後に、ドキュメントが正常に比較され、結果のドキュメントが設定されたパスワードとともに指定されたディレクトリに保存されたことを示す成功メッセージが表示されます。

## 結論
GroupDocs Comparison for .NET で結果のドキュメントにパスワードを設定すると、比較したドキュメントにセキュリティ層が追加され、機密性と整合性が確保されます。このチュートリアルで概説されている手順に従うことで、この機能を .NET アプリケーションに簡単に実装できます。
## よくある質問
### 異なる形式のドキュメントを比較できますか?
はい、GroupDocs Comparison for .NET は、DOCX、PDF、PPTX、XLSX などのさまざまな形式のドキュメントの比較をサポートしています。
### 試用版はありますか?
はい、無料試用版を次からダウンロードできます。[ここ](https://releases.groupdocs.com/).
### 問題が発生した場合、どうすればサポートを受けられますか?
 GroupDocs Comparison コミュニティ フォーラムから支援を求めることができます。[ここ](https://forum.groupdocs.com/c/comparison/12).
### GroupDocs Comparison for .NET を使用するにはライセンスが必要ですか?
はい、次からライセンスを購入できます。[ここ](https://purchase.groupdocs.com/buy)または仮免許を取得する[ここ](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs Comparison for .NET について利用可能なドキュメントはありますか?
はい、ドキュメントにアクセスできます[ここ](https://reference.groupdocs.com/comparison/net/).