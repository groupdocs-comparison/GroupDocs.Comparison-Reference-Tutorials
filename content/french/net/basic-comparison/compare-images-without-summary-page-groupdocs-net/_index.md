---
categories:
- Image Processing
date: '2026-05-31'
description: Apprenez comment comparer des images en .NET en utilisant GroupDocs.Comparison
  tout en désactivant la page de résumé. Ce tutoriel couvre la configuration, le code,
  les conseils de performance et les cas d’utilisation réels.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Comparer des images .NET sans résumé
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
title: Comment comparer des images en .NET – Ignorer la page de résumé
type: docs
url: /fr/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Comment comparer des images dans .NET – Ignorer la page de résumé

Lorsque vous devez **comment comparer des images** programmaticalement dans une application .NET, la dernière chose que vous voulez est une page de résumé supplémentaire qui gaspille du temps et de l'espace de stockage. Que vous construisiez une ligne de contrôle qualité, un pipeline de gestion de contenu, ou une suite de tests de régression visuelle automatisée, ignorer la page de résumé peut économiser quelques secondes à chaque exécution et garder votre empreinte disque légère.

Dans ce tutoriel, vous apprendrez à utiliser **GroupDocs.Comparison for .NET** pour comparer deux images efficacement, configurer la bibliothèque afin de supprimer la génération du résumé, et appliquer des astuces de performance basées sur les meilleures pratiques. Nous explorerons également pourquoi cela importe, quand l'utiliser, et comment éviter les pièges courants.

## Réponses rapides
- **Quelle est la façon la plus rapide de comparer des images sans page de résumé ?** Utilisez `Comparer` avec `CompareOptions` et définissez `GenerateSummaryPage = false`.  
- **Quelle bibliothèque prend cela en charge immédiatement ?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **Ai-je besoin d'une licence ?** Oui, une licence commerciale est requise pour la production ; un essai gratuit fonctionne pour le développement.  
- **Puis-je comparer plus de deux images à la fois ?** Absolument – appelez `Add()` plusieurs fois avant `Compare()`.  
- **Cette approche convient‑elle aux traitements par lots à grande échelle ?** Oui, lorsqu'elle est combinée avec le traitement par lots et une gestion appropriée de la mémoire.

## Qu'est-ce que GroupDocs.Comparison ?
`GroupDocs.Comparison` est une bibliothèque .NET qui détecte les différences visuelles entre documents et images, produisant des résultats côte à côte ou en superposition. Elle prend en charge **plus de 50 formats d'entrée et de sortie**, y compris JPEG, PNG, BMP, TIFF et GIF, et peut traiter des fichiers de plusieurs centaines de pages sans charger le fichier complet en mémoire.

## Pourquoi ignorer la page de résumé ?
Désactiver la page de résumé réduit les entrées/sorties jusqu'à **70 %** pour les comparaisons d'images uniquement et diminue le temps de traitement d'environ **30 %** en moyenne, selon la suite de benchmarks de la bibliothèque. Lorsque vous n'avez besoin que de l'image de différence (pour les tests automatisés ou les décisions de validation QC), le rapport HTML supplémentaire n'apporte aucune valeur et ne consomme que de l'espace disque.

## Prérequis et configuration de l'environnement

### Ce dont vous aurez besoin
- **GroupDocs.Comparison for .NET** version **25.4.0** ou plus récente  
- Visual Studio 2019 + ou tout IDE compatible .NET  
- .NET Framework 4.6.1 + **ou** .NET Core 2.0 +  
- Connaissances de base en C# et familiarité avec les entrées/sorties de fichiers  

### Extras recommandés
- Un petit projet de test contenant une paire d'images d'exemple (par ex., `source.png` et `target.png`).  
- Optionnel : configuration d'injection de dépendances si vous préférez une architecture orientée services.  

### Pourquoi ces prérequis sont importants
La version de bibliothèque spécifiée inclut le drapeau `GenerateSummaryPage` et des améliorations de performance que les versions antérieures n'ont pas. Utiliser un IDE moderne vous permet de profiter de la gestion de paquets NuGet et de voir les avertissements de compilation tôt.

## Comment installer GroupDocs.Comparison
GroupDocs.Comparison peut être ajouté à n'importe quel projet .NET via NuGet, qui gère le téléchargement des binaires et la mise à jour du fichier de projet. Choisissez la méthode qui correspond à votre flux de travail : la console du gestionnaire de packages pour les utilisateurs de Visual Studio ou le CLI .NET pour les environnements en ligne de commande. Les deux commandes résolvent automatiquement les dépendances et garantissent que la bonne version est référencée.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Remplacez `25.4.0` par la version exacte que vous prévoyez de verrouiller.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```
Les deux commandes ajoutent la bibliothèque à votre fichier de projet et restaurent les binaires nécessaires.

**Astuce :** Épinglez la version dans votre `.csproj` pour éviter les mises à jour accidentelles qui pourraient modifier le comportement de l'API.

## Considérations de licence
GroupDocs.Comparison nécessite une licence pour tout déploiement en production. Vous pouvez commencer avec un **essai gratuit** qui offre toutes les fonctionnalités, puis passer à une **licence temporaire** pour des tests prolongés, et enfin à une **licence commerciale complète** pour la production. N'oubliez pas de placer le fichier `GroupDocs.Comparison.lic` à la racine de l'application ou de spécifier son chemin de façon programmatique.

## Configuration de projet de base
Créez une nouvelle application console (ou intégrez‑la à un service existant) et ajoutez le code de base suivant. Cet extrait montre la configuration minimale requise avant de plonger dans la logique de comparaison.

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

> **Important :** Utilisez toujours `Path.Combine()` pour les chemins de fichiers. Il gère automatiquement les séparateurs de chemin spécifiques au système d'exploitation et évite les bugs subtils lors du passage entre des conteneurs Windows et Linux.

## Guide d'implémentation étape par étape

### Comment comparer des images sans page de résumé ?
`Comparer` est la classe principale de GroupDocs.Comparison qui orchestre les opérations de comparaison de documents et d'images. `CompareOptions` contient les paramètres de configuration qui contrôlent la façon dont la comparaison est effectuée, comme la génération d'une page de résumé. Chargez l'image source, configurez `CompareOptions` pour désactiver le résumé, ajoutez l'image cible, et invoquez `Compare()`. La méthode renvoie un `ComparisonResult` contenant le flux de l'image de différence, que vous pouvez écrire sur le disque, envoyer sur un réseau, ou intégrer dans un composant UI. Cette approche garantit que seule la différence essentielle est produite, éliminant tout rapport HTML ou PDF supplémentaire.

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

Le code ci‑above effectue toute la comparaison en **quatre étapes logiques** et écrit uniquement l'image de différence, en laissant de côté tout résumé HTML ou PDF.

### Étape 1 : Initialiser l'objet Comparer
La classe `Comparer` est la porte d'entrée de toutes les opérations de comparaison. Elle implémente `IDisposable`, donc l'encapsuler dans un bloc `using` garantit que les handles de fichiers et la mémoire non gérée sont libérés rapidement, même si une exception est levée.

### Étape 2 : Configurer CompareOptions pour aucun résumé
Définissez `GenerateSummaryPage = false` sur l'instance `CompareOptions`. Ce drapeau indique au moteur de sauter la création du rapport HTML par défaut, qui est la principale source d'E/S supplémentaires dans les scénarios d'images uniquement.

### Étape 3 : Ajouter l'image(s) cible(s) pour la comparaison
Vous pouvez appeler `Add()` plusieurs fois pour comparer une source à plusieurs cibles dans un même lot. Chaque appel peut recevoir son propre `CompareOptions` si vous avez besoin de personnalisations par image.

### Étape 4 : Exécuter la comparaison et enregistrer les résultats
`Comparer.Compare()` effectue le travail lourd et renvoie un `ComparisonResult`. Le résultat contient un `Stream` avec l'image de différence, que vous pouvez enregistrer directement sur le disque, envoyer sur un réseau, ou intégrer dans un composant UI.

## Méthode prête pour la production complète
Ci‑dessous se trouve une méthode prête à l'emploi que vous pouvez intégrer à n'importe quel service .NET. Elle inclut la validation des chemins, la gestion des exceptions, et des points d'accroche de journalisation optionnels.

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

## Pièges courants d'implémentation (et comment les éviter)

- **Problèmes de chemin :** Vérifiez toujours que les fichiers source et cible existent avec `File.Exists()`. Un fichier manquant déclenchera une `FileNotFoundException` qui peut être interceptée tôt.  
- **Pression mémoire :** Les grandes images (10 Mo +) peuvent consommer beaucoup de RAM. Traitez‑les par lots et envisagez de réduire la résolution si une précision pixel‑par‑pixel n’est pas requise.  
- **Verrous de fichiers :** Assurez‑vous qu'aucun autre processus ne détient un verrou exclusif sur les fichiers image. Ceci est particulièrement important dans les environnements multi‑threadés ou conteneurisés.

## Applications pratiques et cas d'utilisation

### Contrôle qualité en fabrication
Une ligne de production capture des images de chaque article et les compare à une référence d'or. Ignorer la page de résumé permet au système de décider « pass » ou « fail » en quelques millisecondes, maintenant la ligne à grande vitesse.

### Systèmes de gestion de contenu
Lorsque les utilisateurs téléchargent des actifs, le CMS peut détecter instantanément les doublons ou quasi‑doublons, évitant le gonflement du stockage et améliorant la pertinence de la recherche. L'image de différence peut être stockée comme vignette pour une inspection visuelle rapide.

### Tests UI automatisés (régression visuelle)
Selenium ou Playwright peuvent capturer des captures d'écran d'une page web, puis les transmettre à cette routine de comparaison. L'image de différence met en évidence les changements UI, et comme aucun résumé n'est généré, le pipeline CI reste rapide et léger.

### Imagerie médicale (avec audit)
Les flux de travail en radiologie ont parfois besoin de signaler les changements entre des scans successifs. Bien que vous puissiez toujours générer un journal d'audit détaillé, l'image de différence elle‑même peut être produite sans page de résumé, réduisant le temps de traitement pour les gros PNG convertis depuis DICOM.

## Considérations de performance et optimisation

### Meilleures pratiques de gestion de la mémoire
Traitez les images en **lots de 20 à 50** selon la RAM du serveur. Libérez chaque instance `Comparer` rapidement et invoquez `GC.Collect()` uniquement si vous remarquez des pics de mémoire pendant des tâches de longue durée.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Optimisation des E/S disque
Placez vos répertoires d'entrée, de sortie et temporaires sur le même volume SSD rapide. Supprimez les fichiers temporaires immédiatement après l'enregistrement de l'image de différence pour éviter une utilisation disque inutile.

### Considérations de threading et asynchrones
GroupDocs.Comparison est thread‑safe pour les opérations en lecture seule, mais évitez de partager une même instance `Comparer` entre les threads. À la place, lancez des tâches indépendantes :

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Dépannage des problèmes courants

### Erreurs de chemin de fichier et de permission
- **Symptôme :** `FileNotFoundException` ou `UnauthorizedAccessException`.  
- **Solution :** Utilisez `Path.GetFullPath()` pour déboguer le chemin résolu, assurez‑vous que l'identité du pool d'applications (ou l'utilisateur du conteneur Docker) possède les droits de lecture/écriture, et revérifiez que le chemin n'est pas tronqué par les variables d'environnement.

### Goulots d'étranglement mémoire et performance
- **Symptôme :** Exécutions lentes ou `OutOfMemoryException`.  
- **Solution :** Redimensionnez les images à une résolution commune (par ex., 1024 × 768) lorsque la comparaison pixel‑par‑pixel exacte n’est pas requise. Surveillez la mémoire avec des outils comme dotMemory ou le Profilateur de performance intégré.

### Problèmes de licence
- **Symptôme :** Image de différence filigranée ou `LicenseException`.  
- **Solution :** Confirmez que `GroupDocs.Comparison.lic` se trouve dans le répertoire exécutable ou chargez‑le explicitement via `License license = new License(); license.SetLicense("path/to/license.file");`.

## Options de configuration avancées

### Personnalisation de la sensibilité de comparaison
Vous pouvez affiner la façon dont le moteur traite les petites variations de pixels (par ex., artefacts de compression) en ajustant la propriété `Sensitivity` sur `CompareOptions`. Des valeurs plus basses rendent la comparaison plus stricte.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Optimisation du format de sortie
Si vous avez besoin de l'image de différence dans un format spécifique (PNG vs. JPEG), définissez la propriété `OutputFormat` :

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

## Intégration avec les frameworks .NET populaires

### Exemple de service ASP.NET Core
Exposez un point de terminaison HTTP léger qui accepte deux flux d'images, exécute la comparaison, et renvoie l'image de différence sous forme de `FileResult`.

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

### Enregistrement d'injection de dépendances
Ajoutez le comparateur en tant que service scoped dans `Program.cs` ou `Startup.cs` :

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Questions fréquemment posées

**Q : Quelle est l'avantage principal d'ignorer la page de résumé ?**  
R : Elle réduit le temps de traitement jusqu'à 30 % et diminue l'utilisation du disque d'environ 70 % pour les comparaisons d'images uniquement, ce qui est crucial pour les pipelines à haut débit.

**Q : Puis‑je toujours récupérer les métadonnées détaillées des changements sans page de résumé ?**  
R : Oui. L'objet `ComparisonResult` expose une collection `Changes` qui contient des informations programmatiques sur chaque différence détectée.

**Q : Quels formats d'image sont pris en charge ?**  
R : JPEG, PNG, BMP, TIFF, GIF, et plusieurs autres — plus de 50 formats au total.

**Q : Comment gérer les très grandes images (par ex., >20 Mo) ?**  
R : Traitez‑les en plus petits lots, réduisez éventuellement leur taille, et surveillez l'utilisation de la mémoire. Utiliser `Comparer` dans un bloc `using` garantit que les ressources sont libérées rapidement.

**Q : Cette approche est‑elle sûre pour les applications multi‑threadées ?**  
R : Oui, tant que chaque thread crée sa propre instance `Comparer`. Partager une même instance peut entraîner des conditions de concurrence.

## Ressources supplémentaires
- [Documentation GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Référence API](https://reference.groupdocs.com/comparison/net/)
- [Téléchargement](https://releases.groupdocs.com/comparison/net/)
- [Achat](https://purchase.groupdocs.com/buy)
- [Essai gratuit](https://releases.groupdocs.com/comparison/net/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)
- [Forum d'assistance](https://forum.groupdocs.com/c/comparison/)

---

**Dernière mise à jour :** 2026-05-31  
**Testé avec :** GroupDocs.Comparison 25.4.0 for .NET  
**Auteur :** GroupDocs

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

## Tutoriels associés

- [Comparaison d'images .NET - Comparer des images programmatiquement](/comparison/net/image-comparison/compare-images-from-path/)
- [Comparaison d'images .NET - Comparer des images depuis un flux](/comparison/net/image-comparison/compare-images-from-stream/)
- [Tutoriel GroupDocs Comparison .NET - Guide complet d'utilisation de base](/comparison/net/basic-usage/)