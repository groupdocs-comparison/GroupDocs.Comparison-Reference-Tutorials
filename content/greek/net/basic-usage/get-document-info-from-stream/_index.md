---
categories:
- Document Processing
date: '2026-07-01'
description: Μάθετε πώς να διαβάζετε μεταδεδομένα αρχείου C# χρησιμοποιώντας το GroupDocs.Comparison,
  να εξάγετε το file size stream και να λαμβάνετε αποτελεσματικά το document properties
  stream.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Εξαγωγή Πληροφοριών Εγγράφου .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: Ανάγνωση Μεταδεδομένων Αρχείου C# – Εξαγωγή Πληροφοριών Εγγράφου από Streams
type: docs
url: /el/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Ανάγνωση Μεταδεδομένων Αρχείου C# – Εξαγωγή Πληροφοριών Εγγράφου από Ροές

## Εισαγωγή

Η ανάγνωση μεταδεδομένων αρχείου σε C# χωρίς τη φόρτωση ολόκληρου του εγγράφου είναι μια κοινή απαίτηση για τις σύγχρονες εφαρμογές .NET. **Read file metadata C#** σας επιτρέπει να επικυρώνετε μεταφορτώσεις, να εμφανίζετε λεπτομέρειες εγγράφου και να λαμβάνετε αποφάσεις επεξεργασίας διατηρώντας χαμηλή χρήση μνήμης. Το GroupDocs.Comparison για .NET παρέχει ένα γρήγορο, βασισμένο σε ροή API που εξάγει τον τύπο αρχείου, τον αριθμό σελίδων, το μέγεθος και άλλες ιδιότητες απευθείας από ένα `Stream`. Στις επόμενες ενότητες θα δείτε γιατί είναι σημαντικό, πώς να το ρυθμίσετε και κώδικα βήμα‑βήμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “read file metadata C#”;** Σημαίνει την ανάκτηση των ιδιοτήτων ενός εγγράφου (τύπος, σελίδες, μέγεθος) μέσω μιας ροής .NET χωρίς τη φόρτωση του πλήρους περιεχομένου.  
- **Ποια βιβλιοθήκη το διαχειρίζεται;** Το GroupDocs.Comparison για .NET προσφέρει τη μέθοδο `GetDocumentInfo()` για γρήγορη εξαγωγή μεταδεδομένων.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για ανάπτυξη· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να το χρησιμοποιήσω με μεγάλα PDF;** Ναι – η προσέγγιση με ροή επεξεργάζεται αρχεία με εκατοντάδες σελίδες χωρίς υψηλή κατανάλωση μνήμης.  
- **Είναι συμβατό με .NET 6+;** Απολύτως, η βιβλιοθήκη στοχεύει στο .NET Standard 2.0 και λειτουργεί σε .NET 6, .NET 7 και .NET Core.

## Τι είναι η ανάγνωση μεταδεδομένων αρχείου C#

`Read file metadata C#` αναφέρεται στην απόκτηση περιγραφικών πληροφοριών ενός εγγράφου—όπως μορφή, αριθμός σελίδων και μέγεθος σε bytes—χρησιμοποιώντας κώδικα C# που λειτουργεί με ροές. Αυτή η τεχνική αποφεύγει τη φόρτωση ολόκληρου του αρχείου στη μνήμη, κάτι που είναι ιδιαίτερα χρήσιμο για μεγάλα PDF, αρχεία DOCX ή λειτουργίες σε παρτίδες.

## Γιατί να χρησιμοποιήσετε την εξαγωγή μεταδεδομένων GroupDocs από ροές;

Το GroupDocs.Comparison υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου** και μπορεί να εξάγει μεταδεδομένα από αρχεία έως **2 GB** σε μέγεθος διατηρώντας τη χρήση μνήμης κάτω από **10 MB**. Η βιβλιοθήκη διαβάζει μόνο τις απαραίτητες ενότητες κεφαλίδας, παρέχοντας αποτελέσματα σε **κάτω από 150 ms** για τυπικά PDF 100 σελίδων σε έναν τυπικό διακομιστή. Αυτά τα ποσοτικοποιημένα οφέλη μεταφράζονται σε ταχύτερη επικύρωση μεταφορτώσεων, χαμηλότερο κόστος cloud και πιο ομαλή εμπειρία χρήστη.

## Απαιτούμενα και Ρύθμιση

### 1. Εγκατάσταση GroupDocs.Comparison για .NET
Κατεβάστε το τελευταίο πακέτο από την [official download page](https://releases.groupdocs.com/comparison/net/). Εάν προτιμάτε το NuGet, εκτελέστε:

```
Install-Package GroupDocs.Comparison
```

### 2. Βασικές Γνώσεις Ανάπτυξης .NET
Θα πρέπει να είστε άνετοι με τη C# και το μοντέλο I/O του .NET. Η εργασία με `Stream`, `FileStream` και `MemoryStream` είναι ουσιώδης για τα παρακάτω παραδείγματα.

### 3. Περιβάλλον Ανάπτυξης
Το Visual Studio, το VS Code ή το JetBrains Rider υποστηρίζονται όλα. Βεβαιωθείτε ότι το έργο σας στοχεύει σε .NET 6 ή νεότερο για την καλύτερη απόδοση.

## Πώς να διαβάσετε μεταδεδομένα αρχείου C# από ροή;

Φορτώστε το έγγραφο με ένα `FileStream`, δημιουργήστε ένα `Comparer` και καλέστε το `GetDocumentInfo()`. Η ολόκληρη λειτουργία απαιτεί μόνο δύο γραμμές κώδικα και επιστρέφει ένα αντικείμενο `IDocumentInfo` που περιέχει τον τύπο αρχείου, τον αριθμό σελίδων και το μέγεθος. Εσωτερικά η βιβλιοθήκη διαβάζει μόνο τα απαραίτητα bytes της κεφαλίδας, έτσι ακόμη και μεγάλα PDF επεξεργάζονται γρήγορα χωρίς να καταναλώνουν σημαντική μνήμη.  
`Comparer` είναι η κύρια κλάση του GroupDocs.Comparison που οργανώνει την ανάλυση εγγράφων.  
`GetDocumentInfo()` επιστρέφει ένα αντικείμενο `IDocumentInfo` με βασικά μεταδεδομένα.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Βήμα 1: Αρχικοποίηση του Αντικειμένου Comparer με Ροή

Το παρακάτω απόσπασμα δημιουργεί μια παρουσία `Comparer` από ένα μόνο‑ανάγνωση `FileStream`. Η χρήση ενός μπλοκ `using` εγγυάται ότι η ροή κλείνει και ο comparer απελευθερώνεται, αποτρέποντας κλειδώματα αρχείων.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Βήμα 2: Εξαγωγή Πληροφοριών Εγγράφου

Καλώντας το `GetDocumentInfo()` επιστρέφεται ένα αντικείμενο `IDocumentInfo` που περιέχει όλα τα μεταδεδομένα που χρειάζεστε. Η μέθοδος διαβάζει μόνο τα απαραίτητα τμήματα της κεφαλίδας του αρχείου, έτσι ακόμη και ένα PDF 500 σελίδων επεξεργάζεται σε κλάσμα δευτερολέπτου.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Βήμα 3: Εμφάνιση και Χρήση Πληροφοριών Εγγράφου

Τώρα μπορείτε να έχετε πρόσβαση στις ιδιότητες `FileType`, `PageCount` και `Size`. Σε παραγωγή μπορεί να αποθηκεύσετε αυτές τις τιμές σε βάση δεδομένων, να τις εκθέσετε μέσω API ή να τις χρησιμοποιήσετε για να αποφασίσετε αν θα αποδεχθείτε μια μεταφόρτωση.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Κοινές Περιπτώσεις Χρήσης και Πρότυπα Υλοποίησης

### Επικύρωση Μεταφόρτωσης Αρχείου

Όταν ένας χρήστης μεταφορτώνει ένα έγγραφο, μπορείτε αμέσως να επαληθεύσετε τον τύπο και τον αριθμό σελίδων του πριν το αποθηκεύσετε. Αυτό αποτρέπει ανεπιθύμητες μορφές και υπερμεγέθη αρχεία να εισέλθουν στο σύστημά σας.

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### Ανάλυση Εγγράφων σε Παρτίδες

Επεξεργάζεστε έναν φάκελο εγγράφων; Εξάγετε πρώτα τα μεταδεδομένα για να δρομολογήσετε τα αρχεία σε διαφορετικές ροές εργασίας—π.χ., μεγάλα PDF πηγαίνουν σε ασύγχρονο worker, ενώ αρχεία μίας σελίδας διαχειρίζονται εντός της ροής.

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## Κοινά Προβλήματα και Λύσεις

### Προβλήματα Πρόσβασης και Κλειδώματος Αρχείου

**Πρόβλημα**: “The file is being used by another process.”  
**Λύση**: Wrap the stream in a `using` statement and, if necessary, implement a retry policy with exponential back‑off.

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### Διαχείριση Μη Υποστηριζόμενης Μορφής Αρχείου

**Πρόβλημα**: Το API ρίχνει εξαίρεση για άγνωστη μορφή.  
**Λύση**: Εξετάστε την ιδιότητα `FileType`; εάν επιστρέφει `Unknown`, επιστρέψτε ένα φιλικό σφάλμα στον καλούντα και καταγράψτε το περιστατικό.

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### Διαχείριση Μνήμης με Μεγάλα Αρχεία

**Πρόβλημα**: Αύξηση μνήμης κατά την επεξεργασία πολύ μεγάλων εγγράφων.  
**Λύση**: Η προσέγγιση με ροή ήδη ελαχιστοποιεί τη χρήση μνήμης, αλλά θα πρέπει επίσης να καλέσετε `Dispose()` στο `Comparer` μόλις τελειώσετε και να αποφεύγετε τη διατήρηση αναφορών στο `IDocumentInfo` περισσότερο από το απαραίτητο.

## Παρατηρήσεις Απόδοσης και Καλές Πρακτικές

### Καλές Πρακτικές Διαχείρισης Ροής

1. **Πάντα χρησιμοποιείτε δηλώσεις `using`** – Εγγυάται την απελευθέρωση και απελευθερώνει πόρους άμεσα.  
2. **Επαναφέρετε τη θέση της ροής όταν την επαναχρησιμοποιείτε** – Εάν χρειάζεται να διαβάσετε την ίδια ροή δύο φορές, καλέστε `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Επιλέξτε τον κατάλληλο τύπο ροής** – `FileStream` για αρχεία δίσκου, `MemoryStream` για δεδομένα στη μνήμη, `NetworkStream` για απομακρυσμένες πηγές.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Πότε να Προτιμήσετε Αυτή την Προσέγγιση έναντι Πλήρους Φόρτωσης Εγγράφου

**Προτιμήστε εξαγωγή μεταδεδομένων με βάση τη ροή όταν**:
- Χρειάζεστε μόνο υψηλού επιπέδου λεπτομέρειες (τύπος, σελίδες, μέγεθος).
- Επικυρώνετε μεταφορτώσεις ή δημιουργείτε κατάλογο εγγράφων.
- Η απόδοση και το χαμηλό αποτύπωμα μνήμης είναι κρίσιμα.

**Μεταβείτε σε πλήρη επεξεργασία εγγράφου όταν**:
- Χρειάζεται να συγκρίνετε περιεχόμενο, να εξάγετε κείμενο ή να αποδώσετε σελίδες.
- Απαιτείται βαθιά ανάλυση (π.χ., OCR, ανίχνευση υδατογραφήματος).

## Προηγμένες Συμβουλές για Χρήση σε Παραγωγή

### Ανθεκτικές Στρατηγικές Διαχείρισης Σφαλμάτων

Τυλίξτε όλες τις λειτουργίες σε μπλοκ try‑catch που συλλαμβάνει το `GroupDocs.Comparison.Exceptions.ComparisonException`. Το `ComparisonException` ρίχνεται από τη βιβλιοθήκη όταν συμβαίνει σφάλμα κατά την επεξεργασία εγγράφου. Καταγράψτε τις λεπτομέρειες του σφάλματος, επιστρέψτε μια τυποποιημένη απάντηση σφάλματος και εξασφαλίστε ότι το `Comparer` απελευθερώνεται σε ένα μπλοκ `finally`.

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### Ενσωμάτωση με Καταγραφή και Παρακολούθηση

Ενσωματώστε ένα πλαίσιο καταγραφής (π.χ., Serilog ή NLog) και εκδώστε μετρικές όπως χρόνος επεξεργασίας, μέγεθος αρχείου και αριθμοί επιτυχιών/αποτυχιών. Αυτά τα δεδομένα σας βοηθούν να εντοπίζετε νωρίς υποβάθμιση της απόδοσης.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Συχνές Ερωτήσεις

**Q: Είναι το GroupDocs.Comparison για .NET συμβατό με διαφορετικές μορφές εγγράφων;**  
A: Ναι. Η βιβλιοθήκη υποστηρίζει **πάνω από 50 μορφές αρχείων**, συμπεριλαμβανομένων των DOCX, PDF, XLSX, PPTX και πολλών τύπων εικόνων, καθιστώντας την κατάλληλη για σχεδόν οποιαδήποτε ροή εργασίας εγγράφων.

**Q: Μπορώ να δοκιμάσω το GroupDocs.Comparison για .NET πριν την αγορά;**  
A: Απολύτως. Μια δωρεάν δοκιμή είναι διαθέσιμη στην [the website](https://releases.groupdocs.com/), επιτρέποντάς σας να αξιολογήσετε όλες τις λειτουργίες χωρίς άδεια.

**Q: Πού μπορώ να βρω υποστήριξη για το GroupDocs.Comparison για .NET;**  
A: Μπορείτε να λάβετε βοήθεια στο [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12), όπου η κοινότητα και η ομάδα προϊόντος απαντούν σε ερωτήσεις άμεσα.

**Q: Διατίθενται προσωρινές άδειες για δοκιμές;**  
A: Ναι. Προσωρινές άδειες μπορούν να ληφθούν από τη [the licensing page](https://purchase.groupdocs.com/temporary-license/), ιδανικές για περιβάλλοντα ανάπτυξης και QA.

**Q: Είναι το GroupDocs.Comparison για .NET κατάλληλο για επιχειρησιακές αναπτύξεις;**  
A: Απολύτως. Προσφέρει απόδοση επιπέδου enterprise, εκτενή υποστήριξη μορφών και ανθεκτική διαχείριση σφαλμάτων, όλα απαραίτητα για μεγάλης κλίμακας συστήματα παραγωγής.

**Τελευταία Ενημέρωση:** 2026-07-01  
**Δοκιμή Με:** GroupDocs.Comparison 23.10 for .NET  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Λήψη Ιδιοτήτων Εγγράφου C# .NET - Εξαγωγή Μεταδεδομένων Αρχείου](/comparison/net/basic-usage/get-document-info-from-path/)
- [Διαχείριση Μεταδεδομένων Εγγράφου .NET - Πλήρης Οδηγός για το GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Μάθημα Σύγκρισης Εγγράφων .NET - Διατήρηση Μεταδεδομένων με το GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)