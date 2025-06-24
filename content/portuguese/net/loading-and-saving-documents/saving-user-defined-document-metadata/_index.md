---
"description": "Aprenda a salvar metadados de documentos definidos pelo usuário usando o GroupDocs Comparison para .NET. Compare e manipule metadados facilmente com instruções passo a passo."
"linktitle": "Salvando metadados de documentos definidos pelo usuário na comparação do GroupDocs para .NET"
"second_title": "API .NET do GroupDocs.Comparison"
"title": "Salvando metadados de documentos definidos pelo usuário na comparação do GroupDocs para .NET"
"url": "/pt/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
---

# Salvando metadados de documentos definidos pelo usuário na comparação do GroupDocs para .NET

## Introdução
Neste tutorial, exploraremos como salvar metadados de documentos definidos pelo usuário usando o GroupDocs Comparison para .NET. Metadados são cruciais para organizar e gerenciar documentos com eficiência. Com o GroupDocs Comparison, você pode comparar e manipular metadados facilmente para atender às suas necessidades específicas.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos:
1. Comparação do GroupDocs para .NET: Baixe e instale o Comparação do GroupDocs para .NET em [aqui](https://releases.groupdocs.com/comparison/net/).
2. Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento adequado, como o Visual Studio, instalado no seu sistema.
3. Documentos de origem e destino: prepare os documentos de origem e destino que você deseja comparar e manipular metadados.

## Importar namespaces
Primeiro, importe os namespaces necessários para acessar as funcionalidades fornecidas pelo GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Etapa 1: definir o diretório de saída e o nome do arquivo
Defina o diretório onde você deseja salvar o documento comparado e especifique o nome do arquivo de saída.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Etapa 2: Inicializar o comparador e adicionar documentos
Inicializar o `Comparer` objeto com o documento de origem e adicione o documento de destino para comparação.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Etapa 3: especificar opções de metadados
Especifique as opções de metadados para salvar no documento comparado. Neste exemplo, definimos `CloneMetadataType` para `MetadataType.FileAuthor` e fornecer detalhes para `FileAuthorMetadata`.
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
## Etapa 4: comparar documentos e salvar metadados
Compare os documentos com as opções de metadados especificadas e salve o documento comparado.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Etapa 5: Exibir mensagem de sucesso
Exibe uma mensagem de sucesso indicando que os documentos foram comparados com sucesso e o local de saída.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusão
Neste tutorial, aprendemos como salvar metadados de documentos definidos pelo usuário usando o GroupDocs Comparison para .NET. Seguindo esses passos, você poderá comparar documentos com eficiência, preservando e manipulando metadados de acordo com suas necessidades.
## Perguntas frequentes
### O GroupDocs Comparison for .NET pode manipular vários formatos de documentos?
Sim, o GroupDocs Comparison suporta uma ampla variedade de formatos de documentos, incluindo DOCX, PDF, PPTX, XLSX e muito mais.
### Existe uma avaliação gratuita disponível do GroupDocs Comparison for .NET?
Sim, você pode acessar o teste gratuito [aqui](https://releases.groupdocs.com/).
### Posso personalizar as opções de metadados de acordo com minhas necessidades?
Com certeza, o GroupDocs Comparison oferece opções flexíveis para personalizar o tratamento de metadados durante a comparação de documentos.
### O GroupDocs Comparison oferece suporte técnico?
Sim, você pode obter suporte técnico no fórum de comparação do GroupDocs [aqui](https://forum.groupdocs.com/c/comparison/12).
### Onde posso comprar uma licença para o GroupDocs Comparison for .NET?
Você pode comprar uma licença no site GroupDocs [aqui](https://purchase.groupdocs.com/buy).