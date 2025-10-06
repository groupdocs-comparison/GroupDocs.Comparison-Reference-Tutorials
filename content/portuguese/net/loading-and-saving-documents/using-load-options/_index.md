---
"description": "Aprenda a usar as Opções de Carregamento no GroupDocs Comparison for .NET para comparar documentos com fontes personalizadas facilmente."
"linktitle": "Usando opções de carregamento na comparação do GroupDocs para .NET"
"second_title": "API .NET do GroupDocs.Comparison"
"title": "Usando opções de carregamento na comparação do GroupDocs para .NET"
"url": "/pt/net/loading-and-saving-documents/using-load-options/"
"weight": 13
type: docs
---
# Usando opções de carregamento na comparação do GroupDocs para .NET

## Introdução
Bem-vindo ao nosso tutorial sobre como utilizar as Opções de Carregamento no GroupDocs Comparison para .NET! Neste tutorial, mostraremos passo a passo o processo de comparação de documentos usando as Opções de Carregamento. Seja você um desenvolvedor iniciante ou experiente, este guia ajudará você a integrar perfeitamente o GroupDocs Comparison aos seus aplicativos .NET.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos configurados:
### 1. Instale o GroupDocs Comparison para .NET
Você pode baixar a biblioteca GroupDocs Comparison for .NET em [este link](https://releases.groupdocs.com/comparison/net/). Siga as instruções de instalação fornecidas na documentação para um processo de configuração tranquilo.
### 2. Obtenha documentos de origem e destino
Certifique-se de ter os documentos de origem e destino prontos para comparação. Esses documentos podem estar em vários formatos, como DOCX, PDF ou TXT.
## Importar namespaces
Antes de nos aprofundarmos no código, vamos importar os namespaces necessários para nosso aplicativo:
```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
Agora, vamos dividir o código de exemplo fornecido em várias etapas:
## Etapa 1: definir diretórios de fontes personalizados
```csharp
List<string> fontDirectories = new List<string>();
// É necessário definir o diretório do arquivo com a fonte
fontDirectories.Add(Constants.CUSTOM_FONT);
```
Nesta etapa, criamos uma lista do tipo string para armazenar os diretórios onde as fontes personalizadas estão localizadas. Certifique-se de substituir `Constants.CUSTOM_FONT` com o caminho do diretório real contendo suas fontes personalizadas.
## Etapa 2: Instanciar opções de carga
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontDirectories = fontDirectories;
```
Aqui, instanciamos um `LoadOptions` objeto e atribuir a ele os diretórios de fontes personalizadas. Esta etapa prepara as opções necessárias para carregar os documentos com fontes personalizadas.
## Etapa 3: Comparar documentos
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"), loadOptions))
{
    comparer.Add(File.OpenRead("TARGET.docx"));
    comparer.Compare(File.Create(Path.Combine("Your Document Directory", "RESULT.docx")));
}
```
Agora, criamos um `Comparer` objeto usando o documento de origem e as opções de carregamento definidas anteriormente. Em seguida, adicionamos o documento de destino ao comparador e realizamos a comparação. Por fim, salvamos o documento comparado em um diretório especificado.
## Etapa 4: Exibir mensagem de sucesso
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
Após a conclusão do processo de comparação, exibimos uma mensagem de sucesso junto com o diretório onde o documento comparado foi salvo.
## Conclusão
Concluindo, este tutorial forneceu um guia completo sobre o uso de Opções de Carregamento no GroupDocs Comparison para .NET. Seguindo as instruções passo a passo, você poderá integrar perfeitamente a funcionalidade de comparação de documentos aos seus aplicativos .NET.
## Perguntas frequentes
### P: O GroupDocs Comparison pode manipular documentos de formatos diferentes?
Sim, o GroupDocs Comparison suporta a comparação de documentos em vários formatos, como DOCX, PDF, TXT e mais.
### P: Há uma versão de teste disponível antes da compra?
Sim, você pode acessar a versão de teste gratuita do GroupDocs Comparison em [este link](https://releases.groupdocs.com/).
### P: Como posso obter suporte para o GroupDocs Comparison?
Você pode buscar suporte no fórum da comunidade do GroupDocs [aqui](https://forum.groupdocs.com/c/comparison/12).
### P: Posso usar fontes personalizadas nos documentos comparados?
Com certeza! O GroupDocs Comparison permite que você especifique diretórios de fontes personalizados para uma renderização precisa de documentos.
### P: Há licenças temporárias disponíveis para fins de teste?
Sim, você pode obter licenças temporárias para fins de teste e avaliação em [este link](https://purchase.groupdocs.com/temporary-license/).