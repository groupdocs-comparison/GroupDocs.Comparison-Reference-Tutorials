---
categories:
- Image Processing
date: '2026-05-31'
description: Μάθετε πώς να συγκρίνετε εικόνες στο .NET χρησιμοποιώντας το GroupDocs.Comparison
  ενώ απενεργοποιείτε τη σελίδα σύνοψης. Αυτό το εκπαιδευτικό υλικό καλύπτει τη ρύθμιση,
  τον κώδικα, συμβουλές απόδοσης και πραγματικές περιπτώσεις χρήσης.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Συγκρίνετε εικόνες .NET χωρίς σύνοψη
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Πώς να συγκρίνετε εικόνες στο .NET – Παράλειψη σελίδας σύνοψης
type: docs
url: /el/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Πώς να Συγκρίνετε Εικόνες σε .NET – Παράλειψη Σελίδας Περίληψης

Όταν χρειάζεστε **how to compare images** προγραμματιστικά σε μια εφαρμογή .NET, το τελευταίο που θέλετε είναι μια επιπλέον σελίδα περίληψης που σπαταλά χρόνο και χώρο αποθήκευσης. Είτε χτίζετε μια γραμμή ελέγχου ποιότητας, μια αλυσίδα διαχείρισης περιεχομένου ή μια αυτοματοποιημένη σουίτα οπτικής παλινδρόμησης, η παράλειψη της σελίδας περίληψης μπορεί να μειώσει δευτερόλεπτα από κάθε εκτέλεση και να διατηρήσει το αποτύπωμα δίσκου σας λεπτό.

Σε αυτό το σεμινάριο θα μάθετε πώς να χρησιμοποιείτε το **GroupDocs.Comparison for .NET** για να συγκρίνετε δύο εικόνες αποδοτικά, να ρυθμίσετε τη βιβλιοθήκη ώστε να καταστέλλει τη δημιουργία περίληψης και να εφαρμόσετε τεχνικές βέλτιστης απόδοσης. Θα εξερευνήσουμε επίσης γιατί είναι σημαντικό, πότε να το χρησιμοποιήσετε και πώς να αποφύγετε κοινά προβλήματα.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο πιο γρήγορος τρόπος για να συγκρίνετε εικόνες χωρίς σελίδα περίληψης;** Use `Comparer` with `CompareOptions` and set `GenerateSummaryPage = false`.  
- **Ποια βιβλιοθήκη υποστηρίζει αυτό έτοιμη προς χρήση;** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Χρειάζομαι άδεια;** Yes, a commercial license is required for production; a free trial works for development.  
- **Μπορώ να συγκρίνω περισσότερες από δύο εικόνες ταυτόχρονα;** Absolutely – call `Add()` multiple times before `Compare()`.  
- **Είναι αυτή η προσέγγιση κατάλληλη για μεγάλες παρτίδες εργασιών;** Yes, when combined with batch processing and proper memory handling.

## Τι είναι το GroupDocs.Comparison;

`GroupDocs.Comparison` είναι μια βιβλιοθήκη .NET που εντοπίζει οπτικές διαφορές μεταξύ εγγράφων και εικόνων, παράγοντας αποτελέσματα πλάι‑πλάι ή επικάλυψης. Υποστηρίζει **50+ μορφές εισόδου και εξόδου**, συμπεριλαμβανομένων JPEG, PNG, BMP, TIFF και GIF, και μπορεί να επεξεργαστεί αρχεία πολλών εκατοντάδων σελίδων χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη.

## Γιατί να Παραλείψετε τη Σελίδα Περίληψης;

Η απενεργοποίηση της σελίδας περίληψης μειώνει το I/O έως και **70 %** για συγκρίσεις μόνο εικόνων και μειώνει το χρόνο επεξεργασίας κατά περίπου **30 %** κατά μέσο όρο, σύμφωνα με το σύνολο benchmark της βιβλιοθήκης. Όταν χρειάζεστε μόνο τη διαφορά εικόνας (για αυτοματοποιημένες δοκιμές ή αποφάσεις QC pass/fail), η επιπλέον αναφορά HTML δεν προσθέτει αξία και καταναλώνει μόνο χώρο δίσκου.

## Προαπαιτούμενα και Ρύθμιση Περιβάλλοντος

### Τι Θα Χρειαστείτε
- **GroupDocs.Comparison for .NET** version **25.4.0** ή νεότερη  
- Visual Studio 2019 + ή οποιοδήποτε IDE συμβατό με .NET  
- .NET Framework 4.6.1 + **ή** .NET Core 2.0 +  
- Βασικές γνώσεις C# και εξοικείωση με file I/O  

### Συνιστώμενα Επιπρόσθετα
- Ένα μικρό δοκιμαστικό έργο που περιέχει ένα ζευγάρι δείγμα εικόνων (π.χ., `source.png` και `target.png`).  
- Προαιρετικά: Ρύθμιση dependency injection εάν προτιμάτε αρχιτεκτονική προσανατολισμένη σε υπηρεσίες.  

### Γιατί Αυτά τα Προαπαιτούμενα Είναι Σημαντικά
Η συγκεκριμένη έκδοση της βιβλιοθήκης περιλαμβάνει τη σημαία `GenerateSummaryPage` και βελτιώσεις απόδοσης που λείπουν από παλαιότερες εκδόσεις. Η χρήση ενός σύγχρονου IDE εξασφαλίζει ότι μπορείτε να αξιοποιήσετε τη διαχείριση πακέτων NuGet και να δείτε προειδοποιήσεις κατά τη μεταγλώττιση νωρίς.

## Πώς να Εγκαταστήσετε το GroupDocs.Comparison

Το GroupDocs.Comparison μπορεί να προστεθεί σε οποιοδήποτε έργο .NET μέσω NuGet, το οποίο διαχειρίζεται τη λήψη των δυαδικών αρχείων και την ενημέρωση του αρχείου έργου. Επιλέξτε τη μέθοδο που ταιριάζει στη ροή εργασίας σας: το Package Manager Console για χρήστες Visual Studio ή το .NET CLI για περιβάλλοντα γραμμής εντολών. Και οι δύο εντολές επιλύουν αυτόματα τις εξαρτήσεις και εξασφαλίζουν ότι η σωστή έκδοση αναφέρεται.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Αντικαταστήστε το `25.4.0` με την ακριβή έκδοση που σκοπεύετε να κλειδώσετε.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Και οι δύο εντολές προσθέτουν τη βιβλιοθήκη στο αρχείο έργου σας και επαναφέρουν τα απαραίτητα δυαδικά αρχεία.

**Pro Tip:** Καρφιτσώστε την έκδοση στο `.csproj` σας για να αποφύγετε τυχαίες αναβαθμίσεις που θα μπορούσαν να αλλάξουν τη συμπεριφορά του API.

## Σκέψεις για την Άδεια

Το GroupDocs.Comparison απαιτεί άδεια για οποιαδήποτε παραγωγική ανάπτυξη. Μπορείτε να ξεκινήσετε με μια **δωρεάν δοκιμή** που παρέχει πλήρη λειτουργικότητα, στη συνέχεια να αναβαθμίσετε σε **προσωρινή άδεια** για εκτεταμένες δοκιμές, και τελικά σε **πλήρη εμπορική άδεια** για παραγωγή. Θυμηθείτε να τοποθετήσετε το αρχείο `GroupDocs.Comparison.lic` στη ρίζα της εφαρμογής ή να καθορίσετε τη διαδρομή του προγραμματιστικά.

## Βασική Ρύθμιση Έργου

Δημιουργήστε μια νέα εφαρμογή κονσόλας (ή ενσωματώστε σε υπάρχουσα υπηρεσία) και προσθέστε τον παρακάτω βασικό κώδικα. Αυτό το απόσπασμα δείχνει τη ελάχιστη ρύθμιση που απαιτείται πριν εμβαθύνετε στη λογική σύγκρισης.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Important:** Πάντα χρησιμοποιείτε `Path.Combine()` για διαδρομές αρχείων. Διαχειρίζεται αυτόματα τους διαχωριστές διαδρομών του λειτουργικού συστήματος και αποφεύγει λεπτές δυσλειτουργίες όταν μετακινείστε μεταξύ κοντέινερ Windows και Linux.

## Οδηγός Υλοποίησης Βήμα‑βήμα

### Πώς μπορώ να συγκρίνω εικόνες χωρίς σελίδα περίληψης;

`Comparer` είναι η κύρια κλάση στο GroupDocs.Comparison που οργανώνει τις λειτουργίες σύγκρισης εγγράφων και εικόνων. `CompareOptions` περιέχει ρυθμίσεις διαμόρφωσης που ελέγχουν πώς εκτελείται η σύγκριση, όπως το αν θα δημιουργηθεί σελίδα περίληψης. Φορτώστε την εικόνα προέλευσης, ρυθμίστε το `CompareOptions` ώστε να απενεργοποιεί τη σύνοψη, προσθέστε την εικόνα-στόχο και καλέστε `Compare()`. Η μέθοδος επιστρέφει ένα `ComparisonResult` που περιέχει το ρεύμα της εικόνας diff, το οποίο μπορείτε να γράψετε στο δίσκο, να στείλετε μέσω δικτύου ή να ενσωματώσετε σε στοιχείο UI. Αυτή η προσέγγιση εξασφαλίζει ότι παράγεται μόνο η ουσιώδης διαφορά, εξαλείφοντας τυχόν επιπλέον αναφορές HTML ή PDF.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

Ο παραπάνω κώδικας εκτελεί ολόκληρη τη σύγκριση σε **τέσσερα λογικά βήματα** και γράφει μόνο την εικόνα diff, παραλείποντας οποιαδήποτε σύνοψη HTML ή PDF.

### Βήμα 1: Αρχικοποίηση του Αντικειμένου Comparer

Η κλάση `Comparer` είναι η πύλη για όλες τις λειτουργίες σύγκρισης. Υλοποιεί το `IDisposable`, έτσι η περιτύλιξή της σε μπλοκ `using` εγγυάται ότι τα handles αρχείων και η μη διαχειριζόμενη μνήμη απελευθερώνονται άμεσα, ακόμη και αν προκληθεί εξαίρεση.

### Βήμα 2: Ρύθμιση του CompareOptions για Καμία Σύνοψη

Ορίστε `GenerateSummaryPage = false` στο αντικείμενο `CompareOptions`. Αυτή η σημαία λέει στη μηχανή να παραλείψει τη δημιουργία της προεπιλεγμένης αναφοράς HTML, η οποία είναι η κύρια πηγή επιπλέον I/O σε σενάρια μόνο εικόνας.

### Βήμα 3: Προσθήκη Εικόνας‑Στόχου για Σύγκριση

Μπορείτε να καλέσετε το `Add()` πολλές φορές για να συγκρίνετε μια προέλευση με πολλαπλούς στόχους σε μία παρτίδα. Κάθε κλήση μπορεί να λαμβάνει το δικό της `CompareOptions` εάν χρειάζεστε προσαρμογές ανά εικόνα.

### Βήμα 4: Εκτέλεση Σύγκρισης και Αποθήκευση Αποτελεσμάτων

`Comparer.Compare()` εκτελεί το βαρέως βάρους έργο και επιστρέφει ένα `ComparisonResult`. Το αποτέλεσμα περιέχει ένα `Stream` με την εικόνα diff, το οποίο μπορείτε να αποθηκεύσετε απευθείας στο δίσκο, να στείλετε μέσω δικτύου ή να ενσωματώσετε σε στοιχείο UI.

## Πλήρης Μέθοδος Έτοιμη για Παραγωγή

Παρακάτω είναι μια έτοιμη προς χρήση μέθοδος που μπορείτε να ενσωματώσετε σε οποιαδήποτε υπηρεσία .NET. Περιλαμβάνει επικύρωση διαδρομής, διαχείριση εξαιρέσεων και προαιρετικά hooks καταγραφής.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Συνηθισμένα Πιθανά Λάθη Υλοποίησης (Και Πώς να τα Αποφύγετε)

- **Path Issues:** Πάντα επαληθεύετε ότι τα αρχεία προέλευσης και στόχου υπάρχουν με `File.Exists()`. Ένα ελλιπές αρχείο θα προκαλέσει `FileNotFoundException` που μπορεί να πιαστεί νωρίς.  
- **Memory Pressure:** Μεγάλες εικόνες (10 MB +) μπορούν να καταναλώσουν σημαντική μνήμη RAM. Επεξεργαστείτε τις σε παρτίδες και σκεφτείτε τη μείωση ανάλυσης εάν δεν απαιτείται pixel‑perfect ακρίβεια.  
- **File Locks:** Βεβαιωθείτε ότι καμία άλλη διεργασία δεν κρατά αποκλειστικό κλείδωμα στα αρχεία εικόνας. Αυτό είναι ιδιαίτερα σημαντικό σε πολυνηματικά ή κοντέινερ περιβάλλοντα.

## Πρακτικές Εφαρμογές και Περιπτώσεις Χρήσης

### Έλεγχος Ποιότητας στην Κατασκευή

Μια γραμμή παραγωγής καταγράφει εικόνες κάθε αντικειμένου και τις συγκρίνει με μια χρυσή αναφορά. Η παράλειψη της σελίδας περίληψης επιτρέπει στο σύστημα να αποφασίζει “pass” ή “fail” μέσα σε χιλιοστά του δευτερολέπτου, διατηρώντας τη γραμμή σε υψηλή ταχύτητα.

### Συστήματα Διαχείρισης Περιεχομένου

Όταν οι χρήστες ανεβάζουν περιουσιακά στοιχεία, το CMS μπορεί άμεσα να εντοπίσει διπλότυπα ή σχεδόν διπλότυπα, αποτρέποντας την υπερφόρτωση αποθήκευσης και βελτιώνοντας τη σχετικότητα αναζήτησης. Η εικόνα diff μπορεί να αποθηκευτεί ως μικρογραφία για γρήγορη οπτική επιθεώρηση.

### Αυτοματοποιημένες Δοκιμές UI (Οπτική Παλινδρόμηση)

Το Selenium ή το Playwright μπορούν να καταγράψουν στιγμιότυπα οθόνης μιας ιστοσελίδας, έπειτα να τα δώσουν σε αυτή τη ρουτίνα σύγκρισης. Η εικόνα diff επισημαίνει αλλαγές UI, και επειδή δεν δημιουργείται σύνοψη, η CI pipeline παραμένει γρήγορη και ελαφριά.

### Ιατρική Απεικόνιση (Με Ελεγκτικό Καταγραφή)

Οι ροές εργασίας της ακτινολογίας μερικές φορές χρειάζονται να επισημάνουν αλλαγές μεταξύ διαδοχικών σαρώσεων. Ενώ μπορεί να δημιουργηθεί λεπτομερές αρχείο ελέγχου, η ίδια η εικόνα diff μπορεί να παραχθεί χωρίς σελίδα περίληψης, μειώνοντας το χρόνο επεξεργασίας για μεγάλα DICOM‑μετατρεπόμενα PNG.

## Σκέψεις για Απόδοση και Βελτιστοποίηση

### Βέλτιστες Πρακτικές Διαχείρισης Μνήμης

Επεξεργαστείτε εικόνες σε **παρτίδες 20–50** ανάλογα με τη μνήμη RAM του διακομιστή. Απελευθερώστε κάθε αντικείμενο `Comparer` άμεσα και καλέστε `GC.Collect()` μόνο αν παρατηρήσετε αυξήσεις μνήμης κατά τις μακροχρόνιες εργασίες.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Βελτιστοποίηση I/O Δίσκου

Τοποθετήστε τους καταλόγους εισόδου, εξόδου και προσωρινών αρχείων στον ίδιο γρήγορο SSD όγκο. Διαγράψτε τα προσωρινά αρχεία αμέσως μετά την αποθήκευση της εικόνας diff για να αποφύγετε περιττή χρήση δίσκου.

### Σκέψεις για Threading και Async

Το GroupDocs.Comparison είναι thread‑safe για λειτουργίες μόνο ανάγνωσης, αλλά αποφύγετε την κοινή χρήση ενός ενιαίου αντικειμένου `Comparer` μεταξύ νημάτων. Αντ' αυτού, δημιουργήστε ανεξάρτητα tasks:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Επίλυση Συνηθισμένων Προβλημάτων

### Σφάλματα Διαδρομής Αρχείου και Δικαιωμάτων

- **Symptom:** `FileNotFoundException` ή `UnauthorizedAccessException`.  
- **Solution:** Χρησιμοποιήστε `Path.GetFullPath()` για εντοπισμό της επιλυμένης διαδρομής, βεβαιωθείτε ότι η ταυτότητα του application pool (ή του χρήστη Docker container) έχει δικαιώματα ανάγνωσης/εγγραφής, και ελέγξτε ξανά ότι η διαδρομή δεν έχει περικοπεί από μεταβλητές περιβάλλοντος.

### Στενά Μνήμης και Απόδοσης

- **Symptom:** Αργές εκτελέσεις ή `OutOfMemoryException`.  
- **Solution:** Αλλάξτε το μέγεθος των εικόνων σε κοινή ανάλυση (π.χ., 1024 × 768) όταν δεν απαιτείται ακριβής pixel σύγκριση. Παρακολουθήστε τη μνήμη με εργαλεία όπως dotMemory ή τον ενσωματωμένο Performance Profiler.

### Προβλήματα Άδειας

- **Symptom:** Εικόνα diff με υδατογράφημα ή `LicenseException`.  
- **Solution:** Επιβεβαιώστε ότι το `GroupDocs.Comparison.lic` βρίσκεται στον φάκελο εκτελέσιμου ή φορτώστε το ρητά μέσω `License license = new License(); license.SetLicense("path/to/license.file");`.

## Προχωρημένες Επιλογές Διαμόρφωσης

### Προσαρμογή Ευαισθησίας Σύγκρισης

Μπορείτε να ρυθμίσετε λεπτομερώς πώς η μηχανή αντιμετωπίζει μικρές διαφορές pixel (π.χ., τεχνουργήματα συμπίεσης) ρυθμίζοντας την ιδιότητα `Sensitivity` στο `CompareOptions`. Χαμηλότερες τιμές κάνουν τη σύγκριση πιο αυστηρή.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Βελτιστοποίηση Μορφής Εξόδου

Εάν χρειάζεστε την εικόνα diff σε συγκεκριμένη μορφή (PNG vs. JPEG), ορίστε την ιδιότητα `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```
```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Ενσωμάτωση με Δημοφιλή .NET Frameworks

### Παράδειγμα Υπηρεσίας ASP.NET Core

Αποκτήστε ένα ελαφρύ HTTP endpoint που δέχεται δύο ροές εικόνας, εκτελεί τη σύγκριση και επιστρέφει την εικόνα diff ως `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Καταχώρηση Dependency Injection

Προσθέστε το comparer ως scoped service στο `Program.cs` ή `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Συχνές Ερωτήσεις

**Q: Ποιο είναι το κύριο πλεονέκτημα της παράλειψης της σελίδας περίληψης;**  
A: Μειώνει το χρόνο επεξεργασίας έως και 30 % και μειώνει τη χρήση δίσκου κατά περίπου 70 % για συγκρίσεις μόνο εικόνων, κάτι που είναι κρίσιμο για αγωγούς υψηλής απόδοσης.

**Q: Μπορώ ακόμη να ανακτήσω λεπτομερή μεταδεδομένα αλλαγών χωρίς σελίδα περίληψης;**  
A: Ναι. Το αντικείμενο `ComparisonResult` εκθέτει μια συλλογή `Changes` που περιέχει προγραμματιστικές πληροφορίες για κάθε ανιχνευθείσα διαφορά.

**Q: Ποιες μορφές εικόνας υποστηρίζονται;**  
A: JPEG, PNG, BMP, TIFF, GIF, και αρκετές άλλες — πάνω από 50 μορφές συνολικά.

**Q: Πώς πρέπει να διαχειριστώ πολύ μεγάλες εικόνες (π.χ., >20 MB);**  
A: Επεξεργαστείτε τις σε μικρότερες παρτίδες, προαιρετικά μειώστε την ανάλυση και παρακολουθήστε τη χρήση μνήμης. Η χρήση του `Comparer` σε μπλοκ `using` εξασφαλίζει ότι οι πόροι απελευθερώνονται άμεσα.

**Q: Είναι αυτή η προσέγγιση ασφαλής για πολυνηματικές εφαρμογές;**  
A: Ναι, εφόσον κάθε νήμα δημιουργεί το δικό του αντικείμενο `Comparer`. Η κοινή χρήση ενός ενιαίου αντικειμένου μπορεί να οδηγήσει σε συνθήκες αγώνα.

## Πρόσθετοι Πόροι

- [Τεκμηρίωση GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Αναφορά API](https://reference.groupdocs.com/comparison/net/)
- [Λήψη](https://releases.groupdocs.com/comparison/net/)
- [Αγορά](https://purchase.groupdocs.com/buy)
- [Δωρεάν Δοκιμή](https://releases.groupdocs.com/comparison/net/)
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)
- [Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/comparison/)

---

**Τελευταία Ενημέρωση:** 2026-05-31  
**Δοκιμάστηκε Με:** GroupDocs.Comparison 25.4.0 for .NET  
**Συγγραφέας:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```
```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```
```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```
```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```
```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```
```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```
```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Σχετικά Μαθήματα

- [Σύγκριση Εικόνας .NET - Συγκρίνετε Εικόνες Προγραμματιστικά](/comparison/net/image-comparison/compare-images-from-path/)
- [Σύγκριση Εικόνας .NET - Συγκρίνετε Εικόνες από Ροή](/comparison/net/image-comparison/compare-images-from-stream/)
- [Οδηγός GroupDocs Comparison .NET - Πλήρης Βασικός Οδηγός Χρήσης](/comparison/net/basic-usage/)