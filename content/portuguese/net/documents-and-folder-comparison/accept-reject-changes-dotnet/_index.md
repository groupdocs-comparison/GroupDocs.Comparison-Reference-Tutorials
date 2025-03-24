---
title: Aceitar e rejeitar alterações na comparação de GroupDocs para .NET
linktitle: Aceitar e rejeitar alterações na comparação de GroupDocs para .NET
second_title: API GroupDocs.Comparison .NET
description: Aprenda como aceitar e rejeitar alterações em documentos usando GroupDocs Comparison for .NET. Simplifique seus fluxos de trabalho de documentos sem esforço.
weight: 10
url: /pt/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## Introdução
No domínio do gerenciamento e colaboração de documentos, garantir a precisão e a integridade dos arquivos é fundamental. O GroupDocs Comparison for .NET surge como uma solução robusta, capacitando os desenvolvedores a aceitar e rejeitar alterações em documentos sem esforço, simplificando assim os fluxos de trabalho e aumentando a produtividade. Este tutorial irá guiá-lo através do processo de aceitação e rejeição de alterações usando o GroupDocs Comparison for .NET, detalhando cada etapa para maior clareza e facilidade de implementação.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos em vigor:
### Configuração do ambiente
1. Instale o SDK do .NET: se ainda não o fez, baixe e instale o SDK do .NET adequado para o seu sistema operacional no site do .NET.
2.  Instale o GroupDocs Comparison for .NET: Obtenha a versão mais recente do GroupDocs Comparison for .NET no site fornecido[Link para Download](https://releases.groupdocs.com/comparison/net/) e siga as instruções de instalação.
3. Familiaridade com programação C#: Este tutorial pressupõe um conhecimento básico da linguagem de programação C# e sua sintaxe.

## Importar namespaces
Para começar, importe os namespaces necessários para o seu projeto. Esses namespaces fornecerão acesso às funcionalidades necessárias para comparação e manipulação de documentos.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Etapa 1: Especifique o diretório de saída e os nomes dos arquivos
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Certifique-se de substituir`"Your Document Directory"` com o caminho para o diretório de saída desejado.
## Etapa 2: inicializar o comparador e comparar documentos
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Este código inicializa o objeto Comparer com o documento de origem e adiciona o documento de destino para comparação. Em seguida, executa o processo de comparação.
## Etapa 3: recuperar e manipular alterações
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Recupere as alterações da comparação e manipule-as conforme necessário. Neste exemplo, as alterações são rejeitadas primeiro e depois aceitas. Os documentos resultantes são salvos adequadamente.

## Conclusão
Concluindo, GroupDocs Comparison for .NET oferece uma solução perfeita para aceitar e rejeitar alterações em documentos. Seguindo as etapas descritas neste tutorial, os desenvolvedores podem integrar essa funcionalidade com eficiência em seus aplicativos, garantindo a precisão dos documentos e aprimorando a colaboração.
## Perguntas frequentes
### O GroupDocs Comparison for .NET pode comparar documentos de diferentes formatos?
Sim, o GroupDocs Comparison for .NET oferece suporte à comparação entre documentos de vários formatos, como DOCX, PDF, PPTX e muito mais.
### A comparação do GroupDocs para .NET é compatível com o .NET Core?
Sim, a Comparação de GroupDocs para .NET é compatível com .NET Framework e .NET Core.
### Posso personalizar a aparência das alterações nos documentos comparados?
Com certeza, o GroupDocs Comparison for .NET oferece amplas opções para personalizar a aparência das alterações, incluindo cor, estilo e muito mais.
### O GroupDocs Comparison for .NET oferece suporte à comparação de documentos de várias páginas?
Sim, o GroupDocs Comparison for .NET oferece suporte à comparação de documentos de várias páginas com precisão e exatidão.
### Existe uma versão de teste disponível para GroupDocs Comparison for .NET?
 Sim, você pode aproveitar uma avaliação gratuita do GroupDocs Comparison for .NET no site fornecido[link](https://releases.groupdocs.com/).