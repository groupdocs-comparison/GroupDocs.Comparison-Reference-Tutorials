---
categories:
- Image Processing
date: '2026-05-31'
description: Scopri come confrontare le immagini in .NET usando GroupDocs.Comparison
  disabilitando la pagina di riepilogo. Questo tutorial copre configurazione, codice,
  consigli sulle prestazioni e casi d'uso reali.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Confronta immagini .NET senza riepilogo
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
title: Come confrontare le immagini in .NET – Saltare la pagina di riepilogo
type: docs
url: /it/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Come confrontare le immagini in .NET – Saltare la pagina di riepilogo

Quando hai bisogno di **come confrontare le immagini** programmaticamente in un'applicazione .NET, l'ultima cosa che desideri è una pagina di riepilogo aggiuntiva che spreca tempo e spazio di archiviazione. Che tu stia costruendo una linea di controllo qualità, una pipeline di gestione dei contenuti o una suite di test di regressione visiva automatizzata, saltare la pagina di riepilogo può ridurre di qualche secondo ogni esecuzione e mantenere l'ingombro del disco ridotto.

In questo tutorial imparerai a utilizzare **GroupDocs.Comparison for .NET** per confrontare due immagini in modo efficiente, configurare la libreria per sopprimere la generazione del riepilogo e applicare trucchi di performance basati sulle migliori pratiche. Esploreremo anche perché è importante, quando usarlo e come evitare le insidie comuni.

## Risposte rapide
- **Qual è il modo più veloce per confrontare le immagini senza una pagina di riepilogo?** Usa `Comparer` con `CompareOptions` e imposta `GenerateSummaryPage = false`.  
- **Quale libreria supporta questo subito?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Ho bisogno di una licenza?** Sì, è necessaria una licenza commerciale per la produzione; una prova gratuita funziona per lo sviluppo.  
- **Posso confrontare più di due immagini contemporaneamente?** Assolutamente – chiama `Add()` più volte prima di `Compare()`.  
- **Questo approccio è adatto per lavori batch su larga scala?** Sì, quando combinato con l'elaborazione batch e una corretta gestione della memoria.

## Cos'è GroupDocs.Comparison?
`GroupDocs.Comparison` è una libreria .NET che rileva differenze visive tra documenti e immagini, producendo risultati affiancati o sovrapposti. Supporta **oltre 50 formati di input e output**, inclusi JPEG, PNG, BMP, TIFF e GIF, e può elaborare file con centinaia di pagine senza caricare l'intero file in memoria.

## Perché saltare la pagina di riepilogo?
Disabilitare la pagina di riepilogo riduce I/O fino al **70 %** per confronti solo di immagini e riduce il tempo di elaborazione di circa **30 %** in media, secondo la suite di benchmark della libreria. Quando hai bisogno solo dell'immagine di differenza (per test automatizzati o decisioni di pass/fail QC), il report HTML aggiuntivo non aggiunge valore e consuma solo spazio su disco.

## Prerequisiti e configurazione dell'ambiente

### Cosa ti serve
- **GroupDocs.Comparison for .NET** versione **25.4.0** o più recente
- Visual Studio 2019 + o qualsiasi IDE compatibile con .NET
- .NET Framework 4.6.1 + **o** .NET Core 2.0 +
- Conoscenze di base di C# e familiarità con I/O di file

### Extra consigliati
- Un piccolo progetto di test contenente una coppia di immagini di esempio (ad es., `source.png` e `target.png`).
- Facoltativo: configurazione dell'iniezione delle dipendenze se preferisci un'architettura orientata ai servizi.

### Perché questi prerequisiti sono importanti
La versione specificata della libreria include il flag `GenerateSummaryPage` e miglioramenti delle prestazioni che le versioni precedenti non hanno. Utilizzare un IDE moderno garantisce di poter sfruttare la gestione dei pacchetti NuGet e vedere gli avvisi di compilazione in anticipo.

## Come installare GroupDocs.Comparison
GroupDocs.Comparison può essere aggiunto a qualsiasi progetto .NET tramite NuGet, che gestisce il download dei binari e l'aggiornamento del file di progetto. Scegli il metodo che corrisponde al tuo flusso di lavoro: la Package Manager Console per gli utenti di Visual Studio o la .NET CLI per ambienti da riga di comando. Entrambi i comandi risolvono automaticamente le dipendenze e garantiscono che venga referenziata la versione corretta.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Sostituisci `25.4.0` con la versione esatta che intendi bloccare.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Entrambi i comandi aggiungono la libreria al file di progetto e ripristinano i binari necessari.

**Suggerimento:** Blocca la versione nel tuo `.csproj` per evitare aggiornamenti accidentali che potrebbero modificare il comportamento dell'API.

## Considerazioni sulla licenza
GroupDocs.Comparison richiede una licenza per qualsiasi distribuzione in produzione. Puoi iniziare con una **prova gratuita** che fornisce tutte le funzionalità, poi passare a una **licenza temporanea** per test estesi, e infine a una **licenza commerciale completa** per la produzione. Ricorda di posizionare il file `GroupDocs.Comparison.lic` nella radice dell'applicazione o specificarne il percorso programmaticamente.

## Configurazione di base del progetto
Crea una nuova applicazione console (o integrala in un servizio esistente) e aggiungi il seguente codice di base. Questo snippet dimostra la configurazione minima necessaria prima di immergerti nella logica di confronto.

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

> **Importante:** Usa sempre `Path.Combine()` per i percorsi dei file. Gestisce automaticamente i separatori di percorso specifici del sistema operativo ed evita bug sottili quando si passa da contenitori Windows a Linux.

## Guida all'implementazione passo‑passo

### Come confronto le immagini senza una pagina di riepilogo?
`Comparer` è la classe principale in GroupDocs.Comparison che orchestra le operazioni di confronto di documenti e immagini. `CompareOptions` contiene le impostazioni di configurazione che controllano come viene eseguito il confronto, ad esempio se generare una pagina di riepilogo. Carica l'immagine di origine, configura `CompareOptions` per disabilitare il riepilogo, aggiungi l'immagine di destinazione e invoca `Compare()`. Il metodo restituisce un `ComparisonResult` contenente lo stream dell'immagine di differenza, che puoi scrivere su disco, inviare su una rete o incorporare in un componente UI. Questo approccio garantisce che venga prodotto solo il diff essenziale, eliminando qualsiasi report HTML o PDF aggiuntivo.

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

Il codice sopra esegue l'intero confronto in **quattro passaggi logici** e scrive solo l'immagine di differenza, omettendo qualsiasi riepilogo HTML o PDF.

### Passo 1: Inizializza l'oggetto Comparer
La classe `Comparer` è il gateway a tutte le operazioni di confronto. Implementa `IDisposable`, quindi avvolgerla in un blocco `using` garantisce che i handle dei file e la memoria non gestita vengano rilasciati prontamente, anche se viene sollevata un'eccezione.

### Passo 2: Configura CompareOptions per nessun riepilogo
Imposta `GenerateSummaryPage = false` sull'istanza `CompareOptions`. Questo flag indica al motore di saltare la creazione del report HTML predefinito, che è la principale fonte di I/O extra negli scenari solo immagine.

### Passo 3: Aggiungi immagine(i) di destinazione per il confronto
Puoi chiamare `Add()` più volte per confrontare una sorgente con diverse destinazioni in un unico batch. Ogni chiamata può ricevere il proprio `CompareOptions` se hai bisogno di personalizzazioni per immagine.

### Passo 4: Esegui il confronto e salva i risultati
`Comparer.Compare()` esegue il lavoro pesante e restituisce un `ComparisonResult`. Il risultato contiene uno `Stream` con l'immagine di differenza, che puoi salvare direttamente su disco, inviare su una rete o incorporare in un componente UI.

## Metodo completo pronto per la produzione
Di seguito è riportato un metodo pronto all'uso che puoi inserire in qualsiasi servizio .NET. Include la convalida del percorso, la gestione delle eccezioni e hook di logging opzionali.

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

## Problemi comuni di implementazione (e come evitarli)

- **Problemi di percorso:** Verifica sempre che entrambi i file di origine e destinazione esistano con `File.Exists()`. Un file mancante genererà una `FileNotFoundException` che può essere catturata in anticipo.  
- **Pressione sulla memoria:** Immagini grandi (10 MB +) possono consumare molta RAM. Elaborale in batch e considera il down‑scaling se la precisione pixel‑perfect non è necessaria.  
- **Blocchi di file:** Assicurati che nessun altro processo detenga un lock esclusivo sui file immagine. Questo è particolarmente importante in ambienti multithread o containerizzati.

## Applicazioni pratiche e casi d'uso

### Controllo qualità nella produzione
Una linea di produzione cattura immagini di ogni articolo e le confronta con un riferimento d'oro. Saltare la pagina di riepilogo consente al sistema di decidere “pass” o “fail” entro millisecondi, mantenendo la linea in movimento ad alta velocità.

### Sistemi di gestione dei contenuti
Quando gli utenti caricano risorse, il CMS può rilevare istantaneamente duplicati o quasi‑duplicati, prevenendo l'ingombro di archiviazione e migliorando la rilevanza della ricerca. L'immagine di differenza può essere memorizzata come miniatura per una rapida ispezione visiva.

### Test UI automatizzati (regressione visiva)
Selenium o Playwright possono catturare screenshot di una pagina web, quindi passarli a questa routine di confronto. L'immagine di differenza evidenzia le modifiche UI e, poiché non viene generato alcun riepilogo, la pipeline CI rimane veloce e leggera.

### Imaging medico (con audit)
I flussi di lavoro di radiologia a volte devono segnalare cambiamenti tra scansioni successive. Anche se potresti ancora generare un log di audit dettagliato, l'immagine di differenza stessa può essere prodotta senza una pagina di riepilogo, riducendo il tempo di elaborazione per grandi PNG convertiti da DICOM.

## Considerazioni sulle prestazioni e ottimizzazione

### Best practice per la gestione della memoria
Elabora le immagini in **batch di 20–50** a seconda della RAM del server. Rilascia prontamente ogni istanza `Comparer` e invoca `GC.Collect()` solo se noti picchi di memoria durante lavori a lungo termine.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Ottimizzazione I/O disco
Posiziona le tue directory di input, output e temporanee sullo stesso volume SSD veloce. Elimina i file temporanei subito dopo che l'immagine di differenza è stata salvata per evitare utilizzo inutile del disco.

### Considerazioni su threading e async
GroupDocs.Comparison è thread‑safe per operazioni di sola lettura, ma evita di condividere una singola istanza `Comparer` tra thread. Invece, avvia task indipendenti:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Risoluzione dei problemi comuni

### Errori di percorso file e permessi
- **Sintomo:** `FileNotFoundException` o `UnauthorizedAccessException`.  
- **Soluzione:** Usa `Path.GetFullPath()` per debug del percorso risolto, assicurati che l'identità del pool di applicazioni (o l'utente del contenitore Docker) abbia diritti di lettura/scrittura, e ricontrolla che il percorso non sia troncato dalle variabili d'ambiente.

### Colli di bottiglia di memoria e prestazioni
- **Sintomo:** Esecuzioni lente o `OutOfMemoryException`.  
- **Soluzione:** Ridimensiona le immagini a una risoluzione comune (ad es., 1024 × 768) quando il confronto pixel‑perfect non è richiesto. Monitora la memoria con strumenti come dotMemory o il Performance Profiler integrato.

### Problemi di licenza
- **Sintomo:** Immagine di differenza con filigrana o `LicenseException`.  
- **Soluzione:** Conferma che `GroupDocs.Comparison.lic` si trovi nella directory eseguibile o caricala esplicitamente tramite `License license = new License(); license.SetLicense("path/to/license.file");`.

## Opzioni di configurazione avanzate

### Personalizzazione della sensibilità del confronto
Puoi regolare finemente come il motore tratta le piccole variazioni di pixel (ad es., artefatti di compressione) modificando la proprietà `Sensitivity` su `CompareOptions`. Valori più bassi rendono il confronto più severo.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Ottimizzazione del formato di output
Se hai bisogno dell'immagine di differenza in un formato specifico (PNG vs. JPEG), imposta la proprietà `OutputFormat`:

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

## Integrazione con i framework .NET popolari

### Esempio di servizio ASP.NET Core
Esporre un endpoint HTTP leggero che accetta due stream di immagine, esegue il confronto e restituisce l'immagine di differenza come `FileResult`.

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

### Registrazione dell'iniezione delle dipendenze
Aggiungi il comparatore come servizio scoped in `Program.cs` o `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Domande frequenti

**D: Qual è il principale vantaggio di saltare la pagina di riepilogo?**  
R: Riduce il tempo di elaborazione fino al 30 % e diminuisce l'uso del disco di circa il 70 % per confronti solo immagine, il che è critico per pipeline ad alta velocità.

**D: Posso ancora recuperare metadati dettagliati delle modifiche senza una pagina di riepilogo?**  
R: Sì. L'oggetto `ComparisonResult` espone una collezione `Changes` che contiene informazioni programmatiche su ogni differenza rilevata.

**D: Quali formati di immagine sono supportati?**  
R: JPEG, PNG, BMP, TIFF, GIF e diversi altri — oltre 50 formati in totale.

**D: Come devo gestire immagini molto grandi (ad es., >20 MB)?**  
R: Elaborale in batch più piccoli, opzionalmente ridimensionandole, e monitora l'uso della memoria. Usare `Comparer` in un blocco `using` garantisce il rilascio tempestivo delle risorse.

**D: Questo approccio è sicuro per applicazioni multithread?**  
R: Sì, purché ogni thread crei la propria istanza `Comparer`. Condividere una singola istanza può portare a condizioni di gara.

## Risorse aggiuntive
- [Documentazione di GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Riferimento API](https://reference.groupdocs.com/comparison/net/)
- [Download](https://releases.groupdocs.com/comparison/net/)
- [Acquista](https://purchase.groupdocs.com/buy)
- [Prova gratuita](https://releases.groupdocs.com/comparison/net/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)
- [Forum di supporto](https://forum.groupdocs.com/c/comparison/)

---

**Ultimo aggiornamento:** 2026-05-31  
**Testato con:** GroupDocs.Comparison 25.4.0 per .NET  
**Autore:** GroupDocs

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

## Tutorial correlati
- [Confronto immagini .NET - Confronta immagini programmaticamente](/comparison/net/image-comparison/compare-images-from-path/)
- [Confronto immagini .NET - Confronta immagini dallo stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [Tutorial GroupDocs Comparison .NET - Guida completa all'uso base](/comparison/net/basic-usage/)