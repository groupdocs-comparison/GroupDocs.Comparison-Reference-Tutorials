---
categories:
- Java Development
date: '2026-02-08'
description: Erfahren Sie, wie Sie eine PDF‑Vorschau in Java mit GroupDocs.Comparison
  erstellen. Schritt‑für‑Schritt‑Tutorial mit Codebeispielen für PDF-, Word‑ und Excel‑Vorschauen.
keywords: Java document preview generator, generate document thumbnails Java, Java
  PDF preview creation, document image conversion Java, Java library for document
  thumbnails
lastmod: '2025-01-02'
linktitle: Java Document Preview Generator
tags:
- document-processing
- java-library
- preview-generation
- pdf-thumbnails
title: PDF-Vorschau erstellen in Java – Java-Dokumentvorschau-Generator
type: docs
url: /de/java/preview-generation/groupdocs-comparison-java-generate-previews/
weight: 1
---

# PDF‑Vorschau in Java erstellen – Java Dokumenten‑Vorschau‑Generator

## Einführung

Müssen Sie Dokumentvorschauen in Ihrer Java‑Anwendung erzeugen? Egal, ob Sie ein Dokumenten‑Management‑System, einen Datei‑Browser oder ein Kollaborationstool bauen, das Erstellen visueller Vorschaubilder von Dokumenten ist für ein besseres Benutzererlebnis unerlässlich. In diesem Leitfaden erstellen Sie **create pdf preview java** Schritt für Schritt mit GroupDocs.Comparison und decken alles von der Umgebungseinrichtung bis zur Leistungsoptimierung ab.

### Schnelle Antworten
- **Welche Bibliothek kann ich verwenden, um PDF‑Vorschauen in Java zu erstellen?** GroupDocs.Comparison bietet eine einfache API für hochwertige Vorschauen.  
- **Welche Formate werden unterstützt?** Über 50 Formate, darunter PDF, DOCX, XLSX, PPTX und mehr.  
- **Wie erstelle ich eine Vorschau nur für die erste Seite?** Setzen Sie `previewOptions.setPageNumbers(new int[]{1})`.  
- **Kann ich die Vorschauerstellung asynchron ausführen?** Ja – verwenden Sie `ExecutorService` oder `CompletableFuture`.  
- **Welches Bildformat ist am besten für Thumbnails?** PNG bietet die beste Qualität; JPEG ist für die Web‑Nutzung kleiner.

## Was ist “create pdf preview java”?

Eine PDF‑Vorschau in Java zu erstellen bedeutet, jede Seite einer PDF (oder eines anderen Dokuments) in ein Bild zu konvertieren, das in Browsern oder mobilen Apps angezeigt werden kann. Dieser Vorgang wird häufig als **java convert document to image** bezeichnet und ermöglicht eine schnelle visuelle Indexierung, ohne das gesamte Dokument zu laden.

## Warum einen Java Dokumenten‑Vorschau‑Generator verwenden?

Bevor wir zum Code springen, sollten wir verstehen, warum die Generierung von Dokumentvorschauen für moderne Anwendungen entscheidend ist:

**Vorteile für die Benutzererfahrung**
- Benutzer können Dokumente schnell erkennen, ohne sie zu öffnen.
- Schnellere Navigation durch große Dokumentensammlungen.
- Visuelle Bestätigung vor dem Herunterladen oder Teilen von Dateien.

**Leistungs‑vorteile**
- Reduzierte Serverlast, indem das vollständige Rendern von Dokumenten vermieden wird.
- Bessere Caching‑Strategien mit leichtgewichtigen Vorschaubildern.
- Verbesserte mobile Erfahrung mit optimierten Thumbnails.

**Geschäftsanwendungen**
- Dokumenten‑Management‑Systeme mit visueller Durchsuchung.
- E‑Commerce‑Plattformen, die Produktkataloge anzeigen.
- Kollaborationstools mit Dokumenten‑Sharing‑Funktionen.

## Voraussetzungen und Umgebungseinrichtung

Bevor wir mit dem Bau unseres Java Dokumenten‑Vorschau‑Generators beginnen, stellen Sie sicher, dass Sie Folgendes haben:

**Erforderliche Software**
- **Java Development Kit (JDK)**: Version 8 oder höher (Java 11+ empfohlen für bessere Leistung)
- **Maven oder Gradle**: Für das Abhängigkeitsmanagement
- **IDE**: IntelliJ IDEA, Eclipse oder Ihre bevorzugte Java‑IDE

**Grundkenntnisse**
- Grundlagen der Java‑Programmierung
- Datei‑I/O‑Operationen
- Grundlegendes Verständnis von Bildverarbeitungs‑Konzepten

**Systemanforderungen**
- Mindestens 4 GB RAM (8 GB empfohlen für die Verarbeitung großer Dokumente)
- Ausreichend Festplattenspeicher für temporäre Vorschaudateien

## Einrichtung von GroupDocs.Comparison für Java

### Maven‑Installation und Konfiguration

Der erste Schritt beim Erstellen Ihres Java Dokumenten‑Vorschau‑Generators besteht darin, die GroupDocs.Comparison‑Abhängigkeit hinzuzufügen. Fügen Sie dies zu Ihrer `pom.xml` hinzu:

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

**Profi‑Tipp:** Verwenden Sie stets die neueste Version, um die neuesten Funktionen und Fehlerbehebungen zu erhalten. Prüfen Sie die [GroupDocs releases page](https://releases.groupdocs.com/comparison/java/) für Updates.

### Gradle‑Konfiguration (Alternative)

Wenn Sie Gradle verwenden, fügen Sie dies zu Ihrer `build.gradle` hinzu:

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/comparison/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

### Lizenz‑Einrichtungsoptionen

Sie haben mehrere Lizenzierungsoptionen für Ihren Dokumenten‑Vorschau‑Generator:

**1. Kostenlose Testversion** (Perfekt zum Testen):
- Download von der GroupDocs‑Website
- Beschränkt auf 3 Seiten pro Dokument
- Wasserzeichen im Ausgabe‑Bild

**2. Temporäre Lizenz** (Für die Entwicklung):
- Voller Funktionszugriff für 30 Tage
- Keine Wasserzeichen oder Seitenbeschränkungen
- Ideal für Proof‑of‑Concept‑Projekte

**3. Kommerzielle Lizenz** (Produktions‑Einsatz):
- Unbegrenzte Dokumente und Seiten
- Prioritäts‑Support inklusive
- Verschiedene Lizenzmodelle verfügbar

### Grundlegende Initialisierung

So initialisieren Sie Ihren Dokumenten‑Vorschau‑Generator:

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    // Your preview generation code goes here
}
```

**Wichtig:** Verwenden Sie stets try‑with‑resources, um eine ordnungsgemäße Ressourcen‑Bereinigung sicherzustellen und Speicherlecks zu vermeiden.

## Wie man pdf preview java erstellt – Schritt‑für‑Schritt‑Implementierung

### Verständnis des Vorschau‑Generierungsprozesses

Bevor Sie in den Code eintauchen, verstehen wir, wie die Generierung von Dokumentvorschauen funktioniert:

1. **Dokumenten‑Laden** – Laden Sie das Quell‑Dokument in den Speicher.  
2. **Seiten‑Verarbeitung** – Konvertieren Sie jede Dokumentenseite in ein Bild.  
3. **Stream‑Verwaltung** – Verwalten Sie Ausgabeströme für die erzeugten Bilder.  
4. **Konfiguration** – Wenden Sie Vorschau‑Optionen (Format, Qualität, Seiten) an.  
5. **Aufräumen** – Geben Sie Ressourcen und temporäre Dateien frei.

### Schritt 1: Vorschau‑Optionen konfigurieren

Die Grundlage Ihres Java Dokumenten‑Vorschau‑Generators ist die korrekte Konfiguration. So richten Sie die Vorschau‑Optionen ein:

```java
import com.groupdocs.comparison.options.PreviewOptions;
import java.io.FileOutputStream;

final Delegates.CreatePageStream createPageStream = pageNumber -> {
    String pagePath = "YOUR_OUTPUT_DIRECTORY/result-GetPagePreviewsForSourceDocument_" + pageNumber + ".png";
    try {
        return new FileOutputStream(pagePath);
    } catch (FileNotFoundException e) {
        e.printStackTrace();
        return null;
    }
};
```

**Was hier passiert:**
- Der `CreatePageStream`‑Delegate erstellt für jede Seite einen eindeutigen Ausgabestream.
- Die Dateinamen enthalten Seitenzahlen zur einfachen Identifizierung.
- Das PNG‑Format bietet gute Qualität bei angemessenen Dateigrößen.

### Schritt 2: Dokument‑Vorschauen erzeugen

Jetzt implementieren wir die Kernlogik zur Vorschauerzeugung:

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);
previewOptions.setPageNumbers(new int[]{1, 2, 3}); // Specify desired pages
comparer.getDocument().generatePreview(previewOptions);
```

**Wichtige Punkte**
- `setPageNumbers()` ermöglicht das Erzeugen von Vorschauen nur für bestimmte Seiten, was bei großen Dokumenten für die Leistung entscheidend ist.
- Lassen Sie den Aufruf weg, um Vorschauen für alle Seiten zu erzeugen.

### Erweiterte Konfigurationsoptionen

Für Produktionsanwendungen benötigen Sie mehr Kontrolle über die Erzeugung Ihrer Dokument‑Thumbnails:

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);

// Generate previews for first 5 pages only
previewOptions.setPageNumbers(new int[]{1, 2, 3, 4, 5});

// Set image dimensions (if supported by the format)
// Note: Specific dimension control depends on the output format

// Configure preview format
// PNG: Better quality, larger files
// JPEG: Smaller files, slight quality loss
```

## Häufige Implementierungs‑Herausforderungen und Lösungen

### Herausforderung 1: Speicherverwaltung bei großen Dokumenten

**Problem:** Große PDFs oder Dokumente mit vielen Seiten können einen `OutOfMemoryError` verursachen.

**Lösung:** Verarbeiten Sie Dokumente in Batches und implementieren Sie eine ordnungsgemäße Bereinigung:

```java
// Process in smaller batches
int batchSize = 5;
int totalPages = getTotalPages(document); // Your method to get page count

for (int i = 1; i <= totalPages; i += batchSize) {
    int endPage = Math.min(i + batchSize - 1, totalPages);
    
    // Generate previews for current batch
    int[] pageNumbers = IntStream.rangeClosed(i, endPage).toArray();
    previewOptions.setPageNumbers(pageNumbers);
    
    comparer.getDocument().generatePreview(previewOptions);
    
    // Optional: Force garbage collection between batches
    System.gc();
}
```

### Herausforderung 2: Dateipfad‑ und Verzeichnisverwaltung

**Problem:** Vorschaudateien sind über Verzeichnisse verteilt, Namenskonflikte.

**Lösung:** Implementieren Sie ein strukturiertes Dateimanagement‑System:

```java
public class PreviewFileManager {
    private final String baseDirectory;
    private final String documentId;
    
    public PreviewFileManager(String baseDirectory, String documentId) {
        this.baseDirectory = baseDirectory;
        this.documentId = documentId;
        
        // Create directory structure
        Path previewDir = Paths.get(baseDirectory, "previews", documentId);
        try {
            Files.createDirectories(previewDir);
        } catch (IOException e) {
            throw new RuntimeException("Failed to create preview directory", e);
        }
    }
    
    public String getPreviewPath(int pageNumber) {
        return Paths.get(baseDirectory, "previews", documentId, 
                        String.format("page_%03d.png", pageNumber)).toString();
    }
}
```

### Herausforderung 3: Umgang mit verschiedenen Dokumentformaten

**Problem:** Unterschiedliche Dokumenttypen erfordern unterschiedliche Verarbeitungsansätze.

**Lösung:** Erstellen Sie format‑spezifische Handler:

```java
public class DocumentPreviewGenerator {
    
    public void generatePreviews(String filePath) {
        String extension = getFileExtension(filePath).toLowerCase();
        
        switch (extension) {
            case "pdf":
                generatePdfPreviews(filePath);
                break;
            case "docx":
            case "doc":
                generateWordPreviews(filePath);
                break;
            case "xlsx":
            case "xls":
                generateExcelPreviews(filePath);
                break;
            default:
                generateGenericPreviews(filePath);
        }
    }
    
    private void generatePdfPreviews(String filePath) {
        // PDF-specific optimization
        try (Comparer comparer = new Comparer(filePath)) {
            // PDF documents often have many pages
            // Generate previews for first 10 pages only by default
            PreviewOptions options = createPreviewOptions();
            options.setPageNumbers(new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9, 10});
            comparer.getDocument().generatePreview(options);
        }
    }
}
```

## Leistungsoptimierungs‑Strategien

### CPU‑ und Speicheroptimierung

Beim Bau eines Java Dokumenten‑Vorschau‑Generators für die Produktion ist die Leistung entscheidend:

**1. Nebenläufige Verarbeitung**

```java
ExecutorService executor = Executors.newFixedThreadPool(4);

List<Future<Void>> futures = new ArrayList<>();
for (String documentPath : documentPaths) {
    futures.add(executor.submit(() -> {
        generatePreviewsForDocument(documentPath);
        return null;
    }));
}

// Wait for all tasks to complete
for (Future<Void> future : futures) {
    future.get();
}

executor.shutdown();
```

**2. Caching‑Strategie**

```java
public class PreviewCache {
    private final Map<String, List<String>> cache = new ConcurrentHashMap<>();
    
    public List<String> getPreviewPaths(String documentHash) {
        return cache.get(documentHash);
    }
    
    public void cachePreviewPaths(String documentHash, List<String> previewPaths) {
        cache.put(documentHash, previewPaths);
    }
}
```

### Balance zwischen Bildqualität und Dateigröße

Das richtige Gleichgewicht zwischen Bildqualität und Dateigröße zu finden, ist entscheidend:

- **Hohe Qualität (PNG)** – Ideal für technische Dokumente, Diagramme.  
- **Optimierte Größe (JPEG, 80‑85 % Qualität)** – Besser für Web‑Thumbnails.  
- Erwägen Sie, mehrere Größenvarianten (Thumbnail, Medium, Large) zu erzeugen, um verschiedene Geräte zu bedienen.

## Praktische Anwendungen und Anwendungsfälle

### Integration in Dokumenten‑Management‑Systeme

So integrieren Sie Ihren Java Dokumenten‑Vorschau‑Generator in ein Dokumenten‑Management‑System:

```java
@Service
public class DocumentService {
    
    @Autowired
    private PreviewGenerator previewGenerator;
    
    public DocumentPreview uploadDocument(MultipartFile file) {
        // Save document
        String documentPath = saveDocument(file);
        
        // Generate previews asynchronously
        CompletableFuture.runAsync(() -> {
            try {
                previewGenerator.generatePreviews(documentPath);
            } catch (Exception e) {
                log.error("Failed to generate previews for: " + documentPath, e);
            }
        });
        
        return new DocumentPreview(documentPath);
    }
}
```

### E‑Commerce‑Produktkatalog

Für E‑Commerce‑Plattformen, die Produktdokumente anzeigen:

```java
public class ProductDocumentHandler {
    
    public void processProductDocument(String productId, String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            // Generate thumbnail (first page only for product display)
            PreviewOptions thumbnailOptions = new PreviewOptions(pageNumber -> {
                String thumbnailPath = String.format("products/%s/thumbnail.png", productId);
                return createOutputStream(thumbnailPath);
            });
            thumbnailOptions.setPageNumbers(new int[]{1});
            
            comparer.getDocument().generatePreview(thumbnailOptions);
            
            // Generate detailed previews for product page
            PreviewOptions detailOptions = new PreviewOptions(pageNumber -> {
                String detailPath = String.format("products/%s/page_%d.png", productId, pageNumber);
                return createOutputStream(detailPath);
            });
            
            comparer.getDocument().generatePreview(detailOptions);
        }
    }
}
```

## Best Practices für den Produktionseinsatz

### Fehlerbehandlung und Protokollierung

Implementieren Sie eine umfassende Fehlerbehandlung für Ihren Dokumenten‑Vorschau‑Generator:

```java
public class RobustPreviewGenerator {
    private static final Logger logger = LoggerFactory.getLogger(RobustPreviewGenerator.class);
    
    public boolean generatePreview(String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            logger.info("Starting preview generation for: {}", documentPath);
            
            PreviewOptions options = createPreviewOptions();
            comparer.getDocument().generatePreview(options);
            
            logger.info("Successfully generated previews for: {}", documentPath);
            return true;
            
        } catch (Exception e) {
            logger.error("Failed to generate previews for: " + documentPath, e);
            return false;
        }
    }
}
```

### Ressourcen‑Management

Implementieren Sie stets eine ordnungsgemäße Ressourcen‑Bereinigung:

```java
public class ResourceManagedPreviewGenerator implements AutoCloseable {
    private final ExecutorService executor;
    private final PreviewCache cache;
    
    public ResourceManagedPreviewGenerator() {
        this.executor = Executors.newFixedThreadPool(4);
        this.cache = new PreviewCache();
    }
    
    @Override
    public void close() {
        executor.shutdown();
        try {
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                executor.shutdownNow();
            }
        } catch (InterruptedException e) {
            executor.shutdownNow();
            Thread.currentThread().interrupt();
        }
        
        cache.clear();
    }
}
```

## Fehlersuche bei häufigen Problemen

### Problem 1: “Could not load document” Fehler

**Symptome:** Ausnahme beim Versuch, bestimmte Dokumenttypen zu laden.

**Lösungen**
1. Stellen Sie sicher, dass das Dokument nicht beschädigt ist.  
2. Prüfen Sie, ob das Dateiformat unterstützt wird.  
3. Stellen Sie sicher, dass die Dateiberechtigungen korrekt sind.  
4. Validieren Sie, dass der Dateipfad existiert.

```java
private boolean isDocumentValid(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        logger.error("Document file does not exist: {}", filePath);
        return false;
    }
    
    if (!file.canRead()) {
        logger.error("Cannot read document file: {}", filePath);
        return false;
    }
    
    return true;
}
```

### Problem 2: Schlechte Vorschau‑Qualität

**Symptome:** Generierte Vorschauen sind unscharf oder pixelig.

**Lösungen**
- Überprüfen Sie die Qualität des Quell‑Dokuments.  
- Passen Sie die Ausgabeformat‑Einstellungen an (verwenden Sie PNG für verlustfreie Qualität).  
- Stellen Sie während der Konvertierung ausreichende Systemressourcen sicher.

### Problem 3: Langsame Vorschau‑Erstellung

**Symptome:** Die Vorschauerstellung dauert bei großen Dokumenten zu lange.

**Lösungen**
- Implementieren Sie Seitenbeschränkungen für anfängliche Vorschauen.  
- Verwenden Sie asynchrone Verarbeitung (siehe das `ExecutorService`‑Beispiel).  
- Fügen Sie Fortschrittsanzeiger für Benutzer‑Feedback hinzu.  
- Cache häufig aufgerufene Vorschauen.

## Alternativen zu GroupDocs.Comparison

Obwohl GroupDocs.Comparison hervorragend für die Generierung von Dokumentvorschauen ist, könnten Sie Alternativen in Betracht ziehen:

- **Apache PDFBox** (nur PDF, Open‑Source)  
- **iText** (kommerziell, umfangreiche PDF‑Funktionen)  
- **ImageIO mit Office‑Bibliotheken** (Mehr Kontrolle, höhere Setup‑Komplexität)

## Fazit

Sie haben nun gelernt, wie man **create pdf preview java** mit GroupDocs.Comparison erstellt. Diese Lösung bietet:

- Unterstützung für mehrere Dokumentformate (PDF, Word, Excel, PowerPoint)  
- Hochwertige Vorschauerstellung mit konfigurierbaren Optionen  
- Produktions‑bereite Fehlerbehandlung und Ressourcen‑Management  
- Skalierbare Architektur, geeignet für Unternehmensanwendungen  

### Nächste Schritte

- **Caching implementieren** – Fügen Sie Redis oder dateibasiertes Caching für häufig aufgerufene Vorschauen hinzu.  
- **Fortschrittsverfolgung hinzufügen** – Zeigen Sie Benutzern den Fortschritt der Vorschauerstellung für große Dokumente.  
- **Für Mobile optimieren** – Erstellen Sie responsive Vorschau‑Displays für mobile Anwendungen.  
- **Leistung überwachen** – Fügen Sie Metriken und Monitoring hinzu, um die Systemleistung zu verfolgen.

Bereit, die Dokument‑Vorschau‑Erstellung in Ihrer Java‑Anwendung zu implementieren? Beginnen Sie mit einem kleinen Proof‑of‑Concept und erweitern Sie die Funktionalität schrittweise basierend auf Ihren spezifischen Anforderungen.

## Häufig gestellte Fragen

**F1:** Welche Dokumentformate unterstützt dieser Java Dokumenten‑Vorschau‑Generator?  
**A:** GroupDocs.Comparison unterstützt über 50 Dokumentformate, darunter PDF, DOCX, XLSX, PPTX, TXT, HTML und viele weitere. Siehe die [documentation](https://docs.groupdocs.com/comparison/java/) für eine vollständige Liste.

**F2:** Wie erstelle ich Dokument‑Thumbnails nur für die erste Seite?  
**A:** Verwenden Sie `previewOptions.setPageNumbers(new int[]{1})`, um nur die erste Seite zu rendern. Dies ist ideal für Thumbnail‑Erstellung in Dokumenten‑Browsers.

**F3:** Kann ich das Ausgabe‑Bildformat und die Qualität anpassen?  
**A:** Ja, Sie können das Ausgabeformat über den `CreatePageStream`‑Delegate konfigurieren. Die Bibliothek unterstützt hauptsächlich das PNG‑Format, das exzellente Qualität für Dokumentvorschauen liefert.

**F4:** Wie gehe ich mit sehr großen PDF‑Dateien um, ohne dass der Speicher ausgeht?  
**A:** Verarbeiten Sie große Dokumente in Batches, implementieren Sie eine ordnungsgemäße Ressourcen‑Bereinigung mit try‑with‑resources und erwägen Sie, die JVM‑Heap‑Größe über den Parameter `-Xmx` zu erhöhen.

**F5:** Gibt es eine Möglichkeit, Vorschauen asynchron zu erzeugen?  
**A:** Absolut! Verwenden Sie `CompletableFuture.runAsync()` oder `ExecutorService`, um Vorschauen in Hintergrund‑Threads zu erzeugen. Das verhindert das Blockieren des Haupt‑Anwendungsthreads.

**F6:** Wie behebe ich den Fehler “License not found”?  
**A:** Stellen Sie sicher, dass Ihre Lizenzdatei im Klassenpfad liegt, prüfen Sie, ob die Lizenz nicht abgelaufen ist, und vergewissern Sie sich, dass Sie den korrekten Lizenztyp für Ihre GroupDocs.Comparison‑Version verwenden.

**Zusätzliche Ressourcen**

- **Dokumentation:** [GroupDocs.Comparison Java Documentation](https://docs.groupdocs.com/comparison/java/)  
- **API‑Referenz:** [Complete API Reference](https://reference.groupdocs.com/comparison/java/)  
- **Neueste Version herunterladen:** [GroupDocs.Comparison Downloads](https://releases.groupdocs.com/comparison/java/)  
- **Lizenz kaufen:** [Buy GroupDocs.Comparison License](https://purchase.groupdocs.com/buy)  
- **Kostenlos testen:** [Download Free Trial](https://releases.groupdocs.com/comparison/java/)  
- **Support erhalten:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison)  
- **Temporäre Lizenz:** [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Zuletzt aktualisiert:** 2026-02-08  
**Getestet mit:** GroupDocs.Comparison 25.2  
**Autor:** GroupDocs  

---  
