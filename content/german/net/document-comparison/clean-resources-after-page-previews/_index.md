---
categories:
- Document Management
date: '2026-07-14'
description: Erfahren Sie, wie Sie compare word documents in .NET, page previews erzeugen
  und resources effizient mit GroupDocs.Comparison bereinigen.
keywords:
- compare word documents
- resource management .net
- clean resources .net
- document preview
lastmod: '2026-07-14'
linktitle: Ressourcen nach Page Previews bereinigen
og_description: compare word documents in .NET mit GroupDocs.Comparison. Folgen Sie
  dieser Schritt‑für‑Schritt‑Anleitung, um previews zu erzeugen, resources zu bereinigen
  und memory leaks zu vermeiden.
og_image_alt: 'Guide: compare word documents and clean resources after page previews
  using GroupDocs.Comparison for .NET'
og_title: compare word documents – Ressourcen nach Page Previews in .NET bereinigen
schemas:
- author: GroupDocs
  dateModified: '2026-07-14'
  description: Learn how to compare word documents in .NET, generate page previews,
    and clean resources efficiently with GroupDocs.Comparison.
  headline: compare word documents – Clean Resources After Page Previews in .NET
  type: TechArticle
- description: Learn how to compare word documents in .NET, generate page previews,
    and clean resources efficiently with GroupDocs.Comparison.
  name: compare word documents – Clean Resources After Page Previews in .NET
  steps:
  - name: Define Output Directory and File Name
    text: 'This step sets up where your comparison results will be saved. The `Path.Combine`
      method ensures cross‑platform compatibility by using the correct path separator
      for your operating system. **Why This Matters**: Defining clear output paths
      upfront prevents file‑access errors and makes your code more '
  - name: Initialize Comparer and Add Documents
    text: '**Definition Anchor**: The `Comparer` class is the primary engine in GroupDocs.Comparison
      that loads source and target documents, computes differences, and produces a
      result file. **Direct Answer**: Use a `using` block to instantiate `Comparer`,
      add the target document with `Add()`, and let the `usi'
  - name: Perform Comparison and Generate Output
    text: '**Direct Answer**: Call `comparer.Compare()` and pipe the result into a
      `FileStream` created with `File.Create()`. This single line performs the diff
      and writes the merged document to disk in one atomic operation. This single
      line does the heavy lifting—it compares your documents and creates the out'
  - name: Generate Document Previews
    text: '**Definition Anchor**: `PreviewOptions` is a configuration object that
      tells GroupDocs.Comparison how to render page images, including format, resolution,
      and page range. **Direct Answer**: Create a `PreviewOptions` instance, set `PreviewFormat`
      to your desired image type (e.g., PNG), specify the `P'
  - name: Display Success Message
    text: A simple confirmation that everything worked as expected. In production
      applications, you might want to log this information or trigger a callback instead.
  type: HowTo
- questions:
  - answer: Yes. GroupDocs.Comparison supports 50+ input and output formats—including
      DOCX, PPTX, XLSX, PDF, and many image types—allowing you to compare virtually
      any business document without extra converters.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. You can specify the desired output format (e.g., DOCX, PDF,
      HTML) when saving the comparison result, giving you full control over how the
      merged document is delivered.
    question: Can I customize the output format of compared documents?
  - answer: Yes, you can explore all features of GroupDocs.Comparison for .NET with
      a free trial available [here](https://releases.groupdocs.com/). The trial lets
      you verify that the library meets your needs before purchasing.
    question: Is there a trial version available for testing purposes?
  - answer: You can seek assistance from the GroupDocs.Comparison community forum
      [here](https://forum.groupdocs.com/c/comparison/12). The community is active,
      and the GroupDocs team regularly participates to help resolve technical problems.
    question: How can I get support for any issues or queries related to GroupDocs.Comparison
      for .NET?
  - answer: You can purchase a license from [this link](https://purchase.groupdocs.com/buy).
      Various licensing options are available, from single‑developer to enterprise‑wide
      deployments.
    question: Where can I purchase a license for GroupDocs.Comparison for .NET?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- compare word documents
- GroupDocs.Comparison
- .NET resource management
- document preview
title: compare word documents – Ressourcen nach Page Previews in .NET bereinigen
type: docs
url: /de/net/document-comparison/clean-resources-after-page-previews/
weight: 13
---

# Word-Dokumente vergleichen – Ressourcen nach Seitenvorschauen bereinigen

## Einführung

Haben Sie schon einmal mit Speicherlecks nach der Erstellung von Dokumentvorschauen in Ihrer .NET‑Anwendung zu kämpfen gehabt? Sie sind nicht allein. Wenn Sie **Word‑Dokumente vergleichen** in .NET, ist die Verwaltung von Ressourcen nach dem Erzeugen von Seitenvorschauen ein häufiges Problem. Egal, ob Sie ein Rechtsprüfsystem, eine Bildungsplattform oder eine Business‑App entwickeln, die Dokumentänderungen verfolgt, ineffiziente Ressourcenhandhabung kann eine reibungslos laufende Anwendung schnell in ein speicherhungriges Monster verwandeln.

Die gute Nachricht? GroupDocs.Comparison für .NET bietet eine robuste Lösung, die nicht nur den Dokumentvergleich nahtlos erledigt, sondern Ihnen auch die vollständige Kontrolle über die Bereinigung von Ressourcen gibt. In diesem umfassenden Leitfaden erfahren Sie genau, wie Sie ein korrektes Ressourcenmanagement beim Vergleich von Dokumenten implementieren, sodass Ihre Anwendung leistungsfähig und zuverlässig bleibt.

Am Ende dieses Tutorials wissen Sie, wie Sie Dokumente Schritt für Schritt vergleichen, Vorschauen effizient erzeugen und – am wichtigsten – Ressourcen ordnungsgemäß bereinigen, um Speicherlecks zu verhindern, die Ihre Anwendung zum Absturz bringen könnten.

## Schnelle Antworten
- **Was bedeutet „compare word documents“?** Es bedeutet das Erkennen von Einfügungen, Löschungen und Formatierungsänderungen zwischen zwei Word‑Dateien mithilfe von GroupDocs.Comparison für .NET.  
- **Warum Ressourcen nach Vorschauen bereinigen?** Nicht freigegebene Streams halten Dateihandles offen, was zu Speicherspitzen und „Datei wird verwendet“-Fehlern führt.  
- **Welche Bibliothek übernimmt das?** GroupDocs.Comparison für .NET, unterstützt über 50 Formate und streamt Vorschauen, ohne die gesamte Datei in den Speicher zu laden.  
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion ist verfügbar; für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.  
- **Welche .NET‑Versionen werden unterstützt?** .NET Framework 4.6+, .NET Core 3.1+, .NET 5/6/7.

## Was bedeutet „compare word documents“?

**compare word documents** ist der Vorgang, programmatisch textuelle und visuelle Unterschiede zwischen zwei Word‑Dateien zu identifizieren. GroupDocs.Comparison analysiert die Dokumentstruktur, hebt Änderungen hervor und kann ein zusammengeführtes Ergebnis ausgeben, das Einfügungen, Löschungen und Formatierungsänderungen klar darstellt. Es funktioniert, indem es die XML‑Struktur des Dokuments parst, Änderungen auf Absatz‑, Lauf‑ und Zeichenebene erkennt und diese Unterschiede im Ausgabedokument markiert.

## Warum Ressourcen nach Seitenvorschauen bereinigen?

GroupDocs.Comparison erstellt für jedes Vorschau‑Bild einen separaten Stream. Wenn diese Streams nicht freigegeben werden, verbleiben sie im Speicher, was zu einem schrittweisen Speicherzuwachs und möglichen Out‑of‑Memory‑Ausnahmen führt. Eine ordnungsgemäße Bereinigung garantiert stabile, langfristig laufende Dienste und eine reaktionsfähige Benutzeroberfläche. Zusätzlich können nicht freigegebene Streams die Quelldateien sperren, wodurch weitere Lese‑/Schreib‑Operationen verhindert werden und Fehler auftreten, wenn die Anwendung versucht, dieselben Dokumente erneut zu öffnen.

## Voraussetzungen

Bevor Sie in den Dokumentvergleich mit .NET eintauchen, stellen Sie sicher, dass Sie diese Voraussetzungen erfüllt haben:

1. **GroupDocs.Comparison für .NET**: Laden Sie die Bibliothek von [hier](https://releases.groupdocs.com/comparison/net/) herunter und installieren Sie sie. Dies ist Ihr Hauptwerkzeug für Dokumentvergleichs‑Operationen.  
2. **.NET‑Entwicklungsumgebung**: Stellen Sie sicher, dass Sie eine funktionierende .NET‑Entwicklungsumgebung auf Ihrem Rechner haben. Visual Studio 2019 oder neuer funktioniert hervorragend, aber jede kompatible IDE ist ausreichend.  
3. **Dokumentbeispiele**: Bereiten Sie die Quell‑ und Zieldokumente vor, die Sie vergleichen möchten. Die Bibliothek unterstützt DOCX, PPTX, XLSX, PDF und über 50 weitere Formate.

**Pro‑Tipp**: Beginnen Sie mit kleineren Dokumenten (unter 10 MB), wenn Sie die Bibliothek zum ersten Mal erlernen. Das erleichtert das Erkennen von Ressourcenverwaltungs‑Problemen und das Testen Ihrer Bereinigungs‑Implementierung.

## Namespaces importieren

Beginnen Sie in Ihrem .NET‑Projekt damit, die erforderlichen Namespaces zu importieren, um auf die Funktionalitäten von GroupDocs.Comparison für .NET zuzugreifen.

```csharp
using System;
using System.IO;
```

Diese Namespaces geben Ihnen Zugriff auf die Kern‑Vergleichsfunktionen und Dateiverarbeitungs‑Möglichkeiten, die Sie im gesamten Tutorial benötigen.

## Schritt‑für‑Schritt‑Implementierungs‑Leitfaden

### Schritt 1: Ausgabeverzeichnis und Dateinamen festlegen

```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.pptx");
```

Dieser Schritt legt fest, wo Ihre Vergleichsergebnisse gespeichert werden. Die Methode `Path.Combine` sorgt für plattformübergreifende Kompatibilität, indem sie den richtigen Pfadtrenner für Ihr Betriebssystem verwendet.

**Warum das wichtig ist**: Das frühzeitige Definieren klarer Ausgabepfade verhindert Datei‑Zugriffs‑Fehler und macht Ihren Code wartbarer. Verwenden Sie in Produktionsumgebungen stets absolute Pfade, um Verwirrungen zu vermeiden.

### Schritt 2: Comparer initialisieren und Dokumente hinzufügen

```csharp
using (Comparer comparer = new Comparer("SOURCE.pptx"))
{
    comparer.Add("TARGET.pptx");
```

**Definition**: Die Klasse `Comparer` ist die zentrale Engine in GroupDocs.Comparison, die Quell‑ und Zieldokumente lädt, Unterschiede berechnet und eine Ergebnisdatei erzeugt.

**Direkte Antwort**: Verwenden Sie einen `using`‑Block, um `Comparer` zu instanziieren, das Zieldokument mit `Add()` hinzuzufügen und das `using`‑Statement das Objekt automatisch entsorgen zu lassen, wodurch garantiert wird, dass alle nicht verwalteten Ressourcen freigegeben werden, selbst wenn eine Ausnahme auftritt.

Das `using`‑Statement ist entscheidend – es stellt sicher, dass das `Comparer`‑Objekt ordnungsgemäß entsorgt wird, selbst wenn eine Ausnahme auftritt. Dies ist Ihre erste Verteidigungslinie gegen Ressourcen‑Lecks.

**Wichtiger Hinweis**: Der Konstruktor `Comparer` nimmt Ihr Quelldokument entgegen, und die Methode `Add()` fügt das Zieldokument zum Vergleich hinzu. Bei Bedarf können Sie mehrere Zieldokumente hinzufügen.

### Schritt 3: Vergleich durchführen und Ausgabe erzeugen

```csharp
    comparer.Compare(File.Create(outputFileName));
```

**Direkte Antwort**: Rufen Sie `comparer.Compare()` auf und leiten Sie das Ergebnis in einen mit `File.Create()` erstellten `FileStream`. Diese eine Zeile führt den Vergleich aus und schreibt das zusammengeführte Dokument in einem atomaren Vorgang auf die Festplatte.

Diese eine Zeile übernimmt die Hauptarbeit – sie vergleicht Ihre Dokumente und erstellt die Ausgabedatei. Die Methode `File.Create()` öffnet einen Dateistream, in den das Vergleichsergebnis geschrieben wird.

**Performance‑Tipp**: Bei großen Dokumenten kann dieser Vorgang speicherintensiv sein. Erwägen Sie die Implementierung einer Fortschrittsanzeige, wenn Sie mehrere Dateien oder sehr große Dokumente verarbeiten.

### Schritt 4: Dokumentvorschauen erzeugen

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

**Definition**: `PreviewOptions` ist ein Konfigurationsobjekt, das GroupDocs.Comparison mitteilt, wie Seitenbilder gerendert werden sollen, einschließlich Format, Auflösung und Seitenbereich.

**Direkte Antwort**: Erstellen Sie eine Instanz von `PreviewOptions`, setzen Sie `PreviewFormat` auf den gewünschten Bildtyp (z. B. PNG), geben Sie die benötigten `PageNumbers` an und rufen Sie schließlich für jeden erzeugten Stream `ReleasePageStream` auf, um den Speicher sofort freizugeben.

`ReleasePageStream` gibt den Memory‑Stream einer Vorschauseite frei und schließt den zugrunde liegenden Dateihandle.

Hier wird das Ressourcenmanagement kritisch. Die Vorschauerstellung erzeugt Streams für jedes Seitenbild, und ohne ordnungsgemäße Bereinigung können sich diese ansammeln und Speicherprobleme verursachen.

**Wichtige Komponenten erklärt**:
- **PreviewOptions**: Konfiguration, wie Vorschauen erzeugt werden
- **PreviewFormat**: Auswahl von PNG, JPG oder anderen unterstützten Formaten
- **PageNumbers**: Angabe, welche Seiten vorgeschaut werden sollen (spart Ressourcen)
- **ReleasePageStream**: Ihre Bereinigungsmethode – das ist entscheidend!

### Schritt 5: Erfolgsnachricht anzeigen

```csharp
Console.WriteLine($"\nDocument previews generated successfully.\nCheck output in {outputDirectory}.");
```

Eine einfache Bestätigung, dass alles wie erwartet funktioniert hat. In Produktionsanwendungen möchten Sie diese Information möglicherweise protokollieren oder stattdessen einen Callback auslösen.

## Häufige Probleme und Lösungen

### Speicherlecks beim Dokumentvergleich

**Problem**: Der Speicherverbrauch Ihrer Anwendung steigt nach jedem Vergleichsvorgang weiter an.

**Lösung**: Verwenden Sie stets `using`‑Statements mit `IDisposable`‑Objekten wie `Comparer` und `Document`. Implementieren Sie außerdem die Methode `ReleasePageStream` korrekt:

```csharp
private static void UserReleaseStreamMethod(int pageNumber, Stream pageStream)
{
    pageStream?.Dispose();
}
```

### Datei‑Zugriffs‑Fehler

**Problem**: Erhalten von „Datei wird verwendet“-Fehlern beim Versuch, Ressourcen zu bereinigen.

**Lösung**: Stellen Sie sicher, dass alle Dateistreams vor dem Bereinigen ordnungsgemäß geschlossen sind. Das `using`‑Statement erledigt dies automatisch, aber wenn Sie Streams manuell verwalten, rufen Sie stets `Dispose()` in einem `finally`‑Block auf.

### Leistungsprobleme bei großen Dokumenten

**Problem**: Vergleichsvorgänge dauern zu lange oder verbrauchen zu viel Speicher.

**Lösungen**:
- Dokumente, wenn möglich, in kleineren Teilen verarbeiten
- Für Vorschauen spezifische Seitenbereiche verwenden, anstatt alle Seiten zu generieren
- Erwägen Sie die Implementierung asynchroner Muster für eine bessere UI‑Reaktionsfähigkeit

## Best Practices für den Dokumentvergleich in .NET

### Exzellenz im Ressourcenmanagement

1. **Immer `using`‑Statements verwenden**: Dies stellt eine ordnungsgemäße Entsorgung sicher, selbst bei Ausnahmen.
2. **Benutzerdefinierte Release‑Methoden implementieren**: Verlassen Sie sich nicht ausschließlich auf die automatische Garbage Collection.
3. **Speichernutzung überwachen**: Nutzen Sie Performance‑Counter oder Profiling‑Tools während der Entwicklung.
4. **Große Dateien sorgfältig behandeln**: Erwägen Sie Streaming‑Ansätze für sehr große Dokumente.

### Tipps zur Leistungsoptimierung

- **Selektive Vorschau‑Erstellung**: Nur Vorschauen für tatsächlich benötigte Seiten erzeugen.
- **Geeignete Bildformate wählen**: PNG für Qualität, JPG für kleinere Dateigrößen.
- **Batch‑Operationen**: Beim Vergleich mehrerer Dokumente `Comparer`‑Instanzen nach Möglichkeit wiederverwenden.
- **Asynchrone Verarbeitung**: `async/await`‑Muster für ein besseres Benutzererlebnis nutzen.

## Praxisbeispiele

### Rechtsdokumenten‑Prüfung

Anwaltskanzleien nutzen den Dokumentvergleich, um Änderungen in Verträgen, juristischen Schriftsätzen und Gerichtsunterlagen nachzuverfolgen. Ein korrektes Ressourcenmanagement ist entscheidend, wenn täglich Hunderte von Dokumenten verarbeitet werden.

### Bildungsplattformen

Lehrer und Institutionen vergleichen Studenteneinreichungen, um Plagiate zu erkennen oder Versionen von Aufgaben zu verfolgen. Eine saubere Ressourcenhandhabung sorgt dafür, dass das System bei hoher Auslastung reaktionsfähig bleibt.

### Business‑Dokumenten‑Management

Unternehmen verlassen sich auf den Vergleich für Versionskontrolle, Compliance‑Prüfungen und kollaboratives Editing. Speicherlecks können Systemausfälle verursachen, weshalb eine ordnungsgemäße Bereinigung unerlässlich ist.

## Leistungsüberlegungen

Bei der Implementierung des Dokumentvergleichs in der Produktion sollten Sie diese Faktoren berücksichtigen:

- **Speicherverwaltung**: Jedes geladene Dokument verbraucht RAM. Für Anwendungen, die mehrere Dokumente gleichzeitig verarbeiten, sollten Sie Queuing‑ und Ressourcen‑Grenzwerte implementieren.
- **Datei‑I/O‑Optimierung**: Verwenden Sie asynchrone Dateioperationen, um UI‑Blockaden zu vermeiden, insbesondere in Web‑Apps.
- **Caching‑Strategie**: Zwischenspeichern von Vergleichsergebnissen für häufig aufgerufene Dokumentpaare, jedoch mit Ablaufsteuerung, um veraltete Daten zu vermeiden.

## Fehlersuch‑Leitfaden

### Ressourcen‑Lecks debuggen

Wenn Sie Speicherlecks vermuten, verwenden Sie diese Techniken:

1. **Prozess‑Speicher überwachen**: Verwenden Sie den Task‑Manager oder den Performance‑Monitor, um die Speichernutzung im Zeitverlauf zu verfolgen.
2. **Garbage‑Collection‑Logging aktivieren**: Fügen Sie GC‑Logging hinzu, um Sammelmuster zu identifizieren.
3. **Speicher‑Profiler verwenden**: Werkzeuge wie JetBrains dotMemory helfen, Objekt‑Retention‑Probleme zu lokalisieren.

### Datei‑Sperr‑Probleme behandeln

Manchmal bleiben Dateien nach Vergleichsvorgängen gesperrt:

```csharp
// Ensure all streams are disposed
using (var fileStream = File.OpenRead(fileName))
{
    // Your processing code here
} // Stream automatically disposed here
```

### Umgang mit nicht unterstützten Dateiformaten

Überprüfen Sie stets die Kompatibilität des Dokumentformats, bevor Sie einen Vergleich versuchen:

```csharp
// Add format validation before processing
if (!IsValidFormat(sourceDocument))
{
    throw new ArgumentException("Unsupported document format");
}
```

## Fazit

Das Beherrschen von **compare word documents** in .NET mit korrektem Ressourcenmanagement geht über das reine Funktionieren des Codes hinaus – es geht darum, Anwendungen zu erstellen, die unter realen Bedingungen zuverlässig arbeiten. In diesem Leitfaden haben Sie gelernt, wie Sie GroupDocs.Comparison für .NET implementieren und dabei eine hervorragende Ressourcenhygiene wahren.

Die wichtigsten Erkenntnisse: Verpacken Sie immer Disposable‑Objekte in `using`‑Statements, implementieren Sie korrekte Stream‑Release‑Methoden und überwachen Sie die Speichernutzung während der Entwicklung. Diese Praktiken sparen Ihnen unzählige Stunden Debugging und sorgen dafür, dass Ihre Nutzer ein reibungsloses Erlebnis haben.

Sind Sie bereit, diese Techniken in Ihrem eigenen Projekt umzusetzen? Beginnen Sie mit dem grundlegenden Vergleichs‑Workflow und fügen Sie nach und nach die Verbesserungen im Ressourcenmanagement hinzu. Ihr zukünftiges Ich (und Ihre Nutzer) werden Ihnen dankbar sein, dass Sie es richtig gemacht haben.

## Häufig gestellte Fragen

**Q: Ist GroupDocs.Comparison für .NET mit verschiedenen Dokumentformaten kompatibel?**  
A: Ja. GroupDocs.Comparison unterstützt über 50 Eingabe‑ und Ausgabeformate – darunter DOCX, PPTX, XLSX, PDF und viele Bildtypen – sodass Sie praktisch jedes Business‑Dokument ohne zusätzliche Konverter vergleichen können.

**Q: Kann ich das Ausgabeformat der verglichenen Dokumente anpassen?**  
A: Absolut. Sie können beim Speichern des Vergleichsergebnisses das gewünschte Ausgabeformat (z. B. DOCX, PDF, HTML) angeben, wodurch Sie die vollständige Kontrolle darüber haben, wie das zusammengeführte Dokument bereitgestellt wird.

**Q: Gibt es eine Testversion für Testzwecke?**  
A: Ja, Sie können alle Funktionen von GroupDocs.Comparison für .NET mit einer kostenlosen Testversion, die [hier](https://releases.groupdocs.com/) verfügbar ist, ausprobieren. Die Testversion ermöglicht es Ihnen, zu prüfen, ob die Bibliothek Ihren Anforderungen entspricht, bevor Sie kaufen.

**Q: Wie kann ich Unterstützung für Probleme oder Fragen zu GroupDocs.Comparison für .NET erhalten?**  
A: Sie können Unterstützung im GroupDocs.Comparison‑Community‑Forum [hier](https://forum.groupdocs.com/c/comparison/12) erhalten. Die Community ist aktiv, und das GroupDocs‑Team beteiligt sich regelmäßig, um technische Probleme zu lösen.

**Q: Wo kann ich eine Lizenz für GroupDocs.Comparison für .NET erwerben?**  
A: Sie können eine Lizenz über [diesen Link](https://purchase.groupdocs.com/buy) erwerben. Es stehen verschiedene Lizenzoptionen zur Verfügung, von Einzelentwickler‑ bis hin zu Unternehmens‑Deployments.

---

**Zuletzt aktualisiert:** 2026-07-14  
**Getestet mit:** GroupDocs.Comparison 5.6 für .NET  
**Autor:** GroupDocs

## Verwandte Tutorials

- [Wie man Dokumente mit GroupDocs.Comparison für .NET vergleicht](/comparison/net/basic-comparison/)
- [Dokumentvorschau‑Erstellung .NET – Seiten‑Thumbnails in C# erstellen](/comparison/net/document-comparison/generate-page-previews-source-document/)
- [Dokumentvergleich .NET‑Tutorial – Benutzerdefinierte Vorschau‑Bilder erzeugen](/comparison/net/document-comparison/set-specific-image-sizes-for-previews/)