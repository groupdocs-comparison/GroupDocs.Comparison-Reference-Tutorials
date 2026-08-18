---
categories:
- Document Comparison
date: '2026-06-15'
description: Apprenez comment extraire les métadonnées des résultats de comparaison
  .NET en utilisant GroupDocs.Comparison. Guide étape par étape avec des exemples
  de code et des conseils pratiques.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Extraire les informations du document à partir des résultats de comparaison
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
title: Comment extraire les métadonnées des résultats de comparaison .NET – Guide
  complet
type: docs
url: /fr/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Comment extraire les métadonnées des résultats de comparaison .NET – Guide complet

Lorsque vous travaillez avec des comparaisons de documents dans des applications .NET, vous vous demandez peut‑être **comment extraire les métadonnées** des résultats de comparaison. Les métadonnées telles que le type de fichier, le nombre de pages et la taille du document peuvent être essentielles pour les pistes d’audit, l’optimisation des performances, ou simplement afficher des informations utiles aux utilisateurs finaux. Ce tutoriel vous guide pour récupérer ces données efficacement avec GroupDocs.Comparison pour .NET.

## Réponses rapides
- **Quelle est la classe principale pour la comparaison ?** `Comparer` charge le document source et exécute le moteur de comparaison.  
- **Quelle méthode renvoie les métadonnées ?** `GetDocumentInfo()` sur un document cible renvoie un objet `IDocumentInfo`.  
- **Puis‑je obtenir la taille du document en .NET ?** Oui – la propriété `Size` de `IDocumentInfo` renvoie la taille en octets.  
- **Ai‑je besoin d’une licence pour l’extraction des métadonnées ?** Une licence valide de GroupDocs.Comparison est requise pour une utilisation en production ; l’essai gratuit prend en charge toutes les fonctionnalités de métadonnées.  
- **L’API est‑elle compatible avec .NET 6 ?** Absolument – GroupDocs.Comparison prend en charge .NET Framework 4.6.1+, .NET Core 2.0+, et .NET 5/6+.

La méthode `GetDocumentInfo()` renvoie un objet `IDocumentInfo` contenant les métadonnées du document.

## Qu’est‑ce que l’extraction de métadonnées dans la comparaison de documents ?
L’extraction de métadonnées est le processus de récupération d’informations descriptives — telles que le type de fichier, le nombre de pages et la taille du fichier — à partir des documents impliqués dans une opération de comparaison. GroupDocs.Comparison expose ces données via une API unifiée, facilitant leur journalisation, affichage ou utilisation pour un traitement conditionnel.

## Pourquoi extraire les métadonnées des résultats de comparaison ?
L’extraction des métadonnées vous permet de créer des journaux d’audit détaillés, de router les fichiers en fonction de leur type et d’ajuster les stratégies de traitement pour les gros documents. En connaissant le type de fichier, le nombre de pages et la taille, vous pouvez appliquer des règles de conformité, estimer le temps de traitement et présenter des informations claires aux utilisateurs avant qu’ils ne lancent une comparaison.

## Prérequis
1. **GroupDocs.Comparison for .NET** – Installez la bibliothèque depuis la [page officielle des releases](https://releases.groupdocs.com/comparison/net/).  
   Vous pouvez également parcourir toutes les releases sur la [page des releases GroupDocs](https://releases.groupdocs.com/).  
2. **Environnement de développement** – Visual Studio, VS Code, ou tout IDE supportant .NET 6+.  
3. **Documents d’exemple** – Deux fichiers (par ex., `SOURCE.docx` et `TARGET.docx`) pour les tests. L’API fonctionne avec plus de **50 formats de documents**.

## Importer les espaces de noms
Les directives `using` suivantes vous donnent accès au moteur de comparaison principal, aux utilitaires de gestion de fichiers et aux interfaces de métadonnées.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Ces importations sont requises avant d’instancier tout objet GroupDocs.

## Comment extraire les métadonnées des résultats de comparaison ?
La classe `Comparer` charge le document source et orchestre le processus de comparaison.

Pour récupérer les métadonnées, chargez d’abord le document source avec une instance de `Comparer`, puis ajoutez le(s) document(s) cible(s). Une fois le moteur de comparaison initialisé, appelez `GetDocumentInfo()` sur chaque cible pour obtenir un objet `IDocumentInfo` contenant des propriétés telles que le type de fichier, le nombre de pages et la taille. Cette approche fonctionne de manière uniforme sur tous les formats pris en charge.

### Étape 1 : Initialiser le Comparer avec le document source
`Comparer` est la classe principale de GroupDocs.Comparison qui charge le document source et orchestre les opérations de comparaison. Utiliser un bloc `using` garantit que toutes les ressources non gérées sont libérées automatiquement.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Astuce :** Vous pouvez passer n’importe quel `Stream` (fichier, mémoire, cloud) au constructeur `Comparer`, pas seulement un chemin de fichier.

### Étape 2 : Ajouter le document cible pour la comparaison
La méthode `Add()` accepte des flux supplémentaires ou des chemins de fichier, permettant des comparaisons un‑à‑plusieurs.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Important :** L’ordre des documents ajoutés influence la façon dont les modifications sont mises en évidence dans le rapport final.

### Étape 3 : Récupérer les informations du document à partir du document résultat
`IDocumentInfo` fournit une vue unifiée des métadonnées du document telles que le type de fichier, le nombre de pages et la taille, pour tous les formats pris en charge.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Comprendre les données :** L’objet retourné fonctionne de la même manière pour DOCX, PDF, XLSX et PPTX, vous permettant d’écrire du code indépendant du format.

### Étape 4 : Afficher les informations du document
Une fois que vous avez l’instance `IDocumentInfo`, vous pouvez journaliser, stocker ou présenter ses propriétés.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Les trois propriétés les plus couramment utilisées sont :
- **FileType** – par ex., `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – nombre total de pages ou de diapositives.  
- **Size** – taille du fichier en octets (utile pour les calculs de stockage).

## Comment obtenir la taille du document en .NET ?
La propriété `Size` renvoie la taille du fichier en octets.

La taille du document peut être accédée directement depuis l’instance `IDocumentInfo` via sa propriété `Size`. Cette propriété renvoie le nombre exact d’octets du fichier original, vous permettant de le convertir en kilooctets ou mégaoctets pour l’affichage ou les calculs de stockage. Elle reflète la taille du fichier source, pas celle d’une version traitée.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Remarque :** La valeur `Size` reflète la taille du fichier original, pas la taille après un traitement ou une compression interne.

## Cas d’utilisation courants et applications pratiques
- **Traitement par lots :** Utilisez le type de fichier pour router les fichiers DOCX vers un flux de travail spécifique à Word et les PDF vers un pipeline optimisé pour les PDF.  
- **Gestion du stockage :** Archivez automatiquement les documents de plus de 10 Mo dans un bucket de stockage à froid.  
- **Retour utilisateur :** Affichez le nombre de pages et la taille avant la comparaison pour définir des attentes réalistes concernant le temps de traitement.  
- **Assurance qualité :** Vérifiez que les fichiers téléchargés sont complets en comparant le nombre de pages attendu et réel.

## Résolution des problèmes courants
- **Erreurs d’accès aux fichiers :** Vérifiez les permissions de lecture et utilisez des chemins absolus pendant le développement.  
- **Pression mémoire avec les gros fichiers :** Privilégiez le streaming (`File.OpenRead`) plutôt que de charger le fichier entier en mémoire.  
- **Exceptions de référence nulle :** `FirstOrDefault()` peut renvoyer `null` si aucune cible n’a été ajoutée ; vérifiez toujours avant d’accéder à `GetDocumentInfo()`.  

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

- **Métadonnées limitées pour le texte brut :** Les formats comme `.txt` peuvent ne pas exposer de `PageCount` significatif. Protégez-vous contre les valeurs manquantes.

## Considérations de performance
- **Gestion des flux :** Enveloppez toujours les flux dans des instructions `using` pour libérer rapidement les poignées de fichiers.  
- **Mise en cache :** Stockez les métadonnées fréquemment accédées dans un cache pour éviter les extractions répétées.  
- **Opérations par lots :** Traitez les documents par groupes pour réduire la surcharge et améliorer le débit.

## Bonnes pratiques pour la production
- **Gestion robuste des erreurs :** Encapsulez l’extraction des métadonnées dans des blocs try‑catch pour gérer gracieusement les fichiers corrompus ou non pris en charge.  
- **Journalisation complète :** Enregistrez le type de document, la taille et le nombre de pages pour chaque comparaison afin d’aider au dépannage et à la conformité d’audit.  
- **Hygiène de sécurité :** Évitez d’exposer les chemins de fichiers complets ou les détails internes du serveur dans les messages UI.  
- **Libération des ressources :** Libérez rapidement les instances de `Comparer`, surtout dans les services web gérant de nombreuses requêtes concurrentes.

## Scénarios avancés
### Documents cibles multiples
Si vous comparez une source à plusieurs cibles, parcourez la collection `Targets` et extrayez les métadonnées de chacune.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Traitement conditionnel basé sur les métadonnées
```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Stocker les métadonnées dans une base de données
Persistez `FileType`, `PageCount` et `Size` dans une table relationnelle pour permettre le reporting et l’analyse sur des milliers de comparaisons.

## Questions fréquemment posées
**Q : GroupDocs.Comparison pour .NET est‑il compatible avec divers formats de documents ?**  
R : Oui, il prend en charge **plus de 50 formats** dont DOCX, PDF, PPTX, XLSX, TXT et bien d’autres, offrant une extraction de métadonnées cohérente pour chacun.

**Q : Puis‑je personnaliser les paramètres de comparaison sans affecter l’extraction des métadonnées ?**  
R : Absolument. Des paramètres comme la sensibilité, les types de modifications et le format de sortie sont indépendants de l’appel `GetDocumentInfo()`.

**Q : Existe‑t‑il une version d’essai que je puisse utiliser pour évaluer ?**  
R : Oui, téléchargez une version d’essai gratuite depuis la [page des releases GroupDocs](https://releases.groupdocs.com/). L’essai inclut toutes les capacités d’extraction de métadonnées.

**Q : Où puis‑je obtenir de l’aide pour les questions d’implémentation ?**  
R : Utilisez le [forum GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) pour l’aide de la communauté et le support officiel de l’équipe GroupDocs.

**Q : Quelles options de licence sont disponibles pour les déploiements en production ?**  
R : GroupDocs propose des licences développeur, site et OEM. Les options d’achat sont répertoriées sur la [page d’achat GroupDocs](https://purchase.groupdocs.com/buy).

---

**Dernière mise à jour :** 2026-06-15  
**Testé avec :** GroupDocs.Comparison 6.0 for .NET  
**Auteur :** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Tutoriels associés
- [Gestion des métadonnées de documents .NET – Guide complet pour GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Obtenir les propriétés du document C# .NET – Extraire les métadonnées du fichier](/comparison/net/basic-usage/get-document-info-from-path/)
- [Conserver les métadonnées cibles avec GroupDocs.Comparison – Tutoriel .NET](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)