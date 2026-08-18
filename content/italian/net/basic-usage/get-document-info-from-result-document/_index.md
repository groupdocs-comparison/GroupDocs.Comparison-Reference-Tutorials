---
categories:
- Document Comparison
date: '2026-06-15'
description: Scopri come estrarre i metadati dai risultati di confronto .NET utilizzando
  GroupDocs.Comparison. Guida passo‑passo con esempi di codice e consigli pratici.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Estrai informazioni del documento dai risultati di confronto
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: Come estrarre i metadati dai risultati di confronto .NET – Guida completa
type: docs
url: /it/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Come estrarre i metadati dai risultati del confronto .NET – Guida completa

When you're working with document comparisons in .NET applications, you might wonder **come estrarre i metadati** from the comparison results. Metadata such as file type, page count, and document size can be crucial for audit trails, performance tuning, or simply displaying useful information to end users. This tutorial walks you through retrieving that data efficiently with GroupDocs.Comparison for .NET.

## Risposte rapide
- **Qual è la classe principale per il confronto?** `Comparer` carica il documento sorgente e avvia il motore di confronto.  
- **Quale metodo restituisce i metadati?** `GetDocumentInfo()` su un documento di destinazione restituisce un oggetto `IDocumentInfo`.  
- **Posso ottenere la dimensione del documento in .NET?** Sì – la proprietà `Size` di `IDocumentInfo` restituisce la dimensione in byte.  
- **È necessaria una licenza per l'estrazione dei metadati?** È richiesta una licenza valida di GroupDocs.Comparison per l'uso in produzione; la versione di prova gratuita supporta tutte le funzionalità di metadati.  
- **L'API è compatibile con .NET 6?** Assolutamente – GroupDocs.Comparison supporta .NET Framework 4.6.1+, .NET Core 2.0+, e .NET 5/6+.

Il metodo `GetDocumentInfo()` restituisce un oggetto `IDocumentInfo` contenente i metadati del documento.

## Cos'è l'estrazione dei metadati nel confronto di documenti?
L'estrazione dei metadati è il processo di recupero di informazioni descrittive — come tipo di file, numero di pagine e dimensione del file — dai documenti coinvolti in un'operazione di confronto. GroupDocs.Comparison espone questi dati tramite un'API unificata, facilitando il logging, la visualizzazione o l'uso per elaborazioni condizionali.

## Perché estrarre i metadati dai risultati del confronto?
L'estrazione dei metadati consente di creare log di audit dettagliati, instradare i file in base al tipo e regolare le strategie di elaborazione per documenti di grandi dimensioni. Conoscendo il tipo di file, il numero di pagine e la dimensione è possibile applicare regole di conformità, stimare i tempi di elaborazione e presentare informazioni chiare agli utenti prima che avviino un confronto.

## Prerequisiti

1. **GroupDocs.Comparison for .NET** – Installa la libreria dalla [pagina dei rilasci ufficiali](https://releases.groupdocs.com/comparison/net/).  
   Puoi anche sfogliare tutti i rilasci nella [pagina dei rilasci di GroupDocs](https://releases.groupdocs.com/).  
2. **Ambiente di sviluppo** – Visual Studio, VS Code, o qualsiasi IDE che supporti .NET 6+.  
3. **Documenti di esempio** – Due file (ad es., `SOURCE.docx` e `TARGET.docx`) per i test. L'API funziona con oltre **50 formati di documento**.

## Importare gli spazi dei nomi

Le seguenti direttive `using` ti danno accesso al motore di confronto core, alle utility di gestione file e alle interfacce dei metadati.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Queste importazioni sono necessarie prima di istanziare qualsiasi oggetto GroupDocs.

## Come estrarre i metadati dai risultati del confronto?

La classe `Comparer` carica il documento sorgente e orchestra il processo di confronto.

Per recuperare i metadati, prima carica il documento sorgente con un'istanza di `Comparer`, quindi aggiungi il(i) documento(i) di destinazione. Dopo che il motore di confronto è stato inizializzato, chiama `GetDocumentInfo()` su ogni destinazione per ottenere un oggetto `IDocumentInfo` che contiene proprietà come tipo di file, numero di pagine e dimensione. Questo approccio funziona uniformemente su tutti i formati supportati.

### Passo 1: Inizializzare Comparer con il documento sorgente

`Comparer` è la classe core in GroupDocs.Comparison che carica il documento sorgente e orchestra le operazioni di confronto. L'uso di un blocco `using` garantisce che tutte le risorse non gestite vengano rilasciate automaticamente.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Suggerimento:** Puoi passare qualsiasi `Stream` (file, memoria, cloud) al costruttore `Comparer`, non solo un percorso di file.

### Passo 2: Aggiungere il documento di destinazione per il confronto

Il metodo `Add()` accetta stream o percorsi di file aggiuntivi, consentendo confronti uno‑a‑molti.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Importante:** L'ordine dei documenti aggiunti influisce sul modo in cui le modifiche sono evidenziate nel report finale.

### Passo 3: Recuperare le informazioni del documento dal documento risultato

`IDocumentInfo` fornisce una vista unificata dei metadati del documento come tipo di file, numero di pagine e dimensione su tutti i formati supportati.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Comprendere i dati:** L'oggetto restituito funziona allo stesso modo per DOCX, PDF, XLSX e PPTX, quindi puoi scrivere codice indipendente dal formato.

### Passo 4: Visualizzare le informazioni del documento

Una volta ottenuta l'istanza `IDocumentInfo`, puoi registrare, memorizzare o presentare le sue proprietà.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Le tre proprietà più comunemente usate sono:

- **FileType** – ad es., `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – pagine o diapositive totali.  
- **Size** – dimensione del file in byte (utile per calcoli di archiviazione).

## Come ottenere la dimensione del documento in .NET?

La proprietà `Size` restituisce la dimensione del file in byte.

La dimensione del documento può essere acceduta direttamente dall'istanza `IDocumentInfo` tramite la sua proprietà `Size`. Questa proprietà restituisce il numero esatto di byte del file originale, consentendo di convertirlo in kilobyte o megabyte per la visualizzazione o i calcoli di archiviazione. Riflette la dimensione del file sorgente, non di una versione elaborata.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Nota:** Il valore `Size` riflette la dimensione originale del file, non la dimensione dopo eventuali elaborazioni o compressioni interne.

## Casi d'uso comuni e applicazioni pratiche

- **Elaborazione batch:** Usa il tipo di file per instradare i file DOCX a un flusso di lavoro specifico per Word e i PDF a una pipeline ottimizzata per PDF.  
- **Gestione dell'archiviazione:** Archivia automaticamente i documenti più grandi di 10 MB in un bucket di cold‑storage.  
- **Feedback utente:** Mostra il numero di pagine e la dimensione prima del confronto per impostare aspettative realistiche sui tempi di elaborazione.  
- **Assicurazione della qualità:** Verifica che i file caricati siano completi confrontando il numero di pagine previsto con quello reale.

## Risoluzione dei problemi comuni

- **Errori di accesso al file:** Verifica i permessi di lettura e usa percorsi assoluti durante lo sviluppo.  
- **Pressione di memoria con file grandi:** Preferisci lo streaming (`File.OpenRead`) rispetto al caricamento dell'intero file in memoria.  
- **Eccezioni di riferimento nullo:** `FirstOrDefault()` può restituire `null` se non è stato aggiunto alcun target; controlla sempre prima di accedere a `GetDocumentInfo()`.  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **Metadati limitati per testo semplice:** Formati come `.txt` potrebbero non esporre un `PageCount` significativo. Proteggi il codice contro valori mancanti.

## Considerazioni sulle prestazioni

- **Gestione degli stream:** Avvolgi sempre gli stream in istruzioni `using` per rilasciare rapidamente i handle dei file.  
- **Caching:** Memorizza i metadati frequentemente accessi in una cache per evitare estrazioni ripetute.  
- **Operazioni batch:** Elabora i documenti in gruppi per ridurre l'overhead e migliorare il throughput.

## Best practice per l'uso in produzione

- **Gestione robusta degli errori:** Racchiudi l'estrazione dei metadati in blocchi try‑catch per gestire file corrotti o non supportati in modo elegante.  
- **Logging completo:** Registra tipo di documento, dimensione e numero di pagine per ogni confronto per facilitare la risoluzione dei problemi e la conformità di audit.  
- **Igiene della sicurezza:** Evita di esporre percorsi completi dei file o dettagli interni del server nei messaggi UI.  
- **Disposizione delle risorse:** Disporre prontamente delle istanze `Comparer`, specialmente nei servizi web che gestiscono molte richieste concorrenti.

## Scenari avanzati

### Documenti di destinazione multipli

Se confronti una sorgente con più destinazioni, itera attraverso la collezione `Targets` ed estrai i metadati da ciascuna.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Elaborazione condizionale basata sui metadati

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Memorizzare i metadati in un database

Persisti `FileType`, `PageCount` e `Size` in una tabella relazionale per abilitare report e analisi su migliaia di confronti.

## Domande frequenti

**Q: GroupDocs.Comparison per .NET è compatibile con vari formati di documento?**  
A: Sì, supporta **oltre 50 formati** tra cui DOCX, PDF, PPTX, XLSX, TXT e molti altri, fornendo un'estrazione dei metadati coerente su tutti.

**Q: Posso personalizzare le impostazioni di confronto senza influire sull'estrazione dei metadati?**  
A: Assolutamente. Impostazioni come sensibilità, tipi di modifica e formato di output sono indipendenti dalla chiamata `GetDocumentInfo()`.

**Q: Esiste una versione di prova che posso usare per la valutazione?**  
A: Sì, scarica una prova gratuita dalla [pagina dei rilasci di GroupDocs](https://releases.groupdocs.com/). La versione di prova include tutte le capacità di estrazione dei metadati.

**Q: Dove posso ottenere supporto per domande di implementazione?**  
A: Usa il [forum di GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) per aiuto della community e supporto ufficiale dal team di GroupDocs.

**Q: Quali opzioni di licenza sono disponibili per le distribuzioni in produzione?**  
A: GroupDocs offre licenze per sviluppatori, sito e OEM. Le opzioni di acquisto sono elencate nella [pagina di acquisto di GroupDocs](https://purchase.groupdocs.com/buy).

---

**Ultimo aggiornamento:** 2026-06-15  
**Testato con:** GroupDocs.Comparison 6.0 per .NET  
**Autore:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Tutorial correlati

- [Gestione dei metadati dei documenti .NET - Guida completa per GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Ottenere le proprietà del documento C# .NET - Estrarre i metadati del file](/comparison/net/basic-usage/get-document-info-from-path/)
- [Preservare i metadati di destinazione con GroupDocs.Comparison – Tutorial .NET](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)