---
categories:
- Image Processing
date: '2026-05-31'
description: Aprenda a comparar imágenes en .NET usando GroupDocs.Comparison mientras
  desactiva la página de resumen. Este tutorial cubre la configuración, el código,
  consejos de rendimiento y casos de uso reales.
keywords:
- how to compare images
- compare two images
- optimize image comparison
- compare images c#
- automated image testing
- disable summary page
lastmod: '2026-05-31'
linktitle: Comparar imágenes .NET sin resumen
schemas:
- author: GroupDocs
  dateModified: '2026-05-31'
  description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  headline: How to Compare Images in .NET – Skip Summary Page
  type: TechArticle
- description: Learn how to compare images in .NET using GroupDocs.Comparison while
    disabling the summary page. This tutorial covers setup, code, performance tips,
    and real‑world use cases.
  name: How to Compare Images in .NET – Skip Summary Page
  steps:
  - name: Initialize the Comparer Object
    text: The `Comparer` class is the gateway to all comparison operations. It implements
      `IDisposable`, so wrapping it in a `using` block guarantees that file handles
      and unmanaged memory are released promptly, even if an exception is thrown.
  - name: Configure CompareOptions for No Summary
    text: Set `GenerateSummaryPage = false` on the `CompareOptions` instance. This
      flag tells the engine to skip the creation of the default HTML report, which
      is the primary source of extra I/O in image‑only scenarios.
  - name: Add Target Image(s) for Comparison
    text: You can call `Add()` multiple times to compare one source against several
      targets in a single batch. Each call can receive its own `CompareOptions` if
      you need per‑image customizations.
  - name: Execute Comparison and Save Results
    text: '`Comparer.Compare()` performs the heavy lifting and returns a `ComparisonResult`.
      The result contains a `Stream` with the diff image, which you can save directly
      to disk, send over a network, or embed in a UI component.'
  type: HowTo
- questions:
  - answer: It cuts processing time by up to 30 % and reduces disk usage by roughly
      70 % for image‑only comparisons, which is critical for high‑throughput pipelines.
    question: What is the main advantage of skipping the summary page?
  - answer: Yes. The `ComparisonResult` object exposes a `Changes` collection that
      contains programmatic information about each detected difference.
    question: Can I still retrieve detailed change metadata without a summary page?
  - answer: JPEG, PNG, BMP, TIFF, GIF, and several others—over 50 formats in total.
    question: Which image formats are supported?
  - answer: Process them in smaller batches, optionally down‑scale them, and monitor
      memory usage. Using `Comparer` in a `using` block ensures resources are released
      promptly.
    question: How should I handle very large images (e.g., >20 MB)?
  - answer: Yes, as long as each thread creates its own `Comparer` instance. Sharing
      a single instance can lead to race conditions.
    question: Is this approach safe for multi‑threaded applications?
  type: FAQPage
tags:
- dotnet
- image-comparison
- groupdocs
- csharp
title: Cómo comparar imágenes en .NET – Omitir página de resumen
type: docs
url: /es/net/basic-comparison/compare-images-without-summary-page-groupdocs-net/
weight: 1
---

# Cómo comparar imágenes en .NET – Omitir página de resumen

Cuando necesitas **how to compare images** programáticamente en una aplicación .NET, lo último que deseas es una página de resumen adicional que pierda tiempo y espacio de almacenamiento. Ya sea que estés construyendo una línea de control de calidad, una canalización de gestión de contenido, o una suite de pruebas de regresión visual automatizada, omitir la página de resumen puede ahorrar segundos en cada ejecución y mantener tu huella de disco ligera.

En este tutorial aprenderás a usar **GroupDocs.Comparison for .NET** para comparar dos imágenes de manera eficiente, configurar la biblioteca para suprimir la generación del resumen y aplicar trucos de rendimiento de mejores prácticas. También exploraremos por qué esto es importante, cuándo usarlo y cómo evitar errores comunes.

## Respuestas rápidas
- **¿Cuál es la forma más rápida de comparar imágenes sin una página de resumen?** Use `Comparer` with `CompareOptions` and set `GenerateSummaryPage = false`.  
- **¿Qué biblioteca admite esto directamente?** GroupDocs.Comparison for .NET (v25.4.0+).  
- **¿Necesito una licencia?** Yes, a commercial license is required for production; a free trial works for development.  
- **¿Puedo comparar más de dos imágenes a la vez?** Absolutely – call `Add()` multiple times before `Compare()`.  
- **¿Es este enfoque adecuado para trabajos por lotes a gran escala?** Yes, when combined with batch processing and proper memory handling.

## Qué es GroupDocs.Comparison?
`GroupDocs.Comparison` es una biblioteca .NET que detecta diferencias visuales entre documentos e imágenes, produciendo resultados lado a lado o superpuestos. Soporta **50+ input and output formats**, incluyendo JPEG, PNG, BMP, TIFF y GIF, y puede procesar archivos de cientos de páginas sin cargar todo el archivo en memoria.

## Por qué omitir la página de resumen?
Desactivar la página de resumen reduce I/O hasta en **70 %** para comparaciones solo de imágenes y reduce el tiempo de procesamiento aproximadamente un **30 %** en promedio, según el conjunto de pruebas de referencia de la biblioteca. Cuando solo necesitas la imagen de diferencia (para pruebas automatizadas o decisiones de paso/fallo de control de calidad), el informe HTML adicional no aporta valor y solo consume espacio en disco.

## Requisitos previos y configuración del entorno

### Lo que necesitarás
- **GroupDocs.Comparison for .NET** versión **25.4.0** o más reciente  
- Visual Studio 2019 + o cualquier IDE compatible con .NET  
- .NET Framework 4.6.1 + **or** .NET Core 2.0 +  
- Conocimientos básicos de C# y familiaridad con I/O de archivos  

### Extras recomendados
- Un pequeño proyecto de prueba que contenga un par de imágenes de ejemplo (p. ej., `source.png` y `target.png`).  
- Opcional: configuración de inyección de dependencias si prefieres una arquitectura orientada a servicios.  

### Por qué estos requisitos son importantes
La versión de biblioteca especificada incluye la bandera `GenerateSummaryPage` y mejoras de rendimiento que las versiones anteriores no tienen. Usar un IDE moderno garantiza que puedas aprovechar la gestión de paquetes NuGet y ver advertencias de compilación temprano.

## Cómo instalar GroupDocs.Comparison
GroupDocs.Comparison se puede añadir a cualquier proyecto .NET mediante NuGet, que se encarga de descargar los binarios y actualizar el archivo del proyecto. Elige el método que coincida con tu flujo de trabajo: la consola del Administrador de paquetes para usuarios de Visual Studio o la CLI de .NET para entornos de línea de comandos. Ambos comandos resuelven automáticamente las dependencias y garantizan que se haga referencia a la versión correcta.

```text
Install-Package GroupDocs.Comparison -Version 25.4.0
```
*(Reemplaza `25.4.0` con la versión exacta que planeas bloquear.)*

```text
dotnet add package GroupDocs.Comparison --version 25.4.0
```

Ambos comandos añaden la biblioteca a tu archivo de proyecto y restauran los binarios necesarios.

**Pro Tip:** Fija la versión en tu `.csproj` para evitar actualizaciones accidentales que puedan cambiar el comportamiento de la API.

## Consideraciones de licencia
GroupDocs.Comparison requiere una licencia para cualquier despliegue en producción. Puedes comenzar con una **free trial** que brinda funcionalidad completa, luego actualizar a una **temporary license** para pruebas extendidas, y finalmente a una **full commercial license** para producción. Recuerda colocar el archivo `GroupDocs.Comparison.lic` en la raíz de la aplicación o especificar su ruta programáticamente.

## Configuración básica del proyecto
Crea una nueva aplicación de consola (o intégrala en un servicio existente) y añade el siguiente código base. Este fragmento muestra la configuración mínima requerida antes de sumergirte en la lógica de comparación.

```csharp
using System;
using System.IO;
using GroupDocs.Comparison;

// Define directory paths for input images and output results
string documentDirectory = "YOUR_DOCUMENT_DIRECTORY";
string outputDirectory = "YOUR_OUTPUT_DIRECTORY";

// Initialize paths to your source and target images
string sourceImagePath = Path.Combine(documentDirectory, "sourceImage.jpg");
string targetImagePath = Path.Combine(documentDirectory, "targetImage.jpg");

// Output image path for comparison result
string resultImagePath = Path.Combine(outputDirectory, "resultImage.jpg");
```

> **Important:** Siempre usa `Path.Combine()` para rutas de archivo. Maneja automáticamente los separadores de ruta específicos del SO y evita errores sutiles al mover entre contenedores Windows y Linux.

## Guía de implementación paso a paso

### ¿Cómo comparar imágenes sin una página de resumen?
`Comparer` es la clase principal en GroupDocs.Comparison que orquesta las operaciones de comparación de documentos e imágenes. `CompareOptions` contiene la configuración que controla cómo se realiza la comparación, como si se debe generar una página de resumen. Carga la imagen de origen, configura `CompareOptions` para desactivar el resumen, añade la imagen objetivo y llama a `Compare()`. El método devuelve un `ComparisonResult` que contiene el flujo de la imagen de diferencia, que puedes escribir en disco, enviar por red o incrustar en un componente UI. Este enfoque garantiza que solo se produzca la diferencia esencial, eliminando cualquier informe HTML o PDF adicional.

```csharp
using (Comparer comparer = new Comparer())
{
    // Load source image
    comparer.Add(sourcePath);

    // Configure options – this is where we turn off the summary page
    CompareOptions options = new CompareOptions
    {
        GenerateSummaryPage = false,
        // You can also tweak sensitivity here if needed
        Sensitivity = 0.5
    };

    // Add the target image for comparison
    comparer.Add(targetPath, options);

    // Execute comparison and retrieve the result image stream
    ComparisonResult result = comparer.Compare();

    // Save the diff image
    using (FileStream outStream = new FileStream(outputPath, FileMode.Create))
    {
        result.Save(outStream);
    }
}
```

El código anterior realiza toda la comparación en **cuatro pasos lógicos** y escribe solo la imagen de diferencia, omitiendo cualquier resumen HTML o PDF.

### Paso 1: Inicializar el objeto Comparer
La clase `Comparer` es la puerta de entrada a todas las operaciones de comparación. Implementa `IDisposable`, por lo que envolverla en un bloque `using` garantiza que los manejadores de archivos y la memoria no administrada se liberen rápidamente, incluso si se lanza una excepción.

### Paso 2: Configurar CompareOptions para sin resumen
Establece `GenerateSummaryPage = false` en la instancia de `CompareOptions`. Esta bandera indica al motor que omita la creación del informe HTML predeterminado, que es la principal fuente de I/O adicional en escenarios solo de imágenes.

### Paso 3: Añadir imagen(es) objetivo para la comparación
Puedes llamar a `Add()` varias veces para comparar una fuente contra varios objetivos en un solo lote. Cada llamada puede recibir su propio `CompareOptions` si necesitas personalizaciones por imagen.

### Paso 4: Ejecutar la comparación y guardar los resultados
`Comparer.Compare()` realiza el trabajo pesado y devuelve un `ComparisonResult`. El resultado contiene un `Stream` con la imagen de diferencia, que puedes guardar directamente en disco, enviar por red o incrustar en un componente UI.

## Método completo listo para producción
A continuación se muestra un método listo para usar que puedes insertar en cualquier servicio .NET. Incluye validación de rutas, manejo de excepciones y ganchos de registro opcionales.

```csharp
public static void CompareImagesWithoutSummary(string sourcePath, string targetPath, string outputPath)
{
    try
    {
        using (Comparer comparer = new Comparer(sourcePath))
        {
            // Configure options to skip summary generation
            CompareOptions options = new CompareOptions
            {
                GenerateSummaryPage = false
            };
            
            // Add target image and execute comparison
            comparer.Add(targetPath);
            comparer.Compare(outputPath, options);
            
            Console.WriteLine($"Comparison completed successfully. Result saved to: {outputPath}");
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Error during image comparison: {ex.Message}");
        throw; // Re-throw for proper error handling upstream
    }
}
```

## Errores comunes de implementación (y cómo evitarlos)

- **Path Issues:** Siempre verifica que los archivos de origen y destino existan con `File.Exists()`. Un archivo faltante lanzará una `FileNotFoundException` que puede ser capturada temprano.  
- **Memory Pressure:** Las imágenes grandes (10 MB +) pueden consumir RAM significativa. Procésalas en lotes y considera reducir la escala si no se requiere precisión de píxel.  
- **File Locks:** Asegúrate de que ningún otro proceso mantenga un bloqueo exclusivo sobre los archivos de imagen. Esto es especialmente importante en entornos multihilo o contenedorizados.

## Aplicaciones prácticas y casos de uso

### Control de calidad en fabricación
Una línea de producción captura imágenes de cada artículo y las compara con una referencia de referencia. Omitir la página de resumen permite al sistema decidir “aprobado” o “rechazado” en milisegundos, manteniendo la línea en movimiento a alta velocidad.

### Sistemas de gestión de contenido
Cuando los usuarios suben recursos, el CMS puede detectar instantáneamente duplicados o casi duplicados, evitando el aumento de almacenamiento y mejorando la relevancia de búsqueda. La imagen de diferencia puede almacenarse como miniatura para una inspección visual rápida.

### Pruebas UI automatizadas (Regresión visual)
Selenium o Playwright pueden capturar capturas de pantalla de una página web, luego alimentarlas a esta rutina de comparación. La imagen de diferencia resalta cambios en la UI, y al no generarse un resumen, la canalización CI sigue siendo rápida y ligera.

### Imágenes médicas (con auditoría)
Los flujos de trabajo de radiología a veces necesitan marcar cambios entre escaneos sucesivos. Aunque aún puedes generar un registro de auditoría detallado, la propia imagen de diferencia puede producirse sin una página de resumen, reduciendo el tiempo de procesamiento para grandes PNG convertidos de DICOM.

## Consideraciones de rendimiento y optimización

### Mejores prácticas de gestión de memoria
Procesa imágenes en **lotes de 20–50** según la RAM del servidor. Libera cada instancia de `Comparer` rápidamente e invoca `GC.Collect()` solo si notas picos de memoria durante trabajos de larga duración.

```csharp
foreach (var batch in imageBatches)
{
    using (Comparer comparer = new Comparer())
    {
        // batch processing logic here
    }
}
```

### Optimización de I/O de disco
Coloca tus directorios de entrada, salida y temporales en el mismo volumen SSD rápido. Elimina los archivos temporales inmediatamente después de guardar la imagen de diferencia para evitar uso innecesario de disco.

### Consideraciones de subprocesamiento y async
GroupDocs.Comparison es seguro para subprocesos en operaciones de solo lectura, pero evita compartir una única instancia de `Comparer` entre hilos. En su lugar, crea tareas independientes:

```csharp
var tasks = images.Select(pair => Task.Run(() => ComparePair(pair)));
await Task.WhenAll(tasks);
```

## Solución de problemas comunes

### Errores de ruta de archivo y permisos
- **Symptom:** `FileNotFoundException` or `UnauthorizedAccessException`.  
- **Solution:** Usa `Path.GetFullPath()` para depurar la ruta resuelta, asegura que la identidad del pool de aplicaciones (o el usuario del contenedor Docker) tenga derechos de lectura/escritura, y verifica que la ruta no esté truncada por variables de entorno.

### Cuellos de botella de memoria y rendimiento
- **Symptom:** Slow runs or `OutOfMemoryException`.  
- **Solution:** Redimensiona las imágenes a una resolución común (p. ej., 1024 × 768) cuando no se requiera una comparación de píxeles exacta. Monitorea la memoria con herramientas como dotMemory o el Profilador de Rendimiento incorporado.

### Problemas de licencia
- **Symptom:** Watermarked diff image or `LicenseException`.  
- **Solution:** Confirma que `GroupDocs.Comparison.lic` está ubicado en el directorio ejecutable o cárgalo explícitamente mediante `License license = new License(); license.SetLicense("path/to/license.file");`.

## Opciones de configuración avanzadas

### Personalizar la sensibilidad de comparación
Puedes afinar cómo el motor trata variaciones menores de píxeles (p. ej., artefactos de compresión) ajustando la propiedad `Sensitivity` en `CompareOptions`. Valores más bajos hacen la comparación más estricta.

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    DetectStyleChanges = false,  // Focus on content changes only
    DetalisationLevel = DetalisationLevel.Low  // Faster processing
};
```

### Optimización del formato de salida
Si necesitas la imagen de diferencia en un formato específico (PNG vs. JPEG), establece la propiedad `OutputFormat`:

```csharp
options.OutputFormat = ImageSaveOptions.SaveFormat.Png;
```

```csharp
CompareOptions options = new CompareOptions
{
    GenerateSummaryPage = false,
    ShowDeletedContent = true,
    ShowInsertedContent = true,
    // Customize highlighting colors if needed
    DeletedItemStyle = new StyleSettings
    {
        HighlightColor = Color.Red,
        FontColor = Color.DarkRed
    }
};
```

## Integración con frameworks .NET populares

### Ejemplo de servicio ASP.NET Core
Expón un endpoint HTTP ligero que acepte dos flujos de imagen, ejecute la comparación y devuelva la imagen de diferencia como un `FileResult`.

```csharp
public interface IImageComparisonService
{
    Task<string> CompareImagesAsync(string sourceImage, string targetImage);
}

public class ImageComparisonService : IImageComparisonService
{
    private readonly ILogger<ImageComparisonService> _logger;
    private readonly string _outputDirectory;

    public ImageComparisonService(ILogger<ImageComparisonService> logger, IConfiguration config)
    {
        _logger = logger;
        _outputDirectory = config.GetValue<string>("ImageComparison:OutputDirectory");
    }

    public async Task<string> CompareImagesAsync(string sourceImage, string targetImage)
    {
        // Your implementation here
        return await Task.FromResult("comparisonResult.jpg");
    }
}
```

### Registro de inyección de dependencias
Añade el comparador como un servicio scoped en `Program.cs` o `Startup.cs`:

```csharp
services.AddScoped<IImageComparisonService, ImageComparisonService>();
```

## Preguntas frecuentes

**Q: ¿Cuál es la principal ventaja de omitir la página de resumen?**  
A: Reduce el tiempo de procesamiento hasta un 30 % y disminuye el uso de disco aproximadamente un 70 % para comparaciones solo de imágenes, lo cual es crítico para canalizaciones de alto rendimiento.

**Q: ¿Puedo seguir obteniendo metadatos detallados de cambios sin una página de resumen?**  
A: Sí. El objeto `ComparisonResult` expone una colección `Changes` que contiene información programática sobre cada diferencia detectada.

**Q: ¿Qué formatos de imagen son compatibles?**  
A: JPEG, PNG, BMP, TIFF, GIF y varios otros—más de 50 formatos en total.

**Q: ¿Cómo debo manejar imágenes muy grandes (p. ej., >20 MB)?**  
A: Procésalas en lotes más pequeños, opcionalmente redúcelas y monitorea el uso de memoria. Usar `Comparer` en un bloque `using` garantiza que los recursos se liberen rápidamente.

**Q: ¿Es este enfoque seguro para aplicaciones multihilo?**  
A: Sí, siempre que cada hilo cree su propia instancia de `Comparer`. Compartir una única instancia puede provocar condiciones de carrera.

## Recursos adicionales
- [Documentación de GroupDocs.Comparison](https://docs.groupdocs.com/comparison/net/)
- [Referencia de API](https://reference.groupdocs.com/comparison/net/)
- [Descargar](https://releases.groupdocs.com/comparison/net/)
- [Comprar](https://purchase.groupdocs.com/buy)
- [Prueba gratuita](https://releases.groupdocs.com/comparison/net/)
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/)
- [Foro de soporte](https://forum.groupdocs.com/c/comparison/)

---

**Última actualización:** 2026-05-31  
**Probado con:** GroupDocs.Comparison 25.4.0 for .NET  
**Autor:** GroupDocs

```bash
Install-Package GroupDocs.Comparison -Version 25.4.0
```

```bash
dotnet add package GroupDocs.Comparison --version 25.4.0
```

```csharp
// Create a Comparer object with the source image path
using (Comparer comparer = new Comparer(sourceImagePath))
{
    // Configuration will follow in subsequent steps
}
```

```csharp
// Set up compare options to avoid generating a summary page
CompareOptions options = new CompareOptions();
options.GenerateSummaryPage = false;
```

```csharp
// Add the target image to the comparison
comparer.Add(targetImagePath);
```

```csharp
// Execute comparison with configured options and save to result path
comparer.Compare(resultImagePath, options);
```

```csharp
public static void ProcessImageBatch(List<string> imagePairs, int batchSize = 10)
{
    for (int i = 0; i < imagePairs.Count; i += batchSize)
    {
        var batch = imagePairs.Skip(i).Take(batchSize);
        // Process batch and allow garbage collection between batches
        foreach (var pair in batch)
        {
            // Your comparison logic here
        }
        
        // Explicit garbage collection after each batch (use sparingly)
        GC.Collect();
        GC.WaitForPendingFinalizers();
    }
}
```

```csharp
public static async Task<bool> CompareImagesAsync(string source, string target, string output)
{
    return await Task.Run(() =>
    {
        try
        {
            CompareImagesWithoutSummary(source, target, output);
            return true;
        }
        catch
        {
            return false;
        }
    });
}
```

## Tutoriales relacionados
- [Comparación de imágenes .NET - Comparar imágenes programáticamente](/comparison/net/image-comparison/compare-images-from-path/)
- [Comparación de imágenes .NET - Comparar imágenes desde Stream](/comparison/net/image-comparison/compare-images-from-stream/)
- [Tutorial de GroupDocs Comparison .NET - Guía completa de uso básico](/comparison/net/basic-usage/)