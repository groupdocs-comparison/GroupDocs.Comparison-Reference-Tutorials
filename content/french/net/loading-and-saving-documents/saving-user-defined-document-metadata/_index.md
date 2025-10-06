---
"description": "Découvrez comment enregistrer les métadonnées de documents définies par l'utilisateur avec GroupDocs Comparison pour .NET. Comparez et manipulez facilement les métadonnées grâce à des instructions détaillées."
"linktitle": "Enregistrement des métadonnées de document définies par l'utilisateur dans la comparaison GroupDocs pour .NET"
"second_title": "API .NET GroupDocs.Comparison"
"title": "Enregistrement des métadonnées de document définies par l'utilisateur dans la comparaison GroupDocs pour .NET"
"url": "/fr/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
type: docs
---
# Enregistrement des métadonnées de document définies par l'utilisateur dans la comparaison GroupDocs pour .NET

## Introduction
Dans ce tutoriel, nous découvrirons comment enregistrer des métadonnées de documents personnalisées avec GroupDocs Comparison pour .NET. Les métadonnées sont essentielles pour organiser et gérer efficacement les documents. Avec GroupDocs Comparison, vous pouvez facilement comparer et manipuler les métadonnées pour répondre à vos besoins spécifiques.
## Prérequis
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. Comparaison GroupDocs pour .NET : téléchargez et installez Comparaison GroupDocs pour .NET à partir de [ici](https://releases.groupdocs.com/comparison/net/).
2. Environnement de développement : assurez-vous que vous disposez d’un environnement de développement approprié tel que Visual Studio installé sur votre système.
3. Documents source et cible : préparez les documents source et cible pour lesquels vous souhaitez comparer et manipuler les métadonnées.

## Importer des espaces de noms
Tout d’abord, importez les espaces de noms nécessaires pour accéder aux fonctionnalités fournies par GroupDocs Comparison pour .NET.
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
## Étape 2 : Initialiser le comparateur et ajouter des documents
Initialiser le `Comparer` objet avec le document source et ajouter le document cible pour comparaison.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Étape 3 : Spécifier les options de métadonnées
Spécifiez les options de métadonnées à enregistrer dans le document comparé. Dans cet exemple, nous définissons `CloneMetadataType` à `MetadataType.FileAuthor` et fournir des détails pour `FileAuthorMetadata`.
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
## Étape 4 : comparer les documents et enregistrer les métadonnées
Comparez les documents avec les options de métadonnées spécifiées et enregistrez le document comparé.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Étape 5 : Afficher le message de réussite
Affiche un message de réussite indiquant que les documents ont été comparés avec succès et l'emplacement de sortie.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusion
Dans ce tutoriel, nous avons appris à enregistrer des métadonnées de document définies par l'utilisateur à l'aide de GroupDocs Comparison pour .NET. En suivant ces étapes, vous pourrez comparer efficacement des documents tout en préservant et en manipulant les métadonnées selon vos besoins.
## FAQ
### GroupDocs Comparison pour .NET peut-il gérer différents formats de documents ?
Oui, GroupDocs Comparison prend en charge une large gamme de formats de documents, notamment DOCX, PDF, PPTX, XLSX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs Comparison pour .NET ?
Oui, vous pouvez accéder à l'essai gratuit [ici](https://releases.groupdocs.com/).
### Puis-je personnaliser les options de métadonnées en fonction de mes besoins ?
Absolument, GroupDocs Comparison fournit des options flexibles pour personnaliser la gestion des métadonnées lors de la comparaison de documents.
### GroupDocs Comparison offre-t-il un support technique ?
Oui, vous pouvez obtenir une assistance technique via le forum de comparaison GroupDocs [ici](https://forum.groupdocs.com/c/comparison/12).
### Où puis-je acheter une licence pour GroupDocs Comparison pour .NET ?
Vous pouvez acheter une licence sur le site Web GroupDocs [ici](https://purchase.groupdocs.com/buy).