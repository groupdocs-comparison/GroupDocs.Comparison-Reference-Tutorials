---
title: GroupDocs Comparison for .NET でのロード オプションの使用
linktitle: GroupDocs Comparison for .NET でのロード オプションの使用
second_title: GroupDocs.Comparison .NET API
description: GroupDocs Comparison for .NET の読み込みオプションを使用して、ドキュメントとカスタム フォントをシームレスに比較する方法を学びます。
weight: 13
url: /ja/net/loading-and-saving-documents/using-load-options/
---
## 導入
GroupDocs Comparison for .NET でのロード オプションの利用に関するチュートリアルへようこそ。このチュートリアルでは、ロード オプションを使用してドキュメントを比較するプロセスを段階的に説明します。初心者でも経験豊富な開発者でも、このガイドは GroupDocs Comparison を .NET アプリケーションにシームレスに統合するのに役立ちます。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
### 1. GroupDocs Comparison for .NET をインストールする
 GroupDocs Comparison for .NET ライブラリは、次からダウンロードできます。[このリンク](https://releases.groupdocs.com/comparison/net/)。セットアップ プロセスをスムーズに行うには、ドキュメントに記載されているインストール手順に従ってください。
### 2. ソースドキュメントとターゲットドキュメントを入手する
比較できるようにソース文書とターゲット文書を用意してください。これらのドキュメントは、DOCX、PDF、TXT などのさまざまな形式にすることができます。
## 名前空間のインポート
コードを詳しく調べる前に、アプリケーションに必要な名前空間をインポートしましょう。
```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
ここで、提供されているコード例を複数のステップに分けて見てみましょう。
## ステップ 1: カスタム フォント ディレクトリを定義する
```csharp
List<string> fontDirectories = new List<string>();
//フォントを含むファイルのディレクトリを設定する必要があります
fontDirectories.Add(Constants.CUSTOM_FONT);
```
このステップでは、カスタム フォントが配置されているディレクトリを保持する文字列タイプのリストを作成します。必ず交換してください`Constants.CUSTOM_FONT`カスタム フォントを含む実際のディレクトリ パスに置き換えます。
## ステップ 2: ロード オプションをインスタンス化する
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontDirectories = fontDirectories;
```
ここでは、`LoadOptions`オブジェクトを作成し、それにカスタム フォント ディレクトリを割り当てます。このステップでは、カスタム フォントを使用してドキュメントを読み込むために必要なオプションを準備します。
## ステップ 3: ドキュメントを比較する
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"), loadOptions))
{
    comparer.Add(File.OpenRead("TARGET.docx"));
    comparer.Compare(File.Create(Path.Combine("Your Document Directory", "RESULT.docx")));
}
```
ここで、`Comparer`ソースドキュメントと以前に定義されたロードオプションを使用してオブジェクトを読み込みます。次に、ターゲット ドキュメントを比較関数に追加し、比較を実行します。最後に、比較したドキュメントを指定したディレクトリに保存します。
## ステップ 4: 成功メッセージを表示する
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
比較プロセスが完了すると、成功メッセージと比較されたドキュメントが保存されているディレクトリが表示されます。
## 結論
結論として、このチュートリアルは、GroupDocs Comparison for .NET でのロード オプションの使用に関する包括的なガイドを提供しました。段階的な手順に従うことで、ドキュメント比較機能を .NET アプリケーションにシームレスに統合できます。
## よくある質問
### Q: GroupDocs Comparison は、異なる形式のドキュメントを処理できますか?
はい、GroupDocs Comparison は、DOCX、PDF、TXT などのさまざまな形式のドキュメントの比較をサポートしています。
### Q: 購入前に利用できる試用版はありますか?
はい。GroupDocs Comparison の無料試用版には、以下からアクセスできます。[このリンク](https://releases.groupdocs.com/).
### Q: GroupDocs 比較のサポートを受けるにはどうすればよいですか?
 GroupDocs コミュニティ フォーラムからサポートを求めることができます[ここ](https://forum.groupdocs.com/c/comparison/12).
### Q: 比較するドキュメントでカスタム フォントを使用できますか?
絶対に！ GroupDocs Comparison を使用すると、ドキュメントを正確にレンダリングするためにカスタム フォント ディレクトリを指定できます。
### Q: 一時ライセンスはテスト目的で利用できますか?
はい、テストおよび評価目的で一時ライセンスを次のサイトから取得できます。[このリンク](https://purchase.groupdocs.com/temporary-license/).