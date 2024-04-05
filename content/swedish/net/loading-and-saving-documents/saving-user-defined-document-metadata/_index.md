---
title: Spara användardefinierade dokumentmetadata i GroupDocs Comparison för .NET
linktitle: Spara användardefinierade dokumentmetadata i GroupDocs Comparison för .NET
second_title: GroupDocs.Comparison .NET API
description: Lär dig hur du sparar användardefinierad dokumentmetadata med GroupDocs Comparison för .NET. Jämför och manipulera enkelt metadata med steg-för-steg-instruktioner.
type: docs
weight: 16
url: /sv/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Introduktion
I den här handledningen kommer vi att utforska hur man sparar användardefinierad dokumentmetadata med hjälp av GroupDocs Comparison for .NET. Metadata är avgörande för att organisera och hantera dokument effektivt. Med GroupDocs Comparison kan du enkelt jämföra och manipulera metadata för att möta dina specifika krav.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1.  GroupDocs Comparison for .NET: Ladda ner och installera GroupDocs Comparison for .NET från[här](https://releases.groupdocs.com/comparison/net/).
2. Utvecklingsmiljö: Se till att du har en lämplig utvecklingsmiljö som Visual Studio installerad på ditt system.
3. Käll- och måldokument: Förbered käll- och måldokumenten som du vill jämföra och manipulera metadata för.

## Importera namnområden
Importera först de nödvändiga namnområdena för att komma åt funktionerna som tillhandahålls av GroupDocs Comparison för .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Steg 1: Definiera utdatakatalog och filnamn
Definiera katalogen där du vill spara det jämförda dokumentet och ange utdatafilens namn.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Steg 2: Initiera Comparer och lägg till dokument
 Initiera`Comparer` objekt med källdokumentet och lägg till måldokumentet för jämförelse.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Steg 3: Ange metadataalternativ
 Ange metadataalternativ för att spara i det jämförda dokumentet. I det här exemplet ställer vi in`CloneMetadataType` till`MetadataType.FileAuthor` och ge detaljer för`FileAuthorMetadata`.
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
## Steg 5: Visa framgångsmeddelande
Visa ett framgångsmeddelande som indikerar att dokumenten har jämförts framgångsrikt och utdataplatsen.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Slutsats
I den här handledningen har vi lärt oss hur man sparar användardefinierad dokumentmetadata med hjälp av GroupDocs Comparison för .NET. Genom att följa dessa steg kan du effektivt jämföra dokument samtidigt som du bevarar och manipulerar metadata enligt dina krav.
## FAQ's
### Kan GroupDocs Comparison för .NET hantera olika dokumentformat?
Ja, GroupDocs Comparison stöder ett brett utbud av dokumentformat inklusive DOCX, PDF, PPTX, XLSX och mer.
### Finns det en gratis testversion tillgänglig för GroupDocs Comparison för .NET?
 Ja, du kan komma åt den kostnadsfria provperioden[här](https://releases.groupdocs.com/).
### Kan jag anpassa metadataalternativ efter mina behov?
Absolut, GroupDocs Comparison ger flexibla alternativ för att anpassa metadatahantering under dokumentjämförelse.
### Erbjuder GroupDocs Comparison teknisk support?
Ja, du kan få teknisk support från GroupDocs Comparison forum[här](https://forum.groupdocs.com/c/comparison/12).
### Var kan jag köpa en licens för GroupDocs Comparison för .NET?
 Du kan köpa en licens från GroupDocs-webbplatsen[här](https://purchase.groupdocs.com/buy).