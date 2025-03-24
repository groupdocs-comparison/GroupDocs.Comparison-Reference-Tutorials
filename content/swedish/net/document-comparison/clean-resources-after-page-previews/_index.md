---
title: Rengör resurser efter förhandsvisningar av sidan
linktitle: Rengör resurser efter förhandsvisningar av sidan
second_title: GroupDocs.Comparison .NET API
description: Lär dig hur du jämför dokument med GroupDocs.Comparison för .NET steg för steg. Förbättra dina .NET-applikationer med effektiv dokumenthantering.
weight: 13
url: /sv/net/document-comparison/clean-resources-after-page-previews/
---
## Introduktion
en värld av .NET-utveckling är det viktigt att hantera och jämföra dokument effektivt för olika applikationer, från advokatbyråer till utbildningsinstitutioner. Lyckligtvis kan utvecklare med verktyg som GroupDocs.Comparison för .NET effektivisera processen att jämföra dokument med lätthet. I den här handledningen kommer vi att utforska hur man använder GroupDocs.Comparison för .NET för att jämföra dokument steg för steg.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:
1.  GroupDocs.Comparison for .NET: Ladda ner och installera biblioteket från[här](https://releases.groupdocs.com/comparison/net/).
2. .NET-utvecklingsmiljö: Se till att du har en fungerande .NET-utvecklingsmiljö inställd på din dator.
3. Dokumentexempel: Förbered käll- och måldokumenten du vill jämföra.

## Importera namnområden
I ditt .NET-projekt börjar du med att importera de nödvändiga namnområdena för att komma åt funktionerna i GroupDocs.Comparison for .NET.

```csharp
using System;
using System.IO;
```

## Steg 1: Definiera utdatakatalog och filnamn
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```
## Steg 2: Initiera Comparer och lägg till dokument
```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```
## Steg 3: Utför jämförelse och generera utdata
```csharp
    comparer.Compare(File.Create(outputFileName));
```
## Steg 4: Skapa dokumentförhandsvisningar
```csharp
    Document document = new Document(File.OpenRead(outputFileName));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(Constants.SamplesPath, $"result_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    document.GeneratePreview(previewOptions);
}
```
## Steg 5: Visa framgångsmeddelande
```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

## Slutsats
Sammanfattningsvis erbjuder GroupDocs.Comparison for .NET en robust lösning för att jämföra dokument utan ansträngning inom .NET-applikationer. Genom att följa stegen som beskrivs i den här handledningen kan utvecklare sömlöst integrera funktionalitet för dokumentjämförelse i sina projekt, vilket ökar produktiviteten och effektiviteten.
## FAQ's
### Är GroupDocs.Comparison for .NET kompatibelt med olika dokumentformat?
Ja, GroupDocs.Comparison for .NET stöder ett brett utbud av dokumentformat, inklusive DOCX, PPTX, XLSX, PDF och mer.
### Kan jag anpassa utdataformatet för jämförda dokument?
Absolut, GroupDocs.Comparison för .NET erbjuder flexibilitet när det gäller att välja utdataformat enligt dina krav.
### Finns det en testversion tillgänglig för teständamål?
 Ja, du kan utforska funktionerna i GroupDocs.Comparison för .NET med en gratis testversion tillgänglig[här](https://releases.groupdocs.com/).
### Hur kan jag få support för eventuella problem eller frågor relaterade till GroupDocs.Comparison for .NET?
 Du kan söka hjälp från GroupDocs.Comparison-gemenskapsforumet[här](https://forum.groupdocs.com/c/comparison/12).
### Var kan jag köpa en licens för GroupDocs.Comparison för .NET?
Du kan köpa en licens för GroupDocs.Comparison för .NET från[den här länken](https://purchase.groupdocs.com/buy).