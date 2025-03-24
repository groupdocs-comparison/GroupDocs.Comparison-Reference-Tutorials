---
title: Usando opções de carregamento na comparação de GroupDocs para .NET
linktitle: Usando opções de carregamento na comparação de GroupDocs para .NET
second_title: API GroupDocs.Comparison .NET
description: Aprenda como usar as opções de carregamento na comparação de GroupDocs para .NET para comparar documentos com fontes personalizadas perfeitamente.
weight: 13
url: /pt/net/loading-and-saving-documents/using-load-options/
---
## Introdução
Bem-vindo ao nosso tutorial sobre como utilizar opções de carregamento na comparação de GroupDocs para .NET! Neste tutorial, orientaremos você passo a passo no processo de comparação de documentos usando Opções de carregamento. Quer você seja um desenvolvedor iniciante ou experiente, este guia o ajudará a integrar perfeitamente o GroupDocs Comparison em seus aplicativos .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos configurados:
### 1. Instale a comparação de GroupDocs para .NET
 Você pode baixar a biblioteca GroupDocs Comparison for .NET em[esse link](https://releases.groupdocs.com/comparison/net/). Siga as instruções de instalação fornecidas na documentação para um processo de configuração tranquilo.
### 2. Obtenha documentos de origem e destino
Certifique-se de ter os documentos de origem e de destino prontos para comparação. Esses documentos podem estar em vários formatos, como DOCX, PDF ou TXT.
## Importar namespaces
Antes de nos aprofundarmos no código, vamos importar os namespaces necessários para nossa aplicação:
```csharp
using System;
using System.IO;
using System.Collections.Generic;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
Agora, vamos dividir o código de exemplo fornecido em várias etapas:
## Etapa 1: definir diretórios de fontes personalizadas
```csharp
List<string> fontDirectories = new List<string>();
//Precisa definir o diretório do arquivo com a fonte
fontDirectories.Add(Constants.CUSTOM_FONT);
```
 Nesta etapa, criamos uma lista de tipos de string para conter os diretórios onde as fontes personalizadas estão localizadas. Certifique-se de substituir`Constants.CUSTOM_FONT` pelo caminho do diretório real que contém suas fontes personalizadas.
## Etapa 2: instanciar opções de carregamento
```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontDirectories = fontDirectories;
```
 Aqui, instanciamos um`LoadOptions` objeto e atribua os diretórios de fontes personalizados a ele. Esta etapa prepara as opções necessárias para carregar os documentos com fontes personalizadas.
## Etapa 3: comparar documentos
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx"), loadOptions))
{
    comparer.Add(File.OpenRead("TARGET.docx"));
    comparer.Compare(File.Create(Path.Combine("Your Document Directory", "RESULT.docx")));
}
```
 Agora, criamos um`Comparer` objeto usando o documento de origem e as opções de carregamento definidas anteriormente. Em seguida, adicionamos o documento de destino ao comparador e realizamos a comparação. Finalmente, salvamos o documento comparado em um diretório especificado.
## Etapa 4: exibir mensagem de sucesso
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {Directory.GetCurrentDirectory()}.");
```
Após a conclusão do processo de comparação, exibimos uma mensagem de sucesso junto com o diretório onde o documento comparado foi salvo.
## Conclusão
Concluindo, este tutorial forneceu um guia abrangente sobre como usar opções de carregamento na comparação de GroupDocs para .NET. Seguindo as instruções passo a passo, você pode integrar perfeitamente a funcionalidade de comparação de documentos em seus aplicativos .NET.
## Perguntas frequentes
### P: O GroupDocs Comparison pode lidar com documentos de diferentes formatos?
Sim, o GroupDocs Comparison oferece suporte à comparação de documentos em vários formatos, como DOCX, PDF, TXT e muito mais.
### P: Existe uma versão de teste disponível antes da compra?
 Sim, você pode acessar a versão de avaliação gratuita do GroupDocs Comparison em[esse link](https://releases.groupdocs.com/).
### P: Como posso obter suporte para comparação de GroupDocs?
 Você pode buscar suporte no fórum da comunidade GroupDocs[aqui](https://forum.groupdocs.com/c/comparison/12).
### P: Posso usar fontes personalizadas nos documentos comparados?
Absolutamente! A comparação de GroupDocs permite que você especifique diretórios de fontes personalizados para renderização precisa de documentos.
### P: As licenças temporárias estão disponíveis para fins de teste?
Sim, você pode obter licenças temporárias para fins de teste e avaliação em[esse link](https://purchase.groupdocs.com/temporary-license/).