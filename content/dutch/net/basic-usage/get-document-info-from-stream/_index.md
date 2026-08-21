---
categories:
- Document Processing
date: '2026-07-01'
description: Leer hoe je bestandsmetadata in C# kunt lezen met GroupDocs.Comparison,
  de bestandsgrootte‑stream kunt extraheren en documenteigenschappen‑stream efficiënt
  kunt ophalen.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Documentinformatie extraheren .NET
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
title: Bestandsmetadata lezen C# – Documentinformatie extraheren uit streams
type: docs
url: /nl/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Bestandsmetadata lezen C# – Documentinformatie extraheren uit streams

## Inleiding

Het lezen van bestandsmetadata in C# zonder het volledige document te laden is een veelvoorkomende eis voor moderne .NET-toepassingen. **Read file metadata C#** stelt je in staat uploads te valideren, documentdetails weer te geven en verwerkingsbeslissingen te nemen terwijl het geheugenverbruik laag blijft. GroupDocs.Comparison for .NET biedt een snelle, op streams gebaseerde API die bestandstype, paginatelling, grootte en andere eigenschappen direct uit een `Stream` haalt. In de volgende secties zie je waarom dit belangrijk is, hoe je het instelt en stap‑voor‑stap code die je in elk .NET‑project kunt gebruiken.

## Snelle antwoorden
- **What does “read file metadata C#” mean?** Het betekent het ophalen van de eigenschappen van een document (type, pagina's, grootte) via een .NET‑stream zonder de volledige inhoud te laden.  
- **Which library handles this?** GroupDocs.Comparison for .NET biedt de `GetDocumentInfo()`‑methode voor snelle metadata‑extractie.  
- **Do I need a license?** Een gratis proefversie werkt voor ontwikkeling; een commerciële licentie is vereist voor productie.  
- **Can I use this with large PDFs?** Ja – de stream‑benadering verwerkt bestanden met honderden pagina's zonder hoog geheugenverbruik.  
- **Is it compatible with .NET 6+?** Zeker, de bibliotheek richt zich op .NET Standard 2.0 en werkt op .NET 6, .NET 7 en .NET Core.

## Wat is read file metadata C#?
`Read file metadata C#` verwijst naar het verkrijgen van beschrijvende informatie van een document — zoals formaat, paginatelling en bestandsgrootte — met C#‑code die met streams werkt. Deze techniek voorkomt het laden van het volledige bestand in het geheugen, wat vooral waardevol is voor grote PDF‑s, DOCX‑bestanden of batch‑bewerkingen.

## Waarom GroupDocs-metadata‑extractie uit streams gebruiken?
GroupDocs.Comparison ondersteunt **50+ invoer‑ en uitvoerformaten** en kan metadata extraheren uit bestanden tot **2 GB** groot, terwijl het geheugenverbruik onder **10 MB** blijft. De bibliotheek leest alleen de benodigde header‑secties en levert resultaten in **minder dan 150 ms** voor typische 100‑pagina‑PDF's op een standaard server. Deze kwantificeerbare voordelen vertalen zich naar snellere uploadvalidatie, lagere cloudkosten en een soepelere gebruikerservaring.

## Vereisten en installatie

### 1. Installeer GroupDocs.Comparison voor .NET
Download het nieuwste pakket van de [officiële downloadpagina](https://releases.groupdocs.com/comparison/net/). Als je NuGet verkiest, voer dan uit:

```
Install-Package GroupDocs.Comparison
```

### 2. Basiskennis .NET-ontwikkeling
Je moet vertrouwd zijn met C# en het .NET I/O‑model. Werken met `Stream`, `FileStream` en `MemoryStream` is essentieel voor de onderstaande voorbeelden.

### 3. Ontwikkelomgeving
Visual Studio, VS Code of JetBrains Rider worden allemaal ondersteund. Zorg ervoor dat je project .NET 6 of hoger target voor optimale prestaties.

## Hoe bestandsmetadata lezen C# uit een stream?

Laad het document met een `FileStream`, maak een `Comparer`‑instantie aan en roep `GetDocumentInfo()` aan. De volledige bewerking bestaat uit slechts twee regels code en retourneert een `IDocumentInfo`‑object met het bestandstype, het aantal pagina's en de grootte. Intern leest de bibliotheek alleen de benodigde header‑bytes, zodat zelfs grote PDF's snel worden verwerkt zonder veel geheugen te verbruiken.  
`Comparer` is de hoofdklasse van GroupDocs.Comparison die documentanalyse coördineert.  
`GetDocumentInfo()` retourneert een `IDocumentInfo`‑object met basismetadata.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Stap 1: Initialiseer het Comparer‑object met een stream
De volgende code maakt een `Comparer`‑instantie aan vanuit een alleen‑lezen `FileStream`. Het gebruik van een `using`‑blok garandeert dat de stream wordt gesloten en de comparer wordt vrijgegeven, waardoor bestandsvergrendelingen worden voorkomen.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Stap 2: Documentinformatie extraheren
Het aanroepen van `GetDocumentInfo()` retourneert een `IDocumentInfo`‑object dat alle benodigde metadata bevat. De methode leest alleen de noodzakelijke delen van de bestandsheader, zodat zelfs een PDF van 500 pagina's in een fractie van een seconde wordt verwerkt.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Stap 3: Documentinformatie weergeven en gebruiken
Je kunt nu de eigenschappen `FileType`, `PageCount` en `Size` benaderen. In productie kun je deze waarden opslaan in een database, beschikbaar stellen via een API, of gebruiken om te bepalen of een upload geaccepteerd wordt.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Veelvoorkomende gebruikssituaties en implementatiepatronen

### Bestandsuploadvalidatie
Wanneer een gebruiker een document uploadt, kun je direct het type en het aantal pagina's verifiëren voordat je het opslaat. Dit voorkomt ongewenste formaten en te grote bestanden in je systeem.

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

### Batch‑documentanalyse
Verwerk je een map met documenten? Extraheer eerst de metadata om bestanden naar verschillende pipelines te routeren — bijvoorbeeld, grote PDF's gaan naar een asynchrone worker, terwijl één‑pagina‑bestanden inline worden afgehandeld.

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

## Veelvoorkomende problemen en oplossingen

### Bestands‑toegang en vergrendelingsproblemen
**Probleem**: “The file is being used by another process.”  
**Oplossing**: Wrap the stream in a `using` statement and, if necessary, implement a retry policy with exponential back‑off.

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

### Niet‑ondersteunde bestandsformaatafhandeling
**Probleem**: The API throws an exception for an unknown format.  
**Oplossing**: Inspect the `FileType` property; if it returns `Unknown`, return a friendly error to the caller and log the incident.

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

### Geheugenbeheer bij grote bestanden
**Probleem**: Memory spikes when processing very large documents.  
**Oplossing**: The stream‑based approach already minimizes memory use, but you should also call `Dispose()` on the `Comparer` as soon as you’re done and avoid holding references to the `IDocumentInfo` longer than needed.

## Prestatieoverwegingen en best practices

### Best practices voor stream‑beheer
1. **Altijd `using`‑statements gebruiken** – Garandeert vrijgave en maakt bronnen snel vrij.  
2. **Reset stream‑positie bij hergebruik** – Als je dezelfde stream twee keer moet lezen, roep `stream.Seek(0, SeekOrigin.Begin)` aan.  
3. **Kies het juiste stream‑type** – `FileStream` voor schijfbestanden, `MemoryStream` voor in‑memory data, `NetworkStream` voor externe bronnen.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Wanneer deze benadering verkiezen boven volledige documentlading
**Voorkeur voor stream‑gebaseerde metadata‑extractie wanneer**:
- Je alleen hoog‑niveau details nodig hebt (type, pagina's, grootte).  
- Je uploads valideert of een documentcatalogus bouwt.  
- Prestaties en een lage geheugengebruik zijn cruciaal.

**Overschakelen naar volledige documentverwerking wanneer**:
- Je inhoud moet vergelijken, tekst moet extraheren of pagina's moet renderen.  
- Diepe analyse (bijv. OCR, watermerkdetectie) vereist is.  

## Geavanceerde tips voor productiegebruik

### Robuuste foutafhandelingsstrategieën
Omring alle bewerkingen met een try‑catch‑blok dat `GroupDocs.Comparison.Exceptions.ComparisonException` opvangt. `ComparisonException` wordt door de bibliotheek gegooid wanneer er een fout optreedt tijdens documentverwerking. Log de foutdetails, retourneer een gestandaardiseerde foutrespons, en zorg ervoor dat de `Comparer` wordt vrijgegeven in een `finally`‑clausule.

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

### Integratie met logging en monitoring
Injecteer een logging‑framework (bijv. Serilog of NLog) en genereer metrics zoals verwerkingstijd, bestandsgrootte en aantallen geslaagd/mislukt. Deze gegevens helpen je prestatie‑regressies vroegtijdig te detecteren.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Veelgestelde vragen

**Q: Is GroupDocs.Comparison for .NET compatible with different document formats?**  
A: Ja. De bibliotheek ondersteunt **meer dan 50 bestandsformaten**, waaronder DOCX, PDF, XLSX, PPTX en vele afbeeldingsformaten, waardoor hij geschikt is voor vrijwel elke documentworkflow.

**Q: Can I try GroupDocs.Comparison for .NET before purchasing?**  
A: Absoluut. Een gratis proefversie is beschikbaar op [the website](https://releases.groupdocs.com/), waarmee je alle functies kunt evalueren zonder licentie.

**Q: Where can I find support for GroupDocs.Comparison for .NET?**  
A: Je kunt hulp krijgen in het [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12), waar de community en het productteam snel op vragen reageren.

**Q: Are temporary licenses available for testing?**  
A: Ja. Tijdelijke licenties zijn verkrijgbaar via [the licensing page](https://purchase.groupdocs.com/temporary-license/), ideaal voor ontwikkelings- en QA‑omgevingen.

**Q: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?**  
A: Zeker. Het biedt enterprise‑niveau prestaties, uitgebreide formaatondersteuning en robuuste foutafhandeling, die allemaal essentieel zijn voor grootschalige productiesystemen.

---

**Laatst bijgewerkt:** 2026-07-01  
**Getest met:** GroupDocs.Comparison 23.10 for .NET  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Documenteigenschappen ophalen C# .NET - Bestandsmetadata extraheren](/comparison/net/basic-usage/get-document-info-from-path/)
- [Documentmetadata‑beheer .NET - Complete gids voor GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Documentvergelijking .NET‑tutorial - Metadata behouden met GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)