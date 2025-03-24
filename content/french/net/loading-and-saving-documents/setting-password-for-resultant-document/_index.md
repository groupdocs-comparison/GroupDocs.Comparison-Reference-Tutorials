---
title: Définition du mot de passe pour le document résultant dans la comparaison GroupDocs pour .NET
linktitle: Définition du mot de passe pour le document résultant dans la comparaison GroupDocs pour .NET
second_title: API GroupDocs.Comparison .NET
description: Découvrez comment définir un mot de passe pour les documents résultants dans GroupDocs Comparison for .NET. Améliorez la sécurité et protégez vos fichiers comparés.
weight: 17
url: /fr/net/loading-and-saving-documents/setting-password-for-resultant-document/
---
## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus de définition d'un mot de passe pour le document résultant à l'aide de GroupDocs Comparison for .NET. Cette fonctionnalité ajoute une couche de sécurité supplémentaire à vos documents comparés, garantissant que seules les personnes autorisées peuvent y accéder.
## Conditions préalables
Avant de continuer, assurez-vous d'avoir les éléments suivants :
1.  Comparaison GroupDocs pour .NET : assurez-vous que la bibliothèque de comparaison GroupDocs est installée dans votre environnement .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/comparison/net/).
2. Documents source et cible : préparer le document source (`SOURCE.docx`) et le document cible (`TARGET.docx`) que vous souhaitez comparer et définissez un mot de passe pour le document résultant.

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C# pour utiliser la fonctionnalité de comparaison GroupDocs :
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Étape 1 : Définir le répertoire de sortie et le nom du fichier
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
Spécifiez le répertoire dans lequel vous souhaitez enregistrer le document résultant et définissez le nom du fichier de sortie.
## Étape 2 : comparer les documents avec les paramètres de mot de passe
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    CompareOptions cOptions = new CompareOptions
    {
        PasswordSaveOption = PasswordSaveOption.User
    };
    SaveOptions sOptions = new SaveOptions()
    {
        Password = "YourPasswordHere"
    };
    comparer.Compare(outputFileName, sOptions, cOptions);
}
```
 Ici, nous initialisons un`Comparer` objet avec le document source. Ensuite, nous ajoutons le document cible à comparer. Nous fixons le`PasswordSaveOption` à`User` pour spécifier qu'un mot de passe sera appliqué au document résultant. Fournissez le mot de passe souhaité dans le`Password` propriété du`SaveOptions` objet.
## Étape 3 : Afficher le message de réussite
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```
Enfin, nous affichons un message de réussite indiquant que les documents ont été comparés avec succès et que le document résultant avec le mot de passe défini a été enregistré dans le répertoire spécifié.

## Conclusion
La définition d'un mot de passe pour le document résultant dans GroupDocs Comparison for .NET ajoute une couche de sécurité supplémentaire à vos documents comparés, garantissant ainsi la confidentialité et l'intégrité. En suivant les étapes décrites dans ce didacticiel, vous pouvez facilement implémenter cette fonctionnalité dans vos applications .NET.
## FAQ
### Puis-je comparer des documents dans différents formats ?
Oui, GroupDocs Comparison for .NET prend en charge la comparaison de documents dans différents formats tels que DOCX, PDF, PPTX, XLSX, etc.
### Existe-t-il une version d'essai disponible ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir de[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide si je rencontre des problèmes ?
 Vous pouvez demander de l'aide sur le forum de la communauté GroupDocs Comparison.[ici](https://forum.groupdocs.com/c/comparison/12).
### Ai-je besoin d’une licence pour utiliser GroupDocs Comparison for .NET ?
 Oui, vous pouvez acheter une licence auprès de[ici](https://purchase.groupdocs.com/buy) ou obtenir un permis temporaire[ici](https://purchase.groupdocs.com/temporary-license/).
### Existe-t-il une documentation disponible pour la comparaison GroupDocs pour .NET ?
 Oui, vous pouvez accéder à la documentation[ici](https://tutorials.groupdocs.com/comparison/net/).