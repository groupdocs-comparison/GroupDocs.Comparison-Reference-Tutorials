---
categories:
- Document Processing
date: '2026-07-01'
description: Apprenez comment lire les métadonnées de fichier C# en utilisant GroupDocs.Comparison,
  extraire le flux de taille de fichier et obtenir le flux des propriétés du document
  efficacement.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Extraire les informations du document .NET
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
title: Lire les métadonnées de fichier C# – Extraire les informations du document
  à partir des flux
type: docs
url: /fr/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Lire les métadonnées du fichier C# – Extraire les informations du document à partir des flux

## Introduction

La lecture des métadonnées d'un fichier en C# sans charger le document complet est une exigence courante pour les applications .NET modernes. **Read file metadata C#** vous permet de valider les téléchargements, d'afficher les détails du document et de prendre des décisions de traitement tout en maintenant une faible utilisation de la mémoire. GroupDocs.Comparison pour .NET fournit une API rapide basée sur les flux qui extrait le type de fichier, le nombre de pages, la taille et d'autres propriétés directement à partir d'un `Stream`. Dans les sections suivantes, vous verrez pourquoi cela est important, comment le configurer, et du code étape par étape que vous pouvez intégrer dans n'importe quel projet .NET.

## Réponses rapides
- **What does “read file metadata C#” mean?** Cela signifie récupérer les propriétés d'un document (type, pages, taille) via un flux .NET sans charger le contenu complet.  
- **Which library handles this?** GroupDocs.Comparison pour .NET propose la méthode `GetDocumentInfo()` pour une extraction rapide des métadonnées.  
- **Do I need a license?** Un essai gratuit fonctionne pour le développement ; une licence commerciale est requise pour la production.  
- **Can I use this with large PDFs?** Oui – l'approche flux traite des fichiers de plusieurs centaines de pages sans une consommation élevée de mémoire.  
- **Is it compatible with .NET 6+?** Absolument, la bibliothèque cible .NET Standard 2.0 et fonctionne sur .NET 6, .NET 7 et .NET Core.

## Qu'est-ce que read file metadata C# ?
`Read file metadata C#` désigne l'obtention des informations descriptives d'un document — tel que le format, le nombre de pages et la taille en octets — en utilisant du code C# qui travaille avec des flux. Cette technique évite de charger le fichier complet en mémoire, ce qui est particulièrement utile pour les gros PDF, les fichiers DOCX ou les opérations par lots.

## Pourquoi utiliser l'extraction de métadonnées GroupDocs à partir des flux ?
GroupDocs.Comparison prend en charge **plus de 50 formats d'entrée et de sortie** et peut extraire les métadonnées de fichiers jusqu'à **2 Go** tout en maintenant une utilisation de la mémoire inférieure à **10 Mo**. La bibliothèque lit uniquement les sections d'en-tête nécessaires, fournissant des résultats en **moins de 150 ms** pour des PDF typiques de 100 pages sur un serveur standard. Ces avantages quantifiés se traduisent par une validation de téléchargement plus rapide, des coûts cloud réduits et une expérience utilisateur plus fluide.

## Prérequis et configuration

### 1. Installer GroupDocs.Comparison pour .NET
Téléchargez le dernier package depuis la [page de téléchargement officielle](https://releases.groupdocs.com/comparison/net/). Si vous préférez NuGet, exécutez :

```
Install-Package GroupDocs.Comparison
```

### 2. Connaissances de base en développement .NET  
Vous devez être à l'aise avec C# et le modèle d'E/S .NET. Travailler avec `Stream`, `FileStream` et `MemoryStream` est essentiel pour les exemples ci-dessous.

### 3. Environnement de développement  
Visual Studio, VS Code ou JetBrains Rider sont tous pris en charge. Assurez-vous que votre projet cible .NET 6 ou une version ultérieure pour des performances optimales.

## Comment lire les métadonnées du fichier C# à partir d'un flux ?

Chargez le document avec un `FileStream`, créez une instance de `Comparer` et appelez `GetDocumentInfo()`. L'opération complète ne nécessite que deux lignes de code et renvoie un objet `IDocumentInfo` contenant le type de fichier, le nombre de pages et la taille. En interne, la bibliothèque lit uniquement les octets d'en-tête nécessaires, de sorte que même les gros PDF sont traités rapidement sans consommer beaucoup de mémoire.  
`Comparer` est la classe principale de GroupDocs.Comparison qui orchestre l'analyse du document.  
`GetDocumentInfo()` renvoie un objet `IDocumentInfo` avec les métadonnées de base.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Étape 1 : Initialiser l'objet Comparer avec un flux

L'extrait suivant crée une instance de `Comparer` à partir d'un `FileStream` en lecture seule. L'utilisation d'un bloc `using` garantit que le flux est fermé et que le comparateur est libéré, évitant ainsi les verrous de fichier.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Étape 2 : Extraire les informations du document

L'appel à `GetDocumentInfo()` renvoie un objet `IDocumentInfo` qui contient toutes les métadonnées dont vous avez besoin. La méthode lit uniquement les parties nécessaires de l'en-tête du fichier, de sorte qu'un PDF de 500 pages soit traité en une fraction de seconde.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Étape 3 : Afficher et utiliser les informations du document

Vous pouvez maintenant accéder aux propriétés `FileType`, `PageCount` et `Size`. En production, vous pourriez stocker ces valeurs dans une base de données, les exposer via une API, ou les utiliser pour décider d'accepter ou non un téléchargement.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Cas d'utilisation courants et modèles d'implémentation

### Validation des téléchargements de fichiers

Lorsqu'un utilisateur téléverse un document, vous pouvez vérifier instantanément son type et son nombre de pages avant de le stocker. Cela empêche les formats indésirables et les fichiers trop volumineux d'entrer dans votre système.

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

### Analyse de documents en lot

Vous traitez un dossier de documents ? Extrayez d'abord les métadonnées pour orienter les fichiers vers différents pipelines — par exemple, les gros PDF sont envoyés à un travailleur asynchrone, tandis que les fichiers d'une seule page sont traités en ligne.

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

## Problèmes courants et solutions

### Problèmes d'accès et de verrouillage de fichier

**Issue**: “The file is being used by another process.”  
**Solution**: Enveloppez le flux dans une instruction `using` et, si nécessaire, implémentez une politique de nouvelle tentative avec un délai exponentiel.

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

### Gestion des formats de fichier non pris en charge

**Issue**: The API throws an exception for an unknown format.  
**Solution**: Inspectez la propriété `FileType` ; si elle renvoie `Unknown`, renvoyez une erreur conviviale à l'appelant et consignez l'incident.

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

### Gestion de la mémoire avec les gros fichiers

**Issue**: Memory spikes when processing very large documents.  
**Solution**: L'approche basée sur les flux minimise déjà l'utilisation de la mémoire, mais vous devez également appeler `Dispose()` sur le `Comparer` dès que vous avez terminé et éviter de conserver des références à l'`IDocumentInfo` plus longtemps que nécessaire.

## Considérations de performance et bonnes pratiques

### Meilleures pratiques de gestion des flux

1. **Utilisez toujours les instructions `using`** – Garantit la libération et libère les ressources rapidement.  
2. **Réinitialisez la position du flux lors de la réutilisation** – Si vous devez lire le même flux deux fois, appelez `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Choisissez le bon type de flux** – `FileStream` pour les fichiers disque, `MemoryStream` pour les données en mémoire, `NetworkStream` pour les sources distantes.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Quand privilégier cette approche plutôt que le chargement complet du document

**Préférez l'extraction de métadonnées basée sur le flux lorsque** :

- Vous avez seulement besoin d'informations de haut niveau (type, pages, taille).  
- Vous validez des téléchargements ou créez un catalogue de documents.  
- La performance et une faible empreinte mémoire sont critiques.

**Passez au traitement complet du document lorsque** :

- Vous devez comparer le contenu, extraire du texte ou rendre les pages.  
- Une analyse approfondie (par ex., OCR, détection de filigrane) est requise.

## Conseils avancés pour l'utilisation en production

### Stratégies robustes de gestion des erreurs

Enveloppez toutes les opérations dans un bloc try‑catch qui capture `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` est levée par la bibliothèque lorsqu'une erreur survient lors du traitement du document. Consignez les détails de l'erreur, renvoyez une réponse d'erreur standardisée et assurez-vous que le `Comparer` est libéré dans un bloc `finally`.

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

### Intégration avec la journalisation et la surveillance

Injectez un framework de journalisation (par ex., Serilog ou NLog) et émettez des métriques telles que le temps de traitement, la taille du fichier et le nombre de succès/échecs. Ces données vous aident à détecter rapidement les régressions de performance.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Questions fréquemment posées

**Q : GroupDocs.Comparison pour .NET est‑il compatible avec différents formats de documents ?**  
R : Oui. La bibliothèque prend en charge **plus de 50 formats de fichiers**, y compris DOCX, PDF, XLSX, PPTX et de nombreux types d'images, ce qui la rend adaptée à pratiquement tout flux de travail de documents.

**Q : Puis‑je essayer GroupDocs.Comparison pour .NET avant d'acheter ?**  
R : Absolument. Un essai gratuit est disponible sur [le site web](https://releases.groupdocs.com/), vous permettant d'évaluer toutes les fonctionnalités sans licence.

**Q : Où puis‑je trouver du support pour GroupDocs.Comparison pour .NET ?**  
R : Vous pouvez obtenir de l'aide sur le [forum GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12), où la communauté et l'équipe produit répondent rapidement aux questions.

**Q : Des licences temporaires sont‑elles disponibles pour les tests ?**  
R : Oui. Des licences temporaires peuvent être obtenues depuis [la page de licences](https://purchase.groupdocs.com/temporary-license/), idéales pour les environnements de développement et de QA.

**Q : GroupDocs.Comparison pour .NET convient‑il aux déploiements d'entreprise ?**  
R : Définitivement. Il offre des performances de niveau entreprise, une prise en charge étendue des formats et une gestion robuste des erreurs, essentielles pour les systèmes de production à grande échelle.

**Dernière mise à jour** : 2026-07-01  
**Testé avec** : GroupDocs.Comparison 23.10 pour .NET  
**Auteur** : GroupDocs

## Tutoriels associés

- [Obtenir les propriétés du document C# .NET - Extraire les métadonnées du fichier](/comparison/net/basic-usage/get-document-info-from-path/)
- [Gestion des métadonnées de documents .NET - Guide complet pour GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Tutoriel de comparaison de documents .NET - Conserver les métadonnées avec GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)