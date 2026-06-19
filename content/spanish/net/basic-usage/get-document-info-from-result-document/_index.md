---
categories:
- Document Comparison
date: '2026-06-15'
description: Aprenda cómo extraer metadatos de los resultados de comparación de .NET
  usando GroupDocs.Comparison. Guía paso a paso con ejemplos de código y consejos
  prácticos.
keywords:
- how to extract metadata
- get document size .net
- document comparison metadata
- GroupDocs Comparison document info
lastmod: '2026-06-15'
linktitle: Extraer información del documento de los resultados de comparación
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
title: Cómo extraer metadatos de los resultados de comparación de .NET – Guía completa
type: docs
url: /es/net/basic-usage/get-document-info-from-result-document/
weight: 12
---

# Cómo extraer metadatos de los resultados de comparación .NET – Guía completa

Cuando trabajas con comparaciones de documentos en aplicaciones .NET, puede que te preguntes **cómo extraer metadatos** de los resultados de la comparación. Metadatos como tipo de archivo, número de páginas y tamaño del documento pueden ser cruciales para auditorías, afinación de rendimiento o simplemente para mostrar información útil a los usuarios finales. Este tutorial te guía para recuperar esos datos de manera eficiente con GroupDocs.Comparison para .NET.

## Respuestas rápidas
- **¿Cuál es la clase principal para la comparación?** `Comparer` carga el documento fuente y ejecuta el motor de comparación.  
- **¿Qué método devuelve los metadatos?** `GetDocumentInfo()` en un documento objetivo devuelve un objeto `IDocumentInfo`.  
- **¿Puedo obtener el tamaño del documento en .NET?** Sí – la propiedad `Size` de `IDocumentInfo` devuelve el tamaño en bytes.  
- **¿Necesito una licencia para la extracción de metadatos?** Se requiere una licencia válida de GroupDocs.Comparison para uso en producción; la prueba gratuita soporta todas las funciones de metadatos.  
- **¿Es la API compatible con .NET 6?** Absolutamente – GroupDocs.Comparison soporta .NET Framework 4.6.1+, .NET Core 2.0+, y .NET 5/6+.

El método `GetDocumentInfo()` devuelve un objeto `IDocumentInfo` que contiene los metadatos del documento.

## ¿Qué es la extracción de metadatos en la comparación de documentos?
La extracción de metadatos es el proceso de obtener información descriptiva —como tipo de archivo, número de páginas y tamaño del archivo— de los documentos involucrados en una operación de comparación. GroupDocs.Comparison expone estos datos a través de una API unificada, facilitando su registro, visualización o uso para procesamiento condicional.

## ¿Por qué extraer metadatos de los resultados de comparación?
Extraer metadatos le permite crear registros de auditoría detallados, enrutar archivos según su tipo y ajustar las estrategias de procesamiento para documentos grandes. Al conocer el tipo de archivo, el número de páginas y el tamaño, puede aplicar reglas de cumplimiento, estimar el tiempo de procesamiento y presentar información clara a los usuarios antes de iniciar una comparación.

## Requisitos previos

1. **GroupDocs.Comparison for .NET** – Instale la biblioteca desde la [página oficial de lanzamientos](https://releases.groupdocs.com/comparison/net/).  
   También puede explorar todos los lanzamientos en la [página de lanzamientos de GroupDocs](https://releases.groupdocs.com/).  
2. **Entorno de desarrollo** – Visual Studio, VS Code, o cualquier IDE que soporte .NET 6+.  
3. **Documentos de muestra** – Dos archivos (p. ej., `SOURCE.docx` y `TARGET.docx`) para pruebas. La API funciona con más de **50 formatos de documento**.

## Importar espacios de nombres

Las siguientes directivas `using` le dan acceso al motor central de comparación, utilidades de manejo de archivos y las interfaces de metadatos.

```csharp
using System;
using System.IO;
using System.Linq;
using GroupDocs.Comparison;
using GroupDocs.Comparison.Interfaces;
```

Estas importaciones son necesarias antes de instanciar cualquier objeto de GroupDocs.

## ¿Cómo extraer metadatos de los resultados de comparación?

La clase `Comparer` carga el documento fuente y orquesta el proceso de comparación.

Para obtener los metadatos, primero cargue el documento fuente con una instancia de `Comparer`, luego añada el(los) documento(s) objetivo. Después de que el motor de comparación se haya inicializado, llame a `GetDocumentInfo()` en cada objetivo para obtener un objeto `IDocumentInfo` que contiene propiedades como tipo de archivo, número de páginas y tamaño. Este enfoque funciona de manera uniforme en todos los formatos compatibles.

### Paso 1: Inicializar Comparer con el documento fuente

`Comparer` es la clase central en GroupDocs.Comparison que carga el documento fuente y orquesta las operaciones de comparación. Usar un bloque `using` garantiza que todos los recursos no administrados se liberen automáticamente.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

> **Consejo profesional:** Puede pasar cualquier `Stream` (archivo, memoria, nube) al constructor de `Comparer`, no solo una ruta de archivo.

### Paso 2: Añadir documento objetivo para la comparación

El método `Add()` acepta flujos adicionales o rutas de archivo, habilitando comparaciones de uno a muchos.

```csharp
comparer.Add(File.OpenRead("TARGET.docx"));
```

> **Importante:** El orden de los documentos añadidos influye en la forma en que los cambios se resaltan en el informe final.

### Paso 3: Recuperar información del documento del documento resultante

`IDocumentInfo` proporciona una vista unificada de los metadatos del documento, como tipo de archivo, número de páginas y tamaño, en todos los formatos compatibles.

```csharp
IDocumentInfo info = comparer.Targets.FirstOrDefault().GetDocumentInfo();
```

> **Entendiendo los datos:** El objeto devuelto funciona igual para DOCX, PDF, XLSX y PPTX, por lo que puede escribir código independiente del formato.

### Paso 4: Mostrar información del documento

Una vez que tenga la instancia `IDocumentInfo`, puede registrar, almacenar o presentar sus propiedades.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
```

Las tres propiedades más usadas son:

- **FileType** – p. ej., `DOCX`, `PDF`, `XLSX`.  
- **PageCount** – total de páginas o diapositivas.  
- **Size** – tamaño del archivo en bytes (útil para cálculos de almacenamiento).

## ¿Cómo obtener el tamaño del documento en .NET?

La propiedad `Size` devuelve el tamaño del archivo en bytes.

El tamaño del documento se puede acceder directamente desde la instancia `IDocumentInfo` mediante su propiedad `Size`. Esta propiedad devuelve el número exacto de bytes del archivo original, permitiendo convertirlo a kilobytes o megabytes para su visualización o cálculos de almacenamiento. Refleja el tamaño del archivo fuente, no de ninguna versión procesada.

```csharp
long sizeInBytes = documentInfo.Size;
double sizeInMegabytes = sizeInBytes / (1024.0 * 1024.0);
Console.WriteLine($"Document size: {sizeInMegabytes:F2} MB");
```

> **Nota:** El valor `Size` refleja el tamaño original del archivo, no el tamaño después de cualquier procesamiento interno o compresión.

## Casos de uso comunes y aplicaciones prácticas

- **Procesamiento por lotes:** Use el tipo de archivo para dirigir los archivos DOCX a un flujo de trabajo específico de Word y los PDFs a una canalización optimizada para PDF.  
- **Gestión de almacenamiento:** Archive documentos mayores de 10 MB a un depósito de almacenamiento en frío automáticamente.  
- **Retroalimentación al usuario:** Muestre el número de páginas y el tamaño antes de la comparación para establecer expectativas realistas sobre el tiempo de procesamiento.  
- **Aseguramiento de calidad:** Verifique que los archivos subidos estén completos comparando el número de páginas esperado versus el real.

## Solución de problemas comunes

- **Errores de acceso a archivos:** Verifique los permisos de lectura y use rutas absolutas durante el desarrollo.  
- **Presión de memoria con archivos grandes:** Prefiera el streaming (`File.OpenRead`) en lugar de cargar todo el archivo en memoria.  
- **Excepciones de referencia nula:** `FirstOrDefault()` puede devolver `null` si no se añadió ningún objetivo; siempre verifique antes de acceder a `GetDocumentInfo()`.  

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

- **Metadatos limitados para texto plano:** Formatos como `.txt` pueden no exponer un `PageCount` significativo. Proteja contra valores ausentes.

## Consideraciones de rendimiento

- **Gestión de streams:** Siempre envuelva los streams en sentencias `using` para liberar los manejadores de archivo rápidamente.  
- **Caché:** Almacene los metadatos accedidos con frecuencia en una caché para evitar extracciones repetidas.  
- **Operaciones por lotes:** Procese documentos en grupos para reducir la sobrecarga y mejorar el rendimiento.

## Mejores prácticas para uso en producción

- **Manejo robusto de errores:** Encierre la extracción de metadatos en bloques try‑catch para manejar archivos corruptos o no soportados de forma elegante.  
- **Registro integral:** Registre el tipo de documento, tamaño y número de páginas para cada comparación para ayudar en la solución de problemas y cumplimiento de auditorías.  
- **Higiene de seguridad:** Evite exponer rutas completas de archivos o detalles internos del servidor en los mensajes de la UI.  
- **Liberación de recursos:** Libere rápidamente las instancias de `Comparer`, especialmente en servicios web que manejan muchas solicitudes concurrentes.

## Escenarios avanzados

### Múltiples documentos objetivo

Si compara una fuente contra varios objetivos, itere a través de la colección `Targets` y extraiga los metadatos de cada uno.

```csharp
foreach (var target in comparer.Targets)
{
    IDocumentInfo info = target.GetDocumentInfo();
    // Process each target's information
}
```

### Procesamiento condicional basado en metadatos

```csharp
if (info.Size > 5 * 1024 * 1024) // larger than 5 MB
{
    // Apply a different comparison setting or queue for background processing
}
```

### Almacenar metadatos en una base de datos

Persista `FileType`, `PageCount` y `Size` en una tabla relacional para habilitar informes y análisis en miles de comparaciones.

## Preguntas frecuentes

**Q: ¿GroupDocs.Comparison para .NET es compatible con varios formatos de documento?**  
A: Sí, soporta **más de 50 formatos** incluyendo DOCX, PDF, PPTX, XLSX, TXT y muchos otros, proporcionando una extracción de metadatos consistente en todos ellos.

**Q: ¿Puedo personalizar la configuración de comparación sin afectar la extracción de metadatos?**  
A: Absolutamente. Configuraciones como sensibilidad, tipos de cambios y formato de salida son independientes de la llamada `GetDocumentInfo()`.

**Q: ¿Existe una versión de prueba que pueda usar para evaluación?**  
A: Sí, descargue una prueba gratuita desde la [página de lanzamientos de GroupDocs](https://releases.groupdocs.com/). La prueba incluye capacidades completas de extracción de metadatos.

**Q: ¿Dónde puedo obtener soporte para preguntas de implementación?**  
A: Utilice el [foro de GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12) para ayuda de la comunidad y soporte oficial del equipo de GroupDocs.

**Q: ¿Qué opciones de licencia están disponibles para implementaciones en producción?**  
A: GroupDocs ofrece licencias para desarrolladores, sitio y OEM. Las opciones de compra se enumeran en la [página de compra de GroupDocs](https://purchase.groupdocs.com/buy).

---

**Última actualización:** 2026-06-15  
**Probado con:** GroupDocs.Comparison 6.0 para .NET  
**Autor:** GroupDocs

```csharp
var targetDoc = comparer.Targets.FirstOrDefault();
if (targetDoc != null)
{
    IDocumentInfo info = targetDoc.GetDocumentInfo();
    // Process document info
}
```

## Tutoriales relacionados

- [Gestión de metadatos de documentos .NET - Guía completa para GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Obtener propiedades del documento C# .NET - Extraer metadatos de archivo](/comparison/net/basic-usage/get-document-info-from-path/)
- [Conservar metadatos del objetivo con GroupDocs.Comparison – Tutorial .NET](/comparison/net/advanced-comparison/groupdocs-comparison-net-metadata-target/)