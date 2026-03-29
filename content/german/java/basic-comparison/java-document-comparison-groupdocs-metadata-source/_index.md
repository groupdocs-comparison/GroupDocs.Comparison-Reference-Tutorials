---
categories:
- Java Development
date: '2026-02-23'
description: Lernen Sie, wie Sie Dokumente in Java mit der GroupDocs.Comparison‑API
  vergleichen, einschließlich des Vergleichs mehrerer Dateien und passwortgeschützter
  Dokumente. Schritt‑für‑Schritt‑Anleitung mit Code, bewährten Methoden und Fehlersuche.
keywords: Java document comparison tutorial, GroupDocs Java API guide, compare documents
  in java, java compare multiple files, java compare password protected, Java file
  comparison library, how to compare Word documents in Java
lastmod: '2026-02-23'
linktitle: Java Document Comparison Tutorial
tags:
- document-comparison
- groupdocs
- java-tutorial
- api-integration
title: Dokumente in Java vergleichen – vollständiger Leitfaden zur GroupDocs‑API
type: docs
url: /de/java/basic-comparison/java-document-comparison-groupdocs-metadata-source/
weight: 1
---

compare documents in java" could become "Dokumente in Java vergleichen". Let's do that.

Proceed.

I'll rewrite each paragraph.

Be careful with bold **...** keep formatting.

Also bullet lists.

Also code block placeholders remain unchanged.

Also markdown links keep same.

Let's produce final content.

# Dokumente in Java vergleichen – GroupDocs API Vollständiger Leitfaden

## Einführung

Haben Sie schon einmal versucht, zwei Dokumente Zeile für Zeile manuell zu vergleichen und dabei kritische Unterschiede übersehen? Sie sind definitiv nicht allein. **Dokumente in Java vergleichen** ist eine häufige Herausforderung, besonders wenn Sie Metadaten erhalten, passwortgeschützte Dateien verarbeiten oder viele Dateien gleichzeitig vergleichen müssen.

**Der springende Punkt**: Die meisten Entwickler kämpfen damit, weil sie entweder etwas von Grund auf neu bauen (was ewig dauert) oder einfache Diff‑Tools verwenden, die Formatierung, Metadaten und Sicherheitseinstellungen ignorieren. Genau hier kommt **GroupDocs.Comparison for Java** ins Spiel.

In diesem umfassenden Tutorial erfahren Sie, wie Sie robuste Dokumentvergleiche in Ihren Java‑Anwendungen implementieren. Wir decken alles ab – von der Grundkonfiguration bis hin zur erweiterten Metadatenverarbeitung, plus praxisnahe Beispiele, die Sie tatsächlich in der Produktion einsetzen können. Am Ende wissen Sie, wie Sie:

- GroupDocs.Comparison in Ihrem Java‑Projekt einrichten (es ist einfacher als Sie denken)  
- **Dokumente in Java vergleichen** und dabei die Integrität der Metadaten bewahren  
- Szenarien wie **java compare multiple files** und **java compare password protected** handhaben  
- Die Leistung für die Verarbeitung großer Dokumentenmengen optimieren  

Bereit, den Dokumentvergleich in Ihren Java‑Apps zum Kinderspiel zu machen? Dann legen wir los!

## Schnelle Antworten
- **Welche Bibliothek ermöglicht mir, Dokumente in Java zu vergleichen?** GroupDocs.Comparison for Java  
- **Kann ich mehrere Dateien gleichzeitig vergleichen?** Ja – fügen Sie so viele Zieldokumente hinzu, wie Sie benötigen  
- **Wie gehe ich mit passwortgeschützten Dokumenten um?** Verwenden Sie `LoadOptions` mit dem Dokumenten‑Passwort  
- **Benötige ich eine Lizenz für die Produktion?** Eine gültige GroupDocs‑Lizenz entfernt Wasserzeichen und Beschränkungen  
- **Welche Java‑Version wird benötigt?** JDK 8+, JDK 11+ empfohlen  

## Was ist **Dokumente in Java vergleichen**?
Dokumente in Java zu vergleichen bedeutet, programmatisch Unterschiede – Textänderungen, Formatierungsänderungen oder Metadaten‑Updates – zwischen zwei oder mehr Dateien zu erkennen, wobei eine Bibliothek verwendet wird, die die Dokumentstruktur versteht. GroupDocs.Comparison abstrahiert die Komplexität und bietet Ihnen eine einfache API, um ein Diff‑Dokument zu erzeugen, das jede Änderung hervorhebt.

## Warum GroupDocs.Comparison for Java verwenden?
- **Umfangreiche Formatunterstützung** – DOCX, PDF, XLSX, PPTX, TXT und mehr  
- **Metadaten‑Handling** – Quelle, Ziel oder keine Metadaten für das Ergebnis wählen  
- **Passwortunterstützung** – geschützte Dateien öffnen, ohne manuell zu entschlüsseln  
- **Skalierbare Leistung** – Batch‑Verarbeitung, asynchrone Ausführung und speichereffizientes Design  

## Voraussetzungen

- **Java‑Umgebung:** JDK 8+ (JDK 11+ empfohlen), IDE Ihrer Wahl, Maven (oder Gradle)  
- **GroupDocs.Comparison‑Bibliothek:** Version 25.2 oder höher (immer die neueste Version verwenden)  
- **Lizenz:** Kostenlose Testversion, temporäre 30‑Tage‑Lizenz oder kommerzielle Lizenz  

## GroupDocs.Comparison in Ihrem Projekt einrichten

### Maven‑Konfiguration

Zuerst fügen Sie das GroupDocs‑Repository und die Abhängigkeit zu Ihrer `pom.xml` hinzu. Das ist dort, wo die meisten Tutorials unnötig kompliziert werden, aber es ist eigentlich ziemlich einfach:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Pro‑Tipp:** Prüfen Sie immer die aktuelle Versionsnummer auf der [GroupDocs releases page](https://releases.groupdocs.com/comparison/java/). Neue Versionen enthalten häufig Leistungsverbesserungen und Fehlerbehebungen, die Ihnen Kopfschmerzen ersparen.

### Lizenz einrichten

Hier ist, was die meisten Entwickler nicht realisieren: Sie können GroupDocs.Comparison sofort mit der kostenlosen Testversion testen. Keine Kreditkarte nötig, keine versteckten Bedingungen.

**Ihre Optionen:**
1. **Kostenlose Testversion** – perfekt zum Testen und für kleine Projekte. Einfach herunterladen und loslegen!  
2. **Temporäre Lizenz** – benötigen Sie mehr Zeit für die Evaluierung? Holen Sie sich eine 30‑Tage‑temporäre Lizenz [hier](https://purchase.groupdocs.com/temporary-license/)  
3. **Kommerzielle Lizenz** – bereit für die Produktion? Preise finden Sie [hier](https://purchase.groupdocs.com/buy)

Die kostenlose Testversion enthält alle Funktionen, fügt jedoch ein Wasserzeichen zu Ausgabedateien hinzu. Für Entwicklung und Tests ist das in der Regel in Ordnung.

## Implementierung des Dokumentvergleichs: Der komplette Leitfaden

Jetzt zum Hauptteil! Wir bauen Schritt für Schritt eine vollständige Dokumentvergleichslösung. Keine Sorge – wir erklären nicht nur das „Wie“, sondern auch das „Warum“ hinter jeder Entscheidung.

### Verständnis der Metadaten‑Quellen (Das ist wichtig!)

Bevor wir mit dem Coden beginnen, sprechen wir über etwas, das vielen Entwicklern Kopfzerbrechen bereitet: Metadaten‑Quellen. Wenn Sie **Dokumente in Java vergleichen**, müssen Sie entscheiden, welche Metadaten (Autor, Erstellungsdatum, benutzerdefinierte Eigenschaften usw.) im Ergebnis erhalten bleiben sollen.

GroupDocs.Comparison bietet Ihnen drei Optionen:
- **SOURCE** – Metadaten aus dem Originaldokument verwenden  
- **TARGET** – Metadaten aus dem zu vergleichenden Dokument verwenden  
- **NONE** – alle Metadaten aus dem Ergebnis entfernen  

Für die meisten geschäftlichen Anwendungen möchten Sie **SOURCE** verwenden, um Konsistenz zu gewährleisten.

### Schritt‑für‑Schritt‑Implementierung

Wir erstellen ein wiederverwendbares Utility, das Sie in jedes Projekt einbinden können.

#### Schritt 1: Erforderliche Klassen importieren

```java
import com.groupdocs.comparison.Comparer;
import com.groupdocs.comparison.options.enums.MetadataType;
import com.groupdocs.comparison.options.save.SaveOptions;
import java.nio.file.Path;
import java.io.IOException;
```

#### Schritt 2: Comparer‑Instanz erstellen

Hier beginnt die Magie. Die Klasse `Comparer` ist Ihr Haupteinstiegspunkt für alle Vergleichsvorgänge:

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source.docx")) {
    // All our comparison logic goes here
}
```

**Warum try‑with‑resources verwenden?** Die Klasse `Comparer` implementiert `AutoCloseable`, was bedeutet, dass sie Ressourcen korrekt freigibt, wenn Sie fertig sind. Das verhindert Speicherlecks – besonders wichtig bei der Verarbeitung vieler Dokumente.

#### Schritt 3: Zieldokumente zum Vergleich hinzufügen

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
```

**Ein cooler Trick:** Sie können tatsächlich mehrere Zieldokumente hinzufügen und alle gegen Ihr Quell‑Dokument in einem Vorgang vergleichen. Rufen Sie einfach `add()` mehrfach auf:

```java
comparer.add("YOUR_DOCUMENT_DIRECTORY/target1.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target2.docx");
comparer.add("YOUR_DOCUMENT_DIRECTORY/target3.docx");
```

#### Schritt 4: Metadaten‑Handling konfigurieren und Vergleich ausführen

Hier legen wir die Metadaten‑Quelle fest und starten den eigentlichen Vergleich:

```java
final Path resultPath = comparer.compare("output/comparison_result.docx",
        new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
```

**Was passiert hier?** Wir sagen GroupDocs, dass es:
1. Alle hinzugefügten Dokumente gegen das Quell‑Dokument vergleichen soll  
2. Das Ergebnis an dem von uns angegebenen Pfad speichern soll  
3. Die Metadaten des **SOURCE**‑Dokuments im finalen Ergebnis verwenden soll  

### Vollständiges funktionierendes Beispiel

Fassen wir alles in einer Methode zusammen, die Sie direkt verwenden können:

```java
public class DocumentComparison {
    
    public static Path compareDocumentsWithMetadata(
            String sourcePath, 
            String targetPath, 
            String outputPath) throws IOException {
        
        try (Comparer comparer = new Comparer(sourcePath)) {
            // Add the target document
            comparer.add(targetPath);
            
            // Configure comparison options
            SaveOptions saveOptions = new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build();
            
            // Execute comparison and return result path
            return comparer.compare(outputPath, saveOptions);
        }
    }
}
```

## Häufige Stolperfallen und wie man sie vermeidet

Nachdem ich hunderten Entwicklern beim Implementieren von Dokumentvergleichen geholfen habe, sehe ich immer wieder dieselben Probleme. Hier die wichtigsten (und wie Sie sie beheben):

### Probleme mit Dateipfaden

**Problem**: `FileNotFoundException`, obwohl die Datei existiert  
**Lösung**: Immer absolute Pfade verwenden oder relative Pfade korrekt auflösen

```java
// Instead of this:
String sourcePath = "documents/source.docx";

// Do this:
String sourcePath = Paths.get("documents", "source.docx").toAbsolutePath().toString();
```

### Speicherverwaltungs‑Probleme

**Problem**: Out‑of‑Memory‑Fehler beim Vergleich großer Dokumente  
**Lösung**: JVM‑Heap‑Größe erhöhen und Ressourcen korrekt verwalten

```bash
# Add these JVM arguments when running your application
-Xmx4g -XX:+UseG1GC
```

### Falsches Metadaten‑Handling

**Problem**: Wichtige Dokumentmetadaten gehen beim Vergleich verloren  
**Lösung**: Immer explizit den Metadaten‑Typ setzen – nicht auf Standardwerte vertrauen

```java
// Always be explicit about metadata handling
SaveOptions saveOptions = new SaveOptions.Builder()
        .setCloneMetadataType(MetadataType.SOURCE)  // Be explicit!
        .build();
```

### Lizenz‑Konfigurations‑Probleme

**Problem**: Wasserzeichen erscheinen in der Produktion  
**Lösung**: Sicherstellen, dass Ihre Lizenz korrekt geladen ist, bevor `Comparer`‑Instanzen erstellt werden

```java
// Load license at application startup
License license = new License();
license.setLicense("path/to/your/license.lic");
```

## Best Practices für den Produktionseinsatz

Basierend auf realen Erfahrungen sind dies die Praktiken, die Amateur‑Implementierungen von produktions‑reifen Lösungen unterscheiden:

### Fehlerbehandlung, die wirklich hilft

Nicht nur Ausnahmen abfangen – sie sinnvoll verarbeiten:

```java
public ComparisonResult compareDocuments(String source, String target) {
    try (Comparer comparer = new Comparer(source)) {
        comparer.add(target);
        Path result = comparer.compare("output.docx", 
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        
        return new ComparisonResult(true, result.toString(), null);
        
    } catch (IOException e) {
        logger.error("File access error during comparison", e);
        return new ComparisonResult(false, null, "Unable to access document files");
        
    } catch (Exception e) {
        logger.error("Unexpected error during document comparison", e);
        return new ComparisonResult(false, null, "Document comparison failed");
    }
}
```

### Leistungsoptimierung

Für Szenarien mit hohem Volumen sollten Sie folgende Optimierungen in Betracht ziehen:

1. **`Comparer`‑Instanzen wiederverwenden**, wenn möglich (aber auf Thread‑Safety achten)  
2. **Dokumente in Batches verarbeiten**, um Systemressourcen nicht zu überlasten  
3. **Asynchrone Verarbeitung** für große Dokumente nutzen  
4. **Speichernutzung überwachen** und JVM‑Einstellungen entsprechend anpassen  

### Sicherheitsaspekte

Beim Umgang mit sensiblen Dokumenten:

- **Dateitypen validieren** bevor sie verarbeitet werden  
- **Zugriffskontrollen implementieren**  
- **Temporäre Dateien sofort löschen** nach Gebrauch  
- **Ergebnisse verschlüsseln** in Betracht ziehen  

## Praxisbeispiele und Anwendungsfälle

Schauen wir uns an, wie Entwickler GroupDocs.Comparison tatsächlich in der Produktion einsetzen:

### Juristische Dokumentenprüfung

Anwaltskanzleien nutzen den Dokumentvergleich, um Änderungen in Verträgen und Rechtsvereinbarungen nachzuverfolgen. Die Metadaten‑Erhaltungs‑Funktion ist hier entscheidend, weil die Dokumenten‑Provenienz erhalten bleiben muss.

```java
// Typical legal document comparison workflow
public void reviewContractChanges(String originalContract, String revisedContract) {
    try (Comparer comparer = new Comparer(originalContract)) {
        comparer.add(revisedContract);
        
        SaveOptions options = new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)  // Preserve original metadata
                .build();
        
        Path result = comparer.compare("contract_review.docx", options);
        
        // Send result to legal team for review
        notifyLegalTeam(result);
    }
}
```

### Content‑Management‑Systeme

CMS‑Plattformen verwenden den Dokumentvergleich für Versionskontrolle und Änderungsverfolgung:

```java
public class CMSDocumentVersioning {
    
    public VersionComparisonResult compareVersions(
            DocumentVersion current, 
            DocumentVersion previous) {
        
        try (Comparer comparer = new Comparer(current.getFilePath())) {
            comparer.add(previous.getFilePath());
            
            String outputName = String.format("comparison_%s_vs_%s.docx", 
                current.getVersionNumber(), 
                previous.getVersionNumber());
            
            Path result = comparer.compare(outputName, 
                new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build());
            
            return new VersionComparisonResult(result, current, previous);
        }
    }
}
```

### Finanzdokumentenanalyse

Finanzinstitute nutzen dies für regulatorische Konformität und Prüfpfade:

```java
public AuditResult auditFinancialDocument(String originalReport, String submittedReport) {
    // Compare submitted report against original
    // Metadata preservation is critical for audit compliance
    try (Comparer comparer = new Comparer(originalReport)) {
        comparer.add(submittedReport);
        
        Path auditResult = comparer.compare("audit_comparison.docx",
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        
        return generateAuditReport(auditResult);
    }
}
```

## Leistungsoptimierung und Skalierung

Wenn Sie ernsthafte Dokumentvolumina verarbeiten wollen, halten diese Strategien Ihre Anwendung reaktionsfähig:

### Speicherverwaltung

Große Dokumente können schnell den verfügbaren Speicher verbrauchen. So gehen Sie effizient damit um:

```java
public class OptimizedDocumentProcessor {
    
    private final ExecutorService executor = Executors.newFixedThreadPool(
        Runtime.getRuntime().availableProcessors());
    
    public CompletableFuture<Path> compareDocumentsAsync(
            String source, 
            String target, 
            String output) {
        
        return CompletableFuture.supplyAsync(() -> {
            try (Comparer comparer = new Comparer(source)) {
                comparer.add(target);
                return comparer.compare(output, 
                    new SaveOptions.Builder()
                        .setCloneMetadataType(MetadataType.SOURCE)
                        .build());
            }
        }, executor);
    }
}
```

### Batch‑Verarbeitung

Für mehrere Dokumentvergleiche ist Batch‑Verarbeitung Ihr Freund:

```java
public List<ComparisonResult> processBatch(List<DocumentPair> documentPairs) {
    return documentPairs.parallelStream()
        .map(this::compareDocumentPair)
        .collect(Collectors.toList());
}

private ComparisonResult compareDocumentPair(DocumentPair pair) {
    try (Comparer comparer = new Comparer(pair.getSourcePath())) {
        comparer.add(pair.getTargetPath());
        Path result = comparer.compare(pair.getOutputPath(),
            new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.SOURCE)
                .build());
        return new ComparisonResult(pair, result, true);
    } catch (Exception e) {
        return new ComparisonResult(pair, null, false, e.getMessage());
    }
}
```

## Fehlersuch‑Leitfaden

Wenn etwas schiefgeht (und das passiert manchmal), ist hier Ihre Debug‑Checkliste:

### „Comparison Failed“-Fehler

**Häufigste Ursachen:**
1. Nicht unterstütztes Dateiformat  
2. Beschädigte Quelldokumente  
3. Unzureichender Speicher  
4. Dateiberechtigungs‑Probleme  

**Debug‑Schritte:**

```java
// Add comprehensive logging to identify the issue
logger.debug("Starting comparison: source={}, target={}", sourcePath, targetPath);

try (Comparer comparer = new Comparer(sourcePath)) {
    logger.debug("Comparer initialized successfully");
    
    comparer.add(targetPath);
    logger.debug("Target document added successfully");
    
    Path result = comparer.compare(outputPath, saveOptions);
    logger.info("Comparison completed successfully: result={}", result);
    
    return result;
} catch (Exception e) {
    logger.error("Comparison failed", e);
    throw new DocumentComparisonException("Failed to compare documents", e);
}
```

### Leistungsprobleme

Wenn Vergleiche zu lange dauern:

1. **Dokumentgröße prüfen** – Dateien über 100 MB benötigen ggf. Sonderbehandlung  
2. **Speichernutzung überwachen** – Heap‑Größe bei Bedarf erhöhen  
3. **Datei‑I/O‑Leistung prüfen** – langsamer Speicher kann zum Engpass werden  
4. **Dateiformat berücksichtigen** – manche Formate sind komplexer zu verarbeiten  

### Speicherlecks

Anzeichen für mögliche Speicherlecks:

- Anwendungsleistung verschlechtert sich über die Zeit  
- `OutOfMemoryError` nach Verarbeitung vieler Dokumente  
- Hohe Garbage‑Collection‑Aktivität  

**Lösung**: Immer try‑with‑resources verwenden und die Anwendung mit Profiling‑Tools überwachen.

## Umgang mit passwortgeschützten Dateien

Wenn Sie **java compare password protected** Dokumente benötigen, verwenden Sie `LoadOptions` beim Öffnen von Quelle oder Ziel:

```java
LoadOptions loadOptions = new LoadOptions("your_password");
try (Comparer comparer = new Comparer("protected_document.docx", loadOptions)) {
    // Process password‑protected document
}
```

## Wie man passwortgeschützte Dokumente in Java vergleicht

Passwortgeschützte Dateien sind in regulierten Branchen üblich. Durch das Übergeben des Passworts über `LoadOptions` bleibt der Vergleichs‑Workflow unverändert, während die Bibliothek die Datei sicher entschlüsseln kann. Denken Sie daran, Passwörter niemals hard‑codiert zu speichern; nutzen Sie einen sicheren Tresor oder Umgebungsvariablen und injizieren Sie sie zur Laufzeit.

## Wie man große Dokumente in Java verarbeitet

Wenn Dokumente mehrere hundert Megabyte überschreiten, können Sie auf langsamere Verarbeitung oder höheren Speicherverbrauch stoßen. So mildern Sie das:

- **JVM‑Heap erhöhen** (`-Xmx`), besonders für Batch‑Jobs.  
- **Streaming aktivieren**, wo möglich – GroupDocs.Comparison verarbeitet Dateien intern in Chunks, Sie können den Speicherdruck weiter reduzieren, indem Sie vermeiden, ganze Dateien selbst zu laden.  
- **Vergleiche asynchron ausführen** (siehe das Async‑Beispiel weiter oben), um die UI reaktionsfähig zu halten.  
- **Sehr große PDFs in logische Abschnitte aufteilen**, falls die Geschäftslogik das zulässt.  

## Integration mit Spring Boot

Für Entwickler, die Microservices bauen, verpacken Sie die Vergleichslogik in einen Spring‑Service‑Bean:

```java
@Service
public class DocumentComparisonService {
    
    public ComparisonResult compareDocuments(String source, String target) {
        try (Comparer comparer = new Comparer(source)) {
            comparer.add(target);
            Path result = comparer.compare("output.docx",
                new SaveOptions.Builder()
                    .setCloneMetadataType(MetadataType.SOURCE)
                    .build());
            return new ComparisonResult(result);
        }
    }
}
```

## Häufig gestellte Fragen

**F: Kann ich mehr als zwei Dokumente gleichzeitig vergleichen?**  
A: Absolut! Fügen Sie mehrere Zieldokumente mit `comparer.add()` hinzu, bevor Sie den Vergleich ausführen.

**F: Welche Dateiformate unterstützt GroupDocs.Comparison?**  
A: Es unterstützt DOCX, PDF, XLSX, PPTX, TXT und viele weitere. Die vollständige Liste finden Sie in der offiziellen Dokumentation.

**F: Wie gehe ich mit passwortgeschützten Dokumenten um?**  
A: Verwenden Sie die Klasse `LoadOptions`, um das Passwort beim Erstellen der `Comparer`‑Instanz zu übergeben (siehe das Beispiel oben).

**F: Ist GroupDocs.Comparison thread‑sicher?**  
A: Eine einzelne `Comparer`‑Instanz ist nicht thread‑sicher, aber Sie können mehrere Instanzen in parallelen Threads sicher verwenden.

**F: Wie kann ich die Leistung für große Dokumente verbessern?**  
A: JVM‑Heap erhöhen (`-Xmx`), Dateien asynchron verarbeiten, stapelweise verarbeiten und `Comparer`‑Objekte wiederverwenden, wenn sinnvoll.

## Weitere Ressourcen

- [GroupDocs.Comparison Documentation](https://docs.groupdocs.com/comparison/java/) – umfassende API‑Referenz und Beispiele  
- [GroupDocs Community Forum](https://forum.groupdocs.com/) – Hilfe von anderen Entwicklern erhalten  

---

**Zuletzt aktualisiert:** 2026-02-23  
**Getestet mit:** GroupDocs.Comparison 25.2  
**Autor:** GroupDocs  

---