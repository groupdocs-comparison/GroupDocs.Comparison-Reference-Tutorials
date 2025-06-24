---
"description": "Lär dig hur du sparar användardefinierade dokumentmetadata med GroupDocs Comparison för .NET. Jämför och manipulera enkelt metadata med steg-för-steg-instruktioner."
"linktitle": "Spara användardefinierade dokumentmetadata i GroupDocs-jämförelse för .NET"
"second_title": "GroupDocs.Comparison .NET API"
"title": "Spara användardefinierade dokumentmetadata i GroupDocs-jämförelse för .NET"
"url": "/sv/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
---

# Spara användardefinierade dokumentmetadata i GroupDocs-jämförelse för .NET

## Introduktion
I den här handledningen ska vi utforska hur man sparar användardefinierade dokumentmetadata med GroupDocs Comparison för .NET. Metadata är avgörande för att organisera och hantera dokument effektivt. Med GroupDocs Comparison kan du enkelt jämföra och manipulera metadata för att möta dina specifika behov.
## Förkunskapskrav
Innan vi börjar, se till att du har följande förutsättningar:
1. GroupDocs-jämförelse för .NET: Ladda ner och installera GroupDocs-jämförelse för .NET från [här](https://releases.groupdocs.com/comparison/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö, till exempel Visual Studio, installerad på ditt system.
3. Käll- och måldokument: Förbered de käll- och måldokument som du vill jämföra och manipulera metadata för.

## Importera namnrymder
Importera först de namnrymder som behövs för att komma åt funktionerna som tillhandahålls av GroupDocs Comparison för .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Steg 1: Definiera utdatakatalog och filnamn
Definiera katalogen där du vill spara det jämförda dokumentet och ange namnet på utdatafilen.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Steg 2: Initiera jämföraren och lägg till dokument
Initiera `Comparer` objektet med källdokumentet och lägg till måldokumentet för jämförelse.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Steg 3: Ange metadataalternativ
Ange metadataalternativen för att spara i det jämförda dokumentet. I det här exemplet ställer vi in `CloneMetadataType` till `MetadataType.FileAuthor` och ge detaljer för `FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## Steg 4: Jämför dokument och spara metadata
Jämför dokumenten med angivna metadataalternativ och spara det jämförda dokumentet.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Steg 5: Visa meddelande om framgång
Visa ett meddelande som anger att dokumenten har jämförts och var de är gjorda.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Slutsats
den här handledningen har vi lärt oss hur man sparar användardefinierade dokumentmetadata med GroupDocs Comparison för .NET. Genom att följa dessa steg kan du effektivt jämföra dokument samtidigt som du bevarar och manipulerar metadata enligt dina behov.
## Vanliga frågor
### Kan GroupDocs Comparison för .NET hantera olika dokumentformat?
Ja, GroupDocs Comparison stöder ett brett utbud av dokumentformat, inklusive DOCX, PDF, PPTX, XLSX med flera.
### Finns det en gratis testversion av GroupDocs Comparison för .NET?
Ja, du kan få tillgång till gratis provperioden [här](https://releases.groupdocs.com/).
### Kan jag anpassa metadataalternativen efter mina behov?
Absolut, GroupDocs Comparison erbjuder flexibla alternativ för att anpassa hanteringen av metadata under dokumentjämförelse.
### Erbjuder GroupDocs Comparison teknisk support?
Ja, du kan få teknisk support från GroupDocs Comparison-forumet. [här](https://forum.groupdocs.com/c/comparison/12).
### Var kan jag köpa en licens för GroupDocs Comparison för .NET?
Du kan köpa en licens från GroupDocs webbplats [här](https://purchase.groupdocs.com/buy).