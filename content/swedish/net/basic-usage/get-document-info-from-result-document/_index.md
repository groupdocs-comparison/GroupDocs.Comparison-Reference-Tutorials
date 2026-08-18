---
categories:
- Document Comparison
date: '2026-06-15'
description: Lär dig hur du extraherar metadata från .NET Comparison-resultat med
  hjälp av GroupDocs.Comparison. Steg‑för‑steg guide med kodexempel och praktiska
  tips.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Extrahera dokumentinformation från Comparison-resultat
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
title: Hur man extraherar metadata från .NET Comparison-resultat – Komplett guide
type: docs
url: /sv/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Så extraherar du metadata från .NET Comparison Results – Komplett guide

När du arbetar med dokumentjämförelser i .NET‑applikationer kan du undra **hur man extraherar metadata** från jämförelsresultaten. Metadata som filtyp, sidantal och dokumentstorlek kan vara avgörande för revisionsspår, prestandaoptimering eller helt enkelt för att visa användbar information för slutanvändare. Denna handledning visar dig hur du hämtar dessa data effektivt med GroupDocs.Comparison för .NET.

## Snabba svar
- **Vad är huvudklassen för jämförelse?** `Comparer` laddar källdokumentet och kör jämförelsesmotorn.  
- **Vilken metod returnerar metadata?** `GetDocumentInfo()` på ett mål‑dokument returnerar ett `IDocumentInfo`‑objekt.  
- **Kan jag få dokumentets storlek i .NET?** Ja – `Size`‑egenskapen i `IDocumentInfo` returnerar storleken i byte.  
- **Behöver jag en licens för att extrahera metadata?** En giltig GroupDocs.Comparison‑licens krävs för produktionsanvändning; gratisprovversionen stödjer alla metadata‑funktioner.  
- **Är API‑et kompatibelt med .NET 6?** Absolut – GroupDocs.Comparison stödjer .NET Framework 4.6.1+, .NET Core 2.0+, och .NET 5/6+.

`GetDocumentInfo()`‑metoden returnerar ett `IDocumentInfo`‑objekt som innehåller dokumentmetadata.

## Vad är metadataextraktion i dokumentjämförelse?
Metadataextraktion är processen att hämta beskrivande information—såsom filtyp, sidantal och filstorlek—från de dokument som är involverade i en jämförelsoperation. GroupDocs.Comparison exponerar dessa data via ett enhetligt API, vilket gör det enkelt att logga, visa eller använda för villkorad bearbetning.

## Varför extrahera metadata från jämförelsresultat?
Att extrahera metadata låter dig skapa detaljerade revisionsloggar, dirigera filer baserat på typ och justera bearbetningsstrategier för stora dokument. Genom att känna till filtyp, sidantal och storlek kan du upprätthålla efterlevnadsregler, uppskatta bearbetningstid och presentera tydlig information för användare innan de påbörjar en jämförelse.

## Förutsättningar

1. **GroupDocs.Comparison for .NET** – Installera biblioteket från den [officiella releases‑sidan](https://releases.groupdocs.com/comparison/net/).  
   Du kan också bläddra bland alla releaser på [GroupDocs releases‑sidan](https://releases.groupdocs.com/).  
2. **Utvecklingsmiljö** – Visual Studio, VS Code eller någon IDE som stödjer .NET 6+.  
3. **Exempeldokument** – Två filer (t.ex. `SOURCE.docx` och `TARGET.docx`) för testning. API‑et fungerar med över **50 dokumentformat**.

## Importera namnrymder

Följande `using`‑direktiv ger dig åtkomst till den centrala jämförelsesmotorn, filhanteringsverktyg och metadata‑gränssnitten.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Dessa importeringar krävs innan du instansierar några GroupDocs‑objekt.

## Hur man extraherar metadata från jämförelsresultat?

`Comparer`‑klassen laddar källdokumentet och styr jämförelsprocessen.

För att hämta metadata, ladda först källdokumentet med en `Comparer`‑instans, lägg sedan till mål‑dokumentet(erna). När jämförelsesmotorn är initierad, anropa `GetDocumentInfo()` på varje mål för att få ett `IDocumentInfo`‑objekt som innehåller egenskaper som filtyp, sidantal och storlek. Detta tillvägagångssätt fungerar enhetligt för alla stödda format.

### Steg 1: Initiera Comparer med källdokument

`Comparer` är kärnklassen i GroupDocs.Comparison som laddar källdokumentet och styr jämförelsoperationer. Att använda ett `using`‑block garanterar att alla ohanterade resurser frigörs automatiskt.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Proffstips:** Du kan skicka vilken `Stream` (fil, minne, moln) som helst till `Comparer`‑konstruktorn, inte bara en filsökväg.

### Steg 2: Lägg till mål‑dokument för jämförelse

`Add()`‑metoden accepterar ytterligare strömmar eller filsökvägar, vilket möjliggör en‑till‑många‑jämförelser.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Viktigt:** Ordningen på tillagda dokument påverkar hur förändringar markeras i den slutgiltiga rapporten.

### Steg 3: Hämta dokumentinformation från resultatdokumentet

`IDocumentInfo` ger en enhetlig vy av dokumentmetadata såsom filtyp, sidantal och storlek för alla stödda format.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Förstå data:** Det returnerade objektet fungerar likadant för DOCX, PDF, XLSX och PPTX, så du kan skriva format‑oberoende kod.

### Steg 4: Visa dokumentinformation

När du har `IDocumentInfo`‑instansen kan du logga, lagra eller presentera dess egenskaper.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

De tre mest använda egenskaperna är:

- **FileType** – t.ex. `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – totala sidor eller bilder.  
- **Size** – filstorlek i byte (användbart för lagringsberäkningar).

## Hur man får dokumentstorlek i .NET?

`Size`‑egenskapen returnerar filstorleken i byte.

Dokumentstorleken kan nås direkt från `IDocumentInfo`‑instansen via dess `Size`‑egenskap. Denna egenskap returnerar det exakta antalet byte i originalfilen, vilket gör att du kan konvertera den till kilobyte eller megabyte för visning eller lagringsberäkningar. Den speglar källfilens storlek, inte någon bearbetad version.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Obs:** `Size`‑värdet speglar originalfilens storlek, inte storleken efter intern bearbetning eller komprimering.

## Vanliga användningsfall och praktiska tillämpningar

- **Batch‑bearbetning:** Använd filtyp för att dirigera DOCX‑filer till ett Word‑specifikt arbetsflöde och PDF‑filer till en PDF‑optimerad pipeline.  
- **Lagringshantering:** Arkivera dokument större än 10 MB till en kall‑lagringsbucket automatiskt.  
- **Användarfeedback:** Visa sidantal och storlek innan jämförelse för att sätta realistiska förväntningar på bearbetningstid.  
- **Kvalitetssäkring:** Verifiera att uppladdade filer är kompletta genom att jämföra förväntat mot faktiskt sidantal.

## Felsökning av vanliga problem

- **Filåtkomstfel:** Verifiera läsbehörigheter och använd absoluta sökvägar under utveckling.  
- **Minnespåverkan med stora filer:** Föredra streaming (`File.OpenRead`) framför att ladda hela filen i minnet.  
- **Null‑referens‑undantag:** `FirstOrDefault()` kan returnera `null` om inget mål har lagts till; kontrollera alltid innan du anropar `GetDocumentInfo()`.  

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

- **Begränsad metadata för ren text:** Format som `.txt` kanske inte exponerar ett meningsfullt `PageCount`. Skydda mot saknade värden.

## Prestandaöverväganden

- **Strömhantering:** Omslut alltid strömmar i `using`‑satser för att snabbt frigöra filhandtag.  
- **Cachning:** Lagra ofta åtkomna metadata i en cache för att undvika upprepad extraktion.  
- **Batch‑operationer:** Bearbeta dokument i grupper för att minska overhead och förbättra genomströmning.

## Bästa praxis för produktionsanvändning

- **Robust felhantering:** Inneslut metadataextraktion i try‑catch‑block för att hantera korrupta eller ej stödda filer på ett smidigt sätt.  
- **Omfattande loggning:** Logga dokumenttyp, storlek och sidantal för varje jämförelse för att underlätta felsökning och revisionsöverensstämmelse.  
- **Säkerhetshygien:** Undvik att exponera fullständiga filsökvägar eller interna serverdetaljer i UI‑meddelanden.  
- **Resursdisposition:** Frigör `Comparer`‑instanser omedelbart, särskilt i webbtjänster som hanterar många samtidiga förfrågningar.

## Avancerade scenarier

### Flera mål‑dokument

Om du jämför en källa mot flera mål, iterera genom `Targets`‑samlingen och extrahera metadata från var och en.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Villkorad bearbetning baserad på metadata

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Lagra metadata i en databas

Spara `FileType`, `PageCount` och `Size` i en relationsdatabas för att möjliggöra rapportering och analys över tusentals jämförelser.

## Vanliga frågor

**Q: Är GroupDocs.Comparison för .NET kompatibel med olika dokumentformat?**  
A: Ja, den stödjer **50+ format** inklusive DOCX, PDF, PPTX, XLSX, TXT och många fler, och ger konsekvent metadataextraktion för dem.

**Q: Kan jag anpassa jämförelsinställningar utan att påverka metadataextraktion?**  
A: Absolut. Inställningar som känslighet, förändringstyper och utdataformat är oberoende av `GetDocumentInfo()`‑anropet.

**Q: Finns det en provversion jag kan använda för utvärdering?**  
A: Ja, ladda ner en gratis provversion från [GroupDocs releases‑sidan](https://releases.groupdocs.com/). Provet inkluderar fullständig metadataextraktionsfunktionalitet.

**Q: Var kan jag få support för implementationsfrågor?**  
A: Använd [GroupDocs.Comparison‑forumet](https://forum.groupdocs.com/c/comparison/12) för gemenskapsstöd och officiell support från GroupDocs‑teamet.

**Q: Vilka licensalternativ finns för produktionsdistributioner?**  
A: GroupDocs erbjuder utvecklar-, site- och OEM‑licenser. Köpalternativ listas på [GroupDocs köp‑sidan](https://purchase.groupdocs.com/buy).

---

**Senast uppdaterad:** 2026-06-15  
**Testad med:** GroupDocs.Comparison 6.0 för .NET  
**Författare:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Relaterade handledningar

- [Dokumentmetadatahantering .NET – Komplett guide för GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Hämta dokumentegenskaper C# .NET – Extrahera filmetadata](/comparison/net/basic-usage/get-document-info-from-path/)
- [Bevara mål‑metadata med GroupDocs.Comparison – .NET‑handledning](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)