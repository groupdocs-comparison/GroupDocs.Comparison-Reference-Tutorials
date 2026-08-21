---
categories:
- Document Processing
date: '2026-07-01'
description: Scopri come leggere i metadati del file C# usando GroupDocs.Comparison,
  estrarre file size stream e ottenere document properties stream in modo efficiente.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Estrai le informazioni del documento .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: Leggi i metadati del file C# – Estrai le informazioni del documento dagli stream
type: docs
url: /it/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Leggi i Metadati del File C# – Estrai le Informazioni del Documento da Stream

## Introduzione

Leggere i metadati di un file in C# senza caricare l'intero documento è un requisito comune per le moderne applicazioni .NET. **Read file metadata C#** ti consente di convalidare gli upload, visualizzare i dettagli del documento e prendere decisioni di elaborazione mantenendo basso l'uso della memoria. GroupDocs.Comparison per .NET fornisce un'API veloce basata su stream che estrae il tipo di file, il conteggio delle pagine, la dimensione e altre proprietà direttamente da un `Stream`. Nelle sezioni successive vedrai perché è importante, come configurarlo e il codice passo‑paso da inserire in qualsiasi progetto .NET.

## Risposte Rapide
- **Cosa significa “read file metadata C#”?** Indica il recupero delle proprietà di un documento (tipo, pagine, dimensione) tramite uno stream .NET senza caricare l'intero contenuto.  
- **Quale libreria gestisce questa operazione?** GroupDocs.Comparison per .NET offre il metodo `GetDocumentInfo()` per un'estrazione rapida dei metadati.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per lo sviluppo; è richiesta una licenza commerciale per la produzione.  
- **Posso usarlo con PDF di grandi dimensioni?** Sì – l'approccio basato su stream elabora file con centinaia di pagine senza un elevato consumo di memoria.  
- **È compatibile con .NET 6+?** Assolutamente, la libreria è mirata a .NET Standard 2.0 e funziona su .NET 6, .NET 7 e .NET Core.

## Cos'è read file metadata C#?
`Read file metadata C#` si riferisce all'ottenimento delle informazioni descrittive di un documento — come formato, numero di pagine e dimensione in byte — usando codice C# che lavora con gli stream. Questa tecnica evita di caricare l'intero file in memoria, il che è particolarmente utile per PDF di grandi dimensioni, file DOCX o operazioni batch.

## Perché utilizzare l'estrazione dei metadati di GroupDocs da stream?
GroupDocs.Comparison supporta **oltre 50 formati di input e output** e può estrarre metadati da file fino a **2 GB** mantenendo l'uso della memoria sotto **10 MB**. La libreria legge solo le sezioni di intestazione necessarie, fornendo risultati in **meno di 150 ms** per PDF tipici di 100 pagine su un server standard. Questi vantaggi quantificati si traducono in una convalida degli upload più veloce, costi cloud ridotti e un'esperienza utente più fluida.

## Prerequisiti e Configurazione

### 1. Installa GroupDocs.Comparison per .NET
Scarica l'ultimo pacchetto dalla [official download page](https://releases.groupdocs.com/comparison/net/). Se preferisci NuGet, esegui:

```
Install-Package GroupDocs.Comparison
```

### 2. Conoscenze di Base dello Sviluppo .NET  
Dovresti sentirti a tuo agio con C# e il modello I/O di .NET. Lavorare con `Stream`, `FileStream` e `MemoryStream` è fondamentale per gli esempi seguenti.

### 3. Ambiente di Sviluppo  
Visual Studio, VS Code o JetBrains Rider sono tutti supportati. Assicurati che il tuo progetto punti a .NET 6 o versioni successive per ottenere le migliori prestazioni.

## Come leggere i metadati di un file C# da uno stream?

Carica il documento con un `FileStream`, istanzia un `Comparer` e chiama `GetDocumentInfo()`. L'intera operazione richiede solo due righe di codice e restituisce un oggetto `IDocumentInfo` contenente il tipo di file, il conteggio delle pagine e la dimensione. Internamente la libreria legge solo i byte di intestazione necessari, così anche i PDF di grandi dimensioni vengono elaborati rapidamente senza consumare molta memoria.  
`Comparer` è la classe principale di GroupDocs.Comparison che orchestra l'analisi del documento.  
`GetDocumentInfo()` restituisce un oggetto `IDocumentInfo` con i metadati di base.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Passo 1: Inizializza l'Oggetto Comparer con lo Stream

Il frammento seguente crea un'istanza di `Comparer` a partire da un `FileStream` in sola lettura. L'uso di un blocco `using` garantisce che lo stream venga chiuso e il comparer eliminato, evitando blocchi di file.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Passo 2: Estrai le Informazioni del Documento

Chiamare `GetDocumentInfo()` restituisce un oggetto `IDocumentInfo` che contiene tutti i metadati di cui hai bisogno. Il metodo legge solo le parti necessarie dell'intestazione del file, così anche un PDF di 500 pagine viene processato in una frazione di secondo.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Passo 3: Visualizza e Usa le Informazioni del Documento

Ora puoi accedere alle proprietà `FileType`, `PageCount` e `Size`. In produzione potresti memorizzare questi valori in un database, esporli tramite un'API o usarli per decidere se accettare un upload.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Casi d'Uso Comuni e Modelli di Implementazione

### Convalida degli Upload di File

Quando un utente carica un documento, puoi verificare immediatamente il suo tipo e il numero di pagine prima di salvarlo. Questo impedisce l'ingresso di formati indesiderati e file troppo grandi nel tuo sistema.

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### Analisi Batch di Documenti

Stai elaborando una cartella di documenti? Estrai prima i metadati per instradare i file in pipeline diverse — ad esempio, i PDF di grandi dimensioni vanno a un worker asincrono, mentre i file a pagina singola vengono gestiti inline.

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## Problemi Comuni e Soluzioni

### Problemi di Accesso e Blocco del File

**Problema**: “The file is being used by another process.”  
**Soluzione**: Avvolgi lo stream in una dichiarazione `using` e, se necessario, implementa una politica di retry con back‑off esponenziale.

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### Gestione di Formati di File Non Supportati

**Problema**: L'API lancia un'eccezione per un formato sconosciuto.  
**Soluzione**: Controlla la proprietà `FileType`; se restituisce `Unknown`, restituisci un errore amichevole al chiamante e registra l'incidente.

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### Gestione della Memoria con File di Grandi Dimensioni

**Problema**: Picchi di memoria durante l'elaborazione di documenti molto grandi.  
**Soluzione**: L'approccio basato su stream riduce già al minimo l'uso della memoria, ma dovresti anche chiamare `Dispose()` sul `Comparer` non appena hai finito e evitare di mantenere riferimenti a `IDocumentInfo` più a lungo del necessario.

## Considerazioni sulle Prestazioni e Best Practice

### Best Practice per la Gestione degli Stream

1. **Usa sempre le istruzioni `using`** – Garantisce lo smaltimento e libera le risorse tempestivamente.  
2. **Reimposta la posizione dello stream quando lo riutilizzi** – Se devi leggere lo stesso stream due volte, chiama `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Scegli il tipo di stream corretto** – `FileStream` per file su disco, `MemoryStream` per dati in memoria, `NetworkStream` per sorgenti remote.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Quando Preferire Questo Approccio vs. Caricamento Completo del Documento

**Preferisci l'estrazione dei metadati basata su stream quando**:

- Hai bisogno solo di dettagli di alto livello (tipo, pagine, dimensione).  
- Stai convalidando upload o costruendo un catalogo di documenti.  
- Le prestazioni e un basso consumo di memoria sono critici.

**Passa al caricamento completo del documento quando**:

- Devi confrontare contenuti, estrarre testo o renderizzare pagine.  
- È necessaria un'analisi approfondita (ad es. OCR, rilevamento di filigrane).  

## Suggerimenti Avanzati per l'Uso in Produzione

### Strategie di Gestione degli Errori

Avvolgi tutte le operazioni in un blocco try‑catch che cattura `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` viene lanciata dalla libreria quando si verifica un errore durante l'elaborazione del documento. Registra i dettagli dell'errore, restituisci una risposta di errore standardizzata e assicurati che il `Comparer` sia eliminato in un blocco `finally`.

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### Integrazione con Logging e Monitoring

Inietta un framework di logging (ad es. Serilog o NLog) ed emetti metriche come tempo di elaborazione, dimensione del file e conteggi di successi/fallimenti. Questi dati ti aiutano a individuare regressioni di prestazioni in anticipo.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Domande Frequenti

**D: GroupDocs.Comparison per .NET è compatibile con diversi formati di documento?**  
R: Sì. La libreria supporta **oltre 50 formati di file**, inclusi DOCX, PDF, XLSX, PPTX e molti tipi di immagine, rendendola adatta a praticamente qualsiasi flusso di lavoro documentale.

**D: Posso provare GroupDocs.Comparison per .NET prima di acquistarlo?**  
R: Assolutamente. Una prova gratuita è disponibile sul [the website](https://releases.groupdocs.com/), permettendoti di valutare tutte le funzionalità senza licenza.

**D: Dove posso trovare supporto per GroupDocs.Comparison per .NET?**  
R: Puoi ottenere aiuto nel [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12), dove la community e il team di prodotto rispondono rapidamente alle domande.

**D: Sono disponibili licenze temporanee per i test?**  
R: Sì. Le licenze temporanee possono essere ottenute dalla [the licensing page](https://purchase.groupdocs.com/temporary-license/), ideali per ambienti di sviluppo e QA.

**D: GroupDocs.Comparison per .NET è adatto a deployment aziendali?**  
R: Definitivamente. Offre prestazioni di livello enterprise, ampio supporto di formati e una gestione robusta degli errori, tutti elementi essenziali per sistemi di produzione su larga scala.

---

**Ultimo Aggiornamento:** 2026-07-01  
**Testato Con:** GroupDocs.Comparison 23.10 per .NET  
**Autore:** GroupDocs

## Tutorial Correlati

- [Get Document Properties C# .NET - Extract File Metadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Document Metadata Management .NET - Complete Guide for GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Document Comparison .NET Tutorial - Preserve Metadata with GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)