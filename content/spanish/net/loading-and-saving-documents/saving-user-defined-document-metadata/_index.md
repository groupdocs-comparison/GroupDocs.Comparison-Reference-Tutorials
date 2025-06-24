---
"description": "Aprenda a guardar metadatos de documentos definidos por el usuario con GroupDocs Comparison para .NET. Compare y manipule metadatos fácilmente con instrucciones paso a paso."
"linktitle": "Comparación de cómo guardar metadatos de documentos definidos por el usuario en GroupDocs para .NET"
"second_title": "API .NET de GroupDocs.Comparison"
"title": "Comparación de cómo guardar metadatos de documentos definidos por el usuario en GroupDocs para .NET"
"url": "/es/net/loading-and-saving-documents/saving-user-defined-document-metadata/"
"weight": 16
---

# Comparación de cómo guardar metadatos de documentos definidos por el usuario en GroupDocs para .NET

## Introducción
En este tutorial, exploraremos cómo guardar metadatos de documentos definidos por el usuario con GroupDocs Comparison para .NET. Los metadatos son cruciales para organizar y gestionar documentos de forma eficiente. Con GroupDocs Comparison, puede comparar y manipular metadatos fácilmente para satisfacer sus necesidades específicas.
## Prerrequisitos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Comparación de GroupDocs para .NET: Descargue e instale la Comparación de GroupDocs para .NET desde [aquí](https://releases.groupdocs.com/comparison/net/).
2. Entorno de desarrollo: asegúrese de tener un entorno de desarrollo adecuado, como Visual Studio, instalado en su sistema.
3. Documentos de origen y destino: prepare los documentos de origen y destino que desea comparar y manipular metadatos.

## Importar espacios de nombres
Primero, importe los espacios de nombres necesarios para acceder a las funcionalidades proporcionadas por GroupDocs Comparison for .NET.
```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Options;
```
## Paso 1: Definir el directorio de salida y el nombre del archivo
Defina el directorio donde desea guardar el documento comparado y especifique el nombre del archivo de salida.
```csharp
string outputDirectory = "Your Document Directory";
string outputFileName = Path.Combine(outputDirectory, "RESULT.docx");
```
## Paso 2: Inicializar el comparador y agregar documentos
Inicializar el `Comparer` objeto con el documento de origen y agregar el documento de destino para comparar.
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
```
## Paso 3: Especificar las opciones de metadatos
Especifique las opciones de metadatos para guardar en el documento comparado. En este ejemplo, configuramos `CloneMetadataType` a `MetadataType.FileAuthor` y proporcionar detalles para `FileAuthorMetadata`.
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
## Paso 4: Comparar documentos y guardar metadatos
Compare los documentos con las opciones de metadatos especificadas y guarde el documento comparado.
```csharp
comparer.Compare(outputFileName, saveOptions);
```
## Paso 5: Mostrar mensaje de éxito
Muestra un mensaje de éxito indicando que los documentos se han comparado correctamente y la ubicación de salida.
```csharp
Console.WriteLine($"\nDocuments compared successfully.\nCheck output in {outputDirectory}.");
```

## Conclusión
En este tutorial, aprendimos a guardar metadatos de documentos definidos por el usuario con GroupDocs Comparison para .NET. Siguiendo estos pasos, podrá comparar documentos eficientemente, conservando y manipulando los metadatos según sus necesidades.
## Preguntas frecuentes
### ¿Puede GroupDocs Comparison for .NET manejar varios formatos de documentos?
Sí, GroupDocs Comparison admite una amplia gama de formatos de documentos, incluidos DOCX, PDF, PPTX, XLSX y más.
### ¿Hay una prueba gratuita disponible para la comparación de GroupDocs para .NET?
Sí, puedes acceder a la prueba gratuita. [aquí](https://releases.groupdocs.com/).
### ¿Puedo personalizar las opciones de metadatos según mis necesidades?
Por supuesto, GroupDocs Comparison ofrece opciones flexibles para personalizar el manejo de metadatos durante la comparación de documentos.
### ¿GroupDocs Comparison ofrece soporte técnico?
Sí, puede obtener soporte técnico en el foro de comparación de GroupDocs [aquí](https://forum.groupdocs.com/c/comparison/12).
### ¿Dónde puedo comprar una licencia para GroupDocs Comparison para .NET?
Puede comprar una licencia desde el sitio web de GroupDocs [aquí](https://purchase.groupdocs.com/buy).