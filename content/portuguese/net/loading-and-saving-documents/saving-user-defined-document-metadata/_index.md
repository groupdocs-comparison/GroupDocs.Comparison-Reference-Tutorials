---
title: Salvando metadados de documentos definidos pelo usuário na comparação de GroupDocs para .NET
linktitle: Salvando metadados de documentos definidos pelo usuário na comparação de GroupDocs para .NET
second_title: API GroupDocs.Comparison .NET
description: Aprenda como salvar metadados de documentos definidos pelo usuário usando GroupDocs Comparison for .NET. Compare e manipule facilmente metadados com instruções passo a passo.
weight: 16
url: /pt/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Introdução
Neste tutorial, exploraremos como salvar metadados de documentos definidos pelo usuário usando GroupDocs Comparison for .NET. Os metadados são cruciais para organizar e gerenciar documentos de forma eficiente. Com a Comparação de GroupDocs, você pode comparar e manipular facilmente metadados para atender às suas necessidades específicas.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1.  Comparação de GroupDocs para .NET: Baixe e instale a Comparação de GroupDocs para .NET em[aqui](https://releases.groupdocs.com/comparison/net/).
2. Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento adequado, como o Visual Studio, instalado em seu sistema.
3. Documentos de origem e de destino: prepare os documentos de origem e de destino para os quais você deseja comparar e manipular metadados.

## Importar namespaces
Primeiro, importe os namespaces necessários para acessar as funcionalidades fornecidas pelo GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Etapa 1: definir o diretório de saída e o nome do arquivo
Defina o diretório onde deseja salvar o documento comparado e especifique o nome do arquivo de saída.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Etapa 2: inicializar o comparador e adicionar documentos
 Inicialize o`Comparer` objeto com o documento de origem e adicione o documento de destino para comparação.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Etapa 3: especificar opções de metadados
 Especifique as opções de metadados para salvar no documento comparado. Neste exemplo, definimos`CloneMetadataType` para`MetadataType.FileAuthor` e fornecer detalhes para`FileAuthorMetadata`.
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
## Etapa 4: compare documentos e salve metadados
Compare os documentos com opções de metadados especificadas e salve o documento comparado.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Etapa 5: exibir mensagem de sucesso
Exiba uma mensagem de sucesso indicando que os documentos foram comparados com sucesso e o local de saída.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusão
Neste tutorial, aprendemos como salvar metadados de documentos definidos pelo usuário usando GroupDocs Comparison for .NET. Seguindo essas etapas, você pode comparar documentos com eficiência e, ao mesmo tempo, preservar e manipular metadados de acordo com suas necessidades.
## Perguntas frequentes
### O GroupDocs Comparison for .NET pode lidar com vários formatos de documentos?
Sim, o GroupDocs Comparison oferece suporte a uma ampla variedade de formatos de documentos, incluindo DOCX, PDF, PPTX, XLSX e muito mais.
### Existe uma avaliação gratuita disponível para GroupDocs Comparison for .NET?
 Sim, você pode acessar o teste gratuito[aqui](https://releases.groupdocs.com/).
### Posso personalizar as opções de metadados de acordo com minhas necessidades?
Com certeza, o GroupDocs Comparison oferece opções flexíveis para personalizar o tratamento de metadados durante a comparação de documentos.
### A comparação do GroupDocs oferece suporte técnico?
Sim, você pode obter suporte técnico no fórum de comparação do GroupDocs[aqui](https://forum.groupdocs.com/c/comparison/12).
### Onde posso adquirir uma licença do GroupDocs Comparison for .NET?
 Você pode comprar uma licença no site GroupDocs[aqui](https://purchase.groupdocs.com/buy).