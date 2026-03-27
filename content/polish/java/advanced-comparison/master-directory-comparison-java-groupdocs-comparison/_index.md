---
categories:
- Java Development
date: '2026-03-22'
description: Dowiedz się, jak używać GroupDocs Comparison Java do porównywania katalogów
  w Javie. Opanuj audyty plików, automatyzację kontroli wersji i optymalizację wydajności.
keywords: java directory comparison tool, groupdocs comparison tutorial, java file
  audit automation, directory sync java, how to compare folders in java programming
lastmod: '2026-03-22'
linktitle: Java Directory Comparison Guide
tags:
- directory-comparison
- file-audits
- groupdocs
- java-tutorial
title: groupdocs comparison java - Narzędzie do porównywania katalogów w Javie - Kompletny
  przewodnik
type: docs
url: /pl/java/advanced-comparison/master-directory-comparison-java-groupdocs-comparison/
weight: 1
---

# Narzędzie do Porównywania Katalogów w Javie – Kompletny Przewodnik z GroupDocs.Comparison

## Wprowadzenie

Spędziłeś godziny, ręcznie sprawdzając, które pliki zmieniły się między dwoma wersjami projektu? Nie jesteś sam. **groupdocs comparison java** upraszcza to żmudne zadanie, pozwalając porównać dwa foldery jednym wywołaniem API. Porównywanie katalogów to jedno z tych monotonnych zadań, które może pochłonąć cały popołudnie — chyba że je zautomatyzujesz.

**GroupDocs.Comparison for Java** przekształca ten problem w proste wywołanie API. Niezależnie od tego, czy śledzisz zmiany w ogromnej bazie kodu, synchronizujesz pliki między środowiskami, czy przeprowadzasz audyty zgodności, ta biblioteka zajmuje się ciężką pracą, abyś nie musiał.

W tym przewodniku dowiesz się, jak skonfigurować automatyczne porównywanie katalogów, które naprawdę działa w rzeczywistych scenariuszach. Omówimy wszystko – od podstawowej konfiguracji po optymalizację wydajności dla tych potężnych katalogów zawierających tysiące plików.

**Co opanujesz:**
- Pełną konfigurację GroupDocs.Comparison (wraz z pułapkami)
- Krok po kroku implementację porównywania katalogów
- Zaawansowaną konfigurację własnych reguł porównywania
- Optymalizację wydajności dla porównań na dużą skalę  
- Rozwiązywanie typowych problemów (bo się zdarzą)
- Przykłady zastosowań w rzeczywistych branżach

### Szybkie odpowiedzi
- **Jaka jest główna biblioteka?** `groupdocs comparison java`
- **Obsługiwana wersja Javy?** Java 8 lub wyższa
- **Typowy czas konfiguracji?** 10–15 minut dla podstawowego porównania
- **Wymaganie licencyjne?** Tak – potrzebna jest licencja trial lub komercyjna
- **Formaty wyjściowe?** HTML (domyślnie) lub PDF

## Dlaczego Porównywanie Katalogów ma Znaczenie (Więcej niż Myślisz)

Zanim przejdziemy do kodu, porozmawiajmy o tym, dlaczego to ważne. Porównywanie katalogów to nie tylko znajdowanie różnych plików — to utrzymanie integralności danych, zapewnienie zgodności i wykrywanie podstępnych zmian, które mogą zepsuć środowisko produkcyjne.

Typowe scenariusze, w których będzie to potrzebne:
- **Zarządzanie Wydaniami**: Porównywanie katalogów staging vs production przed wdrożeniem
- **Migracja Danych**: Zapewnienie, że wszystkie pliki zostały poprawnie przeniesione między systemami
- **Audyty Zgodności**: Śledzenie zmian dokumentów pod kątem wymogów regulacyjnych
- **Weryfikacja Kopii Zapasowych**: Potwierdzenie, że proces backupu rzeczywiście zadziałał
- **Współpraca Zespołowa**: Identyfikacja, kto co zmienił w współdzielonych katalogach projektu

## Wymagania wstępne i wymagania konfiguracyjne

Zanim zaczniemy kodować, upewnij się, że środowisko jest gotowe. Oto, czego będziesz potrzebować (i dlaczego):

**Podstawowe wymagania:**
1. **Java 8 lub wyższa** – GroupDocs.Comparison korzysta z nowoczesnych funkcji Javy
2. **Maven 3.6+** – Do zarządzania zależnościami (uwierz mi, nie próbuj ręcznego zarządzania JAR‑ami)
3. **IDE z dobrą obsługą Javy** – Zalecane IntelliJ IDEA lub Eclipse
4. **Co najmniej 2 GB RAM** – Porównywanie katalogów może być intensywne pod względem pamięci

**Wymagania wiedzy:**
- Podstawy programowania w Javie (pętle, warunki, obsługa wyjątków)
- Zrozumienie operacji I/O na plikach
- Znajomość zarządzania zależnościami w Mavenie
- Podstawowa znajomość try‑with‑resources (będziemy tego używać intensywnie)

**Opcjonalne, ale przydatne:**
- Doświadczenie z frameworkami logowania (SLF4J/Logback)
- Zrozumienie koncepcji wielowątkowości
- Podstawowa znajomość HTML (do formatowania raportów)

## Konfiguracja GroupDocs.Comparison dla Javy

Zintegrujmy tę bibliotekę poprawnie z projektem. Konfiguracja jest prosta, ale warto zwrócić uwagę na kilka pułapek.

### Konfiguracja Maven

Dodaj poniższy fragment do pliku `pom.xml` – zwróć uwagę na konfigurację repozytorium, którą często pomija się:

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

**Pro Tip**: Zawsze używaj najnowszego numeru wersji dostępnego na stronie GroupDocs. Wersja podana tutaj może nie być najświeższa.

### Konfiguracja licencji (Nie pomijaj tego)

GroupDocs nie jest darmowy, ale oferuje kilka opcji:

- **Bezpłatna wersja próbna**: 30‑dniowy trial z pełnym zestawem funkcji (idealny do oceny)
- **Licencja tymczasowa**: Wydłużony trial do rozwoju/testów
- **Licencja komercyjna**: Do użytku produkcyjnego

Uzyskaj licencję z:
- [Purchase a license](https://purchase.groupdocs.com/buy) for production
- [Get a temporary license](https://purchase.groupdocs.com/temporary-license/) for extended testing

### Podstawowa inicjalizacja i testowanie

Po dodaniu zależności, przetestuj integrację:

```java
import com.groupdocs.comparison.Comparer;

public class Main {
    public static void main(String[] args) {
        try {
            Comparer comparer = new Comparer();
            System.out.println("GroupDocs.Comparison initialized successfully!");
        } catch (Exception e) {
            System.err.println("Setup issue: " + e.getMessage());
        }
    }
}
```

Jeśli uruchomi się bez błędów, możesz przejść dalej. W przeciwnym razie sprawdź konfigurację Maven oraz połączenie internetowe (GroupDocs weryfikuje licencje online).

## Główna implementacja: Porównywanie Katalogów

Teraz najważniejsza część — właściwe porównywanie katalogów. Zacznijmy od podstawowej implementacji, a potem dodamy zaawansowane funkcje.

### Podstawowe Porównywanie Katalogów

To podstawowa wersja, która obsługuje większość przypadków użycia:

#### Krok 1: Ustawienie Ścieżek

```java
String sourceDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/source_directory";
String targetDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/target_directory";
String outputFileName = "YOUR_OUTPUT_DIRECTORY/compare_result.html";
```

**Ważne**: Używaj ścieżek bezwzględnych, zwłaszcza w środowiskach produkcyjnych. Ścieżki względne mogą powodować problemy w zależności od miejsca uruchomienia aplikacji.

#### Krok 2: Konfiguracja opcji porównania

```java
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.FolderComparisonExtension;

CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);
```

**Dlaczego wyjście HTML?** Raporty HTML są czytelne dla człowieka i mogą być otwarte w dowolnej przeglądarce. Idealne do udostępniania wyników osobom nietechnicznym.

#### Krok 3: Wykonanie porównania

```java
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    comparer.add(targetDirectoryPath, compareOptions);
    comparer.compareDirectory(outputFileName, compareOptions);
    System.out.println("Directory comparison completed. Results saved to: " + outputFileName);
} catch (Exception e) {
    System.err.println("Comparison failed: " + e.getMessage());
    e.printStackTrace();
}
```

**Dlaczego try‑with‑resources?** GroupDocs.Comparison zarządza uchwytami plików i pamięcią wewnętrznie. Użycie try‑with‑resources zapewnia prawidłowe zwolnienie zasobów, co jest szczególnie istotne przy dużych porównaniach katalogów.

### Zaawansowane opcje konfiguracji

Podstawowa konfiguracja działa, ale w rzeczywistych scenariuszach potrzebna jest personalizacja. Oto, jak dopasować porównania do własnych potrzeb:

#### Dostosowywanie formatów wyjściowych

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// HTML for human review
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);

// Or PDF for formal reports
// compareOptions.setFolderComparisonExtension(FolderComparisonExtension.PDF);
```

#### Filtrowanie plików i katalogów

Czasami nie chcesz porównywać wszystkiego. Oto, jak wybrać tylko wybrane elementy:

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// Skip temporary files and build directories
// Note: Exact filtering syntax may vary - check current API documentation
compareOptions.setShowDeletedContent(false); // Don't highlight deleted files
compareOptions.setShowInsertedContent(true); // Do highlight new files
```

## Typowe problemy i rozwiązania

Omówmy problemy, które najprawdopodobniej napotkasz (bo prawo Murphy'ego obowiązuje także w kodzie):

### Problem 1: OutOfMemoryError przy dużych katalogach

**Objawy**: Aplikacja kończy działanie z błędem braku pamięci przy porównywaniu katalogów zawierających tysiące plików.

**Rozwiązanie**: Zwiększ rozmiar sterty JVM i przetwarzaj katalogi partiami:

```java
// JVM args: -Xmx4g -Xms2g

// For very large directories, consider processing subdirectories separately
String[] subdirectories = {"subdir1", "subdir2", "subdir3"};
for (String subdir : subdirectories) {
    String sourceSub = sourceDirectoryPath + "/" + subdir;
    String targetSub = targetDirectoryPath + "/" + subdir;
    // Process each subdirectory individually
}
```

### Problem 2: FileNotFoundException mimo poprawnych ścieżek

**Objawy**: Ścieżki wyglądają poprawnie, a mimo to pojawiają się błędy „plik nie znaleziony”.

**Typowe przyczyny i naprawy**:
- **Uprawnienia**: Upewnij się, że aplikacja Java ma dostęp do odczytu katalogów źródłowych i zapis do lokalizacji wyjściowej
- **Znaki specjalne**: Nazwy katalogów zawierające spacje lub znaki specjalne wymagają odpowiedniego escapowania
- **Ścieżki sieciowe**: Ścieżki UNC mogą nie działać zgodnie z oczekiwaniami — skopiuj pliki lokalnie najpierw

```java
// Better path handling
Path sourcePath = Paths.get(sourceDirectoryPath).toAbsolutePath();
Path targetPath = Paths.get(targetDirectoryPath).toAbsolutePath();

if (!Files.exists(sourcePath)) {
    throw new IllegalArgumentException("Source directory doesn't exist: " + sourcePath);
}
if (!Files.exists(targetPath)) {
    throw new IllegalArgumentException("Target directory doesn't exist: " + targetPath);
}
```

### Problem 3: Porównanie trwa wiecznie

**Objawy**: Porównanie działa przez godziny bez zakończenia.

**Rozwiązania**:
1. **Filtruj niepotrzebne pliki** przed porównaniem
2. **Użyj wielowątkowości** dla niezależnych podkatalogów
3. **Wdroż monitorowanie postępu**, aby wiedzieć, co się dzieje

```java
// Add progress monitoring
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// Log progress (pseudo-code - actual implementation may vary)
long startTime = System.currentTimeMillis();
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    comparer.add(targetDirectoryPath, compareOptions);
    comparer.compareDirectory(outputFileName, compareOptions);
    long duration = System.currentTimeMillis() - startTime;
    System.out.println("Comparison completed in: " + (duration / 1000) + " seconds");
}
```

## Optymalizacja wydajności dla porównań na dużą skalę

Gdy masz do czynienia z katalogami zawierającymi tysiące plików, wydajność staje się krytyczna. Oto, jak zoptymalizować proces:

### Najlepsze praktyki zarządzania pamięcią

```java
// Increase heap size via JVM arguments
// -Xmx8g (for 8GB max heap)
// -XX:+UseG1GC (for better garbage collection with large heaps)

// In your code, help the GC by nulling large objects
CompareOptions compareOptions = new CompareOptions();
try (Comparer comparer = new Comparer(sourceDirectoryPath, compareOptions)) {
    // ... do comparison
    comparer.compareDirectory(outputFileName, compareOptions);
} // comparer auto‑closed here
compareOptions = null; // Help GC
```

### Strategia przetwarzania w partiach

Dla ogromnych struktur katalogów przetwarzaj je w kawałkach:

```java
public void compareDirectoriesInBatches(String sourceDir, String targetDir, int batchSize) {
    try {
        File[] sourceFiles = new File(sourceDir).listFiles();
        if (sourceFiles != null) {
            for (int i = 0; i < sourceFiles.length; i += batchSize) {
                int end = Math.min(i + batchSize, sourceFiles.length);
                processBatch(sourceFiles, i, end, targetDir);
                
                // Optional: pause between batches to prevent system overload
                Thread.sleep(1000);
            }
        }
    } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
        throw new RuntimeException("Batch processing interrupted", e);
    }
}
```

### Przetwarzanie równoległe dla niezależnych katalogów

Jeśli porównujesz wiele par katalogów, rób to równolegle:

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

ExecutorService executor = Executors.newFixedThreadPool(4);
List<Future<String>> futures = new ArrayList<>();

for (DirectoryPair pair : directoryPairs) {
    Future<String> future = executor.submit(() -> {
        // Perform comparison for this pair
        return compareDirectoryPair(pair.source, pair.target);
    });
    futures.add(future);
}

// Wait for all comparisons to complete
for (Future<String> future : futures) {
    try {
        String result = future.get();
        System.out.println("Comparison result: " + result);
    } catch (Exception e) {
        System.err.println("Comparison failed: " + e.getMessage());
    }
}

executor.shutdown();
```

## Przykłady zastosowań w rzeczywistych branżach

Porównywanie katalogów to nie tylko narzędzie dewelopera — jest wykorzystywane w różnych branżach do krytycznych procesów biznesowych:

### Rozwój oprogramowania i DevOps

**Zarządzanie wydaniami**: Porównywanie katalogów staging vs production przed wdrożeniem, aby wykryć dryf konfiguracji:

```java
// Automated pre-deployment check
String stagingConfig = "/app/staging/config";
String productionConfig = "/app/production/config";
String reportPath = "/reports/deployment-check-" + LocalDateTime.now().format(DateTimeFormatter.ISO_LOCAL_DATE) + ".html";

CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
options.setFolderComparisonExtension(FolderComparisonExtension.HTML);

try (Comparer comparer = new Comparer(stagingConfig, options)) {
    comparer.add(productionConfig, options);
    comparer.compareDirectory(reportPath, options);
    
    // Integration with deployment pipeline
    if (hasSignificantDifferences(reportPath)) {
        throw new RuntimeException("Deployment blocked: significant configuration differences detected");
    }
}
```

### Finanse i zgodność

**Utrzymanie ścieżki audytu**: Instytucje finansowe używają porównywania katalogów do śledzenia zmian dokumentów pod kątem wymogów regulacyjnych:

```java
// Monthly compliance check
String previousMonthDocs = "/compliance/2024-11/documents";
String currentMonthDocs = "/compliance/2024-12/documents";
String auditReport = "/audit/compliance-changes-december-2024.html";

// Compare and generate audit‑ready reports
performComplianceComparison(previousMonthDocs, currentMonthDocs, auditReport);
```

### Zarządzanie danymi i procesy ETL

**Weryfikacja integralności danych**: Zapewnienie, że migracje danych zakończyły się sukcesem:

```java
public boolean verifyDataMigration(String sourceDataDir, String migratedDataDir) {
    try {
        CompareOptions options = new CompareOptions();
        options.setDirectoryCompare(true);
        
        String tempReport = "/tmp/migration-verification.html";
        try (Comparer comparer = new Comparer(sourceDataDir, options)) {
            comparer.add(migratedDataDir, options);
            comparer.compareDirectory(tempReport, options);
        }
        
        // Custom logic to parse results and determine if migration was successful
        return analyzeComparisonResults(tempReport);
    } catch (Exception e) {
        System.err.println("Migration verification failed: " + e.getMessage());
        return false;
    }
}
```

### Zarządzanie treścią i publikacja

**Kontrola wersji dla zespołów nietechnicznych**: Marketing i zespoły treści mogą śledzić zmiany w repozytoriach dokumentów bez znajomości Gita:

```java
// Weekly content audit for marketing team
String lastWeekContent = "/content/backup/week-47";
String currentContent = "/content/current";
String marketingReport = "/reports/content-changes-week-48.html";

CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
options.setFolderComparisonExtension(FolderComparisonExtension.HTML);

// Generate human‑readable report for non‑technical stakeholders
generateContentChangeReport(lastWeekContent, currentContent, marketingReport, options);
```

## Zaawansowane wskazówki i dobre praktyki

Po pracy z porównywaniem katalogów w środowiskach produkcyjnych, oto kilka wyciągniętych z doświadczenia rad:

### Logowanie i monitorowanie

Zawsze implementuj rozbudowane logowanie:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

private static final Logger logger = LoggerFactory.getLogger(DirectoryComparer.class);

public void compareWithLogging(String source, String target, String output) {
    logger.info("Starting directory comparison: {} vs {}", source, target);
    long startTime = System.currentTimeMillis();
    
    try {
        CompareOptions options = new CompareOptions();
        options.setDirectoryCompare(true);
        
        try (Comparer comparer = new Comparer(source, options)) {
            comparer.add(target, options);
            comparer.compareDirectory(output, options);
        }
        
        long duration = System.currentTimeMillis() - startTime;
        logger.info("Comparison completed successfully in {}ms. Report: {}", duration, output);
        
    } catch (Exception e) {
        logger.error("Directory comparison failed for {} vs {}: {}", source, target, e.getMessage(), e);
        throw new RuntimeException("Comparison failed", e);
    }
}
```

### Odzyskiwanie po błędach i odporność

Zaimplementuj logikę ponawiania dla przejściowych awarii:

```java
public void compareWithRetry(String source, String target, String output, int maxRetries) {
    int attempts = 0;
    Exception lastException = null;
    
    while (attempts < maxRetries) {
        try {
            performComparison(source, target, output);
            return; // Success!
        } catch (Exception e) {
            lastException = e;
            attempts++;
            
            if (attempts < maxRetries) {
                try {
                    Thread.sleep(1000 * attempts); // Exponential backoff
                } catch (InterruptedException ie) {
                    Thread.currentThread().interrupt();
                    throw new RuntimeException("Retry interrupted", ie);
                }
            }
        }
    }
    
    throw new RuntimeException("Comparison failed after " + maxRetries + " attempts", lastException);
}
```

### Zarządzanie konfiguracją

Externalizuj ustawienia, aby móc je modyfikować bez rekompilacji:

```java
// application.properties
comparison.output.format=HTML
comparison.max.retries=3
comparison.batch.size=100
comparison.parallel.threads=4

// In your code
@Value("${comparison.output.format:HTML}")
private String outputFormat;

@Value("${comparison.max.retries:3}")
private int maxRetries;
```

### Obsługa ścieżek niezależna od platformy

```java
// Use platform-independent path handling
Path sourcePath = Paths.get(sourceDirectory);
Path targetPath = Paths.get(targetDirectory);
Path outputPath = Paths.get(outputDirectory);

// Validate permissions before starting
if (!Files.isReadable(sourcePath)) {
    throw new IllegalStateException("Cannot read source directory: " + sourcePath);
}
if (!Files.isReadable(targetPath)) {
    throw new IllegalStateException("Cannot read target directory: " + targetPath);
}
if (!Files.isWritable(outputPath.getParent())) {
    throw new IllegalStateException("Cannot write to output directory: " + outputPath.getParent());
}
```

### Ignorowanie znaczników czasu, gdy nie mają znaczenia

```java
CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
// Configure to ignore timestamps and focus on content
// (exact options may vary - check API documentation)
options.setIgnoreWhitespaces(true);
options.setIgnoreFormatting(true);
```

## Rozwiązywanie typowych problemów wdrożeniowych

### Działa w środowisku deweloperskim, a w produkcji nie

**Objawy**: Porównanie działa lokalnie, ale na serwerze wywala się.

**Przyczyny**:
- Różnice w czułości na wielkość liter (Windows vs Linux)
- Bardziej restrykcyjne uprawnienia systemu plików
- Hard‑kodowane separatory ścieżek (`/` vs `\`)

**Naprawa**: Używaj `Path` i `File.separator` tak, jak pokazano w sekcji *Obsługa ścieżek niezależna od platformy*.

### Niespójne wyniki

**Objawy**: Dwukrotne uruchomienie tego samego porównania daje różne wyniki.

**Możliwe przyczyny**:
- Pliki są modyfikowane w trakcie działania
- Znaczniki czasu są traktowane jako różnice
- Metadane systemu plików różnią się

**Rozwiązanie**: Skonfiguruj `CompareOptions`, aby ignorować znaczniki czasu i skupiać się na rzeczywistej treści (zobacz *Ignorowanie znaczników czasu*).

## Najczęściej zadawane pytania

**P: Jak radzić sobie z katalogami zawierającymi miliony plików?**  
O: Połącz przetwarzanie w partiach, zwiększ stertę JVM (`-Xmx`) i uruchamiaj porównania podkatalogów równolegle. Sekcje *Strategia przetwarzania w partiach* oraz *Przetwarzanie równoległe* zawierają gotowe wzorce.

**P: Czy mogę porównywać katalogi znajdujące się na różnych serwerach?**  
O: Tak, ale opóźnienie sieciowe może dominować czas wykonania. Najlepsza wydajność uzyskasz, kopiując zdalny katalog lokalnie przed wywołaniem porównania lub montując zdalny udział z wystarczającą przepustowością I/O.

**P: Jakie formaty plików są obsługiwane przez GroupDocs.Comparison?**  
O: GroupDocs.Comparison obsługuje szeroką gamę formatów, w tym DOC/DOCX, PDF, PPT/PPTX, XLS/XLSX, TXT, HTML oraz popularne typy obrazów. Aktualną listę znajdziesz w oficjalnej dokumentacji.

**P: Jak zintegrować to porównanie z pipeline CI/CD?**  
O: Owiń logikę porównania w wtyczkę Maven/Gradle lub samodzielny JAR, a następnie wywołaj go jako krok budowania w Jenkins, GitHub Actions, Azure Pipelines itp. Użyj przykładu *Logowanie i monitorowanie*, aby udostępnić wyniki jako artefakty builda.

**P: Czy można dostosować wygląd raportu HTML?**  
O: Wbudowany szablon HTML jest stały, ale możesz poddać wygenerowany plik post‑processingowi (np. wstrzyknąć własny CSS lub JavaScript), aby dopasować go do swojej identyfikacji wizualnej.

---

**Ostatnia aktualizacja:** 2026-03-22  
**Testowane z:** GroupDocs.Comparison 25.2 (Java)  
**Autor:** GroupDocs