---
categories:
- Image Processing
date: '2026-05-31'
description: Aprenda a comparar imagens em .NET usando o GroupDocs.Comparison enquanto
  desativa a página de resumo. Este tutorial cobre configuração, código, dicas de
  desempenho e casos de uso reais.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Comparar imagens .NET sem resumo
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Como comparar imagens em .NET – Ignorar página de resumo
type: docs
url: /pt/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Como Comparar Imagens em .NET – Pular Página de Resumo

Quando você precisa **como comparar imagens** programaticamente em uma aplicação .NET, a última coisa que deseja é uma página de resumo extra que desperdiça tempo e armazenamento. Seja construindo uma linha de controle de qualidade, um pipeline de gerenciamento de conteúdo ou uma suíte de testes de regressão visual automatizada, pular a página de resumo pode economizar segundos em cada execução e manter sua pegada de disco enxuta.

Neste tutorial você aprenderá a usar **GroupDocs.Comparison for .NET** para comparar duas imagens de forma eficiente, configurar a biblioteca para suprimir a geração de resumo e aplicar truques de desempenho baseados nas melhores práticas. Também exploraremos por que isso importa, quando usá‑lo e como evitar armadilhas comuns.

## Respostas Rápidas
- **Qual é a maneira mais rápida de comparar imagens sem uma página de resumo?** Use `Comparer` com `CompareOptions` e defina `GenerateSummaryPage = false`.  
- **Qual biblioteca oferece isso pronto para uso?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Preciso de uma licença?** Sim, uma licença comercial é necessária para produção; um teste gratuito funciona para desenvolvimento.  
- **Posso comparar mais de duas imagens ao mesmo tempo?** Absolutamente – chame `Add()` várias vezes antes de `Compare()`.  
- **Esta abordagem é adequada para trabalhos em lote de grande escala?** Sim, quando combinada com processamento em lote e gerenciamento adequado de memória.

## O que é GroupDocs.Comparison?
`GroupDocs.Comparison` é uma biblioteca .NET que detecta diferenças visuais entre documentos e imagens, produzindo resultados lado a lado ou sobrepostos. Ela suporta **mais de 50 formatos de entrada e saída**, incluindo JPEG, PNG, BMP, TIFF e GIF, e pode processar arquivos com centenas de páginas sem carregar todo o arquivo na memória.

## Por que Pular a Página de Resumo?
Desativar a página de resumo reduz I/O em até **70 %** para comparações apenas de imagens e diminui o tempo de processamento em cerca de **30 %** em média, de acordo com o conjunto de benchmarks da biblioteca. Quando você só precisa da imagem de diferença (para testes automatizados ou decisões de aprovação/reprovação de controle de qualidade), o relatório HTML extra não agrega valor e apenas consome espaço em disco.

## Pré‑requisitos e Configuração do Ambiente

### O que Você Precisa
- **GroupDocs.Comparison for .NET** versão **25.4.0** ou mais recente  
- Visual Studio 2019 + ou qualquer IDE compatível com .NET  
- .NET Framework 4.6.1 + **ou** .NET Core 2.0 +  
- Conhecimento básico de C# e familiaridade com I/O de arquivos  

### Extras Recomendados
- Um pequeno projeto de teste contendo um par de imagens de exemplo (por exemplo, `source.png` e `target.png`).  
- Opcional: configuração de injeção de dependência se você preferir uma arquitetura orientada a serviços.  

### Por que Esses Pré‑requisitos Importam
A versão especificada da biblioteca inclui a flag `GenerateSummaryPage` e melhorias de desempenho que versões anteriores não possuem. Usar uma IDE moderna garante que você possa aproveitar o gerenciamento de pacotes NuGet e ver avisos de compilação antecipadamente.

## Como Instalar o GroupDocs.Comparison
GroupDocs.Comparison pode ser adicionado a qualquer projeto .NET via NuGet, que cuida de baixar os binários e atualizar o arquivo do projeto. Escolha o método que corresponde ao seu fluxo de trabalho: o Package Manager Console para usuários do Visual Studio ou o .NET CLI para ambientes de linha de comando. Ambos os comandos resolvem dependências automaticamente e garantem que a versão correta seja referenciada.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Substitua `25.4.0` pela versão exata que você pretende fixar.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Ambos os comandos adicionam a biblioteca ao seu arquivo de projeto e restauram os binários necessários.

**Dica:** Fixe a versão no seu `.csproj` para evitar atualizações acidentais que possam mudar o comportamento da API.

## Considerações de Licenciamento
GroupDocs.Comparison requer uma licença para qualquer implantação em produção. Você pode começar com um **teste gratuito** que fornece funcionalidade completa, depois atualizar para uma **licença temporária** para testes estendidos e, finalmente, para uma **licença comercial completa** para produção. Lembre‑se de colocar o arquivo `GroupDocs.Comparison.lic` na raiz da aplicação ou especificar seu caminho programaticamente.

## Configuração Básica do Projeto
Crie um novo aplicativo console (ou integre a um serviço existente) e adicione o código boilerplate a seguir. Este trecho demonstra a configuração mínima necessária antes de mergulhar na lógica de comparação.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Importante:** Sempre use `Path.Combine()` para caminhos de arquivos. Ele lida automaticamente com separadores de caminho específicos do SO e evita bugs sutis ao mover entre contêineres Windows e Linux.

## Guia de Implementação Passo a Passo

### Como comparar imagens sem uma página de resumo?
`Comparer` é a classe principal no GroupDocs.Comparison que orquestra operações de comparação de documentos e imagens. `CompareOptions` contém configurações que controlam como a comparação é realizada, como se deve gerar uma página de resumo. Carregue a imagem de origem, configure `CompareOptions` para desativar o resumo, adicione a imagem alvo e invoque `Compare()`. O método retorna um `ComparisonResult` contendo o fluxo da imagem de diferença, que você pode gravar no disco, enviar pela rede ou incorporar em um componente de UI. Essa abordagem garante que apenas a diferença essencial seja produzida, eliminando quaisquer relatórios HTML ou PDF extras.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

O código acima executa toda a comparação em **quatro etapas lógicas** e grava apenas a imagem de diferença, omitindo qualquer resumo HTML ou PDF.

### Etapa 1: Inicializar o Objeto Comparer
A classe `Comparer` é a porta de entrada para todas as operações de comparação. Ela implementa `IDisposable`, portanto, envolvê‑la em um bloco `using` garante que os manipuladores de arquivos e a memória não gerenciada sejam liberados prontamente, mesmo que uma exceção seja lançada.

### Etapa 2: Configurar CompareOptions para Sem Resumo
Defina `GenerateSummaryPage = false` na instância `CompareOptions`. Essa flag indica ao motor que ignore a criação do relatório HTML padrão, que é a principal fonte de I/O extra em cenários apenas de imagem.

### Etapa 3: Adicionar Imagem(ns) Alvo(s) para Comparação
Você pode chamar `Add()` várias vezes para comparar uma fonte contra vários alvos em um único lote. Cada chamada pode receber seu próprio `CompareOptions` se precisar de personalizações por imagem.

### Etapa 4: Executar a Comparação e Salvar os Resultados
`Comparer.Compare()` realiza o trabalho pesado e retorna um `ComparisonResult`. O resultado contém um `Stream` com a imagem de diferença, que você pode salvar diretamente no disco, enviar pela rede ou incorporar em um componente de UI.

## Método Completo Pronto para Produção
Abaixo está um método pronto para uso que você pode inserir em qualquer serviço .NET. Ele inclui validação de caminho, tratamento de exceções e ganchos de registro opcionais.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Armadilhas Comuns de Implementação (E Como Evitá‑las)

- **Problemas de Caminho:** Sempre verifique se os arquivos de origem e destino existem com `File.Exists()`. Um arquivo ausente lançará uma `FileNotFoundException` que pode ser capturada cedo.  
- **Pressão de Memória:** Imagens grandes (10 MB +) podem consumir RAM significativa. Processá‑las em lotes e considerar reduzir a escala se a precisão pixel‑a‑pixel não for necessária.  
- **Bloqueios de Arquivo:** Garanta que nenhum outro processo mantenha um bloqueio exclusivo nos arquivos de imagem. Isso é especialmente importante em ambientes multithread ou conteinerizados.

## Aplicações Práticas e Casos de Uso

### Controle de Qualidade na Fabricação
Uma linha de produção captura imagens de cada item e as compara com uma referência padrão. Pular a página de resumo permite que o sistema decida “aprovar” ou “reprovar” em milissegundos, mantendo a linha em alta velocidade.

### Sistemas de Gerenciamento de Conteúdo
Quando os usuários enviam ativos, o CMS pode detectar instantaneamente duplicatas ou quase‑duplicatas, evitando o inchaço de armazenamento e melhorando a relevância da busca. A imagem de diferença pode ser armazenada como miniatura para inspeção visual rápida.

### Testes de UI Automatizados (Regressão Visual
Selenium ou Playwright podem capturar screenshots de uma página web e então alimentá‑las a esta rotina de comparação. A imagem de diferença destaca alterações na UI e, como nenhum resumo é gerado, o pipeline de CI permanece rápido e leve.

### Imagens Médicas (Com Auditoria)
Fluxos de trabalho de radiologia às vezes precisam sinalizar mudanças entre exames sucessivos. Embora ainda possa gerar um log de auditoria detalhado, a própria imagem de diferença pode ser produzida sem uma página de resumo, reduzindo o tempo de processamento para grandes PNGs convertidos de DICOM.

## Considerações de Desempenho e Otimização

### Melhores Práticas de Gerenciamento de Memória
Processar imagens em **lotes de 20–50** dependendo da RAM do servidor. Libere cada instância `Comparer` prontamente e invoque `GC.Collect()` somente se notar picos de memória durante trabalhos de longa duração.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Otimização de I/O de Disco
Coloque seus diretórios de entrada, saída e temporários no mesmo volume SSD rápido. Delete arquivos temporários imediatamente após a imagem de diferença ser salva para evitar uso desnecessário de disco.

### Considerações de Threading e Async
GroupDocs.Comparison é thread‑safe para operações somente de leitura, mas evite compartilhar uma única instância `Comparer` entre threads. Em vez disso, crie tarefas independentes:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Solução de Problemas de Questões Comuns

### Erros de Caminho de Arquivo e Permissão
- **Sintoma:** `FileNotFoundException` ou `UnauthorizedAccessException`.  
- **Solução:** Use `Path.GetFullPath()` para depurar o caminho resolvido, garanta que a identidade do pool de aplicativos (ou usuário do contêiner Docker) tenha direitos de leitura/escrita e verifique se o caminho não foi truncado por variáveis de ambiente.

### Gargalos de Memória e Desempenho
- **Sintoma:** Execuções lentas ou `OutOfMemoryException`.  
- **Solução:** Redimensione as imagens para uma resolução comum (por exemplo, 1024 × 768) quando a comparação pixel‑a‑pixel exata não for necessária. Monitore a memória com ferramentas como dotMemory ou o Performance Profiler integrado.

### Problemas de Licenciamento
- **Sintoma:** Imagem de diferença com marca d'água ou `LicenseException`.  
- **Solução:** Confirme que `GroupDocs.Comparison.lic` está localizado no diretório executável ou carregue‑o explicitamente via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Opções Avançadas de Configuração

### Personalizando a Sensibilidade da Comparação
Você pode ajustar finamente como o motor trata variações menores de pixel (por exemplo, artefatos de compressão) ajustando a propriedade `Sensitivity` em `CompareOptions`. Valores mais baixos tornam a comparação mais rigorosa.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Otimização do Formato de Saída
Se você precisar da imagem de diferença em um formato específico (PNG vs. JPEG), defina a propriedade `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Integração com Frameworks .NET Populares

### Exemplo de Serviço ASP.NET Core
Exponha um endpoint HTTP leve que aceita dois streams de imagem, executa a comparação e retorna a imagem de diferença como um `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Registro de Injeção de Dependência
Adicione o comparador como um serviço scoped em `Program.cs` ou `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Perguntas Frequentes

**Q: Qual é a principal vantagem de pular a página de resumo?**  
A: Reduz o tempo de processamento em até 30 % e diminui o uso de disco em cerca de 70 % para comparações apenas de imagens, o que é crítico para pipelines de alta taxa de transferência.

**Q: Ainda posso obter metadados detalhados de alterações sem uma página de resumo?**  
A: Sim. O objeto `ComparisonResult` expõe uma coleção `Changes` que contém informações programáticas sobre cada diferença detectada.

**Q: Quais formatos de imagem são suportados?**  
A: JPEG, PNG, BMP, TIFF, GIF e vários outros — mais de 50 formatos no total.

**Q: Como devo lidar com imagens muito grandes (por exemplo, >20 MB)?**  
A: Processá‑las em lotes menores, opcionalmente reduzi‑las e monitorar o uso de memória. Usar `Comparer` em um bloco `using` garante que os recursos sejam liberados prontamente.

**Q: Esta abordagem é segura para aplicações multithread?**  
A: Sim, desde que cada thread crie sua própria instância `Comparer`. Compartilhar uma única instância pode levar a condições de corrida.

## Recursos Adicionais

- [Documentação do GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Referência da API](https://reference.groupdocs.com/comparison/net/)
- [Download](https://releases.groupdocs.com/comparison/net/)
- [Compra](https://purchase.groupdocs.com/buy)
- [Teste Gratuito](https://releases.groupdocs.com/comparison/net/)
- [Licença Temporária](https://purchase.groupdocs.com/temporary-license/)
- [Fórum de Suporte](https://forum.groupdocs.com/c/comparison/)

---

**Última Atualização:** 2026-05-31  
**Testado com:** GroupDocs.Comparison 25.4.0 for .NET  
**Autor:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Tutoriais Relacionados

- [Comparação de Imagens .NET - Comparar Imagens Programaticamente](/comparison/net/image-comparison/compare-images-from-path/)
- [Comparação de Imagens .NET - Comparar Imagens a partir de Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [Tutorial GroupDocs Comparison .NET - Guia Completo de Uso Básico](/comparison/net/basic-usage/)