---
categories:
- Java Development
date: '2026-09-10'
description: Μάθετε πώς να ορίζετε προσαρμοσμένα μεταδεδομένα java χρησιμοποιώντας
  το GroupDocs Comparison και να συγκρίνετε έγγραφα με μεταδεδομένα για αξιόπιστες
  ροές εργασίας Java.
keywords:
- set custom metadata java
- compare docs with metadata
- groupdocs comparison java
lastmod: '2026-09-10'
linktitle: Μεταδεδομένα εγγράφων Java με το GroupDocs
og_description: Ορίστε προσαρμοσμένα μεταδεδομένα java χρησιμοποιώντας το GroupDocs
  Comparison και μάθετε πώς να συγκρίνετε έγγραφα με μεταδεδομένα σε Java. Ακολουθήστε
  αυτό το βήμα‑βήμα tutorial για αξιόπιστες ροές εργασίας.
og_image_alt: Guide showing Java code for setting custom metadata with GroupDocs Comparison
og_title: Ορίστε προσαρμοσμένα μεταδεδομένα java με το GroupDocs Comparison – Οδηγός
  Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-10'
  description: Learn how to set custom metadata java using GroupDocs Comparison and
    compare documents with metadata for robust Java workflows.
  headline: Set custom metadata java with GroupDocs Comparison
  type: TechArticle
- description: Learn how to set custom metadata java using GroupDocs Comparison and
    compare documents with metadata for robust Java workflows.
  name: Set custom metadata java with GroupDocs Comparison
  steps:
  - name: set up your output path
    text: '**Pro tip:** In production you’ll usually generate these paths dynamically—consider
      using `System.getProperty("java.io.tmpdir")` or a dedicated output folder that
      your CI/CD pipeline can clean up automatically.'
  - name: initialize the comparer and add target documents
    text: If you encounter a “file not found” exception, double‑check that the paths
      are absolute during development; relative paths often resolve differently when
      the application runs from a different working directory.
  - name: configure custom metadata (the important part)
    text: '- `MetadataType.FILE_AUTHOR` tells GroupDocs which metadata bucket to touch.
      `MetadataType.FILE_AUTHOR` identifies the author metadata bucket that GroupDocs
      will modify. - The `FileAuthorMetadata.Builder` follows the classic builder
      pattern, allowing you to set author, company, and last‑modified‑by '
  - name: run the comparison and save the result
    text: When the comparison finishes, the output file will contain the exact metadata
      you defined, preserving the audit trail across revisions.
  type: HowTo
- questions:
  - answer: GroupDocs.Comparison supports metadata for Word, PDF, Excel, PowerPoint,
      and several image formats. Use the appropriate `MetadataType` enum (e.g., `FILE_AUTHOR`
      for Word, `PDF_AUTHOR` for PDFs) and test each format early in your pipeline.
    question: How do I handle metadata for different document formats?
  - answer: Yes. Call the `Metadata` API on a loaded document to retrieve current
      values, merge them with your custom fields, and then write the combined set
      back to the file.
    question: Can I read existing metadata before modifying it?
  - answer: By default GroupDocs may preserve source metadata. Using `setCloneMetadataType()`
      gives you explicit control—choose to clone, replace, or ignore metadata as required.
    question: What happens to metadata during document comparison?
  - answer: The overhead is negligible compared with the core comparison algorithm.
      In benchmarks, adding metadata to a 200‑page Word file adds less than 0.2 seconds
      to a 3‑second comparison run.
    question: Is there a performance impact from setting custom metadata?
  - answer: Hook into Git post‑commit or CI pipelines to invoke the comparison routine,
      passing the commit author and hash as metadata values. This automatically ties
      each generated document to a specific source change.
    question: How can I integrate this with version‑control systems?
  type: FAQPage
tags:
- java
- document-management
- metadata
- groupdocs
- tutorial
title: Ορίστε προσαρμοσμένα μεταδεδομένα java με το GroupDocs Comparison
type: docs
url: /el/java/metadata-management/groupdocs-comparison-java-custom-metadata-guide/
weight: 1
---

# Ορισμός προσαρμοσμένων μεταδεδομένων java με το GroupDocs Comparison

Έχετε βρεθεί ποτέ να πνίγεστε στις εκδόσεις εγγράφων, αναρωτιέστε ποιος έκανε ποιες αλλαγές και πότε; Δεν είστε μόνοι. **Set custom metadata java** σας επιτρέπει να ενσωματώσετε στοιχεία συγγραφέα, εταιρείας και αναθεώρησης απευθείας σε ένα αρχείο, μετατρέποντας τα αόρατα δεδομένα σε ένα αναζητήσιμο ίχνος ελέγχου. Σε αυτόν τον ολοκληρωμένο οδηγό θα μάθετε πώς να διαμορφώσετε προσαρμοσμένα μεταδεδομένα, να εκτελέσετε ισχυρές ροές εργασίας σύγκρισης εγγράφων java και να αποφύγετε τα κοινά εμπόδια που παγιδεύουν πολλούς προγραμματιστές.

## Γρήγορες απαντήσεις
- **Ποιος είναι ο κύριος σκοπός του ορισμού προσαρμοσμένων μεταδεδομένων σε Java;** Σας επιτρέπει να ενσωματώσετε στοιχεία συγγραφέα, εταιρείας και αναθεώρησης απευθείας στα έγγραφα για συμμόρφωση και έλεγχο.  
- **Ποια βιβλιοθήκη υποστηρίζει τη διαχείριση μεταδεδομένων και τη σύγκριση εγγράφων;** GroupDocs.Comparison for Java.  
- **Χρειάζομαι άδεια για να δοκιμάσω τα παραδείγματα;** Διατίθεται δωρεάν δοκιμή μέσω της [temporary license request form](https://purchase.groupdocs.com/temporary-license/); πλήρης άδεια μπορεί να αγοραστεί από το [GroupDocs purchase site](https://purchase.groupdocs.com/buy).  
- **Μπορώ να συγκρίνω έγγραφα με μεταδεδομένα σε ένα βήμα;** Ναι—χρησιμοποιήστε `setCloneMetadataType` μαζί με τις ρυθμίσεις προσαρμοσμένων μεταδεδομένων. Το `setCloneMetadataType` καθορίζει πώς τα μεταδεδομένα προέλευσης κλωνοποιούνται, αντικαθίστανται ή αγνοούνται κατά την αποθήκευση.  
- **Ποια έκδοση της Java απαιτείται;** Java 8 ή νεότερη.

## Τι είναι το “set custom metadata java”;
`set custom metadata java` είναι η προγραμματιστική διαδικασία προσθήκης ή ενημέρωσης ιδιοτήτων εγγράφου—όπως συγγραφέας, εταιρεία ή τελευταίος αποθηκευτής—μέσα σε ένα αρχείο από κώδικα Java. Αυτή η τεχνική είναι απαραίτητη για συμμόρφωση, έλεγχο εκδόσεων και αυτοματοποιημένα ίχνη ελέγχου.

## Γιατί να χρησιμοποιήσετε το GroupDocs Comparison για σύγκριση εγγράφων με μεταδεδομένα;
Το GroupDocs.Comparison for Java όχι μόνο επισημαίνει τις διαφορές περιεχομένου αλλά και σας παρέχει λεπτομερή έλεγχο των ιδιοτήτων του εγγράφου. Υποστηρίζει **50+ μορφές εισόδου και εξόδου** και μπορεί να επεξεργαστεί αρχεία με εκατοντάδες σελίδες χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη, καθιστώντας το ιδανικό για μεγάλης κλίμακας νομικές ή επιχειρησιακές ροές εργασίας.

## Προαπαιτούμενα – τι θα χρειαστείτε πριν ξεκινήσετε
Χρειάζεστε μια σταθερή βάση πριν γράψετε μια γραμμή κώδικα.

- **GroupDocs.Comparison for Java** – έκδοση 25.2 ή νεότερη (παλαιότερες εκδόσεις δεν υποστηρίζουν πλήρη μεταδεδομένα). Κατεβάστε το από τη [GroupDocs download page](https://releases.groupdocs.com/comparison/java/).  
- **Java Development Kit** – Java 8 ή νεότερη.  
- **Maven ή Gradle** – για διαχείριση εξαρτήσεων.  
- **IDE** – IntelliJ IDEA, Eclipse ή οποιονδήποτε επεξεργαστή συμβατό με Java.  
- **Sample documents** – ένα ζευγάρι αρχείων Word ή PDF για δοκιμή.

Χρειάζεστε επίσης βασική εξοικείωση με τις κλάσεις Java, το `pom.xml` του Maven και τη διαχείριση διαδρομών αρχείων. Εάν κάτι από αυτά σας είναι άγνωστο, κάντε παύση και ανασκοπήστε τα σχετικά βασικά πριν προχωρήσετε.

## Πώς να ορίσετε προσαρμοσμένα μεταδεδομένα java;
Φορτώστε τα αρχεία προέλευσης, διαμορφώστε ένα `Comparer` και στη συνέχεια εφαρμόστε έναν κατασκευαστή `FileAuthorMetadata` για να ενσωματώσετε τα προσαρμοσμένα πεδία. Το `Comparer` είναι η κύρια κλάση που εκτελεί τη σύγκριση εγγράφων και τη διαχείριση μεταδεδομένων. Το `FileAuthorMetadata` είναι μια κλάση builder που χρησιμοποιείται για να καθορίσει πεδία μεταδεδομένων σχετικών με τον συγγραφέα για το έγγραφο εξόδου. Αυτή η προσέγγιση εξασφαλίζει ότι τα μεταδεδομένα ενσωματώνονται πριν από οποιαδήποτε σύγκριση, διατηρώντας το ίχνος ελέγχου συνεπές μεταξύ των εκδόσεων. Θα δείτε επίσης πώς να διαχειριστείτε τις διαδρομές εξόδου και να χειριστείτε εξαιρέσεις. Τα παρακάτω βήματα σας καθοδηγούν μέσα από μια πλήρη, έτοιμη για παραγωγή υλοποίηση.

### Βήμα 1: ρυθμίστε τη διαδρομή εξόδου
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

**Pro tip:** Σε παραγωγή συνήθως δημιουργείτε αυτές τις διαδρομές δυναμικά—σκεφτείτε τη χρήση του `System.getProperty("java.io.tmpdir")` ή ενός αφιερωμένου φακέλου εξόδου που η CI/CD γραμμή σας μπορεί να καθαρίσει αυτόματα.

### Βήμα 2: αρχικοποιήστε το comparer και προσθέστε τα έγγραφα-στόχους
```java
import com.groupdocs.comparison.Comparer;

public class MetadataBasics {
    public static void main(String[] args) throws Exception {
        // This is your starting point - simple but functional
        try (Comparer comparer = new Comparer("path/to/your/source/document.docx")) {
            System.out.println("GroupDocs.Comparison initialized successfully!");
            // We'll build on this foundation
        }
    }
}
```

Εάν αντιμετωπίσετε εξαίρεση “file not found”, ελέγξτε ξανά ότι οι διαδρομές είναι απόλυτες κατά την ανάπτυξη· οι σχετικές διαδρομές συχνά επιλύονται διαφορετικά όταν η εφαρμογή εκτελείται από διαφορετικό τρέχον φάκελο.

### Βήμα 3: διαμορφώστε προσαρμοσμένα μεταδεδομένα (το σημαντικό μέρος)
```java
String outputFileName = "YOUR_OUTPUT_DIRECTORY/SetDocumentMetadataUserDefined.docx";
```

- `MetadataType.FILE_AUTHOR` λέει στο GroupDocs ποιο “bucket” μεταδεδομένων να επηρεάσει. `MetadataType.FILE_AUTHOR` προσδιορίζει το “bucket” μεταδεδομένων συγγραφέα που θα τροποποιήσει το GroupDocs.  
- Το `FileAuthorMetadata.Builder` ακολουθεί το κλασικό πρότυπο builder, επιτρέποντάς σας να ορίσετε πεδία συγγραφέα, εταιρείας και τελευταίου τροποποιητή με ασφαλή τύπο.  

### Βήμα 4: εκτελέστε τη σύγκριση και αποθηκεύστε το αποτέλεσμα
```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/SOURCE_WORD.docx")) {
    comparer.add("YOUR_DOCUMENT_DIRECTORY/TARGET1_WORD.docx");
    
    // This is where we'll add our metadata magic
}
```

Όταν ολοκληρωθεί η σύγκριση, το αρχείο εξόδου θα περιέχει τα ακριβή μεταδεδομένα που ορίσατε, διατηρώντας το ίχνος ελέγχου μεταξύ των αναθεωρήσεων.

## Πώς να συγκρίνετε έγγραφα με μεταδεδομένα;
Φορτώστε τα δύο αρχεία προέλευσης, δημιουργήστε ένα `Comparer`, περάστε το ίδιο `SaveOptions` που μεταφέρει τα προσαρμοσμένα μεταδεδομένα σας και καλέστε το `compare`. Το `SaveOptions` διαμορφώνει τη μορφή εξόδου και τη διαχείριση μεταδεδομένων για το αποτέλεσμα της σύγκρισης. Το προκύπτον έγγραφο κληρονομεί τα μεταδεδομένα που καθορίσατε, εξασφαλίζοντας ότι οι ελεγκτές μπορούν να δουν ποιος είναι ο συγγραφέας κάθε έκδοσης χωρίς να ανοίξουν το περιεχόμενο του αρχείου.

## Συνηθισμένα προβλήματα και πώς να τα διορθώσετε
### Πρόβλημα 1: τα μεταδεδομένα δεν εμφανίζονται στα έγγραφα εξόδου
**Solution:**  
1. Επιβεβαιώστε ότι χρησιμοποιείτε το GroupDocs.Comparison 25.2 ή νεότερο.  
2. Επαληθεύστε ότι και οι μορφές προέλευσης και προορισμού υποστηρίζουν τον τύπο μεταδεδομένων που επιλέξατε.  
3. Βεβαιωθείτε ότι ο φάκελος εξόδου είναι εγγράψιμος και ότι το αρχείο δεν είναι κλειδωμένο από άλλη διαδικασία.  
4. Ελέγξτε ξανά ότι το `setCloneMetadataType` είναι ορισμένο σε `MetadataType.FILE_AUTHOR` (ή το κατάλληλο enum) πριν από την αποθήκευση.

### Πρόβλημα 2: εξαιρέσεις πρόσβασης αρχείου
**Solution:**  
- Τυλίξτε το `Comparer` σε ένα μπλοκ try‑with‑resources ώστε να κλείνει αυτόματα.  
- Κλείστε τυχόν ανοιχτές προβολές (Word, Acrobat) που μπορεί να κλειδώνουν τα αρχεία.  
- Χορηγήστε δικαιώματα εγγραφής στον φάκελο εξόδου για το χρήστη που εκτελεί το JVM.

### Πρόβλημα 3: προβλήματα αντικατάστασης μεταδεδομένων
**Solution:** Χρησιμοποιήστε το `setCloneMetadataType()` για να ελέγξετε αν τα υπάρχοντα μεταδεδομένα θα διατηρηθούν, θα συγχωνευτούν ή θα αντικατασταθούν. Εάν χρειάζεται να διατηρήσετε ορισμένα αρχικά πεδία, διαβάστε τα πρώτα με το `Metadata` API, συγχωνεύστε τα με τις προσαρμοσμένες τιμές σας, και στη συνέχεια γράψτε τα ξανά. Το `Metadata` API επιτρέπει την ανάγνωση υπαρχουσών ιδιοτήτων εγγράφου όπως συγγραφέας, τίτλος και προσαρμοσμένα πεδία.

## Πραγματικές εφαρμογές και περιπτώσεις χρήσης
### Περίπτωση χρήσης 1: διαχείριση νομικών εγγράφων
Οι νομικές εταιρείες μπορούν αυτόματα να σφραγίζουν ονόματα ελεγκτών, αριθμούς υποθέσεων και επίπεδα εμπιστευτικότητας, δημιουργώντας ένα ανθεκτικό στην παραποίηση ίχνος ελέγχου που ικανοποιεί τις απαιτήσεις του δικαστηρίου.

```java
final Path resultPath = comparer.compare(outputFileName,
        new SaveOptions.Builder()
                .setCloneMetadataType(MetadataType.FILE_AUTHOR)
                .setFileAuthorMetadata(
                        new FileAuthorMetadata.Builder()
                                .setAuthor("Tom")
                                .setCompany("GroupDocs")
                                .setLastSaveBy("Jack")
                                .build())
                .build());
```

### Περίπτωση χρήσης 2: συνεργασία ακαδημαϊκής έρευνας
Οι ερευνητικές ομάδες μπορούν να ενσωματώσουν ταυτοποιητικά συντελεστών και αριθμούς επιχορηγήσεων, καθιστώντας εύκολο το δημιουργία αναφορών συμμόρφωσης για τις χρηματοδοτικές αρχές.

```java
SaveOptions saveOptions = new SaveOptions.Builder()
        .setCloneMetadataType(MetadataType.FILE_AUTHOR)
        .setFileAuthorMetadata(
                new FileAuthorMetadata.Builder()
                        .setAuthor("Tom")
                        .setCompany("GroupDocs")
                        .setLastSaveBy("Jack")
                        .build())
        .build();

// Now you can reuse this configuration across multiple comparisons
```

### Περίπτωση χρήσης 3: ροές εργασίας τεκμηρίωσης λογισμικού
Οι ομάδες ανάπτυξης μπορούν να αυτοματοποιήσουν την επισήμανση εκδόσεων και την ανάθεση συγγραφέα για σημειώσεις κυκλοφορίας, διασφαλίζοντας ότι κάθε αλλαγή είναι ανιχνεύσιμη πίσω σε ένα commit ή εισιτήριο.

```java
public SaveOptions buildMetadataOptions(String author, String company, boolean preserveOriginal) {
    SaveOptions.Builder builder = new SaveOptions.Builder()
            .setCloneMetadataType(MetadataType.FILE_AUTHOR);
    
    if (!preserveOriginal) {
        builder.setFileAuthorMetadata(
                new FileAuthorMetadata.Builder()
                        .setAuthor(author)
                        .setCompany(company)
                        .setLastSaveBy(getCurrentUser())
                        .build());
    }
    
    return builder.build();
}
```

Αυτά τα σενάρια ενσωματώνονται ομαλά με SharePoint, Office 365, CI/CD pipelines και προσαρμοσμένα συστήματα διαχείρισης περιεχομένου, επιτρέποντάς σας να διαδίδετε τα μεταδεδομένα σε όλο το επιχειρησιακό στοίβα.

## Συμβουλές βελτιστοποίησης απόδοσης
### Βέλτιστες πρακτικές διαχείρισης μνήμης
```java
// Automatically set reviewer and review date for legal documents
FileAuthorMetadata legalMetadata = new FileAuthorMetadata.Builder()
        .setAuthor(getCurrentReviewer())
        .setCompany("Legal Department")
        .setLastSaveBy(getCurrentReviewer())
        .build();
```

- Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `SaveOptions` όταν επεξεργάζεστε πολλά αρχεία.  
- Επεξεργαστείτε έγγραφα σε παρτίδες των 10‑20 για να διατηρήσετε τη χρήση του heap υπό έλεγχο.  
- Ενεργοποιήστε τον G1 garbage collector της Java για μεγάλου όγκου εργασίες.

### Συστάσεις επεξεργασίας παρτίδων
Όταν χρειάζεται να διαχειριστείτε χιλιάδες αρχεία, σκεφτείτε ένα πρότυπο παραγωγέα‑καταναλωτή: μια μικρή ομάδα νήματος εργατών διαβάζει αρχεία, εφαρμόζει μεταδεδομένα και γράφει τα αποτελέσματα σε έναν προσωρινό φάκελο. Παρακολουθήστε τον αριθμό των ανοιχτών χειριστών αρχείων για να αποφύγετε σφάλματα “Too many open files”.

### Οδηγίες χρήσης πόρων
- **Heap:** Διατηρήστε τη χρήση κάτω από 75 % του μέγιστου heap του JVM για σταθερότητα.  
- **Disk:** Εξασφαλίστε τουλάχιστον 2 GB ελεύθερου χώρου ανά 100 MB πηγής υλικού, καθώς δημιουργούνται προσωρινά αρχεία σύγκρισης κατά την επεξεργασία.

## Προχωρημένες συμβουλές και βέλτιστες πρακτικές
### Δυναμικά μεταδεδομένα βάσει περιβάλλοντος
```java
// Track multiple contributors in research documents
FileAuthorMetadata researchMetadata = new FileAuthorMetadata.Builder()
        .setAuthor("Dr. Smith")
        .setCompany("University Research Lab")
        .setLastSaveBy("Research Assistant")
        .build();
```

Ανακτήστε τα ονόματα συγγραφέων από το ιστορικό commit του Git, τα IDs έργων από μια βάση δεδομένων ή τις χρονικές σφραγίδες από το περιβάλλον κατασκευής CI για να διατηρήσετε τα μεταδεδομένα συγχρονισμένα με τον κύκλο ζωής της ανάπτυξής σας.

### Διαχείριση σφαλμάτων που πραγματικά βοηθά
```java
// Integrate with version control systems
FileAuthorMetadata devMetadata = new FileAuthorMetadata.Builder()
        .setAuthor(getGitUsername())
        .setCompany("Development Team")
        .setLastSaveBy(getCurrentDeveloper())
        .build();
```

Τυλίξτε κάθε σύγκριση σε ένα μπλοκ try‑catch που καταγράφει το όνομα του αρχείου, τον τύπο της εξαίρεσης και το stack trace. Αυτό κάνει την αντιμετώπιση προβλημάτων των παρτίδων πολύ πιο εύκολη.

### Διαχείριση διαμόρφωσης
Εξωτερικεύστε τα πρότυπα μεταδεδομένων σας σε αρχεία JSON ή YAML ώστε μη‑προγραμματιστές να μπορούν να προσαρμόσουν τα πεδία συγγραφέα χωρίς επαναμεταγλώττιση.

```java
// Good: Proper resource management
try (Comparer comparer = new Comparer("source.docx")) {
    // Do your comparison work here
    // Resources automatically cleaned up
}

// Avoid: Manual resource management
Comparer comparer = new Comparer("source.docx");
// Easy to forget cleanup, leading to memory leaks
```

## Συχνές ερωτήσεις
**Q: Πώς διαχειρίζομαι τα μεταδεδομένα για διαφορετικές μορφές εγγράφων;**  
A: Το GroupDocs.Comparison υποστηρίζει μεταδεδομένα για Word, PDF, Excel, PowerPoint και αρκετές μορφές εικόνας. Χρησιμοποιήστε το κατάλληλο enum `MetadataType` (π.χ., `FILE_AUTHOR` για Word, `PDF_AUTHOR` για PDFs) και δοκιμάστε κάθε μορφή νωρίς στη γραμμή σας.

**Q: Μπορώ να διαβάσω τα υπάρχοντα μεταδεδομένα πριν τα τροποποιήσω;**  
A: Ναι. Καλέστε το `Metadata` API σε ένα φορτωμένο έγγραφο για να ανακτήσετε τις τρέχουσες τιμές, συγχωνεύστε τις με τα προσαρμοσμένα πεδία σας και, στη συνέχεια, γράψτε το συνδυασμένο σύνολο πίσω στο αρχείο.

**Q: Τι συμβαίνει με τα μεταδεδομένα κατά τη σύγκριση εγγράφων;**  
A: Από προεπιλογή το GroupDocs μπορεί να διατηρήσει τα μεταδεδομένα προέλευσης. Χρησιμοποιώντας το `setCloneMetadataType()` έχετε σαφή έλεγχο—επιλέξτε να κλωνοποιήσετε, να αντικαταστήσετε ή να αγνοήσετε τα μεταδεδομένα όπως απαιτείται.

**Q: Υπάρχει επίπτωση στην απόδοση από τον ορισμό προσαρμοσμένων μεταδεδομένων;**  
A: Το κόστος είναι αμελητέο σε σχέση με τον βασικό αλγόριθμο σύγκρισης. Σε δοκιμές, η προσθήκη μεταδεδομένων σε αρχείο Word 200 σελίδων προσθέτει λιγότερο από 0,2 δευτερόλεπτα σε μια εκτέλεση σύγκρισης 3 δευτερολέπτων.

**Q: Πώς μπορώ να ενσωματώσω αυτό με συστήματα ελέγχου εκδόσεων;**  
A: Συνδέστε το με post‑commit του Git ή pipelines CI για να καλέσετε τη ρουτίνα σύγκρισης, περνώντας τον συγγραφέα του commit και το hash ως τιμές μεταδεδομένων. Αυτό συνδέει αυτόματα κάθε παραγόμενο έγγραφο με μια συγκεκριμένη αλλαγή πηγαίου κώδικα.

**Τελευταία ενημέρωση:** 2026-09-10  
**Δοκιμή με:** GroupDocs.Comparison 25.2 for Java  
**Συγγραφέας:** GroupDocs

```java
public FileAuthorMetadata createContextualMetadata(DocumentContext context) {
    return new FileAuthorMetadata.Builder()
            .setAuthor(context.getCurrentUser())
            .setCompany(context.getOrganization())
            .setLastSaveBy(context.getLastModifier())
            .build();
}
```

```java
try (Comparer comparer = new Comparer(sourceFile)) {
    comparer.add(targetFile);
    comparer.compare(outputFile, saveOptions);
} catch (Exception e) {
    logger.error("Failed to process document: " + sourceFile, e);
    // Implement your error handling strategy
    throw new DocumentProcessingException("Comparison failed", e);
}
```

```java
// Load from properties file or database
Properties metadataConfig = loadMetadataConfiguration();
FileAuthorMetadata metadata = new FileAuthorMetadata.Builder()
        .setAuthor(metadataConfig.getProperty("default.author"))
        .setCompany(metadataConfig.getProperty("default.company"))
        .build();
```

## Σχετικά μαθήματα

- [Ορισμός μεταδεδομένων εγγράφου σε Java με το GroupDocs.Comparison](/comparison/java/metadata-management/implement-metadata-groupdocs-comparison-java-guide/)
- [compare pdf java – Πλήρης οδηγός GroupDocs.Comparison για έγγραφα Word](/comparison/java/basic-comparison/java-groupdocs-comparison-document-management-guide/)
- [Πώς να χρησιμοποιήσετε άδεια: Οδηγός διαμόρφωσης URL για GroupDocs Comparison Java](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)