---
categories:
- Document Comparison
date: '2026-06-15'
description: Leer hoe u metadata uit .NET comparison-resultaten kunt extraheren met
  behulp van GroupDocs.Comparison. Stapsgewijze gids met codevoorbeelden en praktische
  tips.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Documentinformatie extraheren uit Comparison-resultaten
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
title: Hoe metadata uit .NET Comparison-resultaten te extraheren – Complete gids
type: docs
url: /nl/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Hoe metadata uit .NET Comparison‑resultaten te extraheren – Complete gids

Wanneer je werkt met documentvergelijkingen in .NET‑toepassingen, vraag je je misschien af **hoe je metadata kunt extraheren** uit de vergelijkingsresultaten. Metadata zoals bestandstype, paginatelling en documentgrootte kan cruciaal zijn voor audit‑trails, prestatie‑optimalisatie, of simpelweg het tonen van nuttige informatie aan eindgebruikers. Deze tutorial leidt je stap voor stap door het efficiënt ophalen van die gegevens met GroupDocs.Comparison voor .NET.

## Snelle antwoorden
- **Wat is de hoofdklasse voor vergelijking?** `Comparer` laadt het brondocument en voert de vergelijkingsengine uit.  
- **Welke methode retourneert metadata?** `GetDocumentInfo()` op een doel‑document retourneert een `IDocumentInfo`‑object.  
- **Kan ik de documentgrootte krijgen in .NET?** Ja – de `Size`‑eigenschap van `IDocumentInfo` retourneert de grootte in bytes.  
- **Heb ik een licentie nodig voor het extraheren van metadata?** Een geldige GroupDocs.Comparison‑licentie is vereist voor productiegebruik; de gratis proefversie ondersteunt alle metadata‑functies.  
- **Is de API compatibel met .NET 6?** Absoluut – GroupDocs.Comparison ondersteunt .NET Framework 4.6.1+, .NET Core 2.0+, en .NET 5/6+.

De `GetDocumentInfo()`‑methode retourneert een `IDocumentInfo`‑object dat documentmetadata bevat.

## Wat is metadata‑extractie bij documentvergelijking?
Metadata‑extractie is het proces van het ophalen van beschrijvende informatie—zoals bestandstype, paginatelling en bestandsgrootte—van de documenten die bij een vergelijkingsoperatie betrokken zijn. GroupDocs.Comparison maakt deze gegevens beschikbaar via een uniforme API, waardoor het eenvoudig is om te loggen, weer te geven of te gebruiken voor conditionele verwerking.

## Waarom metadata uit vergelijkingsresultaten extraheren?
Het extraheren van metadata stelt je in staat gedetailleerde audit‑logs te maken, bestanden te routeren op basis van type, en verwerkingsstrategieën aan te passen voor grote documenten. Door het bestandstype, de paginatelling en de grootte te kennen, kun je nalevingsregels afdwingen, de verwerkingstijd inschatten en duidelijke informatie aan gebruikers presenteren voordat ze een vergelijking starten.

## Voorvereisten

1. **GroupDocs.Comparison for .NET** – Installeer de bibliotheek vanaf de [officiële releases‑pagina](https://releases.groupdocs.com/comparison/net/).  
   U kunt ook alle releases bekijken op de [GroupDocs releases‑pagina](https://releases.groupdocs.com/).  
2. **Ontwikkelomgeving** – Visual Studio, VS Code, of elke IDE die .NET 6+ ondersteunt.  
3. **Voorbeelddocumenten** – Twee bestanden (bijv. `SOURCE.docx` en `TARGET.docx`) voor testen. De API werkt met meer dan **50 documentformaten**.

## Namespaces importeren

De volgende `using`‑directieven geven je toegang tot de kernvergelijkingsengine, bestandsafhandelingshulpmiddelen en de metadata‑interfaces.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Deze imports zijn vereist voordat je enige GroupDocs‑objecten instantieert.

## Hoe metadata uit vergelijkingsresultaten extraheren?

De `Comparer`‑klasse laadt het brondocument en orkestreert het vergelijkingsproces.

Om metadata op te halen, laad je eerst het brondocument met een `Comparer`‑instantie, voeg je vervolgens het doel‑document(en) toe. Nadat de vergelijkingsengine is geïnitialiseerd, roep je `GetDocumentInfo()` aan op elk doel om een `IDocumentInfo`‑object te verkrijgen dat eigenschappen bevat zoals bestandstype, paginatelling en grootte. Deze aanpak werkt uniform voor alle ondersteunde formaten.

### Stap 1: Initialiseert Comparer met brondocument

`Comparer` is de kernklasse in GroupDocs.Comparison die het brondocument laadt en vergelijkingsbewerkingen orkestreert. Het gebruik van een `using`‑blok garandeert dat alle niet‑beheerde bronnen automatisch worden vrijgegeven.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Pro Tip:** Je kunt elke `Stream` (bestand, geheugen, cloud) doorgeven aan de `Comparer`‑constructor, niet alleen een bestandspad.

### Stap 2: Doel‑document toevoegen voor vergelijking

De `Add()`‑methode accepteert extra streams of bestandspaden, waardoor één‑naar‑veel‑vergelijkingen mogelijk zijn.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Belangrijk:** De volgorde van toegevoegde documenten beïnvloedt de manier waarop wijzigingen worden gemarkeerd in het eindrapport.

### Stap 3: Document‑info ophalen uit resultaatdocument

`IDocumentInfo` biedt een uniforme weergave van documentmetadata zoals bestandstype, paginatelling en grootte voor alle ondersteunde formaten.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Begrijpen van de gegevens:** Het geretourneerde object werkt hetzelfde voor DOCX, PDF, XLSX en PPTX, zodat je format‑agnostische code kunt schrijven.

### Stap 4: Document‑info weergeven

Zodra je de `IDocumentInfo`‑instantie hebt, kun je de eigenschappen loggen, opslaan of presenteren.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

De drie meest gebruikte eigenschappen zijn:

- **FileType** – bijv. `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – totaal aantal pagina’s of dia’s.  
- **Size** – bestandsgrootte in bytes (handig voor opslagberekeningen).

## Hoe documentgrootte op te halen in .NET?

De `Size`‑eigenschap retourneert de bestandsgrootte in bytes.

De documentgrootte kan rechtstreeks worden opgevraagd via de `IDocumentInfo`‑instantie via de `Size`‑eigenschap. Deze eigenschap geeft het exacte aantal bytes van het originele bestand terug, waardoor je het kunt omrekenen naar kilobytes of megabytes voor weergave of opslagberekeningen. Het weerspiegelt de grootte van het bronbestand, niet van een verwerkte versie.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Opmerking:** De `Size`‑waarde weerspiegelt de originele bestandsgrootte, niet de grootte na interne verwerking of compressie.

## Veelvoorkomende gebruikssituaties en praktische toepassingen

- **Batch Processing:** Gebruik bestandstype om DOCX‑bestanden naar een Word‑specifieke workflow te routeren en PDF’s naar een PDF‑geoptimaliseerde pijplijn.  
- **Storage Management:** Archiveer documenten groter dan 10 MB automatisch naar een cold‑storage bucket.  
- **User Feedback:** Toon paginatelling en grootte vóór vergelijking om realistische verwachtingen voor verwerkingstijd te scheppen.  
- **Quality Assurance:** Verifieer dat geüploade bestanden compleet zijn door verwachte versus werkelijke paginatellingen te vergelijken.

## Veelvoorkomende problemen oplossen

- **File Access Errors:** Controleer leesrechten en gebruik absolute paden tijdens ontwikkeling.  
- **Memory Pressure with Large Files:** Geef de voorkeur aan streaming (`File.OpenRead`) boven het volledig in het geheugen laden van het bestand.  
- **Null Reference Exceptions:** `FirstOrDefault()` kan `null` retourneren als er geen doel is toegevoegd; controleer altijd voordat je `GetDocumentInfo()` aanroept.  

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

- **Limited Metadata for Plain Text:** Formaten zoals `.txt` bieden mogelijk geen betekenisvolle `PageCount`. Bescherm tegen ontbrekende waarden.

## Prestatie‑overwegingen

- **Stream Management:** Wrap streams altijd in `using`‑statements om bestands‑handles snel vrij te geven.  
- **Caching:** Sla vaak opgevraagde metadata op in een cache om herhaalde extractie te vermijden.  
- **Batch Operations:** Verwerk documenten in groepen om overhead te verminderen en de doorvoersnelheid te verhogen.

## Best practices voor productiegebruik

- **Robust Error Handling:** Plaats metadata‑extractie in try‑catch‑blokken om corrupte of niet‑ondersteunde bestanden gracieus af te handelen.  
- **Comprehensive Logging:** Log documenttype, grootte en paginatelling voor elke vergelijking om troubleshooting en audit‑naleving te ondersteunen.  
- **Security Hygiene:** Vermijd het blootstellen van volledige bestandspaden of interne serverdetails in UI‑berichten.  
- **Resource Disposal:** Maak `Comparer`‑instanties snel vrij, vooral in webservices die veel gelijktijdige verzoeken afhandelen.

## Geavanceerde scenario's

### Meerdere doel‑documenten

Als je één bron vergelijkt met meerdere doelen, doorloop je de `Targets`‑collectie en haal je metadata van elk op.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Conditionele verwerking op basis van metadata

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Metadata opslaan in een database

Sla `FileType`, `PageCount` en `Size` op in een relationele tabel om rapportage en analytics mogelijk te maken over duizenden vergelijkingen.

## Veelgestelde vragen

**Q: Is GroupDocs.Comparison for .NET compatibel met verschillende documentformaten?**  
A: Ja, het ondersteunt **50+ formaten** waaronder DOCX, PDF, PPTX, XLSX, TXT en vele anderen, en biedt consistente metadata‑extractie voor al deze formaten.

**Q: Kan ik vergelijkingsinstellingen aanpassen zonder invloed op metadata‑extractie?**  
A: Absoluut. Instellingen zoals gevoeligheid, wijzigingstypen en uitvoerformaat zijn onafhankelijk van de `GetDocumentInfo()`‑aanroep.

**Q: Is er een proefversie die ik kan gebruiken voor evaluatie?**  
A: Ja, download een gratis proefversie vanaf de [GroupDocs releases‑pagina](https://releases.groupdocs.com/). De proefversie bevat volledige mogelijkheden voor metadata‑extractie.

**Q: Waar kan ik ondersteuning krijgen voor implementatievragen?**  
A: Gebruik het [GroupDocs.Comparison‑forum](https://forum.groupdocs.com/c/comparison/12) voor community‑hulp en officiële ondersteuning van het GroupDocs‑team.

**Q: Welke licentieopties zijn beschikbaar voor productie‑implementaties?**  
A: GroupDocs biedt ontwikkelaar‑, site‑ en OEM‑licenties. Aankoopopties staan vermeld op de [GroupDocs purchase‑pagina](https://purchase.groupdocs.com/buy).

---

**Laatst bijgewerkt:** 2026-06-15  
**Getest met:** GroupDocs.Comparison 6.0 for .NET  
**Auteur:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Gerelateerde tutorials

- [Document Metadata Management .NET - Complete Guide for GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Get Document Properties C# .NET - Extract File Metadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Preserve Target Metadata with GroupDocs.Comparison – .NET Tutorial](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)