---
categories:
- Document Comparison
date: '2026-03-06'
description: Μάθετε πώς να διατηρείτε τα μεταδεδομένα προορισμού κατά τη σύγκριση
  εγγράφων χρησιμοποιώντας το GroupDocs.Comparison για .NET. Οδηγός βήμα‑βήμα με παραδείγματα
  C#.
keywords: preserve target metadata, GroupDocs.Comparison metadata preservation, .NET
  document comparison, metadata preservation tutorial
lastmod: '2026-03-06'
linktitle: Metadata Preservation Tutorial
tags:
- GroupDocs.Comparison
- metadata-preservation
- dotnet-tutorial
- document-management
title: Διατήρηση των Μεταδεδομένων Στόχου με το GroupDocs.Comparison – Οδηγός .NET
type: docs
url: /el/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# Διατήρηση Μεταδεδομένων Στόχου με το GroupDocs.Comparison – .NET Tutorial

## Εισαγωγή

Σας έχει συμβεί ποτέ να συγκρίνετε δύο έγγραφα και να χάσετε σημαντικά μεταδεδομένα στη διαδικασία; Δεν είστε μόνοι. Όταν χρειάζεται να **διατηρήσετε τα μεταδεδομένα στόχου** κατά τη σύγκριση εγγράφων σε μια εφαρμογή .NET, η εργασία μπορεί να φαίνεται δύσκολη—αλλά δεν χρειάζεται να είναι.

Το GroupDocs.Comparison για .NET σας επιτρέπει να αποφασίσετε ποια μεταδεδομένα εγγράφου θα παραμείνουν στο αποτέλεσμα της σύγκρισης. Είτε δημιουργείτε σύστημα διαχείρισης εγγράφων, είτε διαχειρίζεστε νομικές συμβάσεις, είτε διαχειρίζεστε συνεργατικό περιεχόμενο, θα θέλετε τα μεταδεδομένα από το σωστό έγγραφο προέλευσης κάθε φορά.

Σε αυτό το εκπαιδευτικό θα μάθετε πώς να **διατηρήσετε τα μεταδεδομένα στόχου** κατά τη σύγκριση, να αποφύγετε κοινές παγίδες και να υλοποιήσετε τη λύση σε πραγματικά σενάρια.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “διατήρηση μεταδεδομένων στόχου”;** Διατηρεί τα μεταδεδομένα (συγγραφέας, ημερομηνία δημιουργίας, προσαρμοσμένες ιδιότητες κ.λπ.) από το έγγραφο που ορίζετε ως στόχο κατά τη δημιουργία του αποτελέσματος σύγκρισης.  
- **Ποια έκδοση του GroupDocs.Comparison απαιτείται;** Έκδοση 25.4.0 ή νεότερη.  
- **Μπορώ να το χρησιμοποιήσω με .NET Core;** Ναι – .NET Core 2.0+ ή .NET Framework 4.6.1+.  
- **Απαιτείται άδεια για παραγωγή;** Απαιτείται εμπορική άδεια για παραγωγή· μια δωρεάν δοκιμή λειτουργεί για εκμάθηση.  
- **Θα λειτουργεί η δυνατότητα με PDF και DOCX;** Ναι – όλες οι κύριες μορφές Office και PDF υποστηρίζουν τη διατήρηση μεταδεδομένων.

## Γιατί η Διατήρηση Μεταδεδομένων Είναι Σημαντική

Πριν βυθιστούμε στον κώδικα, ας συζητήσουμε γιατί η διατήρηση των μεταδεδομένων στόχου είναι σημαντική. Τα μεταδεδομένα εγγράφου δεν είναι μόνο “ωραία να έχουν”—συχνά απαιτούνται νομικά ή είναι κρίσιμα για την επιχείρηση:

- **Νομικά έγγραφα** – χρειάζεται να διατηρηθούν οι ενδείξεις προνομίου δικηγόρου‑πελάτη.  
- **Εταιρικά αρχεία** – πρέπει να διατηρούν ετικέτες συμμόρφωσης και αλυσίδες έγκρισης.  
- **Ακαδημαϊκές εργασίες** – η απόδοση συγγραφέα και το ιστορικό αναθεωρήσεων είναι απαραίτητα.  
- **Τεχνική τεκμηρίωση** – ο έλεγχος εκδόσεων και η κατάσταση ανασκόπησης έχουν σημασία.

Χωρίς σωστή διαχείριση, μπορεί να αφαιρέσετε τυχαία πληροφορίες που χρειάστηκε μήνες να δημιουργηθούν. Εδώ είναι που η επιλογή **διατήρησης μεταδεδομένων στόχου** ξεχωρίζει.

## Προαπαιτούμενα

### Απαιτούμενες Βιβλιοθήκες και Εκδόσεις
- **GroupDocs.Comparison for .NET**: Έκδοση 25.4.0 ή νεότερη (παλαιότερες εκδόσεις έχουν περιορισμένες επιλογές μεταδεδομένων).  
- **.NET Framework**: 4.6.1 ή υψηλότερη, ή .NET Core 2.0+.

### Ρύθμιση Περιβάλλοντος
- Visual Studio (ή οποιοδήποτε IDE C# προτιμάτε).  
- Βασικές γνώσεις C# (τίποτα πολύ προχωρημένο, υπόσχομαι!).  
- Δύο δείγματα εγγράφων για δοκιμή (Word *.docx* λειτουργεί εξαιρετικά).

### Προαπαιτούμενες Γνώσεις
Δεν χρειάζεται να είστε ειδικός στο GroupDocs, αλλά θα πρέπει να αισθάνεστε άνετα με:
- τις δηλώσεις `using` του C# και τη διαχείριση αρχείων.  
- βασικές έννοιες επεξεργασίας εγγράφων.  
- τι είναι τα μεταδεδομένα (συγγραφέας, τίτλος, προσαρμοσμένες ιδιότητες κ.λπ.).

Έτοιμοι; Ας το ρυθμίσουμε.

## Ρύθμιση του GroupDocs.Comparison για .NET

Η εγκατάσταση του GroupDocs.Comparison είναι απλή, αλλά υπάρχουν μερικά κόλπα που πρέπει να προσέξετε.

### Επιλογές Εγκατάστασης

**NuGet Package Manager Console** (easiest method):
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI** (if you prefer command line):
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**Συμβουλή**: Πάντα να καθορίζετε την έκδοση για να αποφύγετε απρόσμενες αλλαγές που σπάζουν το έργο σας.

### Απόκτηση Άδειας
Εδώ πολλοί προγραμματιστές κολλάνε στην αρχή. Το GroupDocs.Comparison δεν είναι δωρεάν, αλλά έχετε επιλογές:

- **Δωρεάν Δοκιμή** – πλήρης λειτουργικότητα για 30 ημέρες, ιδανική για αξιολόγηση.  
- **Προσωρινή Άδεια** – παρατεταμένη περίοδος αξιολόγησης αν χρειάζεστε περισσότερο χρόνο.  
- **Εμπορική Άδεια** – για χρήση σε παραγωγή (διαθέσιμα διάφορα επίπεδα τιμολόγησης).

Μην ανησυχείτε για την άδεια αυτή τη στιγμή αν απλώς μαθαίνετε—η έκδοση δοκιμής περιλαμβάνει όλες τις δυνατότητες **διατήρησης μεταδεδομένων στόχου**.

### Βασικός Έλεγχος Ρύθμισης

Ας βεβαιωθούμε ότι όλα λειτουργούν με ένα απλό τεστ:
```csharp
using System.IO;
using GroupDocs.Comparison;

string sourceFilePath = "source.docx";
string targetFilePath = "target.docx";

// Initialize the Comparer object.
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // Add the target document for comparison.
    comparer.Add(targetFilePath);
}
```

Αν αυτό μεταγλωττιστεί χωρίς σφάλματα, είστε έτοιμοι. Αν όχι, ελέγξτε ξανά την εγκατάσταση του πακέτου και τις δηλώσεις `using`.

## Πώς να Διατηρήσετε Τα Μεταδεδομένα Στόχου

Τώρα το κύριο θέμα—να διατηρήσουμε πραγματικά τα μεταδεδομένα κατά τη σύγκριση εγγράφων. Εδώ το GroupDocs.Comparison λάμπει πραγματικά.

### Κατανόηση της Ροής των Μεταδεδομένων

Κατά τη διάρκεια μιας τυπικής σύγκρισης:

1. **Πηγαίο έγγραφο** παρέχει το βασικό περιεχόμενο.  
2. **Έγγραφο στόχου** παρέχει τις αλλαγές για σύγκριση.  
3. Το **έγγραφο εξόδου** συνδυάζει και τα δύο, αλλά ποια μεταδεδομένα κερδίζουν;

Από προεπιλογή, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα του πηγαίου εγγράφου. Για να **διατηρήσετε τα μεταδεδομένα στόχου**, πρέπει να το δηλώσετε ρητά στην API.

### Υλοποίηση Βήμα‑Βήμα

#### Βήμα 1: Αρχικοποίηση του Αντικειμένου Comparer
Αυτό καθορίζει το “baseline” έγγραφο—αυτό που συγκρίνετε εναντίον του:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**Γιατί να χρησιμοποιείτε δηλώσεις `using`;** Αυτές απελευθερώνουν αυτόματα τους πόρους, αποτρέποντας διαρροές μνήμης κατά την επεξεργασία μεγάλων εγγράφων. Πιστέψτε με, θα σας ευχαριστήσετε αργότερα όταν δουλεύετε με αρχεία Word 50 MB.

#### Βήμα 2: Προσθήκη του Εγγράφου Στόχου
Δηλώστε στο comparer ποιο έγγραφο περιέχει τις αλλαγές που θέλετε να αναλύσετε:
```csharp
comparer.Add(targetFilePath);
```

**Συνηθισμένο λάθος**: Συγχυση μεταξύ πηγής και στόχου. Σκεφτείτε το έτσι—η πηγή είναι το “αρχικό” σας, ο στόχος είναι η “ενημερωμένη έκδοση”.

#### Βήμα 3: Ορισμός Τύπου Μεταδεδομένων (Εδώ Συμβαίνει η Μαγεία)
Καθορίστε ποια μεταδεδομένα εγγράφου πρέπει να διατηρηθούν στην έξοδο:
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**Τι συμβαίνει;** `CloneMetadataType = MetadataType.Target` λέει στο GroupDocs.Comparison: “Θέλω να κρατήσω τα μεταδεδομένα του εγγράφου στόχου στο τελικό αποτέλεσμα.”

### Πλήρες Παράδειγμα Εργασίας

Εδώ είναι όλα μαζί σε ένα εκτελέσιμο πρόγραμμα:
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            string sourceFile = "original_document.docx";
            string targetFile = "updated_document.docx";
            string outputFile = "comparison_result.docx";
            
            using (Comparer comparer = new Comparer(sourceFile))
            {
                comparer.Add(targetFile);
                
                // Preserve target document metadata
                comparer.Compare(outputFile, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                
                Console.WriteLine($"Comparison completed! Check {outputFile}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error during comparison: {ex.Message}");
        }
    }
}
```

### Συνηθισμένα Πάγια Λάθη που Πρέπει να Αποφύγετε

- **Προβλήματα Διαδρομής Αρχείου** – χρησιμοποιείτε πάντα πλήρεις διαδρομές ή βεβαιωθείτε ότι τα αρχεία σας βρίσκονται στον τρέχοντα φάκελο:
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

- **Διαχείριση Μνήμης** – για μεγάλα έγγραφα, πάντα τυλίξτε τα αντικείμενα `Comparer` σε δηλώσεις `using`.  

- **Συμβατότητα Έκδοσης** – διαφορετικές εκδόσεις του GroupDocs.Comparison εκθέτουν διαφορετικές επιλογές μεταδεδομένων—παραμείνετε στην 25.4.0 ή νεότερη για τα καλύτερα αποτελέσματα.

## Προχωρημένα Σενάρια Μεταδεδομένων

### Πότε να Χρησιμοποιήσετε Μεταδεδομένα Στόχου vs. Πηγής

| Σενάριο | Προτιμάται **Μεταδεδομένα Στόχου** | Προτιμάται **Μεταδεδομένα Πηγής** |
|----------|-----------------------------------|-----------------------------------|
| Απαιτούνται ενημερωμένες πληροφορίες συγγραφέα | ✅ | ❌ |
| Το αρχικό έγγραφο έχει νομική προτεραιότητα | ❌ | ✅ |
| Προσαρμοσμένες ιδιότητες προστέθηκαν μόνο στο νεότερο αρχείο | ✅ | ❌ |
| Θέλετε να διατηρήσετε το ιστορικό του “κύριου” εγγράφου | ❌ | ✅ |

### Διαχείριση Πολλαπλών Εγγράφων Στόχου

Μπορείτε να συγκρίνετε έναντι πολλών στόχων ενώ εξακολουθείτε να διατηρείτε τα μεταδεδομένα από το πρώτο στόχο που προσθέτετε:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    comparer.Add(targetFilePath1);
    comparer.Add(targetFilePath2);
    comparer.Add(targetFilePath3);
    
    // Metadata will come from the first target document
    comparer.Compare(outputFileName, new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    });
}
```

## Πρακτικές Εφαρμογές και Περιπτώσεις Χρήσης

### Διαχείριση Νομικών Εγγράφων
Τα νομικά γραφεία συχνά χρειάζονται να συγκρίνουν εκδόσεις συμβάσεων ενώ διατηρούν συγκεκριμένες ενδείξεις μεταδεδομένων:
```csharp
// Preserve client metadata from updated contract
using (Comparer comparer = new Comparer("original_contract.docx"))
{
    comparer.Add("client_revised_contract.docx");
    
    comparer.Compare("final_contract_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep client's metadata
    });
}
```

### Ακαδημαϊκή και Ερευνητική Συνεργασία
Όταν πολλοί ερευνητές συνεργάζονται, θέλετε να διατηρήσετε τις πιο πρόσφατες πληροφορίες συγγραφέα:
```csharp
// Keep metadata from the researcher's latest submission
using (Comparer comparer = new Comparer("draft_paper.docx"))
{
    comparer.Add("researcher_updates.docx");
    
    comparer.Compare("paper_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Preserve researcher metadata
    });
}
```

### Ροές Εργασίας Εταιρικής Συμμόρφωσης
Σε ρυθμιζόμενες βιομηχανίες, η διατήρηση μεταδεδομένων συμμόρφωσης είναι κρίσιμη:
```csharp
// Preserve compliance tags from updated policy document
using (Comparer comparer = new Comparer("old_policy.docx"))
{
    comparer.Add("compliance_approved_policy.docx");
    
    comparer.Compare("policy_comparison.docx", new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target  // Keep compliance metadata
    });
}
```

## Επίλυση Συνηθισμένων Προβλημάτων

### Σφάλματα “Αρχείο Δεν Βρέθηκε”
Το πιο κοινό πρόβλημα. Εντοπίστε το με ρητούς ελέγχους:
```csharp
string sourceFile = "source.docx";

// Always check if files exist before comparison
if (!File.Exists(sourceFile))
{
    Console.WriteLine($"Source file not found: {Path.GetFullPath(sourceFile)}");
    return;
}

// Same for target files
if (!File.Exists(targetFile))
{
    Console.WriteLine($"Target file not found: {Path.GetFullPath(targetFile)}");
    return;
}
```

### Προβλήματα Μνήμης με Μεγάλα Έγγραφα
Για έγγραφα άνω των 10 MB, σκεφτείτε αυτές τις βελτιστοποιήσεις:
```csharp
// Use explicit disposal for large documents
using (var comparer = new Comparer(sourceFile))
{
    comparer.Add(targetFile);
    
    var saveOptions = new SaveOptions() 
    { 
        CloneMetadataType = MetadataType.Target 
    };
    
    comparer.Compare(outputFile, saveOptions);
    
    // Explicitly clean up
    GC.Collect();
    GC.WaitForPendingFinalizers();
}
```

### Προβλήματα Δικαιωμάτων και Πρόσβασης
Όταν εργάζεστε με προστατευμένα αρχεία ή κοινόχρηστους δίσκους:
```csharp
try
{
    using (var comparer = new Comparer(sourceFile))
    {
        comparer.Add(targetFile);
        comparer.Compare(outputFile, new SaveOptions() 
        { 
            CloneMetadataType = MetadataType.Target 
        });
    }
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine("Access denied. Check file permissions.");
    Console.WriteLine($"Details: {ex.Message}");
}
catch (IOException ex)
{
    Console.WriteLine("File I/O error occurred.");
    Console.WriteLine($"Details: {ex.Message}");
}
```

## Σκέψεις Απόδοσης και Καλές Πρακτικές

### Διαχείριση Μνήμης
Το GroupDocs.Comparison μπορεί να είναι εντατικό σε μνήμη. Χρησιμοποιήστε δηλώσεις `using` για να εγγυηθείτε την απελευθέρωση:
```csharp
// Good - automatic resource cleanup
using (var comparer = new Comparer(sourceFile))
{
    // comparison logic here
}

// Bad - potential memory leaks
var comparer = new Comparer(sourceFile);
// ... comparison logic
// comparer.Dispose(); // Easy to forget!
```

**Επεξεργασία Εγγράφων σε Παρτίδες** – αν συγκρίνετε πολλά αρχεία, επεξεργαστείτε τα σε μικρότερες ομάδες για να μειώσετε τη χρήση μνήμης.

### Ασύγχρονες Λειτουργίες για Καλύτερη Ανταπόκριση
Για εφαρμογές desktop ή web, τυλίξτε τη σύγκριση σε ασύγχρονη μέθοδο:
```csharp
public async Task<bool> CompareDocumentsAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                comparer.Compare(output, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```

### Οδηγίες Μεγέθους Αρχείου
- **Μικρό (< 1 MB)** – επεξεργασία άμεσα.  
- **Μεσαίο (1‑10 MB)** – εμφάνιση προόδου για διατήρηση ανταπόκρισης UI.  
- **Μεγάλο (> 10 MB)** – πάντα χρήση ασύγχρονης επεξεργασίας και σκέψη για ρητό GC όπως φαίνεται παραπάνω.

## Ενσωμάτωση με Μεγαλύτερα Συστήματα

### Ενσωμάτωση ASP.NET Core
Παρακάτω υπάρχει ένας έτοιμος controller που δέχεται δύο ανεβασμένα αρχεία, εκτελεί τη σύγκριση και επιστρέφει το αποτέλεσμα ενώ **διατηρεί τα μεταδεδομένα στόχου**:
```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare-with-target-metadata")]
    public async Task<IActionResult> CompareWithTargetMetadata(
        IFormFile sourceFile, 
        IFormFile targetFile)
    {
        var tempSource = Path.GetTempFileName();
        var tempTarget = Path.GetTempFileName();
        var outputPath = Path.GetTempFileName();
        
        try
        {
            // Save uploaded files temporarily
            await sourceFile.CopyToAsync(new FileStream(tempSource, FileMode.Create));
            await targetFile.CopyToAsync(new FileStream(tempTarget, FileMode.Create));
            
            // Perform comparison with target metadata preservation
            using (var comparer = new Comparer(tempSource))
            {
                comparer.Add(tempTarget);
                comparer.Compare(outputPath, new SaveOptions() 
                { 
                    CloneMetadataType = MetadataType.Target 
                });
            }
            
            // Return comparison result
            var resultBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(resultBytes, "application/vnd.openxmlformats-officedocument.wordprocessingml.document", 
                       "comparison_result.docx");
        }
        finally
        {
            // Clean up temporary files
            if (System.IO.File.Exists(tempSource)) System.IO.File.Delete(tempSource);
            if (System.IO.File.Exists(tempTarget)) System.IO.File.Delete(tempTarget);
            if (System.IO.File.Exists(outputPath)) System.IO.File.Delete(outputPath);
        }
    }
}
```

## Συχνές Ερωτήσεις

**Ε: Μπορώ να διατηρήσω μεταδεδομένα από πολλαπλά έγγραφα στόχου κατά τη σύγκριση;**  
Α: Όταν προσθέτετε πολλά αρχεία στόχου, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα από το **πρώτο** αρχείο στόχου που προστέθηκε. Προσθέστε το έγγραφο του οποίου τα μεταδεδομένα θέλετε να κρατήσετε πρώτο στην αλυσίδα.

**Ε: Τι συμβαίνει αν το έγγραφο στόχου δεν έχει κάποια πεδία μεταδεδομένων;**  
Α: Θα αντιγραφούν μόνο τα μεταδεδομένα που υπάρχουν στο στόχο. Τα πεδία που λείπουν απλώς παραλείπονται· η σύγκριση εξακολουθεί να είναι επιτυχής.

**Ε: Πώς διαχειρίζομαι έγγραφα με κωδικό πρόσβασης;**  
Α: Χρησιμοποιήστε ένα αντικείμενο `LoadOptions` με τον κωδικό, και στη συνέχεια περάστε το στον κατασκευαστή `Comparer`:
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**Ε: Υπάρχει τρόπος να διατηρήσω μόνο επιλεγμένες ιδιότητες μεταδεδομένων;**  
Α: Η τρέχουσα API διατηρεί **όλα** τα μεταδεδομένα από την επιλεγμένη πηγή (Στόχο ή Πηγή). Για λεπτομερή έλεγχο, θα πρέπει να εξάγετε τις ιδιότητες μετά τη σύγκριση και να τις επαναεφαρμόσετε χειροκίνητα.

**Ε: Ποιες μορφές εγγράφων υποστηρίζουν τη διατήρηση μεταδεδομένων;**  
Α: Οι πιο κοινές επιχειρηματικές μορφές—DOCX, PDF, PPTX, XLSX και πολλές άλλες—υποστηρίζουν τη διατήρηση μεταδεδομένων. Δείτε τα επίσημα έγγραφα για την πλήρη λίστα.

**Ε: Πού μπορώ να βρω βοήθεια αν αντιμετωπίσω προβλήματα;**  
Α: Επισκεφθείτε το [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) για βοήθεια από την κοινότητα, ή επικοινωνήστε απευθείας με την υποστήριξη του GroupDocs αν έχετε εμπορική άδεια.

## Πρόσθετοι Πόροι

- **Επίσημη Τεκμηρίωση**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **Αναφορά API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Λήψη Τελευταίας Έκδοσης**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Δωρεάν Δοκιμή**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Επιλογές Αγοράς**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**Last Updated:** 2026-03-06  
**Tested With:** GroupDocs.Comparison 25.4.0 for .NET  
**Author:** GroupDocs