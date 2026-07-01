---
categories:
- Document Processing
date: '2026-07-01'
description: Aprenda cómo leer metadatos de archivo C# usando GroupDocs.Comparison,
  extraer el flujo de tamaño de archivo y obtener el flujo de propiedades del documento
  de manera eficiente.
keywords:
- read file metadata c#
- extract file size stream
- groupdocs metadata extraction
- get document properties stream
lastmod: '2026-07-01'
linktitle: Extraer información del documento .NET
schemas:
- author: GroupDocs
  dateModified: '2026-07-01'
  description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  headline: Read File Metadata C# – Extract Document Information from Streams
  type: TechArticle
- description: Learn how to read file metadata C# using GroupDocs.Comparison, extract
    file size stream and get document properties stream efficiently.
  name: Read File Metadata C# – Extract Document Information from Streams
  steps:
  - name: Initialize the Comparer Object with Stream
    text: The following snippet creates a `Comparer` instance from a read‑only `FileStream`.
      Using a `using` block guarantees that the stream is closed and the comparer
      disposed, preventing file locks.
  - name: Extract Document Information
    text: Calling `GetDocumentInfo()` returns an `IDocumentInfo` object that holds
      all the metadata you need. The method reads only the necessary parts of the
      file header, so even a 500‑page PDF is processed in a fraction of a second.
  - name: Display and Use Document Information
    text: You can now access `FileType`, `PageCount`, and `Size` properties. In production
      you might store these values in a database, expose them via an API, or use them
      to decide whether to accept an upload.
  type: HowTo
- questions:
  - answer: Yes. The library supports **over 50 file formats**, including DOCX, PDF,
      XLSX, PPTX, and many image types, making it suitable for virtually any document
      workflow.
    question: Is GroupDocs.Comparison for .NET compatible with different document
      formats?
  - answer: Absolutely. A free trial is available at [the website](https://releases.groupdocs.com/),
      allowing you to evaluate all features without a license.
    question: Can I try GroupDocs.Comparison for .NET before purchasing?
  - answer: You can get help in the [GroupDocs.Comparison forum](https://forum.groupdocs.com/c/comparison/12),
      where the community and product team respond to questions promptly.
    question: Where can I find support for GroupDocs.Comparison for .NET?
  - answer: Yes. Temporary licenses can be obtained from [the licensing page](https://purchase.groupdocs.com/temporary-license/),
      ideal for development and QA environments.
    question: Are temporary licenses available for testing?
  - answer: Definitely. It offers enterprise‑grade performance, extensive format support,
      and robust error handling, all of which are essential for large‑scale production
      systems.
    question: Is GroupDocs.Comparison for .NET suitable for enterprise deployments?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- metadata-extraction
title: Leer metadatos de archivo C# – Extraer información del documento desde flujos
type: docs
url: /es/net/basic-usage/get-document-info-from-stream/
weight: 14
---

# Leer metadatos de archivo C# – Extraer información del documento desde flujos

## Introducción

Leer metadatos de archivo en C# sin cargar todo el documento es un requisito común para las aplicaciones .NET modernas. **Read file metadata C#** le permite validar cargas, mostrar detalles del documento y tomar decisiones de procesamiento mientras mantiene bajo el uso de memoria. GroupDocs.Comparison for .NET ofrece una API rápida basada en flujos que extrae el tipo de archivo, el número de páginas, el tamaño y otras propiedades directamente de un `Stream`. En las siguientes secciones verá por qué es importante, cómo configurarlo y código paso a paso que puede insertar en cualquier proyecto .NET.

## Respuestas rápidas
- **¿Qué significa “read file metadata C#”?** Significa obtener las propiedades de un documento (tipo, páginas, tamaño) a través de un flujo .NET sin cargar el contenido completo.  
- **¿Qué biblioteca maneja esto?** GroupDocs.Comparison for .NET ofrece el método `GetDocumentInfo()` para una extracción rápida de metadatos.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para desarrollo; se requiere una licencia comercial para producción.  
- **¿Puedo usar esto con PDFs grandes?** Sí, el enfoque basado en flujos procesa archivos de cientos de páginas sin un alto consumo de memoria.  
- **¿Es compatible con .NET 6+?** Absolutamente, la biblioteca se dirige a .NET Standard 2.0 y funciona en .NET 6, .NET 7 y .NET Core.

## ¿Qué es read file metadata C#?
`Read file metadata C#` se refiere a obtener la información descriptiva de un documento —como el formato, el número de páginas y el tamaño en bytes— usando código C# que trabaja con flujos. Esta técnica evita cargar todo el archivo en memoria, lo que es especialmente valioso para PDFs grandes, archivos DOCX o operaciones por lotes.

## ¿Por qué usar la extracción de metadatos de GroupDocs desde flujos?
GroupDocs.Comparison soporta **más de 50 formatos de entrada y salida** y puede extraer metadatos de archivos de hasta **2 GB** de tamaño mientras mantiene el uso de memoria por debajo de **10 MB**. La biblioteca lee solo las secciones de encabezado necesarias, entregando resultados en **menos de 150 ms** para PDFs típicos de 100 páginas en un servidor estándar. Estos beneficios cuantificados se traducen en una validación de carga más rápida, menores costos en la nube y una experiencia de usuario más fluida.

## Requisitos previos y configuración

### 1. Instalar GroupDocs.Comparison para .NET
Descargue el paquete más reciente de la [página oficial de descargas](https://releases.groupdocs.com/comparison/net/). Si prefiere NuGet, ejecute:

```
Install-Package GroupDocs.Comparison
```

### 2. Conocimientos básicos de desarrollo .NET
Debe estar cómodo con C# y el modelo de E/S de .NET. Trabajar con `Stream`, `FileStream` y `MemoryStream` es esencial para los ejemplos a continuación.

### 3. Entorno de desarrollo
Visual Studio, VS Code o JetBrains Rider son compatibles. Asegúrese de que su proyecto apunte a .NET 6 o posterior para obtener el mejor rendimiento.

## ¿Cómo leer metadatos de archivo C# desde un flujo?

Cargue el documento con un `FileStream`, instancie un `Comparer` y llame a `GetDocumentInfo()`. Toda la operación requiere solo dos líneas de código y devuelve un objeto `IDocumentInfo` que contiene el tipo de archivo, el número de páginas y el tamaño. Internamente la biblioteca lee solo los bytes de encabezado necesarios, por lo que incluso los PDFs grandes se procesan rápidamente sin consumir mucha memoria.  
`Comparer` es la clase principal de GroupDocs.Comparison que orquesta el análisis del documento.  
`GetDocumentInfo()` devuelve un objeto `IDocumentInfo` con metadatos básicos.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison.Interfaces;
```

### Paso 1: Inicializar el objeto Comparer con un flujo
El siguiente fragmento crea una instancia de `Comparer` a partir de un `FileStream` de solo lectura. Usar un bloque `using` garantiza que el flujo se cierre y el comparador se deseche, evitando bloqueos de archivos.

```csharp
using (Comparer comparer = new Comparer(File.OpenRead("SOURCE.docx")))
{
```

### Paso 2: Extraer información del documento
Llamar a `GetDocumentInfo()` devuelve un objeto `IDocumentInfo` que contiene todos los metadatos que necesita. El método lee solo las partes necesarias del encabezado del archivo, por lo que incluso un PDF de 500 páginas se procesa en una fracción de segundo.

```csharp
IDocumentInfo info = comparer.Source.GetDocumentInfo();
```

### Paso 3: Mostrar y usar la información del documento
Ahora puede acceder a las propiedades `FileType`, `PageCount` y `Size`. En producción podría almacenar estos valores en una base de datos, exponerlos a través de una API o usarlos para decidir si aceptar una carga.

```csharp
Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## Casos de uso comunes y patrones de implementación

### Validación de carga de archivos
Cuando un usuario carga un documento, puede verificar instantáneamente su tipo y número de páginas antes de guardarlo en el almacenamiento. Esto evita que formatos no deseados y archivos demasiado grandes ingresen a su sistema.

```csharp
// Example: Validating uploaded documents before processing
public bool ValidateUploadedDocument(Stream documentStream)
{
    using (Comparer comparer = new Comparer(documentStream))
    {
        IDocumentInfo info = comparer.Source.GetDocumentInfo();
        
        // Check if it's a supported format
        if (info.FileType == FileType.Unknown)
            return false;
            
        // Ensure it's not too large (e.g., max 50 pages)
        if (info.PageCount > 50)
            return false;
            
        return true;
    }
}
```

### Análisis de documentos por lotes
¿Procesando una carpeta de documentos? Extraiga los metadatos primero para dirigir los archivos a diferentes flujos de trabajo, por ejemplo, PDFs grandes van a un trabajador asíncrono, mientras que los archivos de una sola página se manejan en línea.

```csharp
// Example: Categorizing documents by complexity
public void CategorizeDocuments(string[] filePaths)
{
    foreach (string path in filePaths)
    {
        using (Comparer comparer = new Comparer(File.OpenRead(path)))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            
            if (info.PageCount == 1)
            {
                // Fast processing for single-page documents
                ProcessSimpleDocument(path);
            }
            else
            {
                // More thorough processing for complex documents
                ProcessComplexDocument(path);
            }
        }
    }
}
```

## Problemas comunes y soluciones

### Problema: “The file is being used by another process.”
**Problema**: “The file is being used by another process.”  
**Solución**: Wrap the stream in a `using` statement and, if necessary, implement a retry policy with exponential back‑off.

```csharp
// Example: Retry logic for locked files
public IDocumentInfo GetDocumentInfoWithRetry(string filePath, int maxRetries = 3)
{
    for (int attempt = 0; attempt < maxRetries; attempt++)
    {
        try
        {
            using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
            {
                return comparer.Source.GetDocumentInfo();
            }
        }
        catch (IOException) when (attempt < maxRetries - 1)
        {
            Thread.Sleep(100); // Wait a bit before retrying
        }
    }
    throw new Exception($"Could not access file after {maxRetries} attempts");
}
```

### Problema: The API throws an exception for an unknown format.
**Problema**: The API throws an exception for an unknown format.  
**Solución**: Inspect the `FileType` property; if it returns `Unknown`, return a friendly error to the caller and log the incident.

```csharp
// Example: Safe file type checking
using (Comparer comparer = new Comparer(File.OpenRead(filePath)))
{
    IDocumentInfo info = comparer.Source.GetDocumentInfo();
    
    if (info.FileType == FileType.Unknown)
    {
        Console.WriteLine("Unsupported file format detected");
        return; // or handle appropriately
    }
    
    // Process normally
    ProcessSupportedDocument(info);
}
```

### Problema: Memory spikes when processing very large documents.
**Problema**: Memory spikes when processing very large documents.  
**Solución**: The stream‑based approach already minimizes memory use, but you should also call `Dispose()` on the `Comparer` as soon as you’re done and avoid holding references to the `IDocumentInfo` longer than needed.

## Consideraciones de rendimiento y mejores prácticas

### Mejores prácticas de gestión de flujos
1. **Siempre use `using` statements** – Garantiza la eliminación y libera los recursos rápidamente.  
2. **Restablezca la posición del flujo al reutilizar** – Si necesita leer el mismo flujo dos veces, llame a `stream.Seek(0, SeekOrigin.Begin)`.  
3. **Elija el tipo de flujo correcto** – `FileStream` para archivos en disco, `MemoryStream` para datos en memoria, `NetworkStream` para fuentes remotas.

```csharp
   stream.Position = 0; // Reset to beginning before reuse
   ```

### Cuándo preferir este enfoque vs. cargar el documento completo
**Prefiera la extracción de metadatos basada en flujos cuando**:
- Solo necesita detalles de alto nivel (tipo, páginas, tamaño).  
- Está validando cargas o construyendo un catálogo de documentos.  
- El rendimiento y una huella de memoria baja son críticos.

**Cambie al procesamiento completo del documento cuando**:
- Necesita comparar contenido, extraer texto o renderizar páginas.  
- Se requiere un análisis profundo (p. ej., OCR, detección de marcas de agua).  

## Consejos avanzados para uso en producción

### Estrategias robustas de manejo de errores
Envuelva todas las operaciones en un bloque try‑catch que capture `GroupDocs.Comparison.Exceptions.ComparisonException`. `ComparisonException` es lanzada por la biblioteca cuando ocurre un error durante el procesamiento del documento. Registre los detalles del error, devuelva una respuesta de error estandarizada y asegúrese de que el `Comparer` se deseche en una cláusula `finally`.

```csharp
public DocumentInfoResult GetDocumentInfoSafely(Stream documentStream)
{
    try
    {
        using (Comparer comparer = new Comparer(documentStream))
        {
            IDocumentInfo info = comparer.Source.GetDocumentInfo();
            return new DocumentInfoResult 
            { 
                Success = true, 
                Info = info 
            };
        }
    }
    catch (Exception ex)
    {
        return new DocumentInfoResult 
        { 
            Success = false, 
            ErrorMessage = ex.Message 
        };
    }
}
```

### Integración con registro y monitoreo
Inyecte un framework de registro (p. ej., Serilog o NLog) y emita métricas como tiempo de procesamiento, tamaño del archivo y recuentos de éxito/fracaso. Estos datos le ayudan a detectar regresiones de rendimiento temprano.

```csharp
// Example: Adding performance logging
var stopwatch = System.Diagnostics.Stopwatch.StartNew();
IDocumentInfo info = comparer.Source.GetDocumentInfo();
stopwatch.Stop();

logger.LogInformation($"Document info extraction took {stopwatch.ElapsedMilliseconds}ms for {info.FileType}");
```

## Preguntas frecuentes

**Q: ¿GroupDocs.Comparison para .NET es compatible con diferentes formatos de documento?**  
A: Sí. La biblioteca soporta **más de 50 formatos de archivo**, incluidos DOCX, PDF, XLSX, PPTX y muchos tipos de imagen, lo que la hace adecuada para prácticamente cualquier flujo de trabajo de documentos.

**Q: ¿Puedo probar GroupDocs.Comparison para .NET antes de comprar?**  
A: Absolutamente. Una prueba gratuita está disponible en [el sitio web](https://releases.groupdocs.com/), lo que le permite evaluar todas las funciones sin una licencia.

**Q: ¿Dónde puedo encontrar soporte para GroupDocs.Comparison para .NET?**  
A: Puede obtener ayuda en el [foro de GroupDocs.Comparison](https://forum.groupdocs.com/c/comparison/12), donde la comunidad y el equipo del producto responden a las preguntas rápidamente.

**Q: ¿Hay licencias temporales disponibles para pruebas?**  
A: Sí. Las licencias temporales pueden obtenerse en [la página de licencias](https://purchase.groupdocs.com/temporary-license/), ideal para entornos de desarrollo y QA.

**Q: ¿GroupDocs.Comparison para .NET es adecuado para implementaciones empresariales?**  
A: Definitivamente. Ofrece rendimiento de nivel empresarial, amplio soporte de formatos y manejo robusto de errores, todo lo cual es esencial para sistemas de producción a gran escala.

---

**Última actualización:** 2026-07-01  
**Probado con:** GroupDocs.Comparison 23.10 for .NET  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Obtener propiedades del documento C# .NET - Extraer metadatos de archivo](/comparison/net/basic-usage/get-document-info-from-path/)
- [Gestión de metadatos de documentos .NET - Guía completa para GroupDocs.Comparison](/comparison/net/metadata-management/)
- [Tutorial de comparación de documentos .NET - Conservar metadatos con GroupDocs](/comparison/net/loading-and-saving-documents/saving-documents-metadata-source/)