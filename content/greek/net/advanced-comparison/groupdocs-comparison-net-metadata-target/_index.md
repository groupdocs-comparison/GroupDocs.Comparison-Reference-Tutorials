---
categories:
- Document Comparison
date: '2026-06-05'
description: Μάθετε πώς να διατηρήσετε τα μεταδεδομένα με το GroupDocs Comparison
  για .NET, οδηγός βήμα‑βήμα για τη διατήρηση των ιδιοτήτων του στόχου εγγράφου κατά
  τη σύγκριση.
keywords:
- how to preserve metadata
- keep custom properties
- metadata preservation .NET
lastmod: '2026-06-05'
linktitle: Οδηγός Διατήρησης Μεταδεδομένων
schemas:
- author: GroupDocs
  dateModified: '2026-06-05'
  description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  headline: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  type: TechArticle
- description: Learn how to preserve metadata with GroupDocs Comparison for .NET,
    step‑by‑step guide to keep target document properties during comparison.
  name: How to Preserve Metadata with GroupDocs Comparison – .NET Tutorial
  steps:
  - name: Initialize Your Comparer Object
    text: 'The `Comparer` class is the core component that performs document comparison
      and controls output options. Load the source (original) file and create a `Comparer`
      instance: **Why use `using` statements?** They automatically dispose of resources,
      preventing memory leaks when processing large documents'
  - name: Add the Target Document
    text: 'The `Add` method registers the target document whose changes will be compared
      against the source. Specify the updated file you want to compare: **Common mistake**:
      Confusing source and target. Think of it this way—source is your “original,”
      target is your “updated version.”'
  - name: Set the Metadata Type (The Magic Happens Here)
    text: '`CloneMetadataType` property determines which document''s metadata is copied
      to the result. Tell the comparer to keep the target’s metadata: **What’s happening?**
      `CloneMetadataType = MetadataType.Target` tells GroupDocs.Comparison: “Hey,
      I want to keep the target document’s metadata in my final resu'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'Use a `LoadOptions` object with the password, then pass it to the `Comparer`
      constructor:'
    question: How do I handle password‑protected documents?
  - answer: The current API preserves **all** metadata from the chosen source (Target
      or Source). For granular control you’d need to extract the properties after
      comparison and re‑apply them manually.
    question: Is there a way to preserve only selected metadata properties?
  - answer: Most common business formats—DOCX, PDF, PPTX, XLSX, and many others—support
      metadata preservation. See the official docs for the full list.
    question: Which document formats support metadata preservation?
  type: FAQPage
tags:
- GroupDocs.Comparison
- metadata-preservation
- dotnet-tutorial
- document-management
title: Πώς να διατηρήσετε τα μεταδεδομένα με το GroupDocs Comparison – .NET Tutorial
type: docs
url: /el/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# Πώς να Διατηρήσετε τα Μεταδεδομένα με το GroupDocs Comparison – .NET Tutorial

## Εισαγωγή

Σας έχει συμβεί ποτέ να συγκρίνετε δύο έγγραφα και να χάσετε σημαντικά μεταδεδομένα στη διαδικασία; Δεν είστε μόνοι. Όταν χρειάζεται να **διατηρήσετε τα μεταδεδομένα προορισμού** κατά τη σύγκριση εγγράφων σε μια εφαρμογή .NET, η εργασία μπορεί να φαίνεται δύσκολη—αλλά δεν χρειάζεται να είναι. Αυτό το εκπαιδευτικό δείχνει **πώς να διατηρήσετε τα μεταδεδομένα** ώστε το τελικό αρχείο να διατηρεί τον ακριβή συγγραφέα, την ημερομηνία δημιουργίας και τις προσαρμοσμένες ιδιότητες που αναμένετε.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “preserve target metadata”;** Διατηρεί τα μεταδεδομένα (συγγραφέας, ημερομηνία δημιουργίας, προσαρμοσμένες ιδιότητες κ.λπ.) από το έγγραφο που ορίζετε ως προορισμό κατά τη δημιουργία του αποτελέσματος σύγκρισης.  
- **Ποια έκδοση του GroupDocs.Comparison απαιτείται;** Έκδοση 25.4.0 ή νεότερη.  
- **Μπορώ να το χρησιμοποιήσω με .NET Core;** Ναι – .NET Core 2.0+ ή .NET Framework 4.6.1+.  
- **Απαιτείται άδεια για παραγωγή;** Απαιτείται εμπορική άδεια για παραγωγή· μια δωρεάν δοκιμή λειτουργεί για εκμάθηση.  
- **Θα λειτουργήσει η δυνατότητα με PDF και DOCX;** Ναι – όλες οι κύριες μορφές Office και PDF υποστηρίζουν τη διατήρηση μεταδεδομένων.

## Τι είναι η διατήρηση μεταδεδομένων;

Η διατήρηση μεταδεδομένων σημαίνει τη διατήρηση των περιγραφικών πληροφοριών του πηγαίου εγγράφου—όπως συγγραφέας, τίτλος, αριθμός αναθεώρησης και προσαρμοσμένες ιδιότητες—ακέραια μετά από μια λειτουργία επεξεργασίας. Στο GroupDocs.Comparison, μπορείτε να αποφασίσετε αν τα μεταδεδομένα του πηγαίου ή του εγγράφου-στόχου θα παραμείνουν στο τελικό αποτέλεσμα σύγκρισης.

## Γιατί η Διατήρηση Μεταδεδομένων Είναι Σημαντική

Η διατήρηση των μεταδεδομένων είναι απαραίτητη επειδή πολλοί κλάδοι τα θεωρούν νομική απόδειξη ή κρίσιμη επιχειρηματική πληροφορία. **Γιατί;** Επειδή τα μεταδεδομένα καταγράφουν την ιδιοκτησία, ετικέτες συμμόρφωσης, ιστορικό εκδόσεων και ίχνη ελέγχου που οι οργανισμοί βασίζονται για κανονιστική αναφορά, διαχείριση συμβάσεων και ακαδημαϊκή απονομή. Η απώλεια αυτών των δεδομένων μπορεί να ακυρώσει τη νομική ισχύ ενός εγγράφου ή να διακόψει αυτοματοποιημένες ροές εργασίας.

## Προαπαιτούμενα

### Απαιτούμενες Βιβλιοθήκες και Εκδόσεις
- **GroupDocs.Comparison for .NET**: Έκδοση 25.4.0 ή νεότερη (οι παλαιότερες εκδόσεις έχουν περιορισμένες επιλογές μεταδεδομένων).  
- **.NET Framework**: 4.6.1 ή υψηλότερη, ή .NET Core 2.0+.

### Ρύθμιση Περιβάλλοντος
- Visual Studio (ή οποιοδήποτε IDE C# προτιμάτε).  
- Βασικές γνώσεις C# (τίποτα πολύ προχωρημένο, υποσχόμαστε!).  
- Δύο δείγματα εγγράφων για δοκιμή (Word *.docx* λειτουργεί άψογα).

### Προαπαιτούμενες Γνώσεις
Δεν χρειάζεται να είστε ειδικός στο GroupDocs, αλλά πρέπει να αισθάνεστε άνετα με:
- τις δηλώσεις `using` του C# και τη διαχείριση αρχείων.  
- τις βασικές έννοιες επεξεργασίας εγγράφων.  
- τι είναι τα μεταδεδομένα (συγγραφέας, τίτλος, προσαρμοσμένες ιδιότητες κ.λπ.).

Έτοιμοι; Ας το ρυθμίσουμε.

## Ρύθμιση του GroupDocs.Comparison για .NET

Η εγκατάσταση του GroupDocs.Comparison είναι απλή, αλλά υπάρχουν μερικά κόλπα που πρέπει να προσέξετε.

### Επιλογές Εγκατάστασης

**NuGet Package Manager Console** (η πιο εύκολη μέθοδος):
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**.NET CLI** (αν προτιμάτε γραμμή εντολών):
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

**Συμβουλή**: Πάντα να καθορίζετε την έκδοση για να αποφύγετε απρόσμενες αλλαγές που σπάζουν το έργο σας.

### Απόκτηση Άδειας

Εδώ πολλοί προγραμματιστές κολλάνε αρχικά. Το GroupDocs.Comparison δεν είναι δωρεάν, αλλά έχετε επιλογές:
- **Δωρεάν Δοκιμή** – πλήρης λειτουργικότητα για 30 ημέρες, ιδανική για αξιολόγηση.  
- **Προσωρινή Άδεια** – παρατεταμένη περίοδος αξιολόγησης αν χρειάζεστε περισσότερο χρόνο.  
- **Εμπορική Άδεια** – για χρήση σε παραγωγή (διαθέσιμα διάφορα επίπεδα τιμολόγησης).

Μην ανησυχείτε για την άδεια αυτή τη στιγμή αν απλώς μαθαίνετε—η δοκιμαστική έκδοση περιλαμβάνει όλες τις δυνατότητες **preserve target metadata**.

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

## Πώς να Διατηρήσετε τα Μεταδεδομένα Στόχου

Για να διατηρήσετε τα μεταδεδομένα στόχου, ρυθμίζετε το comparer ώστε να κλωνοποιεί τα μεταδεδομένα από το έγγραφο-στόχο πριν δημιουργηθεί το αποτέλεσμα. Αυτό περιλαμβάνει τον ορισμό της ιδιότητας `CloneMetadataType` σε `MetadataType.Target` στο αντικείμενο `Comparer`. Με αυτόν τον τρόπο, όλα τα πεδία μεταδεδομένων—συγγραφέας, ημερομηνία δημιουργίας, προσαρμοσμένες ιδιότητες—αντιγράφονται από το στόχο στο αρχείο εξόδου, διασφαλίζοντας ότι οι πληροφορίες του ενημερωμένου εγγράφου διατηρούνται.

### Κατανόηση της Ροής των Μεταδεδομένων

Κατά τη διάρκεια μιας τυπικής σύγκρισης:
1. **Έγγραφο πηγής** παρέχει το βασικό περιεχόμενο.  
2. **Έγγραφο στόχου** παρέχει τις αλλαγές για σύγκριση.  
3. Το **έγγραφο εξόδου** συνδυάζει και τα δύο, αλλά ποια μεταδεδομένα κερδίζουν;

Από προεπιλογή, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα του εγγράφου πηγής. Για να **διατηρήσετε τα μεταδεδομένα στόχου**, πρέπει να το δηλώσετε ρητά στο API.

### Υλοποίηση Βήμα‑Βήμα

#### Βήμα 1: Αρχικοποίηση του Αντικειμένου Comparer

Η κλάση `Comparer` είναι το βασικό στοιχείο που εκτελεί τη σύγκριση εγγράφων και ελέγχει τις επιλογές εξόδου.  
Φορτώστε το αρχείο πηγής (αρχικό) και δημιουργήστε μια παρουσία `Comparer`:
```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```

**Γιατί να χρησιμοποιείτε δηλώσεις `using`;** Αυτές απελευθερώνουν αυτόματα τους πόρους, αποτρέποντας διαρροές μνήμης κατά την επεξεργασία μεγάλων εγγράφων. Πιστέψτε με, θα σας ευχαριστήσετε αργότερα όταν δουλεύετε με αρχεία Word 50 MB.

#### Βήμα 2: Προσθήκη του Εγγράφου Στόχου

Η μέθοδος `Add` καταχωρεί το έγγραφο-στόχο του οποίου οι αλλαγές θα συγκριθούν με την πηγή.  
Καθορίστε το ενημερωμένο αρχείο που θέλετε να συγκρίνετε:
```csharp
comparer.Add(targetFilePath);
```

**Συνηθισμένο λάθος**: Σύγχυση μεταξύ πηγής και στόχου. Σκεφτείτε το έτσι—πηγή είναι το “αρχικό” σας, στόχος είναι η “ενημερωμένη έκδοση”.

#### Βήμα 3: Ορισμός του Τύπου Μεταδεδομένων (Εδώ Συμβαίνει η Μαγεία)

Η ιδιότητα `CloneMetadataType` καθορίζει ποια μεταδεδομένα εγγράφου αντιγράφονται στο αποτέλεσμα.  
Πείτε στο comparer να διατηρήσει τα μεταδεδομένα του στόχου:
```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```

**Τι συμβαίνει;** `CloneMetadataType = MetadataType.Target` λέει στο GroupDocs.Comparison: “Θέλω να διατηρήσω τα μεταδεδομένα του εγγράφου-στόχου στο τελικό αποτέλεσμα.”

### Πλήρες Παράδειγμα Εργασίας

Ακολουθεί όλα μαζί σε ένα εκτελέσιμο πρόγραμμα:
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

### Συνηθισμένα Πιθανά Σφάλματα προς Αποφυγή
**Προβλήματα Διαδρομής Αρχείου** – χρησιμοποιείτε πάντα πλήρεις διαδρομές ή βεβαιωθείτε ότι τα αρχεία σας βρίσκονται στον τρέχοντα φάκελο:
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```

**Διαχείριση Μνήμης** – για μεγάλα έγγραφα, πάντα τυλίξτε τα αντικείμενα `Comparer` σε δηλώσεις `using`.

**Συμβατότητα Έκδοσης** – διαφορετικές εκδόσεις του GroupDocs.Comparison εκθέτουν διαφορετικές επιλογές μεταδεδομένων—μείνετε στην έκδοση 25.4.0 ή νεότερη για τα καλύτερα αποτελέσματα.

## Προχωρημένα Σενάρια Μεταδεδομένων

### Πότε να Χρησιμοποιήσετε Μεταδεδομένα Στόχου vs. Πηγής

| Σενάριο | Προτίμηση **Μεταδεδομένων Στόχου** | Προτίμηση **Μεταδεδομένων Πηγής** |
|----------|----------------------------|----------------------------|
| Απαιτούνται ενημερωμένες πληροφορίες συγγραφέα | ✅ | ❌ |
| Το αρχικό έγγραφο έχει νομική προτεραιότητα | ❌ | ✅ |
| Προσαρμοσμένες ιδιότητες προστέθηκαν μόνο στο νεότερο αρχείο | ✅ | ❌ |
| Θέλετε να διατηρήσετε το ιστορικό του “κύριου” εγγράφου | ❌ | ✅ |

### Διαχείριση Πολλαπλών Εγγράφων Στόχου

Μπορείτε να συγκρίνετε με πολλαπλούς στόχους ενώ εξακολουθείτε να διατηρείτε τα μεταδεδομένα από τον πρώτο στόχο που προσθέτετε:
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

Τα νομικά γραφεία συχνά χρειάζονται να συγκρίνουν εκδόσεις συμβάσεων διατηρώντας συγκεκριμένα σημεία μεταδεδομένων:
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

Σε ρυθμιζόμενους κλάδους, η διατήρηση των μεταδεδομένων συμμόρφωσης είναι κρίσιμη:
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

### Σφάλματα “File Not Found”

Το πιο συνηθισμένο πρόβλημα. Εντοπίστε το με ρητούς ελέγχους:
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

Για έγγραφα άνω των 10 MB, εξετάστε αυτές τις βελτιστοποιήσεις:
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

### Προβλήματα Άδειας και Πρόσβασης

Κατά την εργασία με προστατευμένα αρχεία ή κοινόχρηστους δίσκους:
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

Το GroupDocs.Comparison μπορεί να απαιτεί πολλή μνήμη. Χρησιμοποιήστε δηλώσεις `using` για να εγγυηθείτε την απελευθέρωση:
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

### Ασύγχρονες Λειτουργίες για Καλύτερη Απόκριση

Για εφαρμογές desktop ή web, τυλίξτε τη σύγκριση σε μια ασύγχρονη μέθοδο:
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
- **Μεσαίο (1‑10 MB)** – εμφανίστε πρόοδο για να διατηρήσετε την ανταπόκριση του UI.  
- **Μεγάλο (> 10 MB)** – πάντα χρησιμοποιήστε ασύγχρονη επεξεργασία και σκεφτείτε ρητή συλλογή απορριμμάτων (GC) όπως φαίνεται παραπάνω.

## Ενσωμάτωση με Μεγαλύτερα Συστήματα

### Ενσωμάτωση ASP.NET Core

Παρακάτω είναι ένας έτοιμος προς χρήση controller που δέχεται δύο ανεβασμένα αρχεία, εκτελεί τη σύγκριση και επιστρέφει το αποτέλεσμα ενώ **διατηρεί τα μεταδεδομένα στόχου**:
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

**Ε: Μπορώ να διατηρήσω μεταδεδομένα από πολλαπλά έγγραφα-στόχους κατά τη σύγκριση;**  
Α: Όταν προσθέτετε πολλά αρχεία-στόχους, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα από το **πρώτο** αρχείο-στόχο που προστέθηκε. Προσθέστε το έγγραφο του οποίου τα μεταδεδομένα θέλετε να διατηρήσετε πρώτο στη σειρά.

**Ε: Τι συμβαίνει αν το έγγραφο-στόχος δεν έχει ορισμένα πεδία μεταδεδομένων;**  
Α: Μόνο τα μεταδεδομένα που υπάρχουν στον στόχο θα αντιγραφούν στο αποτέλεσμα. Τα πεδία που λείπουν απλώς παραλείπονται· η σύγκριση ολοκληρώνεται επιτυχώς.

**Ε: Πώς να διαχειριστώ έγγραφα με κωδικό πρόσβασης;**  
Α: Χρησιμοποιήστε ένα αντικείμενο `LoadOptions` με τον κωδικό, και στη συνέχεια περάστε το στον κατασκευαστή του `Comparer`:
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```

**Ε: Υπάρχει τρόπος να διατηρήσω μόνο επιλεγμένες ιδιότητες μεταδεδομένων;**  
Α: Το τρέχον API διατηρεί **όλα** τα μεταδεδομένα από την επιλεγμένη πηγή (Target ή Source). Για λεπτομερή έλεγχο θα πρέπει να εξάγετε τις ιδιότητες μετά τη σύγκριση και να τις επαναεφαρμόσετε χειροκίνητα.

**Ε: Ποιες μορφές εγγράφων υποστηρίζουν τη διατήρηση μεταδεδομένων;**  
Α: Οι πιο κοινές επιχειρηματικές μορφές—DOCX, PDF, PPTX, XLSX και πολλές άλλες—υποστηρίζουν τη διατήρηση μεταδεδομένων. Δείτε την επίσημη τεκμηρίωση για την πλήρη λίστα.

**Ε: Πού μπορώ να λάβω βοήθεια αν αντιμετωπίσω προβλήματα;**  
Α: Επισκεφθείτε το [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) για βοήθεια από την κοινότητα, ή επικοινωνήστε απευθείας με την υποστήριξη του GroupDocs αν έχετε εμπορική άδεια.

## Πρόσθετοι Πόροι

- **Επίσημη Τεκμηρίωση**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **Αναφορά API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Λήψη Τελευταίας Έκδοσης**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Δωρεάν Δοκιμή**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Επιλογές Αγοράς**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**Τελευταία Ενημέρωση:** 2026-06-05  
**Δοκιμάστηκε Με:** GroupDocs.Comparison 25.4.0 for .NET  
**Συγγραφέας:** GroupDocs

---

## Σχετικά Εκπαιδευτικά

- [Μεταδεδομένα Εγγράφου .NET - Αποθήκευση & Διατήρηση Προσαρμοσμένων Ιδιοτήτων](/comparison/net/loading-and-saving-documents/saving-user-defined-document-metadata/)  
- [Διαχείριση Μεταδεδομένων Εγγράφου .NET - Πλήρης Οδηγός για το GroupDocs.Comparison](/comparison/net/metadata-management/)  
- [Λήψη Ιδιοτήτων Εγγράφου C# .NET - Εξαγωγή Μεταδεδομένων Αρχείου](/comparison/net/basic-usage/get-document-info-from-path/)