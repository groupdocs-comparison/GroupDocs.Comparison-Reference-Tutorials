---
title: Enregistrement des métadonnées de document définies par l'utilisateur dans la comparaison GroupDocs pour .NET
linktitle: Enregistrement des métadonnées de document définies par l'utilisateur dans la comparaison GroupDocs pour .NET
second_title: API GroupDocs.Comparison .NET
description: Découvrez comment enregistrer les métadonnées de documents définies par l'utilisateur à l'aide de GroupDocs Comparison for .NET. Comparez et manipulez facilement les métadonnées grâce à des instructions étape par étape.
type: docs
weight: 16
url: /fr/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---
## Introduction
Dans ce didacticiel, nous explorerons comment enregistrer les métadonnées de documents définies par l'utilisateur à l'aide de GroupDocs Comparison for .NET. Les métadonnées sont cruciales pour organiser et gérer efficacement les documents. Avec GroupDocs Comparison, vous pouvez facilement comparer et manipuler les métadonnées pour répondre à vos besoins spécifiques.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1.  Comparaison GroupDocs pour .NET : téléchargez et installez la comparaison GroupDocs pour .NET à partir de[ici](https://releases.groupdocs.com/comparison/net/).
2. Environnement de développement : assurez-vous d'avoir un environnement de développement approprié tel que Visual Studio installé sur votre système.
3. Documents source et cible : préparez les documents source et cible pour lesquels vous souhaitez comparer et manipuler les métadonnées.

## Importer des espaces de noms
Tout d’abord, importez les espaces de noms nécessaires pour accéder aux fonctionnalités fournies par GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Étape 1 : Définir le répertoire de sortie et le nom du fichier
Définissez le répertoire dans lequel vous souhaitez enregistrer le document comparé et spécifiez le nom du fichier de sortie.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Étape 2 : initialiser le comparateur et ajouter des documents
 Initialisez le`Comparer` objet avec le document source et ajoutez le document cible pour comparaison.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Étape 3 : Spécifier les options de métadonnées
 Spécifiez les options de métadonnées à enregistrer dans le document comparé. Dans cet exemple, nous définissons`CloneMetadataType` à`MetadataType.FileAuthor` et fournir des détails sur`FileAuthorMetadata`.
```csharp
SaveOptions saveOptions = new SaveOptions()
{
    CloneMetadataType = MetadataType.FileAuthor,
    FileAuthorMetadata = new FileAuthorMetadata
    {
        Author = "Tom",
        Company = "GroupDocs",
        LastSaveBy = "Jack"
    }
};
```
## Étape 4 : Comparez les documents et enregistrez les métadonnées
Comparez les documents avec les options de métadonnées spécifiées et enregistrez le document comparé.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Étape 5 : Afficher le message de réussite
Afficher un message de réussite indiquant que les documents ont été comparés avec succès et l'emplacement de sortie.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusion
Dans ce didacticiel, nous avons appris à enregistrer les métadonnées de documents définies par l'utilisateur à l'aide de GroupDocs Comparison for .NET. En suivant ces étapes, vous pouvez comparer efficacement les documents tout en préservant et en manipulant les métadonnées selon vos besoins.
## FAQ
### GroupDocs Comparison for .NET peut-il gérer différents formats de documents ?
Oui, GroupDocs Comparison prend en charge un large éventail de formats de documents, notamment DOCX, PDF, PPTX, XLSX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs Comparison for .NET ?
 Oui, vous pouvez accéder à l'essai gratuit[ici](https://releases.groupdocs.com/).
### Puis-je personnaliser les options de métadonnées en fonction de mes besoins ?
Absolument, GroupDocs Comparison fournit des options flexibles pour personnaliser la gestion des métadonnées lors de la comparaison de documents.
### GroupDocs Comparison offre-t-il une assistance technique ?
Oui, vous pouvez obtenir une assistance technique sur le forum de comparaison GroupDocs[ici](https://forum.groupdocs.com/c/comparison/12).
### Où puis-je acheter une licence pour GroupDocs Comparison for .NET ?
 Vous pouvez acheter une licence sur le site Web GroupDocs[ici](https://purchase.groupdocs.com/buy).