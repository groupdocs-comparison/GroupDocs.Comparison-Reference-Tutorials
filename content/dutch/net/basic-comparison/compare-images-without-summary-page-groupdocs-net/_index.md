---
categories:
- Image Processing
date: '2026-05-31'
description: Leer hoe u afbeeldingen vergelijkt in .NET met behulp van GroupDocs.Comparison
  terwijl u de samenvattingspagina uitschakelt. Deze tutorial behandelt installatie,
  code, prestatie‑tips en praktijkvoorbeelden.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Afbeeldingen vergelijken .NET zonder samenvatting
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
title: Hoe afbeeldingen vergelijken in .NET – Samenvattingspagina overslaan
type: docs
url: /nl/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Hoe afbeeldingen vergelijken in .NET – Samenvattingspagina overslaan

Wanneer je **hoe afbeeldingen te vergelijken** programmatisch in een .NET‑applicatie moet doen, is het laatste wat je wilt een extra samenvattingspagina die tijd en opslag verspilt. Of je nu een kwaliteits‑controlelijn, een content‑management‑pipeline of een geautomatiseerde visual‑regressietest‑suite bouwt, het overslaan van de samenvattingspagina kan enkele seconden per uitvoering besparen en je schijfvoetafdruk slank houden.

In deze tutorial leer je hoe je **GroupDocs.Comparison for .NET** gebruikt om twee afbeeldingen efficiënt te vergelijken, de bibliotheek configureert om het genereren van een samenvatting te onderdrukken, en best‑practice prestatie‑trucs toepast. We zullen ook onderzoeken waarom dit belangrijk is, wanneer je het moet gebruiken, en hoe je veelvoorkomende valkuilen kunt vermijden.

## Snelle antwoorden
- **Wat is de snelste manier om afbeeldingen te vergelijken zonder een samenvattingspagina?** Gebruik `Comparer` met `CompareOptions` en stel `GenerateSummaryPage = false` in.  
- **Welke bibliotheek ondersteunt dit direct?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Heb ik een licentie nodig?** Ja, een commerciële licentie is vereist voor productie; een gratis proefversie werkt voor ontwikkeling.  
- **Kan ik meer dan twee afbeeldingen tegelijk vergelijken?** Absoluut – roep `Add()` meerdere keren aan vóór `Compare()`.  
- **Is deze aanpak geschikt voor grootschalige batch‑taken?** Ja, wanneer gecombineerd met batchverwerking en juiste geheugenbeheer.

## Wat is GroupDocs.Comparison?
`GroupDocs.Comparison` is een .NET‑bibliotheek die visuele verschillen tussen documenten en afbeeldingen detecteert en resultaten naast‑elkaar of als overlay produceert. Het ondersteunt **meer dan 50 invoer‑ en uitvoerformaten**, waaronder JPEG, PNG, BMP, TIFF en GIF, en kan bestanden met honderden pagina's verwerken zonder het volledige bestand in het geheugen te laden.

## Waarom de samenvattingspagina overslaan?
Het uitschakelen van de samenvattingspagina vermindert I/O tot **70 %** voor alleen‑afbeeldingsvergelijkingen en verkort de verwerkingstijd gemiddeld met ongeveer **30 %**, volgens de benchmark‑suite van de bibliotheek. Wanneer je alleen de diff‑afbeelding nodig hebt (voor geautomatiseerde tests of QC‑pass/fail‑beslissingen), voegt het extra HTML‑rapport geen waarde toe en verbruikt het alleen schijfruimte.

## Vereisten en omgeving configuratie

### Wat je nodig hebt
- **GroupDocs.Comparison for .NET** versie **25.4.0** of nieuwer
- Visual Studio 2019 + of een andere .NET‑compatibele IDE
- .NET Framework 4.6.1 + **of** .NET Core 2.0 +
- Basiskennis van C# en vertrouwdheid met bestands‑I/O

### Aanbevolen extra's
- Een klein testproject met een paar voorbeeldafbeeldingen (bijv. `source.png` en `target.png`).
- Optioneel: Dependency‑injection‑configuratie als je een service‑georiënteerde architectuur verkiest.

### Waarom deze vereisten belangrijk zijn
De opgegeven bibliotheekversie bevat de `GenerateSummaryPage`‑vlag en prestatie‑verbeteringen die oudere releases missen. Het gebruik van een moderne IDE zorgt ervoor dat je NuGet‑pakketbeheer kunt benutten en compile‑tijd waarschuwingen vroeg kunt zien.

## Hoe GroupDocs.Comparison te installeren
GroupDocs.Comparison kan aan elk .NET‑project worden toegevoegd via NuGet, dat het downloaden van de binaries en het bijwerken van het projectbestand afhandelt. Kies de methode die bij je workflow past: de Package Manager Console voor Visual Studio‑gebruikers of de .NET CLI voor command‑line omgevingen. Beide commando's lossen automatisch afhankelijkheden op en zorgen ervoor dat de juiste versie wordt gerefereerd.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Vervang `25.4.0` door de exacte versie die je wilt vastzetten.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Beide commando's voegen de bibliotheek toe aan je projectbestand en herstellen de benodigde binaries.

**Pro Tip:** Zet de versie vast in je `.csproj` om accidentele upgrades te voorkomen die het API‑gedrag kunnen wijzigen.

## Licentieoverwegingen
GroupDocs.Comparison vereist een licentie voor elke productie‑implementatie. Je kunt beginnen met een **gratis proefversie** die volledige functionaliteit biedt, vervolgens upgraden naar een **tijdelijke licentie** voor uitgebreid testen, en uiteindelijk naar een **volledige commerciële licentie** voor productie. Vergeet niet het `GroupDocs.Comparison.lic`‑bestand in de applicatiewortel te plaatsen of het pad programmatisch op te geven.

## Basisprojectconfiguratie
Maak een nieuwe console‑app (of integreer in een bestaande service) en voeg de volgende boilerplate‑code toe. Deze snippet toont de minimale configuratie die nodig is voordat je in de vergelijkingslogica duikt.

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

> **Belangrijk:** Gebruik altijd `Path.Combine()` voor bestands‑paden. Het handelt automatisch OS‑specifieke pad‑scheidingstekens af en voorkomt subtiele bugs bij het verplaatsen tussen Windows‑ en Linux‑containers.

## Stapsgewijze implementatie‑gids

### Hoe vergelijk ik afbeeldingen zonder een samenvattingspagina?
`Comparer` is de primaire klasse in GroupDocs.Comparison die document‑ en afbeeldingsvergelijkingsoperaties coördineert. `CompareOptions` bevat configuratie‑instellingen die bepalen hoe de vergelijking wordt uitgevoerd, zoals of een samenvattingspagina moet worden gegenereerd. Laad de bronafbeelding, configureer `CompareOptions` om de samenvatting uit te schakelen, voeg de doelafbeelding toe, en roep `Compare()` aan. De methode retourneert een `ComparisonResult` met de diff‑afbeeldings‑stream, die je naar schijf kunt schrijven, over een netwerk kunt verzenden, of in een UI‑component kunt embedden. Deze aanpak zorgt ervoor dat alleen de essentiële diff wordt geproduceerd, waardoor extra HTML‑ of PDF‑rapporten worden geëlimineerd.

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

De bovenstaande code voert de volledige vergelijking uit in **vier logische stappen** en schrijft alleen de diff‑afbeelding weg, waarbij elke HTML‑ of PDF‑samenvatting wordt weggelaten.

### Stap 1: Initialiseert het Comparer‑object
De `Comparer`‑klasse is de toegangspoort tot alle vergelijkingsoperaties. Het implementeert `IDisposable`, dus het omhullen met een `using`‑blok garandeert dat bestands‑handles en unmanaged geheugen snel worden vrijgegeven, zelfs als er een uitzondering wordt gegooid.

### Stap 2: Configureer CompareOptions voor geen samenvatting
Stel `GenerateSummaryPage = false` in op de `CompareOptions`‑instantie. Deze vlag instrueert de engine om het maken van het standaard HTML‑rapport over te slaan, wat de belangrijkste bron van extra I/O is in alleen‑afbeeldingsscenario's.

### Stap 3: Voeg doelafbeelding(en) toe voor vergelijking
Je kunt `Add()` meerdere keren aanroepen om één bron te vergelijken met meerdere doelen in één batch. Elke aanroep kan zijn eigen `CompareOptions` ontvangen als je per‑afbeelding aanpassingen nodig hebt.

### Stap 4: Voer de vergelijking uit en sla resultaten op
`Comparer.Compare()` voert het zware werk uit en retourneert een `ComparisonResult`. Het resultaat bevat een `Stream` met de diff‑afbeelding, die je direct naar schijf kunt opslaan, over een netwerk kunt verzenden, of in een UI‑component kunt embedden.

## Volledige productie‑klare methode
Hieronder staat een kant‑klaar methode die je in elke .NET‑service kunt plaatsen. Het bevat padvalidatie, foutafhandeling en optionele logging‑hooks.

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

## Veelvoorkomende implementatie‑valkuilen (en hoe ze te vermijden)

- **Padproblemen:** Verifieer altijd dat zowel bron‑ als doelbestanden bestaan met `File.Exists()`. Een ontbrekend bestand zal een `FileNotFoundException` veroorzaken die vroeg kan worden opgevangen.  
- **Geheugendruk:** Grote afbeeldingen (10 MB +) kunnen veel RAM verbruiken. Verwerk ze in batches en overweeg down‑scaling als pixel‑perfecte nauwkeurigheid niet vereist is.  
- **Bestandsvergrendelingen:** Zorg ervoor dat geen ander proces een exclusieve lock op de afbeeldingsbestanden heeft. Dit is vooral belangrijk in multi‑threaded of gecontaineriseerde omgevingen.

## Praktische toepassingen en use‑cases

### Kwaliteitscontrole in de productie
Een productielijn legt afbeeldingen van elk item vast en vergelijkt ze met een gouden referentie. Het overslaan van de samenvattingspagina stelt het systeem in staat om binnen milliseconden “pass” of “fail” te bepalen, waardoor de lijn met hoge snelheid blijft bewegen.

### Content‑managementsystemen
Wanneer gebruikers assets uploaden, kan het CMS direct duplicaten of bijna‑duplicaten detecteren, waardoor opslagoverschot wordt voorkomen en de zoekrelevantie verbetert. De diff‑afbeelding kan worden opgeslagen als thumbnail voor snelle visuele inspectie.

### Geautomatiseerd UI‑testen (visuele regressie
Selenium of Playwright kan screenshots van een webpagina vastleggen, die vervolgens aan deze vergelijkingsroutine worden gevoed. De diff‑afbeelding benadrukt UI‑wijzigingen, en omdat er geen samenvatting wordt gegenereerd, blijft de CI‑pipeline snel en lichtgewicht.

### Medische beeldvorming (met audit)
Radiologie‑workflows moeten soms wijzigingen tussen opeenvolgende scans markeren. Hoewel je nog steeds een gedetailleerd audit‑log kunt genereren, kan de diff‑afbeelding zelf zonder een samenvattingspagina worden geproduceerd, waardoor de verwerkingstijd voor grote DICOM‑omgezette PNG’s wordt verminderd.

## Prestatie‑overwegingen en optimalisatie

### Best practices voor geheugenbeheer
Verwerk afbeeldingen in **batches van 20–50** afhankelijk van het server‑RAM. Maak elke `Comparer`‑instantie snel vrij en roep `GC.Collect()` alleen aan als je geheugenpieken opmerkt tijdens langdurige taken.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Schijf‑I/O‑optimalisatie
Plaats je input‑, output‑ en tijdelijke mappen op hetzelfde snelle SSD‑volume. Verwijder tijdelijke bestanden direct nadat de diff‑afbeelding is opgeslagen om onnodig schijfgebruik te voorkomen.

### Threading‑ en async‑overwegingen
GroupDocs.Comparison is thread‑safe voor alleen‑lezen operaties, maar vermijd het delen van één `Comparer`‑instantie over threads. Maak in plaats daarvan onafhankelijke taken aan:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Veelvoorkomende problemen oplossen

### Bestands‑pad‑ en permissiefouten
- **Symptoom:** `FileNotFoundException` of `UnauthorizedAccessException`.  
- **Oplossing:** Gebruik `Path.GetFullPath()` om het opgeloste pad te debuggen, zorg ervoor dat de identiteit van de applicatie‑pool (of Docker‑container‑gebruiker) lees‑/schrijfrechten heeft, en controleer dubbel dat het pad niet wordt afgekapt door omgevingsvariabelen.

### Geheugen‑ en prestatie‑knelpunten
- **Symptoom:** Trage uitvoeringen of `OutOfMemoryException`.  
- **Oplossing:** Verklein afbeeldingen tot een gemeenschappelijke resolutie (bijv. 1024 × 768) wanneer exacte pixel‑vergelijking niet vereist is. Monitor geheugen met tools zoals dotMemory of de ingebouwde Performance Profiler.

### Licentieproblemen
- **Symptoom:** Watermerk op diff‑afbeelding of `LicenseException`.  
- **Oplossing:** Bevestig dat `GroupDocs.Comparison.lic` zich bevindt in de uitvoerbare directory of laad het expliciet via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Geavanceerde configuratie‑opties

### Aanpassen van vergelijkingsgevoeligheid
Je kunt fijn afstemmen hoe de engine kleine pixelvariaties (bijv. compressie‑artefacten) behandelt door de `Sensitivity`‑eigenschap op `CompareOptions` aan te passen. Lagere waarden maken de vergelijking strenger.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Optimalisatie van uitvoerformaat
Als je de diff‑afbeelding in een specifiek formaat nodig hebt (PNG versus JPEG), stel dan de `OutputFormat`‑eigenschap in:

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

## Integratie met populaire .NET‑frameworks

### ASP.NET Core service‑voorbeeld
Exposeer een lichtgewicht HTTP‑endpoint dat twee afbeeldings‑streams accepteert, de vergelijking uitvoert, en de diff‑afbeelding retourneert als een `FileResult`.

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

### Dependency‑injection‑registratie
Voeg de comparer toe als een scoped service in `Program.cs` of `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Veelgestelde vragen

**Q: Wat is het belangrijkste voordeel van het overslaan van de samenvattingspagina?**  
A: Het verkort de verwerkingstijd tot wel 30 % en vermindert schijfgebruik met ongeveer 70 % voor alleen‑afbeeldingsvergelijkingen, wat cruciaal is voor high‑throughput pipelines.

**Q: Kan ik nog steeds gedetailleerde wijzigings‑metadata ophalen zonder een samenvattingspagina?**  
A: Ja. Het `ComparisonResult`‑object biedt een `Changes`‑collectie die programmatische informatie over elke gedetecteerde verschil bevat.

**Q: Welke afbeeldingsformaten worden ondersteund?**  
A: JPEG, PNG, BMP, TIFF, GIF, en verschillende andere — meer dan 50 formaten in totaal.

**Q: Hoe moet ik omgaan met zeer grote afbeeldingen (bijv. >20 MB)?**  
A: Verwerk ze in kleinere batches, schaal ze eventueel down‑scale, en monitor het geheugenverbruik. Het gebruik van `Comparer` in een `using`‑blok zorgt ervoor dat bronnen snel worden vrijgegeven.

**Q: Is deze aanpak veilig voor multi‑threaded applicaties?**  
A: Ja, zolang elke thread zijn eigen `Comparer`‑instantie maakt. Het delen van één instantie kan leiden tot race‑conditions.

## Aanvullende bronnen

- [GroupDocs.Comparison Documentatie](https://docs.groupdocs.com/comparison/net/)
- [API‑referentie](https://reference.groupdocs.com/comparison/net/)
- [Download](https://releases.groupdocs.com/comparison/net/)
- [Aankoop](https://purchase.groupdocs.com/buy)
- [Gratis proefversie](https://releases.groupdocs.com/comparison/net/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)
- [Supportforum](https://forum.groupdocs.com/c/comparison/)

---

**Laatst bijgewerkt:** 2026-05-31  
**Getest met:** GroupDocs.Comparison 25.4.0 for .NET  
**Auteur:** GroupDocs

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

## Gerelateerde tutorials

- [Afbeeldingsvergelijking .NET - Afbeeldingen programmatisch vergelijken](/comparison/net/image-comparison/compare-images-from-path/)
- [Afbeeldingsvergelijking .NET - Afbeeldingen vergelijken vanuit stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [GroupDocs Comparison .NET tutorial - Complete basisgebruiksgids](/comparison/net/basic-usage/)