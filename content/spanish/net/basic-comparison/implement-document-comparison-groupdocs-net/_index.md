---
categories:
- Document Processing
date: '2026-06-10'
description: Aprenda cómo comparar documentos .net con GroupDocs.Comparison. Guía
  paso a paso que cubre la configuración, el código, comparar archivos Excel c#, comparar
  archivos PDF c# y mejores prácticas.
keywords:
- compare documents .net
- compare excel files c#
- compare pdf files c#
- document comparison best practices
lastmod: '2026-06-10'
schemas:
- author: GroupDocs
  dateModified: '2026-06-10'
  description: Learn how to compare documents .net with GroupDocs.Comparison. Step‑by‑step
    guide covering setup, code, compare excel files c#, compare pdf files c#, and
    best practices.
  headline: compare documents .net – Complete GroupDocs Implementation Guide
  type: TechArticle
- questions:
  - answer: You can add multiple target documents to a single `Comparer` instance
      using repeated `Add()` calls, but processing them sequentially is recommended
      for large batches.
    question: How many documents can I compare at once?
  - answer: Yes—pass the password when constructing the `Comparer` or loading the
      document.
    question: Can GroupDocs.Comparison handle password‑protected files?
  - answer: Over 50 formats, including DOCX, XLSX, PPTX, PDF, JPEG, PNG, TXT, and
      more.
    question: What file formats does GroupDocs.Comparison support?
  - answer: Use `ComparisonSettings` to set `InsertedColor`, `DeletedColor`, and `StyleChangeColor`.
    question: How do I customize the appearance of changes?
  - answer: Absolutely—disable options like `DetectStyleChanges` or `DetectTableChanges`
      in `ComparisonSettings`.
    question: Is it possible to ignore specific change types?
  type: FAQPage
tags:
- dotnet
- csharp
- document-comparison
- groupdocs
- automation
title: comparar documentos .net – Guía completa de implementación de GroupDocs
type: docs
url: /es/net/basic-comparison/implement-document-comparison-groupdocs-net/
weight: 1
---

# comparar documentos .net – Guía completa de implementación de GroupDocs

Si necesitas **comparar documentos .net**, has llegado al lugar correcto. Imagina abrir dos contratos que parecen idénticos y detectar instantáneamente cada cambio—sin desplazamiento manual, sin ediciones perdidas. Ese es el poder de la comparación automática de documentos, y con **GroupDocs.Comparison for .NET** puedes lograrlo en minutos.

## Respuestas rápidas
- **¿Qué biblioteca maneja la comparación de documentos en .NET?** GroupDocs.Comparison.
- **¿Puedo comparar archivos Word, Excel y PDF?** Sí—se admiten más de 50 formatos.
- **¿Qué versión debo usar?** La versión 25.4.0 ofrece el mejor rendimiento y estabilidad.
- **¿Necesito una licencia para producción?** Se requiere una licencia comercial para implementaciones en producción.
- **¿Es posible el procesamiento asíncrono?** Absolutamente—utiliza `Task.Run` con la API de comparación.

## Qué es GroupDocs.Comparison?
GroupDocs.Comparison es una biblioteca .NET que detecta programáticamente las diferencias entre dos o más documentos y genera un archivo de resultados resaltado. Soporta más de 50 formatos, procesa archivos de cientos de páginas sin cargar todo el contenido en memoria, y brinda un control detallado sobre la configuración de comparación.

## Por qué usar GroupDocs.Comparison para comparar documentos .net?
GroupDocs.Comparison ofrece una comparación de documentos rápida, precisa y escalable para aplicaciones .NET. Puede procesar PDFs y archivos de Office grandes en segundos, preservando el formato y la fidelidad visual mientras resalta inserciones, eliminaciones y cambios de estilo. La biblioteca funciona en .NET Core, .NET 5/6/7 y el .NET Framework completo, lo que la convierte en una opción versátil para cualquier proyecto.

- **Velocidad:** Procesa un PDF de 200 páginas en menos de 2 segundos en un servidor estándar.
- **Precisión:** Detecta texto, formato, tablas e imágenes con una fidelidad del 99,9 %.
- **Escalabilidad:** Maneja trabajos por lotes de miles de archivos usando APIs de streaming.
- **Flexibilidad:** Funciona con .NET Core 3.1+, .NET 5/6/7 y .NET Framework 4.6.1+.

## Requisitos previos
- **Entorno de desarrollo:** .NET Core 3.1 o superior, o .NET Framework 4.6.1 +
- **Biblioteca GroupDocs.Comparison:** Versión 25.4.0 (instalada vía NuGet)
- **Archivos de muestra:** Documentos Word, PDF o Excel para pruebas
- **Conocimientos básicos de C#:** Clases, métodos, sentencias `using`

### Deseable (Opcional)
- Familiaridad con la gestión de paquetes NuGet
- Experiencia con I/O de archivos y streams
- Comprensión de los patrones async/await

## Cómo comparar documentos .net usando GroupDocs.Comparison?
Para comparar dos documentos con GroupDocs.Comparison, carga cada archivo en un stream, configura opcionalmente ComparisonSettings y llama al método Compare en una instancia de Comparer. La API devuelve un documento de resultados que resalta las diferencias, y puedes guardarlo en cualquier formato admitido. Este enfoque requiere solo unas pocas líneas de código mientras te brinda control total sobre el proceso de comparación.

### Implementación paso a paso

### 1️⃣ Gestión inteligente de rutas de documentos
Centralizar las rutas de archivos evita errores de “archivo no encontrado” y hace que los cambios de entorno sean sencillos.

```csharp
public static class Constants
{
    public const string SOURCE_WORD = @"YOUR_DOCUMENT_DIRECTORY\source.docx";
    public const string TARGET_WORD = @"YOUR_DOCUMENT_DIRECTORY\target.docx";

    public static string GetOutputDirectoryPath()
    {
        return @"YOUR_OUTPUT_DIRECTORY";
    }

    public const string RESULT_WORD = "result.docx";
}
```

**Por qué funciona esto:**  
- Un único lugar para actualizar rutas para desarrollo, pruebas o producción.  
- Elimina cadenas codificadas directamente dispersas por la base de código.  

### 2️⃣ Lógica central de comparación
La clase `Comparer` es el motor que impulsa el algoritmo de diferencias.

```csharp
using (Comparer comparer = new Comparer(Constants.SOURCE_WORD))
{
    // Add the target document for comparison
    comparer.Add(Constants.TARGET_WORD);

    // Perform the comparison and save the result
    string outputFileName = Path.Combine(Constants.GetOutputDirectoryPath(), Constants.RESULT_WORD);
    comparer.Compare(outputFileName);
}
```

**Ancla de definición:**  
`Comparer` es la clase central de GroupDocs.Comparison que orquesta el análisis de documentos y produce el resultado resaltado.

**Cómo ayuda:**  
- Soporta múltiples documentos objetivo mediante llamadas repetidas a `Add()`.  
- Genera un archivo de resultados con los cambios resaltados en rojo, verde o colores personalizados.

### 3️⃣ Configuraciones avanzadas para Excel y PDF
Puedes afinar la comparación para ignorar el formato o enfocarte en cambios de datos—perfecto para escenarios de **compare excel files c#**.

```csharp
CompareOptions compareOptions = new CompareOptions()
{
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    StyleChangeDetection = true
};

using (Comparer comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath, compareOptions);
}
```

**Ancla de definición:**  
`ComparisonSettings` te permite habilitar o deshabilitar tipos específicos de cambios como `DetectStyleChanges` o `DetectTableChanges`.

### 4️⃣ Manejo de múltiples formatos
GroupDocs.Comparison detecta automáticamente el tipo de archivo, pero también puedes forzar un formato cuando sea necesario—ideal para **compare pdf files c#**.

```csharp
public static void CompareDocumentsByType(string sourcePath, string targetPath, string outputPath)
{
    string extension = Path.GetExtension(sourcePath).ToLower();
    
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        
        CompareOptions options = GetOptionsForFormat(extension);
        comparer.Compare(outputPath, options);
    }
}

private static CompareOptions GetOptionsForFormat(string extension)
{
    switch (extension)
    {
        case ".pdf":
            return new CompareOptions { DetectStyleChanges = false };
        case ".xlsx":
            return new CompareOptions { CalculateCoordinates = true };
        default:
            return new CompareOptions();
    }
}
```

### 5️⃣ Transmisión de archivos grandes
Al procesar documentos masivos, la transmisión evita cargar todo el archivo en memoria.

```csharp
// For files over 50MB, consider this approach
using (var sourceStream = File.OpenRead(sourcePath))
using (var targetStream = File.OpenRead(targetPath))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

### 6️⃣ Manejo robusto de errores
Nunca permitas que un archivo corrupto haga fallar tu servicio; envuelve las llamadas en bloques try‑catch y registra detalles útiles.

```csharp
try
{
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        comparer.Compare(outputPath);
    }
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Document not found: {ex.FileName}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Access denied: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Comparison failed: {ex.Message}");
}
```

## Mejores prácticas para la comparación de documentos
- **Validar los archivos de entrada** antes de invocar la API para detectar formatos no compatibles temprano.  
- **Usar `Path.Combine`** para la construcción de rutas multiplataforma (ver Problema #1).  
- **Habilitar solo los tipos de cambio necesarios** para mejorar el rendimiento (p.ej., desactivar la detección de estilo para hojas de Excel centradas en datos).  
- **Liberar rápidamente los objetos `Comparer`** para liberar recursos nativos.  

## Problemas comunes y cómo evitarlos

### Problema #1: Problemas con el separador de rutas
**Solución:** Siempre construye rutas con `Path.Combine()` y `Path.DirectorySeparatorChar`.

```csharp
// Wrong - will break on different operating systems
string path = "C:/Documents/source.docx";

// Right - works everywhere
string path = Path.Combine("C:", "Documents", "source.docx");
```

### Problema #2: Agotamiento de memoria en archivos grandes
**Solución:** Cambia al modo de transmisión para archivos mayores de 50 MB.

```csharp
// For files over 50MB, consider this approach
using (var sourceStream = File.OpenRead(sourcePath))
using (var targetStream = File.OpenRead(targetPath))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

### Problema #3: Ignorar excepciones
**Solución:** Implementa bloques try‑catch completos y registra trazas de pila.

```csharp
try
{
    using (Comparer comparer = new Comparer(sourcePath))
    {
        comparer.Add(targetPath);
        comparer.Compare(outputPath);
    }
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Document not found: {ex.FileName}");
}
catch (UnauthorizedAccessException ex)
{
    Console.WriteLine($"Access denied: {ex.Message}");
}
catch (Exception ex)
{
    Console.WriteLine($"Comparison failed: {ex.Message}");
}
```

## Estrategias de optimización de rendimiento

### Gestión de memoria
Reutiliza instancias de `Comparer` cuando sea posible y llama a `Dispose()` después de cada comparación.

```csharp
// Always dispose of resources properly
using (var comparer = new Comparer(sourcePath))
{
    comparer.Add(targetPath);
    comparer.Compare(outputPath);
    
    // Comparer is automatically disposed here
}

// For batch processing, clear resources between comparisons
for (int i = 0; i < documentPairs.Count; i++)
{
    using (var comparer = new Comparer(documentPairs[i].Source))
    {
        comparer.Add(documentPairs[i].Target);
        comparer.Compare(documentPairs[i].Output);
    }
    
    // Force garbage collection every 10 documents if needed
    if (i % 10 == 0)
    {
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

### Procesamiento asíncrono
Ejecuta comparaciones en hilos en segundo plano para mantener la UI responsiva.

```csharp
public async Task<bool> CompareDocumentsAsync(string sourcePath, string targetPath, string outputPath)
{
    return await Task.Run(() =>
    {
        try
        {
            using (var comparer = new Comparer(sourcePath))
            {
                comparer.Add(targetPath);
                comparer.Compare(outputPath);
                return true;
            }
        }
        catch
        {
            return false;
        }
    });
}
```

## Integración con frameworks .NET populares

### Integración de API Web ASP.NET Core
Expón un endpoint REST que acepte dos archivos y devuelva el resultado de la diferencia.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentComparisonController : ControllerBase
{
    [HttpPost("compare")]
    public async Task<IActionResult> CompareDocuments([FromForm] IFormFile sourceFile, [FromForm] IFormFile targetFile)
    {
        if (sourceFile == null || targetFile == null)
            return BadRequest("Both source and target files are required.");

        var tempFolder = Path.GetTempPath();
        var sourcePath = Path.Combine(tempFolder, sourceFile.FileName);
        var targetPath = Path.Combine(tempFolder, targetFile.FileName);
        var outputPath = Path.Combine(tempFolder, $"comparison_{Guid.NewGuid()}.pdf");

        try
        {
            // Save uploaded files
            using (var stream = new FileStream(sourcePath, FileMode.Create))
                await sourceFile.CopyToAsync(stream);
            
            using (var stream = new FileStream(targetPath, FileMode.Create))
                await targetFile.CopyToAsync(stream);

            // Perform comparison
            using (var comparer = new Comparer(sourcePath))
            {
                comparer.Add(targetPath);
                comparer.Compare(outputPath);
            }

            // Return the result file
            var fileBytes = await System.IO.File.ReadAllBytesAsync(outputPath);
            return File(fileBytes, "application/pdf", "comparison_result.pdf");
        }
        finally
        {
            // Clean up temp files
            File.Delete(sourcePath);
            File.Delete(targetPath);
            File.Delete(outputPath);
        }
    }
}
```

### Integración de componente Blazor
Crea un componente reutilizable que muestre la comparación lado a lado en el navegador.

```csharp
@using GroupDocs.Comparison
@inject IJSRuntime JSRuntime

<div class="document-comparison">
    <InputFile OnChange="HandleFileSelection" multiple />
    <button @onclick="CompareDocuments" disabled="@(!CanCompare)">Compare Documents</button>
    
    @if (comparisonResult != null)
    {
        <div class="result">
            <a href="@comparisonResult" download="comparison_result.pdf">Download Result</a>
        </div>
    }
</div>

@code {
    private List<IBrowserFile> selectedFiles = new();
    private string comparisonResult;
    
    private bool CanCompare => selectedFiles.Count == 2;

    private async Task HandleFileSelection(InputFileChangeEventArgs e)
    {
        selectedFiles = e.GetMultipleFiles(2).ToList();
    }

    private async Task CompareDocuments()
    {
        if (selectedFiles.Count != 2) return;

        // Implementation similar to Web API example
        // Save files, compare, and generate result
    }
}
```

## Casos de uso del mundo real

### Escenario 1: Revisión de contratos legales
Los despachos legales pueden resaltar automáticamente adiciones, eliminaciones y cambios de formato en revisiones de contratos.

```csharp
public class ContractReviewService
{
    public ContractComparisonResult ReviewContract(string originalContract, string revisedContract)
    {
        var outputPath = Path.Combine(Path.GetTempPath(), $"contract_review_{DateTime.Now:yyyyMMddHHmmss}.docx");
        
        var compareOptions = new CompareOptions
        {
            ShowDeletedContent = true,
            ShowInsertedContent = true,
            StyleChangeDetection = true,
            WordsSeparatorChars = new[] { ' ', '.', ',', '!', '?' }
        };

        using (var comparer = new Comparer(originalContract))
        {
            comparer.Add(revisedContract);
            comparer.Compare(outputPath, compareOptions);
        }

        return new ContractComparisonResult
        {
            OutputPath = outputPath,
            HasChanges = File.Exists(outputPath),
            ComparisonDate = DateTime.Now
        };
    }
}
```

### Escenario 2: Control de versiones para hojas de cálculo
Los equipos financieros pueden detectar cambios en modelos de Excel sin abrir manualmente cada archivo.

```csharp
public class DocumentVersionControl
{
    public void TrackDocumentChanges(string documentPath, string repositoryPath)
    {
        var versions = Directory.GetFiles(repositoryPath, "*.docx").OrderBy(f => f);
        var latestVersion = versions.LastOrDefault();

        if (latestVersion != null)
        {
            var comparisonPath = Path.Combine(repositoryPath, $"changes_{DateTime.Now:yyyyMMdd}.docx");
            
            using (var comparer = new Comparer(latestVersion))
            {
                comparer.Add(documentPath);
                comparer.Compare(comparisonPath);
            }

            // Archive the comparison for future reference
            ArchiveComparison(comparisonPath);
        }
    }

    private void ArchiveComparison(string comparisonPath)
    {
        // Implementation for archiving comparison results
        var archivePath = Path.Combine(Path.GetDirectoryName(comparisonPath), "archive", Path.GetFileName(comparisonPath));
        Directory.CreateDirectory(Path.GetDirectoryName(archivePath));
        File.Move(comparisonPath, archivePath);
    }
}
```

## Guía de solución de problemas

### Problema 1: “Formato de archivo no soportado”
**Solución:** Verifica la extensión del archivo contra la lista de formatos soportados (más de 50) y convierte los tipos no soportados a PDF primero.

```csharp
private static readonly HashSet<string> SupportedFormats = new HashSet<string>(StringComparer.OrdinalIgnoreCase)
{
    ".docx", ".doc", ".pdf", ".xlsx", ".xls", ".pptx", ".ppt", ".txt", ".rtf"
};

public static bool IsFormatSupported(string filePath)
{
    var extension = Path.GetExtension(filePath);
    return SupportedFormats.Contains(extension);
}
```

### Problema 2: Problemas de memoria con archivos grandes
**Solución:** Habilita la transmisión y procesa los archivos en fragmentos.

```csharp
public static void CompareLargeDocuments(string sourcePath, string targetPath, string outputPath)
{
    var fileInfo = new FileInfo(sourcePath);
    
    if (fileInfo.Length > 50 * 1024 * 1024) // 50MB threshold
    {
        // Use streaming approach
        using (var sourceStream = File.OpenRead(sourcePath))
        using (var targetStream = File.OpenRead(targetPath))
        using (var outputStream = File.Create(outputPath))
        using (var comparer = new Comparer(sourceStream))
        {
            comparer.Add(targetStream);
            comparer.Compare(outputStream);
        }
    }
    else
    {
        // Standard approach for smaller files
        using (var comparer = new Comparer(sourcePath))
        {
            comparer.Add(targetPath);
            comparer.Compare(outputPath);
        }
    }
}
```

### Problema 3: Resultado de comparación vacío
**Solución:** Aumenta la sensibilidad activando `DetectFormattingChanges` o `DetectStyleChanges`.

```csharp
var compareOptions = new CompareOptions
{
    DetectStyleChanges = true,
    DiagramMasterSetting = new DiagramMasterSetting
    {
        UseSourceMaster = true,
        CloneSourceMaster = true
    },
    OriginalSize = new Size(600, 800),
    HeaderFootersComparison = true,
    PaperSize = PaperSize.A4
};
```

## Preguntas frecuentes

**P: ¿Cuántos documentos puedo comparar a la vez?**  
R: Puedes agregar varios documentos objetivo a una única instancia de `Comparer` usando llamadas repetidas a `Add()`, pero se recomienda procesarlos secuencialmente para lotes grandes.

**P: ¿Puede GroupDocs.Comparison manejar archivos protegidos con contraseña?**  
R: Sí—pasa la contraseña al crear el `Comparer` o al cargar el documento.

```csharp
using (var comparer = new Comparer(sourcePath, new LoadOptions("password")))
{
    comparer.Add(targetPath, new LoadOptions("targetPassword"));
    comparer.Compare(outputPath);
}
```

**P: ¿Qué formatos de archivo soporta GroupDocs.Comparison?**  
R: Más de 50 formatos, incluidos DOCX, XLSX, PPTX, PDF, JPEG, PNG, TXT, y más.

**P: ¿Cómo personalizo la apariencia de los cambios?**  
R: Utiliza `ComparisonSettings` para establecer `InsertedColor`, `DeletedColor` y `StyleChangeColor`.

```csharp
var compareOptions = new CompareOptions
{
    InsertedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Green,
        FontColor = Color.DarkGreen
    },
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

**P: ¿Es posible ignorar tipos específicos de cambios?**  
R: Absolutamente—desactiva opciones como `DetectStyleChanges` o `DetectTableChanges` en `ComparisonSettings`.

```csharp
var compareOptions = new CompareOptions
{
    DetectStyleChanges = false, // Ignore formatting changes
    HeaderFootersComparison = false, // Skip headers/footers
    WordsSeparatorChars = new[] { ' ', '\n', '\r', '\t' } // Define word boundaries
};
```

**P: ¿Puedo comparar documentos almacenados en la nube?**  
R: Sí—descarga los streams localmente o compara directamente desde un `MemoryStream`.

```csharp
using (var sourceStream = await DownloadFromCloudAsync(sourceUrl))
using (var targetStream = await DownloadFromCloudAsync(targetUrl))
using (var comparer = new Comparer(sourceStream))
{
    comparer.Add(targetStream);
    comparer.Compare(outputStream);
}
```

**P: ¿Cómo ejecuto GroupDocs.Comparison dentro de un contenedor Docker?**  
R: Incluye las dependencias nativas necesarias en tu Dockerfile y copia el archivo de licencia dentro del contenedor.

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:6.0
# Install necessary fonts and libraries for document processing
RUN apt-get update && apt-get install -y libfontconfig1 libfreetype6
```

**P: ¿Qué licencia se requiere para producción?**  
R: Se requiere una licencia comercial de GroupDocs.Comparison para implementaciones en producción. Las opciones incluyen licencias de desarrollador, sitio y OEM.

**P: ¿Cómo debo manejar fallas de comparación de forma elegante?**  
R: Envuelve la llamada de comparación en un bloque try‑catch, registra la excepción y devuelve un mensaje de error amigable para el usuario.

```csharp
public async Task<ComparisonResult> CompareDocumentsWithRetry(string source, string target, int maxRetries = 3)
{
    for (int attempt = 1; attempt <= maxRetries; attempt++)
    {
        try
        {
            using (var comparer = new Comparer(source))
            {
                comparer.Add(target);
                var outputPath = GenerateOutputPath();
                comparer.Compare(outputPath);
                
                return new ComparisonResult { Success = true, OutputPath = outputPath };
            }
        }
        catch (Exception ex) when (attempt < maxRetries)
        {
            _logger.LogWarning($"Comparison attempt {attempt} failed: {ex.Message}. Retrying...");
            await Task.Delay(TimeSpan.FromSeconds(attempt * 2)); // Exponential backoff
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, $"Comparison failed after {maxRetries} attempts");
            return new ComparisonResult { Success = false, Error = ex.Message };
        }
    }
    
    return new ComparisonResult { Success = false, Error = "Max retries exceeded" };
}
```

## Recursos y documentación esenciales
- **Documentación completa:** [GroupDocs Comparison .NET Docs](https://docs.groupdocs.com/comparison/net/)
- **Guía de referencia API:** [GroupDocs API Reference for .NET](https://reference.groupdocs.com/comparison/net/)
- **Foro de soporte de la comunidad:** [GroupDocs Forum](https://forum.groupdocs.com/c/comparison/)
- **Descargas de la última versión:** [Releases Page](https://releases.groupdocs.com/comparison/net/)
- **Descarga de prueba gratuita:** [Try Free Version](https://releases.groupdocs.com/comparison/net/)
- **Solicitud de licencia temporal:** [Apply for Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Comprar licencia completa:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)
- **Versiones:** [Releases](https://releases.groupdocs.com/comparison/net/)
- **Página de licencia temporal:** [Temporary License Page](https://purchase.groupdocs.com/temporary-license/)
- **Página de compra:** [Purchase Page](https://purchase.groupdocs.com/buy)

**Última actualización:** 2026-06-10  
**Probado con:** GroupDocs.Comparison 25.4.0 for .NET  
**Autor:** GroupDocs

```plaintext
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
using GroupDocs.Comparison;
```

## Tutoriales relacionados
- [GroupDocs Comparison .NET Quick Start - Guía completa de configuración](/comparison/net/quick-start/)
- [GroupDocs Comparison .NET License Setup - Guía completa de FileStream](/comparison/net/licensing-configuration/set-license-file-stream-groupdocs-comparison-dotnet/)
- [Document Comparison Options .NET - Guía completa de configuración](/comparison/net/comparison-options/)