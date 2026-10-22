---
categories:
- Java Development
date: '2026-10-15'
description: Μάθετε πώς να ορίσετε τη ροή άδειας GroupDocs σε Java χρησιμοποιώντας
  έναν κεντρικό διαχειριστή, με οδηγίες βήμα‑βήμα, troubleshooting και βέλτιστες πρακτικές
  για το 2026.
keywords:
- set groupdocs license stream
- centralized license manager
- stream‑based licensing
- GroupDocs Java licensing
lastmod: '2026-10-15'
linktitle: Οδηγός GroupDocs License Java
og_description: Ορίστε τη ροή άδειας GroupDocs σε Java με έναν κεντρικό διαχειριστή.
  Ακολουθήστε αυτόν τον οδηγό του 2026 για ασφαλή, container‑friendly licensing και
  troubleshooting.
og_image_alt: Guide showing Java code for loading GroupDocs license from a stream
og_title: Πώς να ορίσετε τη ροή άδειας GroupDocs σε Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-15'
  description: Learn how to set GroupDocs license stream in Java with a centralized
    manager, including troubleshooting and best practices.
  headline: How to set GroupDocs license stream in Java
  type: TechArticle
- description: Learn how to set GroupDocs license stream in Java with a centralized
    manager, including troubleshooting and best practices.
  name: How to set GroupDocs license stream in Java
  steps:
  - name: Verify license file integrity
    text: Check that the XML is well‑formed and matches the license you purchased.
      A corrupted file will raise a `LicenseException`.
  - name: Debug stream creation
    text: Print the size of the byte array (`licenseBytes.length`) before passing
      it to `setLicense()`; a size of zero indicates an empty stream.
  - name: Test license application
    text: Run a simple comparison task after loading the license. If the output contains
      watermarks, the license was not applied correctly.
  type: HowTo
- questions:
  - answer: No. Once a stream is read, it’s exhausted. Create a fresh stream each
      time or cache the raw byte array and wrap it in a new `ByteArrayInputStream`.
    question: Can I use the same license stream multiple times?
  - answer: GroupDocs runs in evaluation mode, inserting watermarks and limiting the
      number of processed pages.
    question: What happens if I don’t set a license?
  - answer: Yes. By loading the license directly from memory you avoid leaving a readable
      file on disk, which mitigates accidental exposure.
    question: Is stream‑based licensing more secure than file‑based?
  - answer: Absolutely. Call `LicenseManager.setLicense(newStream)` whenever you need
      to change the active license—for example, per‑tenant or per‑feature licensing.
    question: Can I switch licenses at runtime?
  - answer: Each node must load the license independently. Use a shared configuration
      service (Consul, Spring Cloud Config) or environment variables so every instance
      receives the same license data.
    question: How do I handle licensing in a clustered environment?
  type: FAQPage
tags:
- groupdocs
- java-licensing
- document-processing
- stream-api
- license-management
title: Πώς να ορίσετε τη ροή άδειας GroupDocs σε Java
type: docs
url: /el/java/licensing-configuration/set-groupdocs-license-stream-java-guide/
weight: 1
---

# Πώς να ορίσετε τη ροή άδειας GroupDocs σε Java

Εάν ενσωματώνετε το **GroupDocs.Comparison for Java** σε μια σύγχρονη εφαρμογή, ο πιο αξιόπιστος τρόπος διαχείρισης της άδειας είναι με έναν **κεντρικό διαχειριστή άδειας** που λειτουργεί με ροές Java. Αυτή η προσέγγιση σας επιτρέπει να φορτώνετε την άδεια από αρχεία, πόρους classpath, URLs ή ασφαλείς θησαυρούς—αφαιρώντας τις σκληρά κωδικοποιημένες διαδρομές και βελτιώνοντας την ασφάλεια.

## Γρήγορες απαντήσεις
- **Τι είναι ένας κεντρικός διαχειριστής άδειας;** Είναι ένα επαναχρησιμοποιήσιμο στοιχείο που φορτώνει και εφαρμόζει την άδεια GroupDocs για ολόκληρη την εφαρμογή, συνήθως ως singleton ή bean του Spring.  
- **Γιατί να χρησιμοποιήσετε ροές για την άδεια;** Οι ροές σας επιτρέπουν να διαβάζετε την άδεια από οποιαδήποτε πηγή (αρχείο, classpath, URL, θησαυρός) χωρίς να την αποθηκεύετε στον δίσκο, κάτι που ενισχύει την ασφάλεια και τη συμβατότητα με containers.  
- **Πότε πρέπει να μεταβείτε από άδεια βασισμένη σε αρχείο σε άδεια βασισμένη σε ροή;** Όποτε αναπτύσσετε σε Docker, Kubernetes ή οποιοδήποτε περιβάλλον cloud όπου η προσάρτηση αρχείων είναι άβολη.  
- **Πώς να αποφύγετε διαρροές μνήμης;** Τυλίξτε το InputStream σε ένα μπλοκ try‑with‑resources ή κλείστε το ρητά μετά την κλήση του `setLicense()`.  
- **Μπορώ να αλλάξω την άδεια κατά το χρόνο εκτέλεσης;** Ναι—καλέστε το `setLicense()` με μια νέα ροή όποτε χρειαστεί να αλλάξετε άδειες για έναν ενοικιαστή ή σύνολο λειτουργιών.

## Τι είναι ένας κεντρικός διαχειριστής άδειας;
Ένας **κεντρικός διαχειριστής άδειας** είναι μια μοναδική κλάση ή υπηρεσία που περιλαμβάνει όλη τη λογική για τη φόρτωση, την εφαρμογή και την ανανέωση της άδειας GroupDocs. Διατηρώντας αυτή τη λογική σε ένα μέρος, εξαλείφετε τον διπλό κώδικα, απλοποιείτε τις αλλαγές ρυθμίσεων και εξασφαλίζετε ότι κάθε μέρος της εφαρμογής σας χρησιμοποιεί την ίδια έγκυρη άδεια.

## Γιατί να επιλέξετε άδεια βασισμένη σε ροή;
Η χρήση μιας ροής για τη φόρτωση της άδειας GroupDocs παρέχει αρκετά απτά οφέλη σε σύγκριση με την κλασική προσέγγιση μέσω διαδρομής αρχείου. Αποσυνδέει τη θέση της άδειας από την εφαρμογή, επιτρέπει ασφαλή διαχείριση στη μνήμη, λειτουργεί απρόσκοπτα σε περιβάλλοντα containers και επιτρέπει δυναμικές αλλαγές άδειας κατά το χρόνο εκτέλεσης, βελτιώνοντας έτσι την ευελιξία, την ασφάλεια και την κλιμακωσιμότητα.

## Προαπαιτούμενα και ρύθμιση περιβάλλοντος

### Απαιτούμενες βιβλιοθήκες και εκδόσεις
- **GroupDocs.Comparison for Java** – έκδοση **25.2** ή νεότερη (η πιο πρόσφατη έκδοση του 2026).  
- **Java Development Kit (JDK)** – έκδοση **8+** (συνιστάται JDK 11+ για καλύτερη υποστήριξη μονάδων).  
- **Maven ή Gradle** – για διαχείριση εξαρτήσεων (τα παραδείγματα παρακάτω χρησιμοποιούν Maven).

### Διαμόρφωση Maven
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

### Απόκτηση της άδειάς σας
1. **Ξεκινήστε με τη δωρεάν δοκιμή** – έχετε πλήρη πρόσβαση στο API για 30 ημέρες.  
2. **Ζητήστε προσωρινή άδεια** – ιδανική για εκτεταμένη αξιολόγηση σε pipelines CI.  
3. **Αγοράστε άδεια παραγωγής** – απαιτείται για εμπορικές αναπτύξεις και αφαιρεί τα υδατογράμματα αξιολόγησης.

*Συμβουλή*: Αποθηκεύστε το ακατέργαστο κείμενο της άδειας σε έναν διαχειριστή μυστικών (AWS Secrets Manager, Azure Key Vault, HashiCorp Vault) και ανακτήστε το κατά το χρόνο εκτέλεσης. Αυτό διατηρεί την άδεια εκτός ελέγχου πηγαίου κώδικα και του συστήματος αρχείων.

## Επαλήθευση της πηγής της άδειας
Πριν δημιουργήσετε μια ροή, βεβαιωθείτε ότι η πηγή από την οποία σκοπεύετε να διαβάσετε είναι προσβάσιμη. Ένα ελλιπές αρχείο ή μη προσβάσιμο URL είναι η πιο συχνή αιτία σφαλμάτων άδειας.

```java
if (new File("YOUR_DOCUMENT_DIRECTORY/LicensePath.lic").exists()) {
    // Proceed to create an input stream
} else {
    System.out.println("License file does not exist. Please obtain a license from GroupDocs.");
}
```

> **Γιατί είναι σημαντικό** – Η έγκαιρη ανίχνευση μιας ελλιπούς πηγής αποτρέπει σφάλματα `LicenseException` κατά το χρόνο εκτέλεσης που μπορούν να διακόψουν την επεξεργασία εγγράφων.

## Δημιουργία της ροής εισόδου σωστά
`InputStream` είναι μια αφηρημένη κλάση της Java που αντιπροσωπεύει μια πηγή byte για ανάγνωση δεδομένων.

Μπορείτε να μετατρέψετε πολλές διαφορετικές πηγές σε ένα `InputStream`:

```java
InputStream stream = new FileInputStream(new File("YOUR_DOCUMENT_DIRECTORY/LicensePath.lic"));
try {
    // Initialize a License object
} finally {
    if (stream != null) {
        stream.close();
    }
}
```

**Κοινές εναλλακτικές**
- **Πόρος classpath** – `getClass().getResourceAsStream("/licenses/my-license.lic")`
- **Πίνακας byte** – `new ByteArrayInputStream(licenseBytes)`
- **Απομακρυσμένο URL** – `new URL("https://secure.mycompany.com/license").openStream()`

Κάθε ένα από αυτά επιστρέφει μια νέα ροή που μπορεί να περαστεί απευθείας στο αντικείμενο `License` της GroupDocs.

## Εφαρμογή της άδειας
`License` είναι η κλάση της GroupDocs που είναι υπεύθυνη για τη φόρτωση και την εφαρμογή μιας άδειας στο SDK.

```java
try {
    License license = new License();
    license.setLicense(stream);
} catch (Exception e) {
    System.out.println("Failed to set license: " + e.getMessage());
}
```

> **Σημαντικό** – Το `setLicense()` καταναλώνει ολόκληρη τη ροή, επομένως η ροή πρέπει να είναι στην αρχή κάθε φορά που την καλείτε. Η επαναχρήση της ίδιας εξαντλημένης ροής θα προκαλέσει σφάλμα «Το αρχείο άδειας είναι κενό».

## Διαχείριση πόρων (κρίσιμη!)
Μην αφήνετε ποτέ τις ροές να παραμένουν στη μνήμη. Σε υπηρεσίες που τρέχουν για μεγάλο χρονικό διάστημα, μια ανοιχτή ροή μπορεί να προκαλέσει ήπια πίεση μνήμης και τελικά να ενεργοποιήσει `OutOfMemoryError`.

```java
finally {
    if (stream != null) {
        try {
            stream.close();
        } catch (IOException e) {
            // Log the exception but don't let it mask other issues
            System.err.println("Warning: Failed to close license stream: " + e.getMessage());
        }
    }
}
```

## Δημιουργία του κεντρικού διαχειριστή άδειας
`LicenseManager` είναι μια προσαρμοσμένη βοηθητική κλάση που περιλαμβάνει τη φόρτωση και τον ορισμό της άδειας GroupDocs.

Η κλάση `LicenseManager` είναι μια ελαφριά περιτύλιξη που κεντράρει όλες τις λειτουργίες αδειοδότησης, εκθέτοντας μια μοναδική μέθοδο `initializeLicense()` για την εκκίνηση της εφαρμογής και μια μέθοδο `setLicense(InputStream stream)` για αλλαγές κατά το χρόνο εκτέλεσης.

```java
public class LicenseManager {
    private static volatile boolean licenseSet = false;
    
    public static synchronized void initializeLicense() {
        if (!licenseSet) {
            // Your stream‑based license setup here
            licenseSet = true;
        }
    }
}
```

> **Συμβουλή** – Καλέστε το `LicenseManager.initializeLicense()` μία φορά κατά την εκκίνηση της εφαρμογής (π.χ., σε `ServletContextListener`, Spring `@PostConstruct`, ή μέθοδο `main()`). Τα επόμενα στοιχεία μπορούν απλώς να βασίζονται στην ήδη ενεργή άδεια.

## Συνηθισμένα προβλήματα και λύσεις

### Πρόβλημα 1: «Το αρχείο άδειας δεν βρέθηκε»
**Αιτία** – Διαφορές στον τρέχοντα φάκελο μεταξύ IDE, CI και παραγωγικών containers.  
**Διόρθωση** – Προτιμήστε απόλυτες διαδρομές ή πόρους classpath, και καταγράψτε τη διαδρομή που επιλύθηκε για εντοπισμό σφαλμάτων.

```java
InputStream stream = getClass().getClassLoader().getResourceAsStream("licenses/license.lic");
```

### Πρόβλημα 2: Διαρροές μνήμης από ανοιχτές ροές
**Διόρθωση** – Χρησιμοποιήστε το try‑with‑resources της Java (διαθέσιμο από τη Java 7) για να εγγυηθείτε το κλείσιμο.

```java
try (InputStream stream = new FileInputStream(licenseFile)) {
    License license = new License();
    license.setLicense(stream);
} catch (Exception e) {
    // Handle licensing errors
}
```

### Πρόβλημα 3: Μη έγκυρη μορφή άδειας
**Διόρθωση** – Επαληθεύστε ότι το αρχείο είναι κωδικοποιημένο σε UTF‑8 και περιέχει την ακριβή δομή XML που παρέχεται από την GroupDocs. Όταν δημιουργείτε μια ροή από ένα `String`, τυλίξτε το με `new ByteArrayInputStream(str.getBytes(StandardCharsets.UTF_8))`.

```java
byte[] licenseBytes = licenseString.getBytes(StandardCharsets.UTF_8);
InputStream stream = new ByteArrayInputStream(licenseBytes);
```

## Καλές πρακτικές για παραγωγικές εφαρμογές
1. **Κεντράρετε όλο τον κώδικα αδειοδότησης** – κρατήστε τον σε μία κλάση `LicenseManager` για να αποφύγετε την επανάληψη.  
2. **Ρύθμιση ανά περιβάλλον** – χρησιμοποιήστε μεταβλητές περιβάλλοντος στην ανάπτυξη, ασφαλείς θησαυρούς στην παραγωγή, και μυστικά CI για αυτοματοποιημένες δοκιμές.  
3. **Καλό χειρισμό σφαλμάτων** – καταγράψτε αποτυχίες αδειοδότησης και προαιρετικά επιστρέψτε σε λειτουργία αξιολόγησης με σαφή προειδοποίηση προς τους τελικούς χρήστες.  
4. **Κρυφή μνήμη (cache) της άδειας** – μετά την πρώτη επιτυχή φόρτωση, αποθηκεύστε τον πίνακα byte στη μνήμη για να αποφύγετε επαναλαμβανόμενα I/O σε κάθε αίτημα.  

## Πραγματικά σενάρια υλοποίησης

### Σενάριο 1: Αρχιτεκτονική μικροϋπηρεσιών
```java
// Retrieve license from config service
String licenseData = configService.getLicense();
byte[] licenseBytes = Base64.getDecoder().decode(licenseData);
InputStream stream = new ByteArrayInputStream(licenseBytes);
```

Κάθε μικροϋπηρεσία φορτώνει την άδεια από ένα κοινόχρηστο κατάστημα μυστικών κατά τη φάση εκκίνησης, εξασφαλίζοντας συνεπή αδειοδότηση σε όλο το δίκτυο χωρίς εξαρτήσεις από το σύστημα αρχείων.

### Σενάριο 2: Εφαρμογές πολλαπλών ενοικιαστών
```java
public void setTenantLicense(String tenantId) {
    InputStream licenseStream = licenseRepository.getLicenseStream(tenantId);
    // Apply tenant‑specific license
}
```

Άδειες ειδικές για ενοικιαστή μπορούν να ανακτηθούν από πίνακα βάσης δεδομένων, να μετατραπούν σε ροή και να εφαρμοστούν άμεσα πριν την επεξεργασία εγγράφου για εκείνο τον ενοικιαστή.

### Σενάριο 3: Αυτόματοι αγωγοί δοκιμών
```java
@BeforeEach
void setupTestLicense() {
    InputStream testLicense = getClass().getResourceAsStream("/test-licenses/temp-license.lic");
    License license = new License();
    license.setLicense(testLicense);
}
```

Οι αγωγοί CI αντλούν την άδεια από μια κρυπτογραφημένη μεταβλητή περιβάλλοντος, την εφαρμόζουν μία φορά ανά εκτέλεση δοκιμής και στη συνέχεια απορρίπτουν το αντίγραφο στη μνήμη, διατηρώντας το περιβάλλον CI καθαρό.

## Παραμέτρους απόδοσης και βελτιστοποίηση
- **Κρύψτε (cache) την άδεια** μετά την πρώτη φόρτωση· οι επόμενες κλήσεις στο `setLicense()` μπορούν να χρησιμοποιήσουν ξανά τον κρυφό πίνακα byte, εξαλείφοντας την καθυστέρηση δίσκου ή δικτύου.  
- **Χρησιμοποιήστε buffered streams** (`BufferedInputStream`) όταν διαβάζετε μεγάλα αρχεία άδειας από απομακρυσμένα URLs για να μειώσετε το φόρτο I/O.  
- **Ορίστε την άδεια νωρίς** (π.χ., σε `static` initializer) ώστε η επεξεργασία εγγράφων να ξεκινά με έγκυρη άδεια, αποφεύγοντας το μικρό κόστος κατά το πρώτο αίτημα.

### Λογική επανάληψης για πηγές δικτύου
```java
int maxRetries = 3;
for (int i = 0; i < maxRetries; i++) {
    try {
        // Attempt license setup
        break;
    } catch (Exception e) {
        if (i == maxRetries - 1) throw e;
        Thread.sleep(1000 * (i + 1));
    }
}
```

Εφαρμόστε εκθετική καθυστέρηση (exponential back‑off) όταν αντλείτε την άδεια από απομακρυσμένο endpoint. Αυτό αποτρέπει προσωρινά σφάλματα δικτύου από το να καταρρεύσουν την υπηρεσία σας.

## Οδηγός αντιμετώπισης προβλημάτων

### Βήμα 1: Επαλήθευση ακεραιότητας αρχείου άδειας
```java
System.out.println("License file exists: " + licenseFile.exists());
System.out.println("License file size: " + licenseFile.length() + " bytes");
System.out.println("Can read file: " + licenseFile.canRead());
```

Ελέγξτε ότι το XML είναι σωστά δομημένο και ταιριάζει με την άδεια που αγοράσατε. Ένα κατεστραμμένο αρχείο θα προκαλέσει `LicenseException`.

### Βήμα 2: Εντοπισμός σφαλμάτων δημιουργίας ροής
```java
// Add logging to understand what's happening
System.out.println("License file exists: " + licenseFile.exists());
System.out.println("License file size: " + licenseFile.length() + " bytes");
System.out.println("Can read file: " + licenseFile.canRead());
```

Εκτυπώστε το μέγεθος του πίνακα byte (`licenseBytes.length`) πριν το περάσετε στο `setLicense()`· μέγεθος μηδέν υποδεικνύει κενή ροή.

### Βήμα 3: Δοκιμή εφαρμογής άδειας
```java
try {
    License license = new License();
    license.setLicense(stream);
    System.out.println("License applied successfully");
} catch (Exception e) {
    System.err.println("License application failed: " + e.getClass().getSimpleName() + " - " + e.getMessage());
    e.printStackTrace();
}
```

Εκτελέστε μια απλή εργασία σύγκρισης μετά τη φόρτωση της άδειας. Εάν η έξοδος περιέχει υδατογραφήματα, η άδεια δεν εφαρμόστηκε σωστά.

## Συχνές ερωτήσεις

**Ε: Μπορώ να χρησιμοποιήσω την ίδια ροή άδειας πολλές φορές;**  
Α: Όχι. Μόλις διαβαστεί μια ροή, εξαντλείται. Δημιουργήστε μια νέα ροή κάθε φορά ή αποθηκεύστε τον ακατέργαστο πίνακα byte και τυλίξτε τον σε νέο `ByteArrayInputStream`.

**Ε: Τι συμβαίνει αν δεν ορίσω άδεια;**  
Α: Η GroupDocs λειτουργεί σε λειτουργία αξιολόγησης, προσθέτοντας υδατογραφήματα και περιορίζοντας τον αριθμό των επεξεργασμένων σελίδων.

**Ε: Είναι η άδεια βασισμένη σε ροή πιο ασφαλής από την άδεια βασισμένη σε αρχείο;**  
Α: Ναι. Φορτώνοντας την άδεια απευθείας από τη μνήμη αποφεύγετε την ύπαρξη ενός αναγνώσιμου αρχείου στο δίσκο, μειώνοντας τον κίνδυνο τυχαίας έκθεσης.

**Ε: Μπορώ να αλλάξω άδειες κατά το χρόνο εκτέλεσης;**  
Α: Απόλυτα. Καλέστε `LicenseManager.setLicense(newStream)` όποτε χρειάζεται να αλλάξετε την ενεργή άδεια—π.χ., ανά ενοικιαστή ή ανά λειτουργία.

**Ε: Πώς διαχειρίζομαι την αδειοδότηση σε περιβάλλον σύμπλεξης (clustered);**  
Α: Κάθε κόμβος πρέπει να φορτώνει την άδεια ανεξάρτητα. Χρησιμοποιήστε μια κοινόχρηστη υπηρεσία ρυθμίσεων (Consul, Spring Cloud Config) ή μεταβλητές περιβάλλοντος ώστε κάθε παρουσία να λαμβάνει τα ίδια δεδομένα άδειας.

**Ε: Ποιος είναι ο αντίκτυπος στην απόδοση όταν χρησιμοποιούνται ροές;**  
Α: Αμελητέος. Η άδεια συνήθως ορίζεται μία φορά κατά την εκκίνηση· η ανάγνωση της ροής καταναλώνει μόνο λίγα kilobytes, πολύ λιγότερα από τα megabytes που επεξεργάζονται κατά τη σύγκριση εγγράφων.

## Συμπέρασμα
Τώρα έχετε έναν **κεντρικό διαχειριστή άδειας** βασισμένο σε ροές Java, που σας προσφέρει την ευελιξία, την ασφάλεια και την κλιμακωσιμότητα που απαιτούνται για σύγχρονες cloud‑native αναπτύξεις. Ακολουθώντας τα βήματα, τις καλές πρακτικές και τις συμβουλές αντιμετώπισης προβλημάτων σε αυτόν τον οδηγό, μπορείτε με σιγουριά να εφαρμόζετε την αδειοδότηση GroupDocs σε containers, μικροϋπηρεσίες και αρχιτεκτονικές πολλαπλών ενοικιαστών, χωρίς τα προβλήματα των διαδρομών αρχείων.

## Πρόσθετοι πόροι
- [Τεκμηρίωση GroupDocs.Comparison για Java](https://docs.groupdocs.com/comparison/java/)
- [Πλήρης οδηγός αναφοράς API](https://reference.groupdocs.com/comparison/java/)
- [Κυκλοφορίες GroupDocs](https://releases.groupdocs.com/comparison/java/)
- [Αγορά άδειας GroupDocs](https://purchase.groupdocs.com/buy)
- [Φόρουμ κοινότητας GroupDocs](https://forum.groupdocs.com/c/comparison)

**Τελευταία ενημέρωση:** 2026-10-15  
**Δοκιμή με:** GroupDocs.Comparison 25.2 (Java)  
**Συγγραφέας:** GroupDocs  

## Σχετικά μαθήματα
- [Οδηγός ρύθμισης αδειοδότησης GroupDocs.Comparison Java - Πλήρης διαμόρφωση](/comparison/java/licensing-configuration/)
- [Ρύθμιση άδειας GroupDocs Comparison Java - Πλήρης οδηγός διαμόρφωσης URL](/comparison/java/licensing-configuration/set-groupdocs-comparison-license-url-java/)
- [Πώς να χρησιμοποιήσετε το GroupDocs - Ροές σύγκρισης εγγράφων Java – Πλήρης οδηγός](/comparison/java/advanced-comparison/java-groupdocs-comparison-multi-stream-document-guide/)
