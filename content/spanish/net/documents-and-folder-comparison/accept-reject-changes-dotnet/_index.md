---
title: Aceptar y rechazar cambios en la comparación de GroupDocs para .NET
linktitle: Aceptar y rechazar cambios en la comparación de GroupDocs para .NET
second_title: API GroupDocs.Comparison .NET
description: Aprenda a aceptar y rechazar cambios en documentos usando GroupDocs Comparison para .NET. Optimice los flujos de trabajo de sus documentos sin esfuerzo.
type: docs
weight: 10
url: /es/net/documents-and-folder-comparison/accept-reject-changes-dotnet/
---
## Introducción
En el ámbito de la gestión y colaboración de documentos, garantizar la precisión e integridad de los archivos es primordial. GroupDocs Comparison para .NET surge como una solución sólida que permite a los desarrolladores aceptar y rechazar cambios dentro de los documentos sin esfuerzo, simplificando así los flujos de trabajo y mejorando la productividad. Este tutorial lo guiará a través del proceso de aceptar y rechazar cambios usando GroupDocs Comparison para .NET, desglosando cada paso para mayor claridad y facilidad de implementación.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de cumplir con los siguientes requisitos previos:
### Configuración del entorno
1. Instale el SDK de .NET: si aún no lo ha hecho, descargue e instale el SDK de .NET adecuado para su sistema operativo desde el sitio web de .NET.
2.  Instale GroupDocs Comparison para .NET: obtenga la última versión de GroupDocs Comparison para .NET del archivo proporcionado[enlace de descarga](https://releases.groupdocs.com/comparison/net/) y siga las instrucciones de instalación.
3. Familiaridad con la programación C#: este tutorial asume una comprensión básica del lenguaje de programación C# y su sintaxis.

## Importar espacios de nombres
Para empezar, importe los espacios de nombres necesarios a su proyecto. Estos espacios de nombres proporcionarán acceso a las funcionalidades necesarias para la comparación y manipulación de documentos.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Result;
using GroupDocs.Comparison.Options;
```
## Paso 1: especificar el directorio de salida y los nombres de archivo
```csharp
string outputDirectory = "Your Document Directory";
string outputFileNameWithAcceptedChange = Path.Combine(outputDirectory, "RESULT_WITH_ACCEPTED_CHANGE.docx");
string outputFileNameWithRejectedChange = Path.Combine(outputDirectory, "RESULT_WITH_REJECTED_CHANGE.docx");
```
 Asegúrese de reemplazar`"Your Document Directory"` con la ruta al directorio de salida deseado.
## Paso 2: Inicializar Comparer y comparar documentos
```csharp
using (Comparer comparer = new Comparer("SOURCE.docx"))
{
    comparer.Add("TARGET.docx");
    comparer.Compare();
```
Este código inicializa el objeto Comparador con el documento de origen y agrega el documento de destino para comparar. Luego, ejecuta el proceso de comparación.
## Paso 3: recuperar y manipular cambios
```csharp
ChangeInfo[] changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Reject;
comparer.ApplyChanges(outputFileNameWithRejectedChange, new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });
changes = comparer.GetChanges();
changes[0].ComparisonAction = ComparisonAction.Accept;
comparer.ApplyChanges(outputFileNameWithAcceptedChange, new ApplyChangeOptions { Changes = changes });
```
Recupere los cambios de la comparación y manipúlelos según sea necesario. En este ejemplo, los cambios se rechazan primero y luego se aceptan. Los documentos resultantes se guardan en consecuencia.

## Conclusión
En conclusión, GroupDocs Comparison para .NET ofrece una solución perfecta para aceptar y rechazar cambios dentro de los documentos. Siguiendo los pasos descritos en este tutorial, los desarrolladores pueden integrar eficientemente esta funcionalidad en sus aplicaciones, garantizando la precisión de los documentos y mejorando la colaboración.
## Preguntas frecuentes
### ¿Puede GroupDocs Comparison para .NET comparar documentos de diferentes formatos?
Sí, GroupDocs Comparison para .NET admite la comparación entre documentos de varios formatos, como DOCX, PDF, PPTX y más.
### ¿La comparación de GroupDocs para .NET es compatible con .NET Core?
Sí, GroupDocs Comparison para .NET es compatible tanto con .NET Framework como con .NET Core.
### ¿Puedo personalizar la apariencia de los cambios en los documentos comparados?
Por supuesto, GroupDocs Comparison para .NET ofrece amplias opciones para personalizar la apariencia de los cambios, incluidos el color, el estilo y más.
### ¿GroupDocs Comparison para .NET admite la comparación de documentos de varias páginas?
Sí, GroupDocs Comparison para .NET admite la comparación de documentos de varias páginas con precisión y exactitud.
### ¿Existe una versión de prueba disponible para GroupDocs Comparison para .NET?
 Sí, puede aprovechar una prueba gratuita de GroupDocs Comparison para .NET desde el sitio web proporcionado.[enlace](https://releases.groupdocs.com/).