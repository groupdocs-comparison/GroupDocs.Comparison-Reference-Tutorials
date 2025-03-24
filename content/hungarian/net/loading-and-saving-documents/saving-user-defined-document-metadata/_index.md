---
title: Felhasználó által meghatározott dokumentum metaadatok mentése a GroupDocs-összehasonlításban .NET-hez
linktitle: Felhasználó által meghatározott dokumentum metaadatok mentése a GroupDocs-összehasonlításban .NET-hez
second_title: GroupDocs.Comparison .NET API
description: Ismerje meg, hogyan mentheti a felhasználó által definiált dokumentumok metaadatait a GroupDocs Comparison for .NET segítségével. Könnyen összehasonlíthatja és kezelheti a metaadatokat a lépésről lépésre történő utasításokkal.
weight: 16
url: /hu/net/loading-and-saving-documents/saving-user-defined-document-metadata/
---

# Felhasználó által meghatározott dokumentum metaadatok mentése a GroupDocs-összehasonlításban .NET-hez

## Bevezetés
Ebben az oktatóanyagban megvizsgáljuk, hogyan menthetők el a felhasználó által meghatározott dokumentumok metaadatai a GroupDocs Comparison for .NET segítségével. A metaadatok kulcsfontosságúak a dokumentumok hatékony rendszerezéséhez és kezeléséhez. A GroupDocs Comparison segítségével könnyedén összehasonlíthatja és manipulálhatja a metaadatokat, hogy megfeleljenek az Ön speciális követelményeinek.
## Előfeltételek
Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1.  GroupDocs Comparison for .NET: Töltse le és telepítse a GroupDocs Comparison for .NET alkalmazást innen[itt](https://releases.groupdocs.com/comparison/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy megfelelő fejlesztői környezet, például a Visual Studio telepítve van a rendszerére.
3. Forrás- és céldokumentumok: Készítse elő azokat a forrás- és céldokumentumokat, amelyek metaadatait össze szeretné hasonlítani és kezelni.

## Névterek importálása
Először is importálja a szükséges névtereket, hogy hozzáférjen a GroupDocs Comparison for .NET szolgáltatásaihoz.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## 1. lépés: Határozza meg a kimeneti könyvtárat és a fájl nevét
Határozza meg a könyvtárat, ahová az összehasonlított dokumentumot menteni szeretné, és adja meg a kimeneti fájl nevét.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## 2. lépés: Az Összehasonlító inicializálása és dokumentumok hozzáadása
 Inicializálja a`Comparer` objektumot a forrásdokumentummal, és összehasonlítás céljából adja hozzá a céldokumentumot.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## 3. lépés: Adja meg a metaadat-beállításokat
 Adja meg a metaadat-beállításokat a mentéshez az összehasonlított dokumentumban. Ebben a példában beállítjuk`CloneMetadataType` nak nek`MetadataType.FileAuthor` és adja meg a részleteket`FileAuthorMetadata`.
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
## 4. lépés: Hasonlítsa össze a dokumentumokat és mentse a metaadatokat
Hasonlítsa össze a dokumentumokat a megadott metaadat-beállításokkal, és mentse el az összehasonlított dokumentumot.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## 5. lépés: Jelenítse meg a sikeres üzenetet
Jelenítsen meg egy sikerüzenetet, amely jelzi, hogy a dokumentumok és a kimeneti hely sikeres összehasonlítása megtörtént.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Következtetés
Ebben az oktatóanyagban megtanultuk, hogyan mentheti el a felhasználó által meghatározott dokumentumok metaadatait a GroupDocs Comparison for .NET segítségével. Az alábbi lépések követésével hatékonyan összehasonlíthatja a dokumentumokat, miközben megőrzi és módosítja a metaadatokat az Ön igényei szerint.
## GYIK
### A GroupDocs Comparison for .NET kezelheti a különféle dokumentumformátumokat?
Igen, a GroupDocs Comparison a dokumentumformátumok széles skáláját támogatja, beleértve a DOCX, PDF, PPTX, XLSX és egyebeket.
### Elérhető ingyenes próbaverzió a GroupDocs Comparison for .NET számára?
 Igen, hozzáférhet az ingyenes próbaverzióhoz[itt](https://releases.groupdocs.com/).
### Testreszabhatom a metaadat-beállításokat az igényeim szerint?
Természetesen a GroupDocs Comparison rugalmas lehetőségeket kínál a metaadatkezelés testreszabásához a dokumentumok összehasonlítása során.
### A GroupDocs Comparison kínál technikai támogatást?
Igen, technikai támogatást kaphat a GroupDocs Comparison fórumon[itt](https://forum.groupdocs.com/c/comparison/12).
### Hol vásárolhatok licencet a GroupDocs Comparison for .NET-hez?
 Licenceket vásárolhat a GroupDocs webhelyéről[itt](https://purchase.groupdocs.com/buy).