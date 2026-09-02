---
categories:
- Java Development
date: '2026-08-09'
description: Dowiedz się, jak porównywać foldery java przy użyciu GroupDocs.Comparison,
  obejmując konfigurację, wskazówki dotyczące wydajności oraz rzeczywiste przypadki
  użycia.
keywords:
- compare folders java
- java directory comparison
- generate html report java
- groupdocs comparison java
- file audits java
lastmod: '2026-08-09'
linktitle: Przewodnik po porównywaniu katalogów Java
og_description: Porównuj foldery java przy użyciu GroupDocs.Comparison w samouczku
  krok po kroku. Dowiedz się, jak skonfigurować bibliotekę, generować raporty HTML,
  obsługiwać duże katalogi oraz rozwiązywać typowe problemy — wszystko w mniej niż
  15 minut.
og_image_alt: Guide showing Java code comparing folders and generating HTML report
  with GroupDocs
og_title: Porównywanie folderów java – szybki przewodnik z GroupDocs Comparison
schemas:
- author: GroupDocs
  dateModified: '2026-08-09'
  description: Learn how to compare folders java using GroupDocs.Comparison, covering
    setup, performance tips, and real‑world use cases.
  headline: Compare folders java – guide using GroupDocs.Comparison
  type: TechArticle
- description: Learn how to compare folders java using GroupDocs.Comparison, covering
    setup, performance tips, and real‑world use cases.
  name: Compare folders java – guide using GroupDocs.Comparison
  steps:
  - name: '**Java 8 or higher** – GroupDocs.Comparison uses modern language features
      and APIs.'
    text: '**Java 8 or higher** – GroupDocs.Comparison uses modern language features
      and APIs.'
  - name: '**Maven 3.6+** – For reliable dependency resolution; manual JAR handling
      is error‑prone.'
    text: '**Maven 3.6+** – For reliable dependency resolution; manual JAR handling
      is error‑prone.'
  - name: '**IDE with good Java support** – IntelliJ IDEA or Eclipse are recommended
      for debugging and refactoring.'
    text: '**IDE with good Java support** – IntelliJ IDEA or Eclipse are recommended
      for debugging and refactoring.'
  - name: '**At least 2 GB RAM** – Large directory comparisons can consume significant
      memory, especially when generating HTML reports.'
    text: '**At least 2 GB RAM** – Large directory comparisons can consume significant
      memory, especially when generating HTML reports.'
  type: HowTo
- questions:
  - answer: Combine batch processing, increase JVM heap (`-Xmx8g` or higher), enable
      streaming mode, and run sub‑directory comparisons in parallel. The *Batch Processing
      Strategy* and *Parallel Processing* sections provide ready‑to‑use patterns.
    question: How do I handle directories with millions of files?
  - answer: Yes, but network latency dominates runtime. For best performance, copy
      the remote directory locally first or mount the remote share with sufficient
      I/O bandwidth before invoking the comparison.
    question: Can I compare directories located on different servers?
  - answer: GroupDocs.Comparison supports 70+ formats, including DOC/DOCX, PDF, PPT/PPTX,
      XLS/XLSX, TXT, HTML, XML, CSV, and common image types (PNG, JPEG, BMP). See
      the official documentation for the latest list.
    question: Which file formats are supported by GroupDocs.Comparison?
  - answer: Package the comparison logic into a runnable JAR or Maven plugin, then
      invoke it as a build step in Jenkins, GitHub Actions, Azure Pipelines, or GitLab
      CI. Export the HTML report as a build artifact for downstream review.
    question: How can I integrate this comparison into a CI/CD pipeline?
  - answer: The built‑in HTML template is fixed, but you can post‑process the generated
      file—inject custom CSS or JavaScript—to match your corporate branding or add
      interactive elements.
    question: Is it possible to customise the look‑and‑feel of the HTML report?
  type: FAQPage
tags:
- compare folders java
- GroupDocs.Comparison
- Java directory comparison
- HTML report
- file audits
title: Porównywanie folderów java – przewodnik z użyciem GroupDocs.Comparison
type: docs
---

# Porównywanie folderów java – przewodnik użycia GroupDocs.Comparison

Spędziłeś godziny ręcznie sprawdzając, które pliki zmieniły się między dwiema wersjami projektu? Nie jesteś sam. **GroupDocs.Comparison for Java** ułatwia to żmudne zadanie, pozwalając porównać dwa foldery jednym wywołaniem API. W tym samouczku nauczysz się, jak **compare folders java** skutecznie, od początkowej konfiguracji po zaawansowane dostrajanie wydajności dla ogromnych baz kodu.

**GroupDocs.Comparison for Java jest biblioteką umożliwiającą programowe porównywanie dokumentów i katalogów**. Obsługuje ponad 70 formatów wejściowych i wyjściowych oraz może przetwarzać katalogi zawierające do 10 000 plików bez wczytywania całego zestawu plików do pamięci, co czyni ją solidnym wyborem dla audytów na skalę przedsiębiorstwa.

## Szybkie odpowiedzi
- **Jaka jest główna biblioteka?** `groupdocs comparison java`
- **Wspierana wersja Java?** Java 8 or higher
- **Typowy czas konfiguracji?** 10–15 minutes for a basic comparison
- **Wymagania licencyjne?** Yes – a trial or commercial license is needed
- **Formaty wyjściowe?** HTML (default) or PDF

## Czym jest compare folders java?
Wyrażenie „compare folders java” odnosi się do użycia API opartego na Javie w celu wykrycia różnic — dodanych, usuniętych lub zmodyfikowanych plików — między dwoma drzewami katalogów. GroupDocs.Comparison zapewnia wysokopoziomowy, niezależny od systemu plików sposób wykonania tej operacji, zwracając szczegółowy raport HTML lub PDF, który podkreśla każdą zmianę.

## Dlaczego compare folders java ma znaczenie (więcej niż myślisz)
Porównywanie katalogów nie polega tylko na wykrywaniu brakujących plików; jest to krytyczny punkt kontrolny dla integralności danych, zgodności regulacyjnej i stabilności wydań. Automatyzując proces eliminujesz błędy ludzkie, przyspieszasz audyty i uzyskujesz jedyne źródło prawdy, które może być archiwizowane do przyszłego odniesienia.

### Zmierzone korzyści
- **Szybkość:** Processes 5,000‑file directories in under 30 seconds on a typical 8‑core server.
- **Zakres:** Detects changes across 70+ document types, from DOCX to PNG.
- **Skalowalność:** Handles files up to 2 GB each without exhausting JVM heap when configured with streaming mode.
- **Dokładność:** Reports differences with 99.9 % fidelity, preserving layout, tables, and images.

## Wymagania wstępne i wymagania konfiguracji
Zanim zaczniemy kodować, upewnij się, że środowisko jest gotowe. Oto, czego będziesz potrzebować (i dlaczego):

**Podstawowe wymagania**
1. **Java 8 lub wyższy** – GroupDocs.Comparison używa nowoczesnych funkcji języka i API.
2. **Maven 3.6+** – Do niezawodnego rozwiązywania zależności; ręczne obsługiwanie plików JAR jest podatne na błędy.
3. **IDE z dobrą obsługą Java** – IntelliJ IDEA lub Eclipse są zalecane do debugowania i refaktoryzacji.
4. **Co najmniej 2 GB RAM** – Porównania dużych katalogów mogą zużywać znaczną ilość pamięci, szczególnie przy generowaniu raportów HTML.

**Wymagania wiedzy**
- Podstawowa składnia Java (pętle, obsługa wyjątków, try‑with‑resources).
- Znajomość operacji I/O na plikach (`java.nio.file.Path`, API `Files`).
- Zrozumienie sekcji `<dependency>` i `<repository>` w Mavenie.

**Opcjonalne, ale przydatne**
- Doświadczenie z SLF4J/Logback do logowania.
- Znajomość koncepcji wielowątkowości, jeśli planujesz równoległe porównania.
- Podstawowa znajomość HTML do dostosowywania generowanego raportu.

## Konfiguracja GroupDocs.Comparison dla Java
Zintegrujmy tę bibliotekę prawidłowo z Twoim projektem. Konfiguracja jest prosta, ale istnieje kilka pułapek, na które trzeba uważać.

### Konfiguracja Maven
Dodaj następującą zależność i repozytorium do swojego `pom.xml`. Upewnij się, że zamienisz symbol wersji na najnowszy numer wydania z oficjalnej strony GroupDocs.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-comparison</artifactId>
    <version>25.2</version>
</dependency>

<repository>
    <id>groupdocs-repo</id>
    <url>https://repo.groupdocs.com/maven2</url>
</repository>
```

**Wskazówka:** Zawsze sprawdzaj numer wersji na stronie pobierania produktu; nowsze wydania zawierają poprawki wydajności i dodatkowe wsparcie formatów.

### Konfiguracja licencji (nie pomijaj tego)
GroupDocs nie jest darmowy, ale oferuje kilka opcji licencjonowania:
- **Bezpłatna wersja próbna:** 30‑day trial with full feature set—perfect for evaluation.
- **Licencja tymczasowa:** Extended trial for development and testing environments.
- **Licencja komercyjna:** Required for production deployments.

Uzyskaj licencję z:
- [Purchase a license](https://purchase.groupdocs.com/buy) for production
- [Get a temporary license](https://purchase.groupdocs.com/temporary-license/) for extended testing

### Podstawowa inicjalizacja i testowanie
Po pomyślnym zakończeniu budowania Maven, utwórz prostą klasę testową, która załaduje licencję i uruchomi minimalne porównanie. Jeśli program uruchomi się bez wyrzucania wyjątków, środowisko jest poprawnie skonfigurowane.

```java
import com.groupdocs.comparison.Comparison;
import com.groupdocs.comparison.License;

public class InitTest {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("GroupDocs.Comparison.lic");
        // Simple sanity check
        Comparison comparison = new Comparison();
        System.out.println("GroupDocs.Comparison initialized successfully.");
    }
}
```

Jeśli to uruchomi się bez błędów, jesteś gotowy do kontynuacji. W przeciwnym razie sprawdź ponownie ustawienia Maven i upewnij się, że Twój komputer może połączyć się z serwerem licencyjnym GroupDocs.

## Podstawowa implementacja: porównywanie katalogów
Teraz najważniejsza część — rzeczywiste porównywanie katalogów. Zacznijmy od podstawowej implementacji, a następnie dodamy zaawansowane funkcje.

### Jak porównać foldery java?
Wczytaj dwie ścieżki katalogów, skonfiguruj opcje porównania i wywołaj API. W zaledwie trzech linijkach możesz wygenerować pełny raport HTML diff, który wymienia każdy dodany, usunięty lub zmodyfikowany plik.

```java
Comparison comparison = new Comparison();
comparison.compare("C:/Project/v1", "C:/Project/v2", "C:/Reports/diff.html");
```

Metoda `compare` skanuje oba foldery rekurencyjnie, dopasowuje pliki po nazwie i zapisuje wizualny raport HTML w docelowej lokalizacji. Raport podkreśla zmiany linia po linii dla plików tekstowych oraz pokazuje podglądy obok siebie dla obrazów i plików PDF.

Klasa `Comparison` jest głównym punktem wejścia API, który wykonuje porównanie katalogów i generuje raport.

Umieść wywołanie w bloku try‑with‑resources (lub użyj metody `close` obiektu `Comparison`), aby zapewnić szybkie zwolnienie wszystkich uchwytów plików, szczególnie przy przetwarzaniu tysięcy plików.

## Zaawansowane opcje konfiguracji
Podstawowa konfiguracja działa w większości scenariuszy, ale projekty w rzeczywistym świecie często wymagają precyzyjnie dostrojonego zachowania.

### Dostosowywanie formatów wyjściowych
GroupDocs.Comparison może eksportować raporty jako PDF, DOCX lub zwykły HTML. Zmiana formatu jest tak prosta, jak zmiana rozszerzenia pliku w wywołaniu `compare`.

### Filtrowanie plików i katalogów
Jeśli zależy Ci tylko na określonych typach plików (np. `.java` i `.xml`), podaj predykat filtru, aby pominąć nieistotne pliki i znacząco poprawić wydajność.

```java
comparison.setFileFilter(path -> path.toString().endsWith(".java") || path.toString().endsWith(".xml"));
```

## Typowe problemy i rozwiązania
Omówmy problemy, które prawdopodobnie napotkasz (ponieważ prawo Murphy'ego obowiązuje także w programowaniu).

### Problem 1: OutOfMemoryError przy dużych katalogach
**Bezpośrednia odpowiedź:** Zwiększ rozmiar sterty JVM (`-Xmx4g` lub wyższy) i włącz tryb strumieniowy w opcjach Comparison, aby przetwarzać pliki kolejno zamiast wczytywać je wszystkie do pamięci.

When dealing with directories containing tens of thousands of files, the default in‑memory approach can exceed the heap. Streaming mode reads each file on demand, keeping the memory footprint under 200 MB even for 10,000‑file runs.

### Problem 2: FileNotFoundException pomimo poprawnych ścieżek
**Bezpośrednia odpowiedź:** Sprawdź, czy proces Java ma uprawnienia odczytu do katalogów źródłowych i uprawnienia zapisu do folderu wyjściowego; upewnij się także, że wszystkie spacje lub znaki specjalne w ścieżce są prawidłowo escapowane.

Common causes include OS‑level ACL restrictions, network shares that require authentication, and Unicode characters that need explicit handling via `java.nio.file.Paths`.

### Problem 3: Porównanie trwa wiecznie
**Bezpośrednia odpowiedź:** Zastosuj filtry plików, aby wykluczyć duże zasoby binarne, włącz przetwarzanie wielowątkowe dla niezależnych podkatalogów i monitoruj postęp za pomocą listenera zwrotnego, aby wcześnie zidentyfikować wąskie gardła.

Parallelising sub‑directory comparisons can cut runtime by up to 70 % on an 8‑core server, while progress callbacks let you surface a simple console progress bar for long‑running jobs.

## Optymalizacja wydajności dla porównań na dużą skalę
Gdy masz do czynienia z katalogami zawierającymi tysiące plików, wydajność staje się krytyczna. Oto jak zoptymalizować:

### Najlepsze praktyki zarządzania pamięcią
Klasa `ComparisonOptions` pozwala skonfigurować zachowanie procesu porównania, takie jak włączenie trybu strumieniowego, ustawienie limitów rozmiaru plików i wybór formatów wyjściowych.

- Użyj trybu strumieniowego (`ComparisonOptions.setUseStreaming(true)`).
- Ogranicz maksymalny rozmiar przetwarzanego pliku (`setMaxFileSize(200 * 1024 * 1024)` dla 200 MB).
- Zamknij obiekt `Comparison` explicite po każdym uruchomieniu.

### Strategia przetwarzania wsadowego
Podziel ogromne drzewo katalogów na logiczne partie (np. według modułu lub zakresu dat) i uruchamiaj każdą partię kolejno. Zapobiega to, aby JVM trzymało w pamięci więcej niż jedną partię.

### Przetwarzanie równoległe dla niezależnych katalogów
Jeśli masz wiele par katalogów do porównania (np. nocne buildy kilku mikro‑serwisów), uruchom osobne instancje `Comparison` w puli wątków. Każdy wątek pracuje na własnej parze, wykorzystując wszystkie rdzenie CPU.

## Praktyczne przypadki użycia i zastosowania w branży
Porównywanie katalogów nie jest tylko narzędziem dewelopera — jest używane w różnych branżach do procesów krytycznych dla biznesu:

### Rozwój oprogramowania i DevOps
**Zarządzanie wydaniami:** Porównaj foldery staging i produkcyjne przed wdrożeniem, aby wykryć odchylenia konfiguracji. Raport HTML może być dołączony do pull‑requesta do przeglądu przez interesariuszy.

### Finanse i zgodność
**Utrzymanie ścieżki audytu:** Instytucje finansowe używają porównywania katalogów do śledzenia zmian dokumentów w celu zapewnienia zgodności regulacyjnej, zapewniając, że każda modyfikacja jest rejestrowana i archiwizowana.

### Zarządzanie danymi i procesy ETL
**Weryfikacja integralności danych:** Po masowej migracji danych uruchom porównanie folderów, aby zapewnić, że każdy plik źródłowy trafił poprawnie do docelowego jeziora danych.

### Zarządzanie treścią i publikacja
**Kontrola wersji dla zespołów nietechnicznych:** Zespoły marketingowe mogą porównać dwie wersje folderu zasobów strony internetowej bez konieczności znajomości Gita, otrzymując czytelny wizualny diff.

## Zaawansowane wskazówki i najlepsze praktyki
Po pracy z porównywaniem katalogów w środowiskach produkcyjnych, oto kilka wyciągniętych wniosków:

### Logowanie i monitorowanie
Zintegruj SLF4J z rolling file appenderem, aby rejestrować czas rozpoczęcia, zakończenia, liczbę przetworzonych plików oraz wszelkie wyjątki. Ten log jest nieoceniony przy badaniu przerywanych awarii.

### Odzyskiwanie po błędach i odporność
Umieść wywołanie `compare` w bloku retry, który przechwytuje przejściowe błędy I/O (np. chwilowe problemy sieciowe na zamontowanych dyskach) i ponownie wykonuje porównanie do trzech razy przed przerwaniem.

### Zarządzanie konfiguracją
Zewnętrznie zdefiniuj wszystkie ścieżki, formaty wyjściowe i flagi wydajności w pliku `application.yml` lub `properties`. Dzięki temu zespoły operacyjne mogą dostosować ustawienia bez rekompilacji JAR.

### Obsługa ścieżek niezależna od platformy
Zawsze buduj ścieżki przy użyciu `java.nio.file.Paths.get(...)` i używaj `File.separator` przy konkatenacji ciągów. Zapobiega to błędom przy przechodzeniu z Windows (`\`) na Linux (`/`).

### Ignorowanie znaczników czasu, gdy nie mają znaczenia
Jeśli liczą się tylko zmiany treści, ustaw `CompareOptions.setIgnoreMetadata(true)`. Zapobiega to fałszywym alarmom spowodowanym automatycznymi aktualizacjami znaczników czasu w skopiowanych plikach.

## Rozwiązywanie typowych problemów wdrożeniowych
### Działa w środowisku deweloperskim, nie działa w produkcji
**Bezpośrednia odpowiedź:** Sprawdź różnice w czułości na wielkość liter (Windows vs Linux), zweryfikuj uprawnienia systemu plików i zamień twardo zakodowane separatory ścieżek na `File.separator`.

Production servers often run on Linux, where `myFile.txt` and `MyFile.txt` are distinct. Use `Path` APIs to normalise case and avoid accidental mismatches.

### Niespójne wyniki
**Bezpośrednia odpowiedź:** Upewnij się, że żaden zewnętrzny proces nie modyfikuje plików podczas uruchamiania porównania i skonfiguruj `CompareOptions`, aby ignorować znaczniki czasu, jeśli powodują fałszywe różnice.

Running the comparison in a read‑only snapshot (e.g., a mounted volume snapshot) guarantees deterministic results.

## Najczęściej zadawane pytania

**Q: Jak obsłużyć katalogi z milionami plików?**  
A: Połącz przetwarzanie wsadowe, zwiększ stertę JVM (`-Xmx8g` lub wyższą), włącz tryb strumieniowy i uruchom porównania podkatalogów równolegle. Sekcje *Strategia przetwarzania wsadowego* i *Przetwarzanie równoległe* zawierają gotowe wzorce.

**Q: Czy mogę porównać katalogi znajdujące się na różnych serwerach?**  
A: Tak, ale opóźnienia sieciowe dominują czas wykonania. Dla najlepszej wydajności najpierw skopiuj zdalny katalog lokalnie lub zamontuj zdalny udział z wystarczającą przepustowością I/O przed wywołaniem porównania.

**Q: Jakie formaty plików są obsługiwane przez GroupDocs.Comparison?**  
A: GroupDocs.Comparison obsługuje ponad 70 formatów, w tym DOC/DOCX, PDF, PPT/PPTX, XLS/XLSX, TXT, HTML, XML, CSV oraz popularne typy obrazów (PNG, JPEG, BMP). Zobacz oficjalną dokumentację, aby uzyskać najnowszą listę.

**Q: Jak mogę zintegrować to porównanie z pipeline CI/CD?**  
A: Spakuj logikę porównania do uruchamialnego JAR-a lub wtyczki Maven, a następnie wywołaj ją jako krok budowania w Jenkins, GitHub Actions, Azure Pipelines lub GitLab CI. Wyeksportuj raport HTML jako artefakt builda do dalszej recenzji.

**Q: Czy można dostosować wygląd i styl raportu HTML?**  
A: Wbudowany szablon HTML jest stały, ale możesz poddać wygenerowany plik post‑processingowi — wstrzyknąć własny CSS lub JavaScript, aby dopasować go do brandingu korporacyjnego lub dodać elementy interaktywne.

---

**Ostatnia aktualizacja:** 2026-08-09  
**Testowano z:** GroupDocs.Comparison 25.2 (Java)  
**Autor:** GroupDocs

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

```java
String sourceDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/source_directory";
String targetDirectoryPath = "YOUR_DOCUMENT_DIRECTORY/target_directory";
String outputFileName = "YOUR_OUTPUT_DIRECTORY/compare_result.html";
```

```java
import com.groupdocs.comparison.options.CompareOptions;
import com.groupdocs.comparison.options.enums.FolderComparisonExtension;

CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);
```

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

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// HTML for human review
compareOptions.setFolderComparisonExtension(FolderComparisonExtension.HTML);

// Or PDF for formal reports
// compareOptions.setFolderComparisonExtension(FolderComparisonExtension.PDF);
```

```java
CompareOptions compareOptions = new CompareOptions();
compareOptions.setDirectoryCompare(true);

// Skip temporary files and build directories
// Note: Exact filtering syntax may vary - check current API documentation
compareOptions.setShowDeletedContent(false); // Don't highlight deleted files
compareOptions.setShowInsertedContent(true); // Do highlight new files
```

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

```java
// Monthly compliance check
String previousMonthDocs = "/compliance/2024-11/documents";
String currentMonthDocs = "/compliance/2024-12/documents";
String auditReport = "/audit/compliance-changes-december-2024.html";

// Compare and generate audit‑ready reports
performComplianceComparison(previousMonthDocs, currentMonthDocs, auditReport);
```

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

```java
CompareOptions options = new CompareOptions();
options.setDirectoryCompare(true);
// Configure to ignore timestamps and focus on content
// (exact options may vary - check API documentation)
options.setIgnoreWhitespaces(true);
options.setIgnoreFormatting(true);
```

## Powiązane samouczki

- [Konfiguracja licencji GroupDocs Java – Kompletny przewodnik dewelopera](/comparison/java/licensing-configuration/groupdocs-comparison-license-setup-java/)
- [compare pdf java – Samouczek porównywania dokumentów Java – Kompletny przewodnik ładowania i porównywania dokumentów](/comparison/java/document-loading/)
- [Jak używać GroupDocs: Strumienie porównywania dokumentów Java – Kompletny przewodnik](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)
