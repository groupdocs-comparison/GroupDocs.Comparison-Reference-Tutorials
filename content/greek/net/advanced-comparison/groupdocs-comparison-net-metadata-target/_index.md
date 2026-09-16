---
categories:
- Document Comparison
date: '2026-09-15'
description: Μάθετε πώς να διατηρήσετε τα metadata κατά τη σύγκριση εγγράφων χρησιμοποιώντας
  το GroupDocs.Comparison για .NET. Οδηγός βήμα‑βήμα με παραδείγματα C#, βέλτιστες
  πρακτικές και πραγματικές περιπτώσεις χρήσης.
keywords:
- how to preserve metadata
- GroupDocs.Comparison metadata preservation
- .NET document comparison
- metadata handling in .NET
lastmod: '2026-09-15'
linktitle: Εκπαιδευτικό σεμινάριο διατήρησης metadata
og_description: Ανακαλύψτε πώς να διατηρήσετε τα metadata κατά τη σύγκριση εγγράφων
  σε .NET χρησιμοποιώντας το GroupDocs.Comparison. Ακολουθήστε ένα λεπτομερές εκπαιδευτικό
  σεμινάριο με βέλτιστες πρακτικές, συμβουλές αντιμετώπισης προβλημάτων και πραγματικά
  παραδείγματα.
og_image_alt: Developer guide showing metadata preservation with GroupDocs.Comparison
  in a .NET application
og_title: Πώς να διατηρήσετε τα metadata με το GroupDocs.Comparison στο .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-15'
  description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  headline: How to preserve metadata with GroupDocs.Comparison in .NET
  type: TechArticle
- description: Learn how to preserve metadata during document comparison using GroupDocs.Comparison
    for .NET. Step‑by‑step guide with C# examples, best practices, and real‑world
    use cases.
  name: How to preserve metadata with GroupDocs.Comparison in .NET
  steps:
  - name: Initialize your comparer object
    text: '`Comparer` is the core class that orchestrates the comparison process.
      It loads the source file, tracks changes, and generates the output. **Why use
      `using` statements?** They automatically dispose of resources, preventing memory
      leaks when processing large documents. Trust me, you’ll thank yourself'
  - name: Add the target document
    text: '`Comparer.Add` registers the file that contains the modifications you want
      to compare against. **Common mistake**: Confusing source and target. Think of
      it this way—source is your “original,” target is your “updated version.”'
  - name: Set the metadata type (the magic happens here)
    text: '`CloneMetadataType` is a property of `ComparisonOptions` that determines
      which document’s metadata is cloned into the result. **What’s happening?** `CloneMetadataType
      = MetadataType.Target` tells GroupDocs.Comparison: “Hey, I want to keep the
      target document’s metadata in my final result.”'
  type: HowTo
- questions:
  - answer: When you add several target files, GroupDocs.Comparison uses the metadata
      from the **first** target document added. Add the document whose metadata you
      want to keep first in the chain.
    question: Can I preserve metadata from multiple target documents when comparing?
  - answer: Only the metadata that exists in the target will be copied to the output.
      Missing fields are simply omitted; the comparison still succeeds.
    question: What happens if the target document lacks some metadata fields?
  - answer: 'LoadOptions specifies settings such as passwords for opening protected
      documents. Use a `LoadOptions` object with the password, then pass it to the
      `Comparer` constructor: ```csharp var loadOptions = new LoadOptions() { Password
      = "your_password" }; using (var comparer = new Comparer(sourceFile, loadOptions))
      { // comparison logic here } ```'
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
- metadata preservation
- GroupDocs.Comparison
- .NET tutorial
- document management
- C# comparison
title: Πώς να διατηρήσετε τα metadata με το GroupDocs.Comparison στο .NET
type: docs
url: /el/net/advanced-comparison/groupdocs-comparison-net-metadata-target/
weight: 1
---

# Πώς να διατηρήσετε τα μεταδεδομένα με το GroupDocs.Comparison σε .NET

Σε αυτό το μάθημα θα μάθετε **πώς να διατηρήσετε τα μεταδεδομένα** όταν συγκρίνετε δύο έγγραφα με το GroupDocs.Comparison για .NET. Η διατήρηση των μεταδεδομένων είναι απαραίτητη για νομική συμμόρφωση, ίχνη ελέγχου και συνεργατικές ροές εργασίας, και η βιβλιοθήκη σας δίνει λεπτομερή έλεγχο για το ποια μεταδεδομένα εγγράφου παραμένουν στο αποτέλεσμα της σύγκρισης.

## Εισαγωγή

Σας έχει συμβεί ποτέ να συγκρίνετε δύο έγγραφα και να χάσετε σημαντικά μεταδεδομένα στη διαδικασία; Δεν είστε μόνοι. Όταν χρειάζεται να **διατηρήσετε τα μεταδεδομένα προορισμού** κατά τη σύγκριση εγγράφων σε μια εφαρμογή .NET, η εργασία μπορεί να φαίνεται δύσκολη—αλλά δεν χρειάζεται να είναι.

Το GroupDocs.Comparison για .NET σας επιτρέπει να αποφασίσετε ποια μεταδεδομένα εγγράφου παραμένουν στο αποτέλεσμα της σύγκρισης. Είτε δημιουργείτε σύστημα διαχείρισης εγγράφων, χειρίζεστε νομικές συμβάσεις ή διαχειρίζεστε συνεργατικό περιεχόμενο, θα θέλετε πάντα τα μεταδεδομένα από το σωστό πηγαίο έγγραφο.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “διατήρηση μεταδεδομένων προορισμού”;** Διατηρεί τα μεταδεδομένα (συγγραφέας, ημερομηνία δημιουργίας, προσαρμοσμένες ιδιότητες κ.λπ.) από το έγγραφο που ορίζετε ως προορισμό κατά τη δημιουργία του αποτελέσματος σύγκρισης.  
- **Ποια έκδοση του GroupDocs.Comparison απαιτείται;** Έκδοση 25.4.0 ή νεότερη.  
- **Μπορώ να το χρησιμοποιήσω με .NET Core;** Ναι – .NET Core 2.0+ ή .NET Framework 4.6.1+.  
- **Απαιτείται άδεια για παραγωγή;** Απαιτείται εμπορική άδεια για παραγωγή· μια δωρεάν δοκιμή λειτουργεί για εκμάθηση.  
- **Θα λειτουργεί η δυνατότητα με PDF και DOCX;** Ναι – όλες οι κύριες μορφές Office και PDF υποστηρίζουν τη διατήρηση μεταδεδομένων.

## Γιατί η διατήρηση μεταδεδομένων είναι σημαντική

Πριν βυθιστούμε στον κώδικα, ας συζητήσουμε γιατί η διατήρηση των μεταδεδομένων προορισμού είναι σημαντική. Τα μεταδεδομένα εγγράφου δεν είναι μόνο “ωραία να έχουν”—συχνά απαιτούνται νομικά ή είναι κρίσιμα για την επιχείρηση:

- **Νομικά έγγραφα** – χρειάζεται να διατηρηθούν οι δείκτες προνομίων δικηγόρου‑πελάτη.  
- **Εταιρικά αρχεία** – πρέπει να διατηρούν ετικέτες συμμόρφωσης και αλυσίδες έγκρισης.  
- **Ακαδημαϊκές εργασίες** – η απόδοση συγγραφέα και το ιστορικό αναθεωρήσεων είναι απαραίτητα.  
- **Τεχνική τεκμηρίωση** – ο έλεγχος εκδόσεων και η κατάσταση ανασκόπησης έχουν σημασία.

Χωρίς σωστή διαχείριση, μπορεί να αφαιρέσετε κατά λάθος πληροφορίες που χρειάστηκαν μήνες για να δημιουργηθούν. Εδώ η επιλογή **διατήρησης μεταδεδομένων προορισμού** ξεχωρίζει.

## Προαπαιτούμενα

### Απαιτούμενες βιβλιοθήκες και εκδόσεις
- **GroupDocs.Comparison for .NET**: Έκδοση 25.4.0 ή νεότερη (παλαιότερες εκδόσεις έχουν περιορισμένες επιλογές μεταδεδομένων).  
- **.NET Framework**: 4.6.1 ή υψηλότερη, ή .NET Core 2.0+.

### Ρύθμιση περιβάλλοντος
- Visual Studio (ή οποιοδήποτε IDE C# προτιμάτε).  
- Βασικές γνώσεις C# (τίποτα πολύ προχωρημένο, υποσχέση!).  
- Δύο δείγματα εγγράφων για δοκιμή (Word *.docx* λειτουργεί εξαιρετικά).

### Προαπαιτούμενες γνώσεις
Δεν χρειάζεται να είστε ειδικός στο GroupDocs, αλλά θα πρέπει να είστε άνετοι με:
- δηλώσεις C# `using` και διαχείριση αρχείων.  
- βασικές έννοιες επεξεργασίας εγγράφων.  
- τι είναι τα μεταδεδομένα (συγγραφέας, τίτλος, προσαρμοσμένες ιδιότητες κ.λπ.).

Έτοιμοι; Ας το ρυθμίσουμε.

## Ρύθμιση GroupDocs.Comparison για .NET

Η εγκατάσταση του GroupDocs.Comparison είναι απλή, αλλά υπάρχουν μερικά πιθανά προβλήματα που πρέπει να προσέξετε.

### Επιλογές εγκατάστασης

**NuGet Package Manager Console** (η πιο εύκολη μέθοδος):  
```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```  

**.NET CLI** (αν προτιμάτε τη γραμμή εντολών):  
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```  

**Συμβουλή**: Πάντα να καθορίζετε την έκδοση για να αποφύγετε απρόσμενες αλλαγές που σπάζουν το έργο σας.

### Απόκτηση άδειας

Εδώ πολλοί προγραμματιστές κολλάνε αρχικά. Το GroupDocs.Comparison δεν είναι δωρεάν, αλλά έχετε επιλογές:
- **Δωρεάν δοκιμή** – πλήρη λειτουργικότητα για 30 ημέρες, ιδανική για αξιολόγηση.  
- **Προσωρινή άδεια** – παρατεταμένη περίοδος αξιολόγησης αν χρειάζεστε περισσότερο χρόνο.  
- **Εμπορική άδεια** – για παραγωγική χρήση (διαθέσιμα διάφορα επίπεδα τιμολόγησης).

Μην ανησυχείτε για την άδεια αυτή τη στιγμή αν απλώς μαθαίνετε—η δοκιμαστική έκδοση περιλαμβάνει όλες τις δυνατότητες **διατήρησης μεταδεδομένων προορισμού**.

### Βασικός έλεγχος ρύθμισης

Ας βεβαιωθούμε ότι όλα λειτουργούν με μια απλή δοκιμή:  
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

## Πώς να διατηρήσετε τα μεταδεδομένα προορισμού

Φορτώστε τα αρχεία προέλευσης και προορισμού, μετά πείτε στο API να διατηρήσει τα μεταδεδομένα του προορισμού στην τελική έξοδο.

**Άμεση απάντηση (40‑70 λέξεις):**  
Για να διατηρήσετε τα μεταδεδομένα προορισμού, δημιουργήστε ένα `Comparer` με το έγγραφο προέλευσης, προσθέστε το έγγραφο προορισμού μέσω `Add`, ορίστε `CloneMetadataType = MetadataType.Target` στις `ComparisonOptions`, και τέλος καλέστε `Compare`. Αυτό λέει στο GroupDocs.Comparison να αντιγράψει τον συγγραφέα, την ημερομηνία δημιουργίας, τις προσαρμοσμένες ιδιότητες και όλα τα άλλα μεταδεδομένα από το αρχείο προορισμού στο παραγόμενο αποτέλεσμα.

### Κατανόηση της ροής των μεταδεδομένων

Κατά τη διάρκεια μιας τυπικής σύγκρισης:
1. **Έγγραφο προέλευσης** παρέχει το βασικό περιεχόμενο.  
2. **Έγγραφο προορισμού** παρέχει τις αλλαγές για σύγκριση.  
3. Το **έγγραφο εξόδου** συνδυάζει και τα δύο, αλλά ποια μεταδεδομένα κερδίζουν;

Από προεπιλογή, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα του εγγράφου προέλευσης. Για να **διατηρήσετε τα μεταδεδομένα προορισμού**, πρέπει να το πείτε ρητά στο API.

### Υλοποίηση βήμα‑βήμα

#### Βήμα 1: Αρχικοποίηση του αντικειμένου comparer

`Comparer` είναι η βασική κλάση που οργανώνει τη διαδικασία σύγκρισης. Φορτώνει το αρχείο προέλευσης, παρακολουθεί τις αλλαγές και δημιουργεί την έξοδο.  

```csharp
using (Comparer comparer = new Comparer(sourceFilePath))
{
    // All comparison operations happen within this scope
}
```  

**Γιατί να χρησιμοποιείτε δηλώσεις `using`;** Αυτές απελευθερώνουν αυτόματα τους πόρους, αποτρέποντας διαρροές μνήμης κατά την επεξεργασία μεγάλων εγγράφων. Πιστέψτε με, θα σας ευχαριστήσετε αργότερα όταν δουλεύετε με αρχεία Word 50 MB.

#### Βήμα 2: Προσθήκη του εγγράφου προορισμού

`Comparer.Add` καταχωρεί το αρχείο που περιέχει τις τροποποιήσεις που θέλετε να συγκρίνετε.  

```csharp
comparer.Add(targetFilePath);
```  

**Κοινό λάθος**: Συγχυση μεταξύ προέλευσης και προορισμού. Σκεφτείτε το έτσι—η προέλευση είναι το “αρχικό” σας, ο προορισμός είναι η “ενημερωμένη έκδοση”.

#### Βήμα 3: Ορισμός του τύπου μεταδεδομένων (εδώ συμβαίνει η μαγεία)

`CloneMetadataType` είναι μια ιδιότητα του `ComparisonOptions` που καθορίζει ποια μεταδεδομένα εγγράφου θα κλωνοποιηθούν στο αποτέλεσμα.  

```csharp
comparer.Compare(outputFileName, new SaveOptions() { CloneMetadataType = MetadataType.Target });
```  

**Τι συμβαίνει;** `CloneMetadataType = MetadataType.Target` λέει στο GroupDocs.Comparison: “Θέλω να διατηρήσω τα μεταδεδομένα του εγγράφου προορισμού στο τελικό μου αποτέλεσμα.”

## Πλήρες λειτουργικό παράδειγμα

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

## Συνηθισμένα λάθη που πρέπει να αποφύγετε

- **Προβλήματα διαδρομής αρχείου** – πάντα χρησιμοποιείτε πλήρεις διαδρομές ή βεβαιωθείτε ότι τα αρχεία σας βρίσκονται στον τρέχοντα φάκελο:  
```csharp
// Good
string sourceFile = Path.Combine(Directory.GetCurrentDirectory(), "docs", "source.docx");

// Risky (might work locally but fail in production)
string sourceFile = "source.docx";
```  

- **Διαχείριση μνήμης** – για μεγάλα έγγραφα, πάντα τυλίξτε τα αντικείμενα `Comparer` σε δηλώσεις `using`.  

- **Συμβατότητα εκδόσεων** – διαφορετικές εκδόσεις του GroupDocs.Comparison εκθέτουν διαφορετικές επιλογές μεταδεδομένων—παραμείνετε στην 25.4.0 ή νεότερη για τα καλύτερα αποτελέσματα.

## Προχωρημένα σενάρια μεταδεδομένων

### Πότε να χρησιμοποιήσετε μεταδεδομένα προορισμού vs. προέλευσης

| Σενάριο | Προτιμάτε **μεταδεδομένα προορισμού** | Προτιμάτε **μεταδεδομένα προέλευσης** |
|----------|----------------------------|----------------------------|
| Απαιτούνται ενημερωμένες πληροφορίες συγγραφέα | ✅ | ❌ |
| Το αρχικό έγγραφο έχει νομική προτεραιότητα | ❌ | ✅ |
| Προσαρμοσμένες ιδιότητες προστέθηκαν μόνο στο νεότερο αρχείο | ✅ | ❌ |
| Θέλετε να διατηρήσετε το ιστορικό του “κύριου” εγγράφου | ❌ | ✅ |

### Διαχείριση πολλαπλών εγγράφων προορισμού

Μπορείτε να συγκρίνετε με πολλαπλούς προορισμούς διατηρώντας τα μεταδεδομένα από το πρώτο προορισμό που προσθέτετε:  
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

## Πρακτικές εφαρμογές και περιπτώσεις χρήσης

### Διαχείριση νομικών εγγράφων

Τα νομικά γραφεία συχνά χρειάζεται να συγκρίνουν εκδόσεις συμβάσεων διατηρώντας συγκεκριμένους δείκτες μεταδεδομένων:  
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

### Ακαδημαϊκή και ερευνητική συνεργασία

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

### Ροές εργασίας εταιρικής συμμόρφωσης

Σε ρυθμιζόμενες βιομηχανίες, η διατήρηση των μεταδεδομένων συμμόρφωσης είναι κρίσιμη:  
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

## Επίλυση κοινών προβλημάτων

### Σφάλματα “Αρχείο δεν βρέθηκε”

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

### Προβλήματα μνήμης με μεγάλα έγγραφα

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

### Προβλήματα αδειών και πρόσβασης

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

## Σκέψεις απόδοσης και βέλτιστες πρακτικές

### Διαχείριση μνήμης

Το GroupDocs.Comparison μπορεί να καταναλώσει έως **300 MB RAM** όταν επεξεργάζεται ένα PDF 100 σελίδων. Χρησιμοποιήστε δηλώσεις `using` για να εγγυηθείτε την απελευθέρωση και την άμεση ελευθέρωση μνήμης.  
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

**Επεξεργασία εγγράφων σε παρτίδες** – αν συγκρίνετε πολλά αρχεία, επεξεργαστείτε τα σε μικρότερες ομάδες για να μειώσετε τη χρήση μνήμης.

### Ασύγχρονες λειτουργίες για καλύτερη ανταπόκριση

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

### Οδηγίες μεγέθους αρχείου

- **Μικρό (< 1 MB)** – επεξεργασία άμεσα.  
- **Μεσαίο (1‑10 MB)** – εμφάνιση προόδου για διατήρηση ανταπόκρισης UI.  
- **Μεγάλο (> 10 MB)** – πάντα χρησιμοποιήστε ασύγχρονη επεξεργασία και εξετάστε ρητή συλλογή απορριμμάτων όπως φαίνεται παραπάνω.

## Ενσωμάτωση με μεγαλύτερα συστήματα

### Ενσωμάτωση ASP.NET Core

Παρακάτω είναι ένας έτοιμος προς χρήση ελεγκτής που δέχεται δύο ανεβασμένα αρχεία, εκτελεί τη σύγκριση και επιστρέφει το αποτέλεσμα ενώ **διατηρεί τα μεταδεδομένα προορισμού**:  
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

## Συχνές ερωτήσεις

**Ε: Μπορώ να διατηρήσω μεταδεδομένα από πολλαπλά έγγραφα προορισμού κατά τη σύγκριση;**  
Όταν προσθέτετε πολλά αρχεία προορισμού, το GroupDocs.Comparison χρησιμοποιεί τα μεταδεδομένα από το **πρώτο** αρχείο προορισμού που προστέθηκε. Προσθέστε το έγγραφο του οποίου τα μεταδεδομένα θέλετε να διατηρήσετε πρώτο στη σειρά.

**Ε: Τι συμβαίνει αν το έγγραφο προορισμού δεν έχει ορισμένα πεδία μεταδεδομένων;**  
Μόνο τα μεταδεδομένα που υπάρχουν στο προορισμό θα αντιγραφούν στην έξοδο. Τα πεδία που λείπουν απλώς παραλείπονται· η σύγκριση εξακολουθεί να είναι επιτυχής.

**Ε: Πώς να διαχειριστώ έγγραφα με κωδικό πρόσβασης;**  
Το LoadOptions καθορίζει ρυθμίσεις όπως κωδικούς πρόσβασης για το άνοιγμα προστατευμένων εγγράφων. Χρησιμοποιήστε ένα αντικείμενο `LoadOptions` με τον κωδικό, και στη συνέχεια περάστε το στον κατασκευαστή `Comparer`:  
```csharp
var loadOptions = new LoadOptions() { Password = "your_password" };
using (var comparer = new Comparer(sourceFile, loadOptions))
{
    // comparison logic here
}
```  

**Ε: Υπάρχει τρόπος να διατηρήσω μόνο επιλεγμένες ιδιότητες μεταδεδομένων;**  
Το τρέχον API διατηρεί **όλα** τα μεταδεδομένα από την επιλεγμένη πηγή (Target ή Source). Για λεπτομερή έλεγχο, θα πρέπει να εξάγετε τις ιδιότητες μετά τη σύγκριση και να τις εφαρμόσετε ξανά χειροκίνητα.

**Ε: Ποιες μορφές εγγράφων υποστηρίζουν τη διατήρηση μεταδεδομένων;**  
Οι περισσότερες κοινές επιχειρηματικές μορφές—DOCX, PDF, PPTX, XLSX και πολλές άλλες—υποστηρίζουν τη διατήρηση μεταδεδομένων. Δείτε τα επίσημα έγγραφα για την πλήρη λίστα.

**Ε: Πού μπορώ να λάβω βοήθεια αν αντιμετωπίσω προβλήματα;**  
Επισκεφθείτε το [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison) για βοήθεια από την κοινότητα, ή επικοινωνήστε απευθείας με την υποστήριξη του GroupDocs εάν έχετε εμπορική άδεια.

## Πρόσθετοι πόροι

- **Επίσημη τεκμηρίωση**: [GroupDocs.Comparison for .NET Docs](https://docs.groupdocs.com/comparison/net/)  
- **Αναφορά API**: [Complete API Reference](https://reference.groupdocs.com/comparison/net/)  
- **Λήψη τελευταίας έκδοσης**: [GroupDocs Downloads](https://releases.groupdocs.com/comparison/net/)  
- **Δωρεάν δοκιμή**: [Start Your Trial](https://releases.groupdocs.com/comparison/net/)  
- **Επιλογές αγοράς**: [Licensing and Pricing](https://purchase.groupdocs.com/buy)

---

**Τελευταία ενημέρωση:** 2026-09-15  
**Δοκιμάστηκε με:** GroupDocs.Comparison 25.4.0 for .NET  
**Συγγραφέας:** GroupDocs

---

## Σχετικά μαθήματα

- [Οδηγός GroupDocs Comparison NET - Πλήρης οδηγός σύγκρισης εγγράφων με μεταδεδομένα](/comparison/net/metadata-management/guide-groupdocs-comparison-net-metadata-setting/)  
- [Πώς να εξάγετε μεταδεδομένα από αποτελέσματα σύγκρισης .NET – Πλήρης οδηγός](/comparison/net/basic-usage/get-document-info-from-result-document/)  
- [Σύγκριση εγγράφων .NET - Πώς να αποθηκεύσετε τα μεταδεδομένα προορισμού](/comparison/net/loading-and-saving-documents/saving-documents-metadata-target/)