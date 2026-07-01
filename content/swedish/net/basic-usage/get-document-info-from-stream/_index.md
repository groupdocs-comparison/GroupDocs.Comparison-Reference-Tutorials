---
categories:
- Document Processing
date: '2026-07-01'
description: Lär dig hur du läser filmetadata C# med GroupDocs.Comparison, extraherar
  filstorleksström och hämtar dokumentegenskapsström effektivt.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Extrahera dokumentinformation .NET
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
title: Läs filmetadata C# – Extrahera dokumentinformation från strömmar
type: docs
url: /sv/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Läs filmetadata C# – Extrahera dokumentinformation från strömmar

## Introduktion

Att läsa filmetadata i C# utan att ladda hela dokumentet är ett vanligt krav för moderna .NET‑applikationer. **Read file metadata C#** låter dig validera uppladdningar, visa dokumentdetaljer och fatta bearbetningsbeslut samtidigt som minnesanvändningen hålls låg. GroupDocs.Comparison för .NET tillhandahåller ett snabbt, strömbaserat API som extraherar filtyp, sidantal, storlek och andra egenskaper direkt från en `Stream`. I de följande avsnitten kommer du att se varför detta är viktigt, hur du sätter upp det och steg‑för‑steg‑kod som du kan lägga in i vilket .NET‑projekt som helst.

## Snabba svar
- **Vad betyder “read file metadata C#”?** Det betyder att hämta ett dokuments egenskaper (typ, sidor, storlek) via en .NET‑stream utan att ladda hela innehållet.  
- **Vilket bibliotek hanterar detta?** GroupDocs.Comparison för .NET erbjuder metoden `GetDocumentInfo()` för snabb metadataextraktion.  
- **Behöver jag en licens?** En gratis provversion fungerar för utveckling; en kommersiell licens krävs för produktion.  
- **Kan jag använda detta med stora PDF‑filer?** Ja – strömtillvägagångssättet bearbetar filer med flera hundra sidor utan hög minnesförbrukning.  
- **Är det kompatibelt med .NET 6+?** Absolut, biblioteket riktar sig mot .NET Standard 2.0 och fungerar på .NET 6, .NET 7 och .NET Core.

## Vad är read file metadata C#?
`Read file metadata C#` avser att hämta ett dokuments beskrivande information—såsom format, sidantal och byte‑storlek—med C#‑kod som arbetar med strömmar. Denna teknik undviker att ladda hela filen i minnet, vilket är särskilt värdefullt för stora PDF‑filer, DOCX‑filer eller batch‑operationer.

## Varför använda GroupDocs metadataextraktion från strömmar?
GroupDocs.Comparison stöder **50+ in- och utdataformat** och kan extrahera metadata från filer upp till **2 GB** i storlek samtidigt som minnesanvändningen hålls under **10 MB**. Biblioteket läser endast de nödvändiga header‑sektionerna och levererar resultat på **under 150 ms** för typiska 100‑sidiga PDF‑filer på en standardserver. Dessa kvantifierade fördelar omvandlas till snabbare uppladdningsvalidering, lägre molnkostnader och en smidigare användarupplevelse.

## Förutsättningar och installation

### 1. Installera GroupDocs.Comparison för .NET
Ladda ner det senaste paketet från den [officiella nedladdningssidan](https://releases.groupdocs.com/comparison/net/). Om du föredrar NuGet, kör:

```
Install-Package GroupDocs.Comparison
```

### 2. Grundläggande .NET‑utvecklingskunskap  
Du bör vara bekväm med C# och .NET:s I/O‑modell. Att arbeta med `Stream`, `FileStream` och `MemoryStream` är nödvändigt för exemplen nedan.

### 3. Utvecklingsmiljö  
Visual Studio, VS Code eller JetBrains Rider stöds alla. Se till att ditt projekt riktar sig mot .NET 6 eller senare för bästa prestanda.

## Hur man läser filmetadata C# från en ström?

Läs in dokumentet med en `FileStream`, skapa en `Comparer` och anropa `GetDocumentInfo()`. Hela operationen kräver bara två kodrader och returnerar ett `IDocumentInfo`‑objekt som innehåller filtyp, sidantal och storlek. Internt läser biblioteket endast de nödvändiga header‑byten, så även stora PDF‑filer bearbetas snabbt utan att förbruka mycket minne.  
`Comparer` är huvudklassen i GroupDocs.Comparison som samordnar dokumentanalys.  
`GetDocumentInfo()` returnerar ett `IDocumentInfo`‑objekt med grundläggande metadata.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Steg 1: Initiera Comparer‑objektet med ström

Följande kodsnutt skapar en `Comparer`‑instans från en skrivskyddad `FileStream`. Att använda ett `using`‑block garanterar att strömmen stängs och comparer‑objektet disponeras, vilket förhindrar fil‑lås.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Steg 2: Extrahera dokumentinformation

Att anropa `GetDocumentInfo()` returnerar ett `IDocumentInfo`‑objekt som innehåller all metadata du behöver. Metoden läser endast de nödvändiga delarna av filens header, så även en 500‑sidig PDF bearbetas på en bråkdel av en sekund.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Steg 3: Visa och använda dokumentinformation

Du kan nu komma åt egenskaperna `FileType`, `PageCount` och `Size`. I produktion kan du lagra dessa värden i en databas, exponera dem via ett API eller använda dem för att avgöra om en uppladdning ska accepteras.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Vanliga användningsfall och implementationsmönster

### Validering av filuppladdning

När en användare laddar upp ett dokument kan du omedelbart verifiera dess typ och sidantal innan du sparar det. Detta förhindrar oönskade format och för stora filer från att komma in i ditt system.

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

### Batch‑dokumentanalys

Bearbetar du en mapp med dokument? Extrahera metadata först för att dirigera filer till olika pipelines—t.ex. stora PDF‑filer går till en asynkron arbetsprocess, medan enkelsidiga filer hanteras inline.

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

## Vanliga problem och lösningar

### Problem med filåtkomst och låsning

**Problem**: “Filen används av en annan process.”  
**Lösning**: Omge strömmen med ett `using`‑uttalande och, om nödvändigt, implementera en återförsökspolicy med exponentiell back‑off.

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

### Hantering av ej stödda filformat

**Problem**: API:t kastar ett undantag för ett okänt format.  
**Lösning**: Inspektera egenskapen `FileType`; om den returnerar `Unknown`, returnera ett vänligt felmeddelande till anroparen och logga händelsen.

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

### Minneshantering med stora filer

**Problem**: Minnesökningar när mycket stora dokument bearbetas.  
**Lösning**: Det strömbaserade tillvägagångssättet minimerar redan minnesanvändning, men du bör också anropa `Dispose()` på `Comparer` så snart du är klar och undvika att hålla referenser till `IDocumentInfo` längre än nödvändigt.

## Prestandaöverväganden och bästa praxis

### Bästa praxis för strömhantering

1. **Använd alltid `using`‑satser** – Garanterar disponering och frigör resurser omedelbart.  
2. **Återställ strömmens position vid återanvändning** – Om du behöver läsa samma ström två gånger, anropa `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Välj rätt strömtyp** – `FileStream` för diskfiler, `MemoryStream` för data i minnet, `NetworkStream` för fjärrkällor.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### När man bör föredra detta tillvägagångssätt jämfört med fullständig dokumentladdning

**Föredra strömbaserad metadataextraktion när**:

- Du bara behöver hög‑nivådetaljer (typ, sidor, storlek).  
- Du validerar uppladdningar eller bygger ett dokumentkatalog.  
- Prestanda och låg minnesanvändning är kritiska.

**Byt till fullständig dokumentbearbetning när**:

- Du behöver jämföra innehåll, extrahera text eller rendera sidor.  
- Djup analys (t.ex. OCR, vattenstämpeldetektion) krävs.  

## Avancerade tips för produktionsanvändning

### Robusta felhanteringsstrategier

Omge alla operationer med ett try‑catch‑block som fångar `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` kastas av biblioteket när ett fel uppstår under dokumentbearbetning. Logga felinformationen, returnera ett standardiserat felrespons och säkerställ att `Comparer` disponeras i en `finally`‑sats.

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

### Integration med loggning och övervakning

Injicera ett loggningsramverk (t.ex. Serilog eller NLog) och sänd ut mätvärden som bearbetningstid, filstorlek och antal lyckade/misslyckade. Denna data hjälper dig att tidigt upptäcka prestandaregressioner.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Vanliga frågor

**Q: Är GroupDocs.Comparison för .NET kompatibel med olika dokumentformat?**  
A: Ja. Biblioteket stöder **över 50 filformat**, inklusive DOCX, PDF, XLSX, PPTX och många bildtyper, vilket gör det lämpligt för i princip alla dokumentarbetsflöden.

**Q: Kan jag prova GroupDocs.Comparison för .NET innan jag köper?**  
A: Absolut. En gratis provversion finns på [webbplatsen](https://releases.groupdocs.com/), så att du kan utvärdera alla funktioner utan licens.

**Q: Var kan jag hitta support för GroupDocs.Comparison för .NET?**  
A: Du kan få hjälp i [GroupDocs.Comparison‑forumet](https://forum.groupdocs.com/c/comparison/12), där communityn och produktteamet svarar på frågor snabbt.

**Q: Finns tillfälliga licenser tillgängliga för testning?**  
A: Ja. Tillfälliga licenser kan erhållas från [licenssidan](https://purchase.groupdocs.com/temporary-license/), idealiska för utvecklings- och QA‑miljöer.

**Q: Är GroupDocs.Comparison för .NET lämplig för företagsdistributioner?**  
A: Definitivt. Den erbjuder företagsklassad prestanda, omfattande formatstöd och robust felhantering, vilket alla är väsentliga för storskaliga produktionssystem.

---

**Senast uppdaterad:** 2026-07-01  
**Testad med:** GroupDocs.Comparison 23.10 för .NET  
**Författare:** GroupDocs

## Relaterade handledningar

- [Hämta dokumentegenskaper C# .NET - Extrahera filmetadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Dokumentmetadatahantering .NET - Komplett guide för GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Dokumentjämförelse .NET‑handledning - Bevara metadata med GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)