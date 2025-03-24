---
title: Acceptera och avvisa ändringar i GroupDocs Comparison for .NET
linktitle: Acceptera och avvisa ändringar i GroupDocs Comparison for .NET
second_title: GroupDocs.Comparison .NET API
description: Lär dig hur du accepterar och avvisar ändringar i dokument med GroupDocs Comparison for .NET. Effektivisera dina dokumentarbetsflöden utan ansträngning.
weight: 10
url: /sv/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# Acceptera och avvisa ändringar i GroupDocs Comparison for .NET

## Introduktion
När det gäller dokumenthantering och samarbete är det av största vikt att säkerställa filernas noggrannhet och integritet. GroupDocs Comparison for .NET framstår som en robust lösning som ger utvecklare möjlighet att utan ansträngning acceptera och avvisa ändringar i dokument, och därigenom effektivisera arbetsflöden och öka produktiviteten. Den här handledningen guidar dig genom processen att acceptera och avvisa ändringar med GroupDocs Comparison för .NET, och dela upp varje steg för tydlighet och enkel implementering.
## Förutsättningar
Innan du dyker in i handledningen, se till att du har följande förutsättningar på plats:
### Miljöinställningar
1. Installera .NET SDK: Om du inte redan har gjort det, ladda ner och installera .NET SDK som passar ditt operativsystem från .NET-webbplatsen.
2.  Installera GroupDocs Comparison for .NET: Skaffa den senaste versionen av GroupDocs Comparison for .NET från den medföljande[nedladdningslänk](https://releases.groupdocs.com/comparison/net/) och följ installationsanvisningarna.
3. Bekantskap med C#-programmering: Denna handledning förutsätter en grundläggande förståelse av C#-programmeringsspråket och dess syntax.

## Importera namnområden
Till att börja med, importera de nödvändiga namnrymden till ditt projekt. Dessa namnutrymmen ger tillgång till de funktioner som krävs för jämförelse och manipulering av dokument.

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
 Se till att byta ut`"Your Document Directory"` med sökvägen till din önskade utdatakatalog.
## Steg 2: Initiera Comparer och jämför dokument
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Den här koden initierar Comparer-objektet med källdokumentet och lägger till måldokumentet för jämförelse. Sedan kör den jämförelseprocessen.
## Steg 3: Hämta och manipulera ändringar
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Hämta ändringarna från jämförelsen och manipulera dem efter behov. I det här exemplet avvisas ändringar först och accepteras sedan. De resulterande dokumenten sparas därefter.

## Slutsats
Sammanfattningsvis erbjuder GroupDocs Comparison for .NET en sömlös lösning för att acceptera och avvisa ändringar i dokument. Genom att följa stegen som beskrivs i denna handledning kan utvecklare effektivt integrera den här funktionen i sina applikationer, säkerställa dokumentnoggrannhet och förbättra samarbetet.
## FAQ's
### Kan GroupDocs Comparison för .NET jämföra dokument i olika format?
Ja, GroupDocs Comparison for .NET stöder jämförelse mellan dokument i olika format som DOCX, PDF, PPTX och mer.
### Är GroupDocs Comparison for .NET kompatibel med .NET Core?
Ja, GroupDocs Comparison for .NET är kompatibel med både .NET Framework och .NET Core.
### Kan jag anpassa utseendet på ändringar i de jämförda dokumenten?
Absolut, GroupDocs Comparison för .NET ger omfattande alternativ för att anpassa utseendet på ändringar inklusive färg, stil och mer.
### Har GroupDocs Comparison for .NET stöd för flersidiga dokumentjämförelser?
Ja, GroupDocs Comparison for .NET stöder jämförelse av flersidiga dokument med precision och noggrannhet.
### Finns det en testversion tillgänglig för GroupDocs Comparison för .NET?
 Ja, du kan använda en gratis provversion av GroupDocs Comparison för .NET från det medföljande[länk](https://releases.groupdocs.com/).