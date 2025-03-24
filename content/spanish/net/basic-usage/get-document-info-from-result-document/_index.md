---
title: Obtener información del documento del documento de resultados GroupDocs.Comparison para .NET
linktitle: Obtener información del documento del documento de resultados GroupDocs.Comparison para .NET
second_title: API GroupDocs.Comparison .NET
description: Aprenda a recuperar información del documento a partir del documento resultante utilizando GroupDocs.Comparison para .NET. Pasos sencillos explicados para desarrolladores .NET.
weight: 12
url: /es/net/basic-usage/get-document-info-from-result-document/
---
## Introducción
En el ámbito del desarrollo .NET, gestionar y comparar documentos es un requisito común. GroupDocs.Comparison para .NET ofrece una solución sólida para esta tarea, permitiendo a los desarrolladores integrar perfectamente funcionalidades de comparación de documentos en sus aplicaciones. Este tutorial lo guiará a través del proceso de utilización de GroupDocs.Comparison para .NET para recuperar información del documento resultante. 
## Requisitos previos
Antes de sumergirse en este tutorial, asegúrese de tener los siguientes requisitos previos:
1. GroupDocs.Comparison para .NET: instale la biblioteca GroupDocs.Comparison para .NET. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/comparison/net/).
2. Entorno de desarrollo: configure su entorno de desarrollo .NET, incluido IDE (como Visual Studio) y las configuraciones necesarias.
3.  Archivos de documentos: prepare los archivos de documentos de origen y de destino (p. ej.,`SOURCE.docx` y`TARGET.docx`) para comparacion.

## Importar espacios de nombres
En primer lugar, debe importar los espacios de nombres necesarios para acceder a las funcionalidades de GroupDocs.Comparison.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

## Paso 1: inicializar el comparador con el documento fuente
```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```
 En este paso, inicializamos un`Comparer` objeto con el documento fuente (`SOURCE.docx` en este caso) utilizando un`using` declaración para garantizar la eliminación adecuada de los recursos.
## Paso 2: agregue el documento de destino para comparar
```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```
Aquí, agregamos el documento de destino (`TARGET.docx`) al objeto comparador para comparar.
## Paso 3: recuperar la información del documento del documento de resultados
```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```
 Este paso recupera información del documento del documento resultante. Accede al documento de destino utilizando`FirstOrDefault()` y luego llama`GetDocumentInfo()`para obtener información como el tipo de archivo, el número de páginas y el tamaño del documento.
## Paso 4: Mostrar información del documento
```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```
Aquí, mostramos la información del documento recuperado, incluido el tipo de archivo, el número de páginas y el tamaño del documento en bytes.

## Conclusión
GroupDocs.Comparison para .NET simplifica el proceso de comparación de documentos en aplicaciones .NET. Siguiendo este tutorial, habrá aprendido cómo recuperar información del documento resultante usando GroupDocs.Comparison para .NET. Incorpore estas técnicas en sus proyectos para mejorar las capacidades de gestión de documentos.
## Preguntas frecuentes
### ¿GroupDocs.Comparison para .NET es compatible con varios formatos de documentos?
Sí, GroupDocs.Comparison para .NET admite una amplia gama de formatos de documentos, incluidos DOCX, PDF, PPTX, XLSX y más.
### ¿Puedo personalizar la configuración de comparación de documentos?
Por supuesto, GroupDocs.Comparison para .NET ofrece amplias opciones de personalización para la comparación de documentos que se adaptan a sus requisitos específicos.
### ¿Existe una versión de prueba disponible para evaluación?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte para GroupDocs.Comparison para .NET?
 Puede buscar ayuda e interactuar con la comunidad en el foro GroupDocs.Comparison[aquí](https://forum.groupdocs.com/c/comparison/12).
### ¿Cuáles son las opciones de licencia de GroupDocs.Comparison para .NET?
 Puede explorar opciones de licencia y comprar una licencia en[aquí](https://purchase.groupdocs.com/buy).