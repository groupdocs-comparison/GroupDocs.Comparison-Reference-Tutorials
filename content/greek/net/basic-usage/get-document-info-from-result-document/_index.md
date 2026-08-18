---
categories:
- Document Comparison
date: '2026-06-15'
description: Μάθετε πώς να εξάγετε metadata από τα .NET Comparison Results χρησιμοποιώντας
  το GroupDocs.Comparison. Οδηγός βήμα‑βήμα με code examples και practical tips.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Εξαγωγή Document Info από τα Comparison Results
schemas:
- author: GroupDocs
  dateModified: '2026-06-15'
  description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  headline: How to Extract Metadata from .NET Comparison Results – Complete Guide
  type: TechArticle
- description: Learn how to extract metadata from .NET comparison results using GroupDocs.Comparison.
    Step‑by‑step guide with code examples and practical tips.
  name: How to Extract Metadata from .NET Comparison Results – Complete Guide
  steps:
  - name: Initialize Comparer with Source Document
    text: '`Comparer` is the core class in GroupDocs.Comparison that loads the source
      document and orchestrates comparison operations. Using a `using` block guarantees
      that all unmanaged resources are released automatically. > **Pro Tip:** You
      can pass any `Stream` (file, memory, cloud) to the `Comparer` const'
  - name: Add Target Document for Comparison
    text: The `Add()` method accepts additional streams or file paths, enabling one‑to‑many
      comparisons. > **Important:** The order of added documents influences the way
      changes are highlighted in the final report.
  - name: Retrieve Document Info from Result Document
    text: '`IDocumentInfo` provides a unified view of document metadata such as file
      type, page count, and size across all supported formats. > **Understanding the
      Data:** The returned object works the same for DOCX, PDF, XLSX, and PPTX, so
      you can write format‑agnostic code.'
  - name: Display Document Info
    text: 'Once you have the `IDocumentInfo` instance, you can log, store, or present
      its properties. The three most commonly used properties are: - **FileType**
      – e.g., `DOCX`, `PDF`, `XLSX`. - **PageCount** – total pages or slides. - **Size**
      – file size in bytes (useful for storage calculations).'
  type: HowTo
- questions:
  - answer: Yes, it supports **50+ formats** including DOCX, PDF, PPTX, XLSX, TXT,
      and many others, providing consistent metadata extraction across them.
    question: Is GroupDocs.Comparison for .NET compatible with various document formats?
  - answer: Absolutely. Settings such as sensitivity, change types, and output format
      are independent of the `GetDocumentInfo()` call.
    question: Can I customize comparison settings without affecting metadata extraction?
  - answer: Yes, download a free trial from the [GroupDocs releases page](https://releases.groupdocs.com/).
      The trial includes full metadata extraction capabilities.
    question: Is there a trial version I can use for evaluation?
  - answer: Use the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12)
      for community help and official support from the GroupDocs team.
    question: Where can I get support for implementation questions?
  - answer: GroupDocs offers developer, site, and OEM licenses. Purchase options are
      listed on the [GroupDocs purchase page](https://purchase.groupdocs.com/buy).
    question: What licensing options are available for production deployments?
  type: FAQPage
second_title: GroupDocs.Comparison .NET API
tags:
- groupdocs-comparison
- document-metadata
- dotnet-api
- document-properties
title: Πώς να εξάγετε metadata από τα .NET Comparison Results – Πλήρης Οδηγός
type: docs
url: /el/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Πώς να εξάγετε μεταδεδομένα από τα αποτελέσματα σύγκρισης .NET – Πλήρης Οδηγός

Όταν εργάζεστε με συγκρίσεις εγγράφων σε εφαρμογές .NET, μπορεί να αναρωτιέστε **πώς να εξάγετε μεταδεδομένα** από τα αποτελέσματα σύγκρισης. Τα μεταδεδομένα όπως ο τύπος αρχείου, ο αριθμός σελίδων και το μέγεθος του εγγράφου μπορούν να είναι κρίσιμα για τα αρχεία ελέγχου, τη βελτιστοποίηση απόδοσης ή απλώς για την εμφάνιση χρήσιμων πληροφοριών στους τελικούς χρήστες. Αυτό το εκπαιδευτικό υλικό σας καθοδηγεί στην αποδοτική ανάκτηση αυτών των δεδομένων με το GroupDocs.Comparison για .NET.

## Σύντομες Απαντήσεις
- **Ποια είναι η κύρια κλάση για σύγκριση;** `Comparer` loads the source document and runs the comparison engine.  
- **Ποια μέθοδος επιστρέφει μεταδεδομένα;** `GetDocumentInfo()` on a target document returns an `IDocumentInfo` object.  
- **Μπορώ να λάβω το μέγεθος του εγγράφου σε .NET;** Yes – the `Size` property of `IDocumentInfo` returns the size in bytes.  
- **Χρειάζομαι άδεια για την εξαγωγή μεταδεδομένων;** A valid GroupDocs.Comparison license is required for production use; the free trial supports all metadata features.  
- **Είναι το API συμβατό με .NET 6;** Absolutely – GroupDocs.Comparison supports .NET Framework 4.6.1+, .NET Core 2.0+, and .NET 5/6+.

Η μέθοδος `GetDocumentInfo()` επιστρέφει ένα αντικείμενο `IDocumentInfo` που περιέχει μεταδεδομένα εγγράφου.

## Τι είναι η εξαγωγή μεταδεδομένων στη σύγκριση εγγράφων;
Η εξαγωγή μεταδεδομένων είναι η διαδικασία ανάκτησης περιγραφικών πληροφοριών—όπως ο τύπος αρχείου, ο αριθμός σελίδων και το μέγεθος αρχείου—από τα έγγραφα που συμμετέχουν σε μια λειτουργία σύγκρισης. Το GroupDocs.Comparison εκθέτει αυτά τα δεδομένα μέσω ενός ενοποιημένου API, καθιστώντας εύκολο το καταγραφή, η εμφάνιση ή η χρήση τους για υπό όρους επεξεργασία.

## Γιατί να εξάγετε μεταδεδομένα από τα αποτελέσματα σύγκρισης;
Η εξαγωγή μεταδεδομένων σας επιτρέπει να δημιουργήσετε λεπτομερή αρχεία ελέγχου, να δρομολογήσετε αρχεία βάσει τύπου και να προσαρμόσετε στρατηγικές επεξεργασίας για μεγάλα έγγραφα. Γνωρίζοντας τον τύπο αρχείου, τον αριθμό σελίδων και το μέγεθος, μπορείτε να επιβάλλετε κανόνες συμμόρφωσης, να εκτιμήσετε τον χρόνο επεξεργασίας και να παρουσιάσετε σαφείς πληροφορίες στους χρήστες πριν ξεκινήσουν τη σύγκριση.

## Προαπαιτούμενα

1. **GroupDocs.Comparison for .NET** – Εγκαταστήστε τη βιβλιοθήκη από τη [σελίδα επίσημων κυκλοφοριών](https://releases.groupdocs.com/comparison/net/).  
   Μπορείτε επίσης να περιηγηθείτε σε όλες τις κυκλοφορίες στη [σελίδα κυκλοφοριών GroupDocs](https://releases.groupdocs.com/).  
2. **Περιβάλλον Ανάπτυξης** – Visual Studio, VS Code ή οποιοδήποτε IDE που υποστηρίζει .NET 6+.  
3. **Δειγματικά Έγγραφα** – Δύο αρχεία (π.χ., `SOURCE.docx` και `TARGET.docx`) για δοκιμή. Το API λειτουργεί με πάνω από **50 μορφές εγγράφων**.

## Εισαγωγή Χώρων Ονομάτων

Οι παρακάτω οδηγίες `using` σας δίνουν πρόσβαση στον πυρήνα της μηχανής σύγκρισης, τα εργαλεία διαχείρισης αρχείων και τις διεπαφές μεταδεδομένων.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Αυτές οι εισαγωγές απαιτούνται πριν δημιουργήσετε οποιοδήποτε αντικείμενο GroupDocs.

## Πώς να Εξάγετε Μεταδεδομένα από Αποτελέσματα Σύγκρισης;

Η κλάση `Comparer` φορτώνει το έγγραφο προέλευσης και οργανώνει τη διαδικασία σύγκρισης.

Για να ανακτήσετε μεταδεδομένα, πρώτα φορτώστε το έγγραφο προέλευσης με μια παρουσία `Comparer`, στη συνέχεια προσθέστε το(τα) έγγραφο-στόχο. Αφού η μηχανή σύγκρισης αρχικοποιηθεί, καλέστε `GetDocumentInfo()` σε κάθε στόχο για να λάβετε ένα αντικείμενο `IDocumentInfo` που περιέχει ιδιότητες όπως τύπος αρχείου, αριθμός σελίδων και μέγεθος. Αυτή η προσέγγιση λειτουργεί ομοιόμορφα σε όλες τις υποστηριζόμενες μορφές.

### Βήμα 1: Αρχικοποίηση Comparer με Έγγραφο Πηγής

`Comparer` είναι η κύρια κλάση στο GroupDocs.Comparison που φορτώνει το έγγραφο προέλευσης και οργανώνει τις λειτουργίες σύγκρισης. Η χρήση ενός μπλοκ `using` εγγυάται ότι όλοι οι μη διαχειριζόμενοι πόροι απελευθερώνονται αυτόματα.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Συμβουλή:** Μπορείτε να περάσετε οποιοδήποτε `Stream` (αρχείο, μνήμη, σύννεφο) στον κατασκευαστή `Comparer`, όχι μόνο διαδρομή αρχείου.

### Βήμα 2: Προσθήκη Εγγράφου-Στόχου για Σύγκριση

Η μέθοδος `Add()` δέχεται επιπλέον ροές ή διαδρομές αρχείων, επιτρέποντας συγκρίσεις ένας‑προς‑πολλούς.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Σημαντικό:** Η σειρά των προστιθέμενων εγγράφων επηρεάζει τον τρόπο με τον οποίο επισημαίνονται οι αλλαγές στην τελική αναφορά.

### Βήμα 3: Ανάκτηση Πληροφοριών Εγγράφου από το Έγγραφο Αποτελέσματος

`IDocumentInfo` παρέχει μια ενοποιημένη προβολή των μεταδεδομένων εγγράφου όπως τύπος αρχείου, αριθμός σελίδων και μέγεθος σε όλες τις υποστηριζόμενες μορφές.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Κατανόηση των Δεδομένων:** Το επιστρεφόμενο αντικείμενο λειτουργεί το ίδιο για DOCX, PDF, XLSX και PPTX, ώστε να μπορείτε να γράψετε κώδικα ανεξάρτητο από τη μορφή.

### Βήμα 4: Εμφάνιση Πληροφοριών Εγγράφου

Μόλις έχετε την παρουσία `IDocumentInfo`, μπορείτε να καταγράψετε, αποθηκεύσετε ή να παρουσιάσετε τις ιδιότητές της.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Οι τρεις πιο συχνά χρησιμοποιούμενες ιδιότητες είναι:

- **FileType** – π.χ., `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – συνολικές σελίδες ή διαφάνειες.  
- **Size** – μέγεθος αρχείου σε bytes (χρήσιμο για υπολογισμούς αποθήκευσης).

## Πώς να Λάβετε το Μέγεθος Εγγράφου σε .NET;

Η ιδιότητα `Size` επιστρέφει το μέγεθος του αρχείου σε bytes.

Το μέγεθος του εγγράφου μπορεί να προσπελαστεί απευθείας από την παρουσία `IDocumentInfo` μέσω της ιδιότητας `Size`. Αυτή η ιδιότητα επιστρέφει τον ακριβή αριθμό bytes του αρχικού αρχείου, επιτρέποντάς σας να το μετατρέψετε σε kilobytes ή megabytes για εμφάνιση ή υπολογισμούς αποθήκευσης. Αντιπροσωπεύει το μέγεθος του αρχικού αρχείου, όχι κάποια επεξεργασμένη έκδοση.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Σημείωση:** Η τιμή `Size` αντιπροσωπεύει το αρχικό μέγεθος του αρχείου, όχι το μέγεθος μετά από οποιαδήποτε εσωτερική επεξεργασία ή συμπίεση.

## Συνηθισμένες Περιπτώσεις Χρήσης και Πρακτικές Εφαρμογές

- **Batch Processing:** Χρησιμοποιήστε τον τύπο αρχείου για να δρομολογήσετε αρχεία DOCX σε μια ροή εργασίας ειδική για Word και PDFs σε μια βελτιστοποιημένη για PDF διαδικασία.  
- **Storage Management:** Αρχειοθετήστε έγγραφα μεγαλύτερα από 10 MB σε ένα ψυχρό‑αποθηκευτικό bucket αυτόματα.  
- **User Feedback:** Εμφανίστε τον αριθμό σελίδων και το μέγεθος πριν από τη σύγκριση για να θέσετε ρεαλιστικές προσδοκίες για τον χρόνο επεξεργασίας.  
- **Quality Assurance:** Επαληθεύστε ότι τα ανεβασμένα αρχεία είναι πλήρη συγκρίνοντας τους αναμενόμενους με τους πραγματικούς αριθμούς σελίδων.

## Επίλυση Συνηθισμένων Προβλημάτων

- **File Access Errors:** Επαληθεύστε τα δικαιώματα ανάγνωσης και χρησιμοποιήστε απόλυτες διαδρομές κατά την ανάπτυξη.  
- **Memory Pressure with Large Files:** Προτιμήστε τη ροή (`File.OpenRead`) αντί για τη φόρτωση ολόκληρου του αρχείου στη μνήμη.  
- **Null Reference Exceptions:** Η `FirstOrDefault()` μπορεί να επιστρέψει `null` εάν δεν προστέθηκε στόχος· ελέγχετε πάντα πριν προσπελάσετε το `GetDocumentInfo()`.  

```csharp
var target = comparer.Targets.FirstOrDefault();
if (target != null)
{
    var info = target.GetDocumentInfo();
    // Use info safely
}
else
{
    Console.WriteLine("No target document was added.");
}
```

- **Limited Metadata for Plain Text:** Μορφές όπως `.txt` μπορεί να μην εκθέτουν ένα ουσιαστικό `PageCount`. Προστατέψτε τον κώδικα από ελλιπείς τιμές.

## Σκέψεις Απόδοσης

- **Stream Management:** Πάντα τυλίξτε τις ροές σε δηλώσεις `using` για γρήγορη απελευθέρωση των χειριστών αρχείων.  
- **Caching:** Αποθηκεύστε συχνά προσπελαζόμενα μεταδεδομένα σε cache για να αποφύγετε επαναλαμβανόμενη εξαγωγή.  
- **Batch Operations:** Επεξεργαστείτε έγγραφα σε ομάδες για να μειώσετε το κόστος και να βελτιώσετε τη ροή.

## Καλές Πρακτικές για Χρήση σε Παραγωγή

- **Robust Error Handling:** Περιβάλλετε την εξαγωγή μεταδεδομένων σε μπλοκ try‑catch για να διαχειρίζεστε κατεστραμμένα ή μη υποστηριζόμενα αρχεία με χάρη.  
- **Comprehensive Logging:** Καταγράψτε τον τύπο εγγράφου, το μέγεθος και τον αριθμό σελίδων για κάθε σύγκριση ώστε να βοηθήσετε στην επίλυση προβλημάτων και τη συμμόρφωση με τα αρχεία ελέγχου.  
- **Security Hygiene:** Αποφύγετε την αποκάλυψη πλήρων διαδρομών αρχείων ή εσωτερικών λεπτομερειών του διακομιστή σε μηνύματα UI.  
- **Resource Disposal:** Αποδεσμεύστε τις παρουσίες `Comparer` άμεσα, ειδικά σε web services που διαχειρίζονται πολλά ταυτόχρονα αιτήματα.

## Προχωρημένα Σενάρια

### Πολλαπλά Έγγραφα-Στόχοι

Αν συγκρίνετε μία πηγή με πολλούς στόχους, επαναλάβετε τη συλλογή `Targets` και εξάγετε μεταδεδομένα από κάθε ένα.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Υπό Όρους Επεξεργασία Βάσει Μεταδεδομένων

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Αποθήκευση Μεταδεδομένων σε Βάση Δεδομένων

Αποθηκεύστε μόνιμα το `FileType`, το `PageCount` και το `Size` σε έναν σχεσιακό πίνακα για να επιτρέψετε αναφορές και αναλύσεις σε χιλιάδες συγκρίσεις.

## Συχνές Ερωτήσεις

**Q: Είναι το GroupDocs.Comparison για .NET συμβατό με διάφορες μορφές εγγράφων;**  
A: Ναι, υποστηρίζει **πάνω από 50 μορφές** συμπεριλαμβανομένων των DOCX, PDF, PPTX, XLSX, TXT και πολλών άλλων, παρέχοντας συνεπή εξαγωγή μεταδεδομένων σε όλες τις μορφές.

**Q: Μπορώ να προσαρμόσω τις ρυθμίσεις σύγκρισης χωρίς να επηρεάσω την εξαγωγή μεταδεδομένων;**  
A: Απόλυτα. Ρυθμίσεις όπως η ευαισθησία, οι τύποι αλλαγών και η μορφή εξόδου είναι ανεξάρτητες από την κλήση `GetDocumentInfo()`.

**Q: Υπάρχει δοκιμαστική έκδοση που μπορώ να χρησιμοποιήσω για αξιολόγηση;**  
A: Ναι, κατεβάστε μια δωρεάν δοκιμή από τη [σελίδα κυκλοφοριών GroupDocs](https://releases.groupdocs.com/). Η δοκιμή περιλαμβάνει πλήρη δυνατότητα εξαγωγής μεταδεδομένων.

**Q: Πού μπορώ να λάβω υποστήριξη για ερωτήσεις υλοποίησης;**  
A: Χρησιμοποιήστε το [φόρουμ GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) για βοήθεια από την κοινότητα και επίσημη υποστήριξη από την ομάδα του GroupDocs.

**Q: Ποιες επιλογές αδειοδότησης είναι διαθέσιμες για παραγωγικές εγκαταστάσεις;**  
A: Η GroupDocs προσφέρει άδειες για προγραμματιστές, ιστότοπους και OEM. Οι επιλογές αγοράς αναφέρονται στη [σελίδα αγοράς GroupDocs](https://purchase.groupdocs.com/buy).

---

**Τελευταία Ενημέρωση:** 2026-06-15  
**Δοκιμάστηκε Με:** GroupDocs.Comparison 6.0 for .NET  
**Συγγραφέας:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Σχετικά Μαθήματα

- [Διαχείριση Μεταδεδομένων Εγγράφου .NET - Πλήρης Οδηγός για GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Λήψη Ιδιοτήτων Εγγράφου C# .NET - Εξαγωγή Μεταδεδομένων Αρχείου](/comparison/net/basic-usage/get-document-info-from-path/)
- [Διατήρηση Μεταδεδομένων Στόχου με GroupDocs.Comparison – .NET Tutorial](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)