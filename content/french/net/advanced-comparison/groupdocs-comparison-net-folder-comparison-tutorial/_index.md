---
categories:
- File Comparison
date: '2026-03-08'
description: Apprenez à comparer des dossiers dans .NET en utilisant GroupDocs.Comparison,
  générez un rapport HTML ou un journal TXT, et automatisez la gestion des fichiers
  avec des exemples pratiques en C#.
keywords: folder comparison .NET tutorial, GroupDocs comparison save TXT HTML, compare
  directories C# code, .NET file comparison library, automated directory comparison
lastmod: '2026-03-08'
linktitle: How to Compare Folders in .NET
tags:
- groupdocs
- folder-comparison
- dotnet
- csharp
- file-management
title: Comment comparer des dossiers dans .NET – Guide avec GroupDocs
type: docs
url: /fr/net/advanced-comparison/groupdocs-comparison-net-folder-comparison-tutorial/
weight: 1
---

# Comment comparer des dossiers en .NET – Guide avec GroupDocs

Vous êtes-vous déjà retrouvé à vérifier manuellement des centaines de fichiers pour repérer les différences entre deux répertoires ? **Dans ce tutoriel, vous apprendrez comment comparer des dossiers en .NET en utilisant GroupDocs.Comparison**. Que vous gériez des déploiements de code, validiez des sauvegardes ou suiviez les changements de configuration, la comparaison de dossiers en .NET peut vous faire gagner des heures de travail fastidieux.

**GroupDocs.Comparison for .NET** transforme ce point douloureux en un processus simple et automatisé. Vous pouvez comparer des structures de répertoires complètes, identifier les changements instantanément et exporter les résultats dans des formats adaptés à votre flux de travail (TXT pour les journaux, HTML pour les revues visuelles).

## Réponses rapides
- **Quel est le but principal ?** Automatiser la comparaison de dossiers et générer des rapports détaillés au format TXT ou HTML.  
- **Quels formats de sortie sont pris en charge ?** TXT pour un traitement facile et HTML pour générer un rapport visuel.  
- **Ai-je besoin d’une licence ?** Un essai gratuit suffit pour l’apprentissage ; une licence commerciale supprime les filigranes pour la production.  
- **Puis-je l’exécuter sous Linux ?** Oui – GroupDocs.Comparison prend en charge .NET Core sur Linux, macOS et Windows.  
- **Quelles versions de .NET sont compatibles ?** .NET Core 3.1+ et .NET 5/6/7/8.

## Pourquoi la comparaison de dossiers est importante pour les développeurs .NET

Vous êtes-vous déjà retrouvé à vérifier manuellement des centaines de fichiers pour repérer les différences entre deux répertoires ? Vous n’êtes pas seul. Que vous gériez des déploiements de code, validiez des sauvegardes ou suiviez les changements de configuration, **la comparaison de dossiers en .NET** peut vous faire gagner des heures de travail fastidieux.

**GroupDocs.Comparison for .NET** transforme ce point douloureux en un processus simple et automatisé. Vous pouvez comparer des structures de répertoires complètes, identifier les changements instantanément et exporter les résultats dans des formats adaptés à votre flux de travail (TXT pour les journaux, HTML pour les revues visuelles).

Dans ce tutoriel complet, vous découvrirez comment implémenter une fonctionnalité robuste de comparaison de dossiers qui gère tout, des vérifications simples de répertoires aux scénarios complexes de gestion de fichiers au niveau entreprise.

## Ce que vous apprendrez dans ce guide

À la fin de ce tutoriel, vous serez capable de mettre en œuvre en toute confiance des solutions de comparaison de dossiers qui :

- Comparer des répertoires de toute taille de manière efficace  
- Générer des rapports détaillés aux formats TXT et HTML (y compris comment **générer un rapport HTML**)  
- Gérer les cas limites et les considérations de performance  
- S’intégrer parfaitement à vos applications .NET existantes  
- Automatiser les tâches répétitives de gestion de fichiers  

Plongeons dans les prérequis et préparons votre succès !

## Prérequis et configuration de l’environnement

Avant de passer aux choses amusantes, assurons-nous que vous avez tout ce dont vous avez besoin. Pas d’inquiétude – la configuration est simple, et je vous guiderai à chaque étape.

### Ce dont vous avez besoin

**Bibliothèques requises et versions**  
- **GroupDocs.Comparison for .NET** : version 25.4.0 (la dernière version stable à partir de 2025)  
- **.NET Framework/SDK** : compatible avec .NET Core 3.1+ et .NET 5/6/7/8  
- **Environnement de développement** : Visual Studio 2019+ (l’édition Community fonctionne parfaitement)

**Prérequis de connaissances**  
- Compréhension de base de la programmation C# (si vous pouvez écrire une simple application console, vous êtes prêt)  
- Familiarité avec les opérations système de fichiers en .NET (travail avec les chemins, répertoires, fichiers)  
- Connaissance de la gestion des packages NuGet  

### Vérification rapide de l’environnement

Voici une façon simple de vérifier que votre configuration est prête :

1. Ouvrez votre IDE préféré (Visual Studio, VS Code ou JetBrains Rider)  
2. Créez une nouvelle application console ciblant .NET Core 3.1 ou une version ultérieure  
3. Assurez‑vous de pouvoir accéder au gestionnaire de packages NuGet  

Si vous pouvez faire ces trois choses, vous êtes prêt ! Passons maintenant à l’installation et à la configuration de GroupDocs.Comparison.

## Installation et configuration de GroupDocs.Comparison

Installer et faire fonctionner GroupDocs.Comparison dans votre projet est un jeu d’enfant. Vous avez deux méthodes d’installation principales, et je vais vous les présenter.

### Méthodes d’installation

**Option 1 : Console du gestionnaire de packages NuGet (recommandé pour les utilisateurs de Visual Studio)**
```shell
Install-Package GroupDocs.Comparison -Version 25.4.0
```

**Option 2 : .NET CLI (parfait pour les passionnés de ligne de commande)**
```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

Astuce : spécifiez toujours la version pour garantir la cohérence au sein de votre équipe et des environnements de déploiement.

### Comprendre les options de licence

GroupDocs.Comparison propose une licence flexible qui s’adapte à différents besoins :

- **Essai gratuit** : parfait pour l’évaluation – vous donne accès à toutes les fonctionnalités avec quelques limitations  
- **Licence temporaire** : idéale pour les projets de preuve de concept – supprime temporairement les restrictions de l’essai  
- **Licence commerciale** : toutes les fonctionnalités pour les applications de production  

À des fins d’apprentissage, l’essai gratuit est largement suffisant. Vous pouvez toujours passer à une version supérieure plus tard, lorsque vous serez prêt à déployer.

### Initialisation et configuration de base

Voici votre premier extrait de code GroupDocs.Comparison. Cette configuration simple vérifie que tout fonctionne correctement :
```csharp
using System;
using GroupDocs.Comparison;

class Program
{
    static void Main()
    {
        // Initialize the license if available
        License license = new License();
        // license.SetLicense("Path to your license file"); // Uncomment when you have a license

        Console.WriteLine("GroupDocs.Comparison for .NET is ready to use.");
        Console.WriteLine("Let's start comparing some folders!");
    }
}
```

Si ce code s’exécute sans erreur, félicitations ! Vous êtes prêt à commencer à créer une fonctionnalité puissante de comparaison de dossiers.

## Comment comparer des dossiers et enregistrer les résultats au format TXT

Commençons par l’approche la plus simple : comparer deux répertoires et enregistrer les résultats dans un fichier texte. Cette méthode est parfaite pour les scripts automatisés, les systèmes de journalisation ou lorsque vous avez besoin d’un format de sortie simple et analysable.

### Pourquoi choisir la sortie TXT ?

Les fichiers texte sont incroyablement polyvalents. Ils sont légers, faciles à analyser programmatiquement, compatibles avec le contrôle de version et peuvent être visualisés sur n’importe quel système. Idéal pour :

- Processus de construction automatisés  
- Analyse de fichiers journaux  
- Outils en ligne de commande  
- Intégration avec d’autres systèmes  

### Implémentation étape par étape

#### Étape 1 : Configurer vos options de comparaison
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;

string sourceFolder = "YOUR_DOCUMENT_DIRECTORY/SOURCE_FOLDER";
string targetFolder = "YOUR_DOCUMENT_DIRECTORY/TARGET_FOLDER";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Set comparison options for TXT output
Options.CompareOptions compareOptionsTxt = new Options.CompareOptions
{
    DirectoryCompare = true,
    FolderComparisonExtension = GroupDocs.Comparison.Options.FolderComparisonExtension.Txt
};
```

**Que se passe-t-il ici ?** Vous indiquez à GroupDocs.Comparison que vous souhaitez comparer des répertoires entiers (et non des fichiers individuels) et produire les résultats au format texte. Le paramètre `DirectoryCompare = true` est crucial — il active la fonctionnalité de comparaison récursive des répertoires.

#### Étape 2 : Initialiser l’objet Comparer
```csharp
Comparer comparerTxt = new Comparer(sourceFolder, compareOptionsTxt);
// Add target folder for comparison
comparerTxt.Add(targetFolder, compareOptionsTxt);
```

C’est ici que la magie commence. Vous créez une instance `Comparer` avec votre dossier source comme référence, puis ajoutez le dossier cible pour la comparaison. Pensez-y comme « comparer tout le contenu du dossier B avec le dossier A ».

#### Étape 3 : Exécuter la comparaison et enregistrer les résultats
```csharp
string txtOutputFileName = Path.Combine(outputDirectory, "ComparisonResult.txt");
comparerTxt.Compare(txtOutputFileName, compareOptionsTxt);

Console.WriteLine("TXT file with comparison results saved successfully.");
Console.WriteLine($"Check your results at: {txtOutputFileName}");
```

C’est tout ! Vos résultats de comparaison sont maintenant enregistrés dans un fichier texte. La sortie inclura les détails des fichiers ajoutés, supprimés et modifiés, facilitant la compréhension des changements entre les deux répertoires.

### Comprendre le format de sortie TXT

Le fichier texte généré comprend généralement :

- **Fichiers ajoutés** – présents dans la cible mais pas dans la source  
- **Fichiers supprimés** – présents dans la source mais pas dans la cible  
- **Fichiers modifiés** – existent dans les deux répertoires mais ont un contenu différent  
- **Métadonnées du fichier** – taille, dates de modification et autres informations pertinentes  

## Comment comparer des dossiers et enregistrer les résultats au format HTML

Bien que les fichiers TXT soient excellents pour l’automatisation, la sortie HTML brille lorsque vous avez besoin d’un rapport visuel lisible par l’homme. Les résultats de comparaison HTML sont parfaits pour les revues de code, les présentations aux clients ou lorsque vous souhaitez partager les résultats avec des membres d’équipe non techniques.

### Avantages de la sortie HTML (et comment **générer un rapport HTML**)

- **Mise en évidence visuelle des différences** – voyez exactement ce qui a changé grâce à un code couleur  
- **Navigation interactive** – cliquez facilement à travers les fichiers et dossiers  
- **Présentation professionnelle** – idéale pour les rapports et la documentation  
- **Affichage multiplateforme** – s’ouvre dans n’importe quel navigateur web  

### Implémentation HTML étape par étape

#### Étape 1 : Configurer les options de comparaison HTML
```csharp
// Set comparison options for HTML output
Options.CompareOptions compareOptionsHtml = new Options.CompareOptions
{
    DirectoryCompare = true,
    FolderComparisonExtension = GroupDocs.Comparison.Options.FolderComparisonExtension.Html
};
```

La différence clé ici est le paramètre `FolderComparisonExtension.Html`. Cela indique à GroupDocs.Comparison de générer un rapport HTML riche au lieu d’un texte brut.

#### Étape 2 : Initialiser le Comparer pour la sortie HTML
```csharp
Comparer comparerHtml = new Comparer(sourceFolder, compareOptionsHtml);
// Add target folder to the comparison
comparerHtml.Add(targetFolder, compareOptionsHtml);
```

Même schéma qu’auparavant, mais maintenant configuré pour la sortie HTML. La beauté de l’API de GroupDocs.Comparison réside dans sa cohérence — vous utilisez les mêmes méthodes quel que soit le format de sortie.

#### Étape 3 : Générer et enregistrer le rapport HTML
```csharp
string htmlOutputFileName = Path.Combine(outputDirectory, "ComparisonResult.html");
comparerHtml.Compare(htmlOutputFileName, compareOptionsHtml);

Console.WriteLine("HTML file with comparison results saved successfully.");
Console.WriteLine($"Open in browser: {htmlOutputFileName}");
```

Le fichier HTML que vous obtenez est un rapport complet et autonome que vous pouvez ouvrir dans n’importe quel navigateur web. Il comprend des éléments interactifs, la coloration syntaxique (pour les fichiers de code) et une mise en page propre et professionnelle.

### À quoi s’attendre dans votre rapport HTML

Votre sortie HTML comprendra généralement :

- **Tableau de bord récapitulatif** – aperçu du nombre total de changements, des fichiers affectés et des statistiques de comparaison  
- **Comparaisons côte à côte** – vue diff visuelle montrant exactement ce qui a changé  
- **Navigation arborescente des dossiers** – navigation facile à travers la structure des répertoires  
- **Détails au niveau du fichier** – comparaisons de fichiers individuels avec différences mises en évidence  

## Cas d’utilisation courants et applications réelles

Comprendre quand et comment utiliser la comparaison de dossiers peut améliorer considérablement votre flux de travail de développement. Voici quelques scénarios où cette fonctionnalité s’avère indispensable :

### Revue de code et contrôle de version

**Scénario** : Vous examinez les changements entre deux branches ou comparez différentes versions de votre base de code.  
**Pourquoi la comparaison de dossiers aide** : Au lieu de vérifier les fichiers un par un, vous pouvez voir instantanément toutes les modifications, ajouts et suppressions dans l’ensemble de la structure de votre projet. La sortie HTML est particulièrement utile ici – vous pouvez partager des rapports de diff visuels avec votre équipe.

### Vérification de sauvegarde de données

**Scénario** : Vous devez vérifier que votre processus de sauvegarde a correctement copié tous les fichiers et qu’aucune corruption ne s’est produite.  
**Astuce de mise en œuvre** : Utilisez la sortie TXT pour des scripts de vérification automatisés qui peuvent être intégrés à votre flux de sauvegarde. Configurez des alertes lorsqu’une divergence est détectée.

### Gestion de configuration entre environnements

**Scénario** : Vous gérez les configurations d’application entre les environnements de développement, de préproduction et de production.  
**Bonne pratique** : Des comparaisons de dossiers régulières permettent de détecter les dérives de configuration avant qu’elles ne provoquent des problèmes en production. Les rapports HTML sont parfaits pour la documentation de gestion des changements.

### Contrôle de version des documents

**Scénario** : Vous gérez des dépôts de documents où plusieurs membres de l’équipe modifient les fichiers.  
**Astuce pro** : Combinez la comparaison de dossiers avec des tâches planifiées pour générer automatiquement des rapports de changements. Cela est particulièrement utile pour la conformité et les audits.

### Intégration dans les pipelines CI/CD

**Scénario** : Vous souhaitez détecter et signaler automatiquement les changements dans le cadre de votre processus de déploiement.  
**Utilisation avancée** : Intégrez la comparaison de dossiers dans votre pipeline de construction pour générer des rapports de changements à chaque déploiement, facilitant les décisions de rollback et le suivi des changements.

## Optimisation des performances et meilleures pratiques

Lorsque vous travaillez avec de grandes structures de répertoires, les performances deviennent cruciales. Voici des stratégies éprouvées pour que vos comparaisons de dossiers fonctionnent sans accroc :

### Stratégies d’optimisation

1. **Sélection intelligente des répertoires**  
   - Comparez uniquement les répertoires que vous devez réellement analyser  
   - Utilisez des filtres pour exclure les fichiers temporaires, les journaux ou tout autre contenu non pertinent  
   - Envisagez de diviser les très grandes comparaisons en morceaux plus petits et ciblés  

2. **Gestion de la mémoire**  

```csharp
// Dispose of comparer objects properly
using (Comparer comparer = new Comparer(sourceFolder, compareOptions))
{
    comparer.Add(targetFolder, compareOptions);
    comparer.Compare(outputFileName, compareOptions);
} // Automatically disposed here
```

3. **Traitement asynchrone**  
   Pour les comparaisons volumineuses, envisagez de mettre en œuvre des modèles asynchrones afin d’éviter le blocage de l’interface utilisateur dans les applications de bureau ou les problèmes de délai d’attente dans les applications web.

### Conseils de surveillance des performances

- Surveillez l’utilisation de la mémoire pendant les grandes comparaisons  
- Suivez le temps de traitement pour différentes tailles de répertoires  
- Fixez des attentes réalistes pour les utilisateurs en fonction de la complexité des répertoires  
- Envisagez un rapport de progression pour les opérations de longue durée  

## Dépannage des problèmes courants

Même avec un code bien écrit, vous pouvez rencontrer des difficultés. Voici les problèmes les plus courants et leurs solutions :

### Problèmes d’accès aux fichiers et de permissions

**Problème** : erreurs « Accès refusé » ou « fichier en cours d’utilisation »  
**Solution** :  
- Assurez‑vous que votre application s’exécute avec les permissions appropriées  
- Vérifiez que les fichiers ne sont pas verrouillés par d’autres processus  
- Mettez en œuvre une logique de nouvelle tentative pour les verrous temporaires  

### Problèmes de chemin et de répertoire

**Problème** : erreurs de chemin invalide ou répertoire introuvable  

**Solution** :  

```csharp
// Always validate paths before comparison
if (!Directory.Exists(sourceFolder))
{
    throw new DirectoryNotFoundException($"Source directory not found: {sourceFolder}");
}

if (!Directory.Exists(targetFolder))
{
    throw new DirectoryNotFoundException($"Target directory not found: {targetFolder}");
}
```

### Problèmes de mémoire et de performance

**Problème** : exceptions de dépassement de mémoire ou performances lentes  
**Solutions** :  
- Divisez les grandes comparaisons en lots plus petits  
- Excluez les types de fichiers inutiles de la comparaison  
- Surveillez et optimisez les schémas d’utilisation de la mémoire  

### Problèmes de génération de fichiers de sortie

**Problème** : fichiers de sortie non générés ou corrompus  
**Étapes de dépannage** :  
- Vérifiez les permissions d’écriture dans le répertoire de sortie  
- Assurez‑vous qu’il y a suffisamment d’espace disque  
- Vérifiez la présence de caractères invalides dans les chemins de fichiers  
- Validez que le répertoire de sortie existe avant la comparaison  

## Options de configuration avancées

GroupDocs.Comparison propose de nombreuses options de configuration qui vous permettent d’ajuster finement le comportement de comparaison :

### Paramètres de sensibilité de comparaison

Vous pouvez ajuster la sensibilité de la comparaison aux différents types de changements :

- **Gestion des espaces** – ignorer ou inclure les changements d’espacement  
- **Sensibilité à la casse** – contrôler si les différences de casse sont considérées comme des changements  
- **Normalisation des fins de ligne** – gérer les différents formats de fins de ligne  

### Filtrage par type de fichier

Concentrez vos comparaisons sur des types de fichiers spécifiques :
```csharp
compareOptions.FileAuthorMetadata = false; // Ignore metadata changes
compareOptions.GenerateFramePreview = true; // Generate preview frames
```

### Formatage personnalisé de la sortie

Adaptez le format de sortie à vos besoins spécifiques :

- **Modèles personnalisés** – modifier le style de sortie HTML  
- **Inclusion de métadonnées** – contrôler quelles informations de fichier sont incluses  
- **Granularité du diff** – choisir entre des comparaisons au niveau du fichier ou de la ligne  

## Conclusion et prochaines étapes

Félicitations ! Vous avez maîtrisé les bases de la comparaison de dossiers avec GroupDocs.Comparison pour .NET. Vous avez maintenant les compétences pour :

- ✅ Installer et configurer GroupDocs.Comparison dans vos projets  
- ✅ Comparer des répertoires et générer des rapports TXT et HTML (y compris comment **générer un rapport HTML**)  
- ✅ Gérer les défis courants et optimiser les performances  
- ✅ Intégrer la comparaison de dossiers dans des applications réelles  

### Et après ?

Prêt à porter vos compétences en comparaison de dossiers au niveau supérieur ? Envisagez d’explorer :

- **Options de filtrage avancées** pour des comparaisons plus ciblées  
- **Intégration d’API** pour des services de comparaison basés sur le web  
- **Traitement par lots** pour gérer plusieurs paires de répertoires  
- **Formats de rapports personnalisés** adaptés aux besoins de votre organisation  

### Commencez à implémenter dès aujourd’hui

La meilleure façon de maîtriser ces concepts est la pratique. Choisissez l’un de vos projets actuels et identifiez où la comparaison de dossiers pourrait rationaliser votre flux de travail. Commencez petit, expérimentez différents formats de sortie et intégrez progressivement des fonctionnalités plus avancées.

Rappelez‑vous : chaque expert a été un débutant. Prenez votre temps, expérimentez librement, et n’hésitez pas à vous référer à ce guide chaque fois que vous avez besoin d’un rappel !

## Questions fréquemment posées

**Q : Puis‑je utiliser GroupDocs.Comparison pour .NET sur des systèmes Linux ?**  
R : Absolument ! GroupDocs.Comparison prend pleinement en charge le déploiement multiplateforme via .NET Core. Il fonctionne parfaitement sur Linux, macOS et Windows.

**Q : Comment gérer des répertoires très volumineux contenant des milliers de fichiers ?**  
R : Pour les grands répertoires, appliquez ces stratégies : utilisez le traitement asynchrone, divisez les comparaisons en lots plus petits, excluez les types de fichiers inutiles et surveillez l’utilisation de la mémoire. Envisagez de fournir un retour de progression aux utilisateurs pour les opérations de longue durée.

**Q : Existe‑t‑il une limite pratique au nombre de fichiers que je peux comparer ?**  
R : Bien qu’il n’y ait pas de limite stricte dans la bibliothèque, les performances dépendent des ressources de votre système (RAM, CPU, vitesse du disque) et de la taille des fichiers. La plupart des systèmes peuvent gérer des milliers de fichiers sans problème, mais des ensembles de données très volumineux peuvent nécessiter des stratégies d’optimisation.

**Q : GroupDocs.Comparison peut‑il gérer les fichiers chiffrés ou protégés par mot de passe ?**  
R : La bibliothèque ne peut pas comparer directement les fichiers chiffrés. Vous devez d’abord déchiffrer les fichiers si vous disposez des autorisations et des identifiants appropriés. Veillez toujours à respecter les politiques de sécurité de votre organisation lors du traitement de contenus chiffrés.

**Q : Comment intégrer la comparaison de dossiers dans des pipelines CI/CD automatisés ?**  
R : Créez des applications console qui utilisent GroupDocs.Comparison, configurez‑les pour renvoyer des codes de sortie appropriés en fonction des résultats de comparaison, et intégrez‑les à vos scripts de construction. La sortie TXT est particulièrement utile pour analyser les résultats dans des environnements automatisés.

**Q : Quelle est la différence entre les versions d’essai et les versions sous licence ?**  
R : La version d’essai comprend toutes les fonctionnalités mais ajoute des filigranes aux sorties et impose certaines limites d’utilisation. Les versions sous licence suppriment ces restrictions et conviennent à une utilisation en production.

**Q : Puis‑je personnaliser le style et la mise en page de la sortie HTML ?**  
R : Oui, GroupDocs.Comparison offre des options pour personnaliser la sortie HTML. Vous pouvez modifier les modèles, ajuster le style et contrôler les informations incluses dans les rapports.

**Q : Comment gérer les fichiers qui existent dans un répertoire mais pas dans l’autre ?**  
R : GroupDocs.Comparison identifie et signale automatiquement ces différences comme fichiers « ajoutés » ou « supprimés ». Vous pouvez configurer la façon dont ces différences sont présentées dans votre format de sortie.

## Ressources supplémentaires et support

### Documentation
- **Référence complète de l’API** : [Documentation de l’API GroupDocs.Comparison .NET](https://docs.groupdocs.com/comparison/net/)  
- **Guide du développeur** : [Ressources développeur GroupDocs](https://reference.groupdocs.com/comparison/net/)

### Téléchargement et licences
- **Dernière version** : [Télécharger GroupDocs.Comparison](https://releases.groupdocs.com/comparison/net/)  
- **Options d’achat** : [Acheter une licence commerciale](https://purchase.groupdocs.com/buy)  
- **Essai gratuit** : [Commencer votre essai gratuit](https://releases.groupdocs.com/comparison/net/)  
- **Licence temporaire** : [Demander une licence d’évaluation](https://purchase.groupdocs.com/temporary-license)

---

**Dernière mise à jour** : 2026-03-08  
**Testé avec** : GroupDocs.Comparison 25.4.0 for .NET  
**Auteur** : GroupDocs