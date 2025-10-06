---
"description": "Lär dig hur du accepterar och avvisar ändringar i dokument med GroupDocs Comparison för .NET. Effektivisera dina dokumentarbetsflöden utan ansträngning."
"linktitle": "Acceptera och avvisa ändringar i GroupDocs-jämförelse för .NET"
"second_title": "GroupDocs.Comparison .NET API"
"title": "Acceptera och avvisa ändringar i GroupDocs-jämförelse för .NET"
"url": "/sv/net/documents-and-folder-comparison/accept-reject-changes-dotnet/"
"weight": 10
type: docs
---
# Acceptera och avvisa ändringar i GroupDocs-jämförelse för .NET

## Introduktion
Inom dokumenthantering och samarbete är det av största vikt att säkerställa filernas noggrannhet och integritet. GroupDocs Comparison för .NET framstår som en robust lösning som gör det möjligt för utvecklare att enkelt acceptera och avvisa ändringar i dokument, vilket effektiviserar arbetsflöden och ökar produktiviteten. Den här handledningen guidar dig genom processen att acceptera och avvisa ändringar med GroupDocs Comparison för .NET, och bryter ner varje steg för tydlighetens skull och förenkla implementeringen.
## Förkunskapskrav
Innan du börjar med handledningen, se till att du har följande förutsättningar på plats:
### Miljöinställningar
1. Installera .NET SDK: Om du inte redan har gjort det, ladda ner och installera .NET SDK som är lämpligt för ditt operativsystem från .NET-webbplatsen.
2. Installera GroupDocs Comparison för .NET: Hämta den senaste versionen av GroupDocs Comparison för .NET från den medföljande [nedladdningslänk](https://releases.groupdocs.com/comparison/net/) och följ installationsanvisningarna.
3. Bekantskap med C#-programmering: Denna handledning förutsätter en grundläggande förståelse av programmeringsspråket C# och dess syntax.

## Importera namnrymder
Till att börja med, importera de nödvändiga namnrymderna till ditt projekt. Dessa namnrymder ger åtkomst till de funktioner som krävs för dokumentjämförelse och manipulation.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Steg 1: Ange utdatakatalog och filnamn
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
Se till att byta ut `"Your Document Directory"` med sökvägen till önskad utdatakatalog.
## Steg 2: Initiera jämföraren och jämför dokument
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Denna kod initierar Comparer-objektet med källdokumentet och lägger till måldokumentet för jämförelse. Sedan körs jämförelseprocessen.
## Steg 3: Hämta och manipulera ändringar
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Hämta ändringarna från jämförelsen och manipulera dem efter behov. I det här exemplet avvisas ändringarna först och accepteras sedan. De resulterande dokumenten sparas därefter.

## Slutsats
Sammanfattningsvis erbjuder GroupDocs Comparison för .NET en sömlös lösning för att acceptera och avvisa ändringar i dokument. Genom att följa stegen som beskrivs i den här handledningen kan utvecklare effektivt integrera den här funktionen i sina applikationer, vilket säkerställer dokumentens noggrannhet och förbättrar samarbetet.
## Vanliga frågor
### Kan GroupDocs Comparison för .NET jämföra dokument i olika format?
Ja, GroupDocs Comparison för .NET stöder jämförelse mellan dokument i olika format som DOCX, PDF, PPTX med flera.
### Är GroupDocs-jämförelse för .NET kompatibel med .NET Core?
Ja, GroupDocs Comparison för .NET är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på ändringarna i de jämförda dokumenten?
Absolut, GroupDocs Comparison för .NET erbjuder omfattande alternativ för att anpassa utseendet på ändringar, inklusive färg, stil och mer.
### Har GroupDocs Comparison för .NET stöd för jämförelse av dokument över flera sidor?
Ja, GroupDocs Comparison för .NET stöder jämförelse av flersidiga dokument med precision och noggrannhet.
### Finns det en testversion tillgänglig för GroupDocs Comparison för .NET?
Ja, du kan få en gratis provversion av GroupDocs Comparison för .NET från den medföljande [länk](https://releases.groupdocs.com/).