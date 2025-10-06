---
"description": "Lär dig hur du ställer in ett lösenord för resulterande dokument i GroupDocs Comparison för .NET. Förbättra säkerheten och skydda dina jämförda filer."
"linktitle": "Ställa in lösenord för resulterande dokument i GroupDocs-jämförelse för .NET"
"second_title": "GroupDocs.Comparison .NET API"
"title": "Ställa in lösenord för resulterande dokument i GroupDocs-jämförelse för .NET"
"url": "/sv/net/loading-and-saving-documents/setting-password-for-resultant-document/"
"weight": 17
type: docs
---
# Ställa in lösenord för resulterande dokument i GroupDocs-jämförelse för .NET

## Introduktion
I den här handledningen guidar vi dig genom processen att ställa in ett lösenord för det resulterande dokumentet med GroupDocs Comparison för .NET. Den här funktionen lägger till ett extra säkerhetslager till dina jämförda dokument och säkerställer att endast behöriga personer kan komma åt dem.
## Förkunskapskrav
Innan du fortsätter, se till att du har följande:
1. GroupDocs-jämförelse för .NET: Se till att du har GroupDocs-jämförelsebiblioteket installerat i din .NET-miljö. Du kan ladda ner det från [här](https://releases.groupdocs.com/comparison/net/).
2. Käll- och måldokument: Förbered källdokumentet (`SOURCE.docx`) och måldokumentet (`TARGET.docx`) som du vill jämföra och ange ett lösenord för det resulterande dokumentet.

## Importera namnrymder
Först måste du importera de nödvändiga namnrymderna till ditt C#-projekt för att använda GroupDocs Comparison-funktionen:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Steg 1: Definiera utdatakatalog och filnamn
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
Ange katalogen där du vill spara det resulterande dokumentet och definera namnet på utdatafilen.
## Steg 2: Jämför dokument med lösenordsinställningar
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
Här initierar vi en `Comparer` objektet med källdokumentet. Sedan lägger vi till måldokumentet som ska jämföras. Vi ställer in `PasswordSaveOption` till `User` för att ange att ett lösenord ska tillämpas på det resulterande dokumentet. Ange önskat lösenord i `Password` egendomen tillhörande `SaveOptions` objekt.
## Steg 3: Visa meddelande om framgång
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Slutligen visar vi ett meddelande som indikerar att dokumenten har jämförts och att det resulterande dokumentet med det angivna lösenordet har sparats i den angivna katalogen.

## Slutsats
Att ange ett lösenord för det resulterande dokumentet i GroupDocs Comparison för .NET lägger till ett extra säkerhetslager till dina jämförda dokument, vilket säkerställer konfidentialitet och integritet. Genom att följa stegen som beskrivs i den här handledningen kan du enkelt implementera den här funktionen i dina .NET-applikationer.
## Vanliga frågor
### Kan jag jämföra dokument i olika format?
Ja, GroupDocs Comparison för .NET stöder jämförelse av dokument i olika format som DOCX, PDF, PPTX, XLSX med flera.
### Finns det en testversion tillgänglig?
Ja, du kan ladda ner en gratis testversion från [här](https://releases.groupdocs.com/).
### Hur kan jag få support om jag stöter på några problem?
Du kan söka hjälp från GroupDocs Comparison-forumet. [här](https://forum.groupdocs.com/c/comparison/12).
### Behöver jag en licens för att använda GroupDocs Comparison för .NET?
Ja, du kan köpa en licens från [här](https://purchase.groupdocs.com/buy) eller skaffa ett tillfälligt körkort [här](https://purchase.groupdocs.com/temporary-license/).
### Finns det någon dokumentation tillgänglig för GroupDocs Comparison för .NET?
Ja, du kan komma åt dokumentationen [här](https://tutorials.groupdocs.com/comparison/net/).