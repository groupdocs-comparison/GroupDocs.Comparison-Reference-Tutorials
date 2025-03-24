---
title: Accepter et rejeter les modifications dans la comparaison GroupDocs pour .NET
linktitle: Accepter et rejeter les modifications dans la comparaison GroupDocs pour .NET
second_title: API GroupDocs.Comparison .NET
description: Découvrez comment accepter et rejeter les modifications apportées aux documents à l'aide de GroupDocs Comparison for .NET. Rationalisez vos flux de travail documentaires sans effort.
weight: 10
url: /fr/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---

# Accepter et rejeter les modifications dans la comparaison GroupDocs pour .NET

## Introduction
Dans le domaine de la gestion documentaire et de la collaboration, il est primordial de garantir l’exactitude et l’intégrité des fichiers. GroupDocs Comparison for .NET apparaît comme une solution robuste, permettant aux développeurs d'accepter et de rejeter sans effort les modifications apportées aux documents, rationalisant ainsi les flux de travail et améliorant la productivité. Ce didacticiel vous guidera tout au long du processus d'acceptation et de rejet des modifications à l'aide de GroupDocs Comparison for .NET, en décomposant chaque étape pour plus de clarté et de facilité de mise en œuvre.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous que les conditions préalables suivantes sont remplies :
### Configuration de l'environnement
1. Installez le SDK .NET : si vous ne l'avez pas déjà fait, téléchargez et installez le SDK .NET adapté à votre système d'exploitation à partir du site Web .NET.
2.  Installez GroupDocs Comparison for .NET : obtenez la dernière version de GroupDocs Comparison for .NET à partir du[lien de téléchargement](https://releases.groupdocs.com/comparison/net/) et suivez les instructions d'installation.
3. Familiarité avec la programmation C# : ce didacticiel suppose une compréhension de base du langage de programmation C# et de sa syntaxe.

## Importer des espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre projet. Ces espaces de noms donneront accès aux fonctionnalités requises pour la comparaison et la manipulation de documents.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Étape 1 : Spécifiez le répertoire de sortie et les noms de fichiers
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Assurez-vous de remplacer`"Your Document Directory"` avec le chemin d’accès au répertoire de sortie souhaité.
## Étape 2 : initialiser le comparateur et comparer les documents
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Ce code initialise l'objet Comparer avec le document source et ajoute le document cible pour comparaison. Ensuite, il exécute le processus de comparaison.
## Étape 3 : Récupérer et manipuler les modifications
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Récupérez les modifications de la comparaison et manipulez-les si nécessaire. Dans cet exemple, les modifications sont d'abord rejetées puis acceptées. Les documents résultants sont enregistrés en conséquence.

## Conclusion
En conclusion, GroupDocs Comparison for .NET offre une solution transparente pour accepter et rejeter les modifications dans les documents. En suivant les étapes décrites dans ce didacticiel, les développeurs peuvent intégrer efficacement cette fonctionnalité dans leurs applications, garantissant ainsi l'exactitude des documents et améliorant la collaboration.
## FAQ
### La comparaison GroupDocs pour .NET peut-elle comparer des documents de différents formats ?
Oui, GroupDocs Comparison for .NET prend en charge la comparaison entre des documents de différents formats tels que DOCX, PDF, PPTX, etc.
### La comparaison GroupDocs pour .NET est-elle compatible avec .NET Core ?
Oui, GroupDocs Comparison for .NET est compatible avec .NET Framework et .NET Core.
### Puis-je personnaliser l’apparence des modifications dans les documents comparés ?
Absolument, GroupDocs Comparison for .NET offre de nombreuses options pour personnaliser l'apparence des modifications, notamment la couleur, le style, etc.
### GroupDocs Comparison for .NET prend-il en charge la comparaison de documents multipages ?
Oui, GroupDocs Comparison for .NET prend en charge la comparaison de documents de plusieurs pages avec précision et exactitude.
### Existe-t-il une version d’essai disponible pour GroupDocs Comparison for .NET ?
 Oui, vous pouvez bénéficier d'un essai gratuit de GroupDocs Comparison for .NET à partir du[lien](https://releases.groupdocs.com/).