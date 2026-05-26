---
categories:
- Java Development
date: '2026-05-26'
description: Aprenda cómo crear una vista previa de PDF en Java usando GroupDocs.Comparison.
  Tutorial paso a paso con ejemplos de código para vistas previas de PDF, Word y Excel.
keywords:
- create pdf preview java
- java document preview generator
- pdf thumbnail generation java
- document image conversion java
lastmod: '2025-01-02'
linktitle: Generador de vista previa de documentos Java
schemas:
- author: GroupDocs
  dateModified: '2026-05-26'
  description: Learn how to create pdf preview java using GroupDocs.Comparison. Step-by-step
    tutorial with code examples for PDF, Word, Excel previews.
  headline: Create PDF Preview Java – Java Document Preview Generator
  type: TechArticle
- questions:
  - answer: GroupDocs.Comparison provides a simple API for high‑quality previews.
    question: What library can I use to create PDF previews in Java?
  - answer: Over 50 formats including PDF, DOCX, XLSX, PPTX, and more.
    question: Which formats are supported?
  - answer: Set `previewOptions.setPageNumbers(new int[]{1})`.
    question: How do I generate a preview for only the first page?
  - answer: Yes—use `ExecutorService` or `CompletableFuture`.
    question: Can I run preview generation asynchronously?
  - answer: PNG offers the best quality; JPEG is smaller for web use.
    question: What’s the best image format for thumbnails?
  type: FAQPage
tags:
- document-processing
- java-library
- preview-generation
- pdf-thumbnails
title: Crear vista previa de PDF en Java – Generador de vista previa de documentos
  Java
type: docs
url: /es/java/preview-generation/groupdocs-comparison-java-generate-previews/
weight: 1
---

# Crear vista previa de PDF Java – Generador de vista previa de documentos Java

Generar miniaturas visuales de documentos mejora drásticamente la usabilidad de cualquier aplicación de manejo de archivos basada en Java. En este tutorial crearás **pdf preview java** con GroupDocs.Comparison, desde la preparación del entorno hasta la afinación avanzada del rendimiento. Al final tendrás un generador de vistas previas listo para producción que admite más de 50 formatos de archivo y puede ejecutarse de forma segura con PDFs grandes.

## Respuestas rápidas
- **¿Qué biblioteca puedo usar para crear vistas previas de PDF en Java?** GroupDocs.Comparison proporciona una API sencilla para vistas previas de alta calidad.  
- **¿Qué formatos son compatibles?** Más de 50 formatos, incluidos PDF, DOCX, XLSX, PPTX y más.  
- **¿Cómo genero una vista previa solo de la primera página?** Set `previewOptions.setPageNumbers(new int[]{1})`.  
- **¿Puedo ejecutar la generación de vistas previas de forma asíncrona?** Sí—use `ExecutorService` o `CompletableFuture`.  
- **¿Cuál es el mejor formato de imagen para miniaturas?** PNG ofrece la mejor calidad; JPEG es más pequeño para uso web.

## ¿Qué es “create pdf preview java”?

Crear una vista previa de PDF en Java significa convertir cada página de un PDF (o cualquier documento compatible) en una imagen que pueda mostrarse en navegadores o aplicaciones móviles. Esta conversión—a menudo llamada **java convert document to image**—permite a los usuarios explorar grandes colecciones sin abrir los archivos completos, ahorrando ancho de banda y mejorando los tiempos de respuesta.

## ¿Por qué usar un generador de vista previa de documentos Java?

Generar vistas previas en el lado del servidor elimina la necesidad de bibliotecas de renderizado de PDF del lado del cliente y garantiza una experiencia visual uniforme en todos los dispositivos. Acelera la navegación de documentos, reduce el consumo de ancho de banda y simplifica la integración, lo que lo hace ideal para la gestión de documentos, el comercio electrónico y plataformas de colaboración.

- **Velocidad:** La generación de miniaturas suele ser de 5‑10× más rápida que cargar PDFs completos.  
- **Escalabilidad:** GroupDocs.Comparison puede procesar documentos de 200 páginas sin cargar todo el archivo en memoria, gracias a su arquitectura de streaming.  
- **Confiabilidad:** Soporta más de 50 formatos de entrada y salida, garantizando que la mayoría de los documentos empresariales estén cubiertos de forma inmediata.

## Requisitos previos y configuración del entorno

Antes de comenzar a construir nuestro generador de vista previa de documentos Java, asegúrese de tener:

**Software requerido**
- **Java Development Kit (JDK)**: Versión 8 o superior (Java 11+ recomendado para mejor rendimiento)
- **Maven o Gradle**: Para la gestión de dependencias
- **IDE**: IntelliJ IDEA, Eclipse o su IDE Java preferido

**Conocimientos básicos**
- Fundamentos de programación Java
- Operaciones de E/S de archivos
- Comprensión básica de conceptos de procesamiento de imágenes

**Requisitos del sistema**
- Mínimo 4 GB de RAM (8 GB recomendados para procesar documentos grandes)
- Espacio en disco suficiente para archivos temporales de vista previa

## Configuración de GroupDocs.Comparison para Java

### Instalación y configuración de Maven

El paquete `Comparison` se entrega a través de Maven Central. Añada esta dependencia a su `pom.xml`:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/comparison/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-comparison</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

**Consejo profesional:** Siempre use la última versión para obtener las funciones más recientes y correcciones de errores. Consulte la [página de lanzamientos de GroupDocs](https://releases.groupdocs.com/comparison/java/) para actualizaciones.

### Configuración de Gradle (alternativa)

Si prefiere Gradle, incluya lo siguiente en su archivo `build.gradle`:

```gradle
repositories {
    maven {
        url "https://releases.groupdocs.com/comparison/java/"
    }
}

dependencies {
    implementation 'com.groupdocs:groupdocs-comparison:25.2'
}
```

### Opciones de configuración de licencia

Tiene varias opciones de licencia para su generador de vista previa de documentos:

**1. Prueba gratuita** (Perfecta para pruebas):
- Descargue desde el sitio web de GroupDocs
- Limitado a 3 páginas por documento
- Salida con marca de agua

**2. Licencia temporal** (Para desarrollo):
- Acceso completo a funciones durante 30 días
- Sin marcas de agua ni limitaciones de páginas
- Ideal para proyectos de prueba de concepto

**3. Licencia comercial** (Uso en producción):
- Documentos y páginas ilimitados
- Soporte prioritario incluido
- Disponibles varios modelos de licencia

### Inicialización básica

El objeto `Comparison` es el punto de entrada para todas las operaciones de vista previa. Inicializarlo correctamente garantiza la seguridad de hilos y un uso óptimo de la memoria.

```java
try (Comparer comparer = new Comparer("YOUR_DOCUMENT_DIRECTORY/source_document.docx")) {
    // Your preview generation code goes here
}
```

**Importante:** Siempre use try‑with‑resources para asegurar la limpieza adecuada de recursos y evitar fugas de memoria.

## Cómo crear pdf preview java – Implementación paso a paso

Cargue su archivo fuente con `Comparison comparison = new Comparison("license.txt");` y llame a `comparison.generatePreview(inputPath, previewOptions);` — esta única llamada maneja la carga del documento, el renderizado de páginas y la creación del flujo de imagen. La API abstrae el análisis de PDF de bajo nivel, permitiéndole centrarse en la lógica de negocio mientras entrega miniaturas PNG o JPEG de alta calidad.

### Comprendiendo el proceso de generación de vistas previas

Antes de sumergirse en el código, comprendamos cómo funciona la generación de vistas previas de documentos:

1. **Carga del documento** – Carga el documento fuente en memoria.  
2. **Procesamiento de página** – Convierte cada página del documento en una imagen.  
3. **Gestión de flujos** – Maneja los flujos de salida para las imágenes generadas.  
4. **Configuración** – Aplica las opciones de vista previa (formato, calidad, páginas).  
5. **Limpieza** – Libera recursos y archivos temporales.

### Paso 1: Configurar opciones de vista previa

El delegado `CreatePageStream` crea un flujo de salida único para cada página. El objeto `previewOptions` le permite especificar el formato de imagen, la resolución y qué páginas renderizar.

```java
import com.groupdocs.comparison.options.PreviewOptions;
import java.io.FileOutputStream;

final Delegates.CreatePageStream createPageStream = pageNumber -> {
    String pagePath = "YOUR_OUTPUT_DIRECTORY/result-GetPagePreviewsForSourceDocument_" + pageNumber + ".png";
    try {
        return new FileOutputStream(pagePath);
    } catch (FileNotFoundException e) {
        e.printStackTrace();
        return null;
    }
};
```

**Qué está sucediendo aquí:**  
- El delegado escribe cada página en un archivo PNG separado llamado `preview_page_{pageNumber}.png`.  
- El formato PNG ofrece calidad sin pérdida, mientras que una resolución de 150 dpi equilibra claridad y tamaño de archivo para la mayoría de los escenarios web.

### Paso 2: Generar vistas previas del documento

`previewOptions` es un objeto que especifica el formato de salida, la resolución y la selección de páginas para el proceso de generación de vistas previas.  Invoque el motor de vista previa con las opciones configuradas. La API iterará sobre las páginas solicitadas, las renderizará y escribirá los resultados en los flujos que proporcionó.

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);
previewOptions.setPageNumbers(new int[]{1, 2, 3}); // Specify desired pages
comparer.getDocument().generatePreview(previewOptions);
```

**Puntos clave**  
- `setPageNumbers()` le permite generar vistas previas solo de páginas específicas, lo cual es crucial para el rendimiento al manejar documentos grandes.  
- Omitir la llamada para generar vistas previas de todas las páginas.

## Opciones avanzadas de configuración

Los entornos de producción a menudo necesitan un control más estricto sobre el tamaño de salida, la profundidad de color y el almacenamiento en caché. El siguiente fragmento muestra cómo ajustar estas configuraciones:

```java
PreviewOptions previewOptions = new PreviewOptions(createPageStream);

// Generate previews for first 5 pages only
previewOptions.setPageNumbers(new int[]{1, 2, 3, 4, 5});

// Set image dimensions (if supported by the format)
// Note: Specific dimension control depends on the output format

// Configure preview format
// PNG: Better quality, larger files
// JPEG: Smaller files, slight quality loss
```

## Desafíos comunes de implementación y soluciones

### Desafío 1: Gestión de memoria con documentos grandes

Los PDFs grandes pueden agotar el heap de la JVM si cada página se mantiene en memoria. Procese los documentos en lotes y deseche cada flujo de página inmediatamente después de escribirlo.

```java
// Process in smaller batches
int batchSize = 5;
int totalPages = getTotalPages(document); // Your method to get page count

for (int i = 1; i <= totalPages; i += batchSize) {
    int endPage = Math.min(i + batchSize - 1, totalPages);
    
    // Generate previews for current batch
    int[] pageNumbers = IntStream.rangeClosed(i, endPage).toArray();
    previewOptions.setPageNumbers(pageNumbers);
    
    comparer.getDocument().generatePreview(previewOptions);
    
    // Optional: Force garbage collection between batches
    System.gc();
}
```

### Desafío 2: Gestión de rutas de archivos y directorios

Los archivos de vista previa dispersos causan dolores de cabeza en el mantenimiento. Use una jerarquía de carpetas determinista basada en el ID del documento y la marca de tiempo.

```java
public class PreviewFileManager {
    private final String baseDirectory;
    private final String documentId;
    
    public PreviewFileManager(String baseDirectory, String documentId) {
        this.baseDirectory = baseDirectory;
        this.documentId = documentId;
        
        // Create directory structure
        Path previewDir = Paths.get(baseDirectory, "previews", documentId);
        try {
            Files.createDirectories(previewDir);
        } catch (IOException e) {
            throw new RuntimeException("Failed to create preview directory", e);
        }
    }
    
    public String getPreviewPath(int pageNumber) {
        return Paths.get(baseDirectory, "previews", documentId, 
                        String.format("page_%03d.png", pageNumber)).toString();
    }
}
```

### Desafío 3: Manejo de diferentes formatos de documento

No todos los formatos se renderizan idénticamente. GroupDocs.Comparison ofrece optimizaciones específicas por formato; por ejemplo, los archivos DOCX se benefician del renderizado vectorial mientras que las imágenes usan conversión raster.

```java
public class DocumentPreviewGenerator {
    
    public void generatePreviews(String filePath) {
        String extension = getFileExtension(filePath).toLowerCase();
        
        switch (extension) {
            case "pdf":
                generatePdfPreviews(filePath);
                break;
            case "docx":
            case "doc":
                generateWordPreviews(filePath);
                break;
            case "xlsx":
            case "xls":
                generateExcelPreviews(filePath);
                break;
            default:
                generateGenericPreviews(filePath);
        }
    }
    
    private void generatePdfPreviews(String filePath) {
        // PDF-specific optimization
        try (Comparer comparer = new Comparer(filePath)) {
            // PDF documents often have many pages
            // Generate previews for first 10 pages only by default
            PreviewOptions options = createPreviewOptions();
            options.setPageNumbers(new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9, 10});
            comparer.getDocument().generatePreview(options);
        }
    }
}
```

## Estrategias de optimización de rendimiento

### Optimización de CPU y memoria

`ExecutorService` es una utilidad de concurrencia de Java que gestiona un pool de hilos de trabajo para la ejecución de tareas en paralelo.  El procesamiento concurrente puede reducir drásticamente el tiempo total de vista previa en servidores multinúcleo. El siguiente ejemplo crea un pool de hilos fijo y procesa las páginas en paralelo.

```java
ExecutorService executor = Executors.newFixedThreadPool(4);

List<Future<Void>> futures = new ArrayList<>();
for (String documentPath : documentPaths) {
    futures.add(executor.submit(() -> {
        generatePreviewsForDocument(documentPath);
        return null;
    }));
}

// Wait for all tasks to complete
for (Future<Void> future : futures) {
    future.get();
}

executor.shutdown();
```

### Estrategia de caché

`Redis` es un almacén de datos en memoria comúnmente usado para el caché rápido de objetos como miniaturas generadas.  Cachee miniaturas generadas previamente en Redis o en un almacén de archivos local. La clave de caché debe combinar el hash del documento, el número de página y el tamaño de imagen solicitado.

```java
public class PreviewCache {
    private final Map<String, List<String>> cache = new ConcurrentHashMap<>();
    
    public List<String> getPreviewPaths(String documentHash) {
        return cache.get(documentHash);
    }
    
    public void cachePreviewPaths(String documentHash, List<String> previewPaths) {
        cache.put(documentHash, previewPaths);
    }
}
```

### Equilibrio entre calidad de imagen y tamaño de archivo

Encontrar el equilibrio adecuado entre calidad de imagen y tamaño de archivo es crucial:

- **Alta calidad (PNG)** – Ideal para documentos técnicos, diagramas.  
- **Tamaño optimizado (JPEG, 80‑85 % de calidad)** – Mejor para miniaturas web.  
- Considere generar múltiples variantes de tamaño (miniatura, mediano, grande) para servir a diferentes dispositivos.

## Aplicaciones prácticas y casos de uso

### Integración con sistemas de gestión documental

Integre el generador de vistas previas en un flujo de trabajo DMS para que cada archivo subido reciba automáticamente una miniatura PNG almacenada junto al original.

```java
@Service
public class DocumentService {
    
    @Autowired
    private PreviewGenerator previewGenerator;
    
    public DocumentPreview uploadDocument(MultipartFile file) {
        // Save document
        String documentPath = saveDocument(file);
        
        // Generate previews asynchronously
        CompletableFuture.runAsync(() -> {
            try {
                previewGenerator.generatePreviews(documentPath);
            } catch (Exception e) {
                log.error("Failed to generate previews for: " + documentPath, e);
            }
        });
        
        return new DocumentPreview(documentPath);
    }
}
```

### Catálogo de productos de comercio electrónico

Para plataformas de comercio electrónico que venden manuales de productos descargables, genere una imagen de vista previa para cada manual y muéstrela en las páginas de producto, mejorando las tasas de conversión.

```java
public class ProductDocumentHandler {
    
    public void processProductDocument(String productId, String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            // Generate thumbnail (first page only for product display)
            PreviewOptions thumbnailOptions = new PreviewOptions(pageNumber -> {
                String thumbnailPath = String.format("products/%s/thumbnail.png", productId);
                return createOutputStream(thumbnailPath);
            });
            thumbnailOptions.setPageNumbers(new int[]{1});
            
            comparer.getDocument().generatePreview(thumbnailOptions);
            
            // Generate detailed previews for product page
            PreviewOptions detailOptions = new PreviewOptions(pageNumber -> {
                String detailPath = String.format("products/%s/page_%d.png", productId, pageNumber);
                return createOutputStream(detailPath);
            });
            
            comparer.getDocument().generatePreview(detailOptions);
        }
    }
}
```

## Mejores prácticas para despliegue en producción

### Manejo de errores y registro

Implemente un manejo integral de errores para capturar problemas de licencia, formatos no compatibles y fallos de E/S. Registre cada excepción con un ID de correlación único para facilitar la solución de problemas.

```java
public class RobustPreviewGenerator {
    private static final Logger logger = LoggerFactory.getLogger(RobustPreviewGenerator.class);
    
    public boolean generatePreview(String documentPath) {
        try (Comparer comparer = new Comparer(documentPath)) {
            logger.info("Starting preview generation for: {}", documentPath);
            
            PreviewOptions options = createPreviewOptions();
            comparer.getDocument().generatePreview(options);
            
            logger.info("Successfully generated previews for: {}", documentPath);
            return true;
            
        } catch (Exception e) {
            logger.error("Failed to generate previews for: " + documentPath, e);
            return false;
        }
    }
}
```

### Gestión de recursos

Siempre cierre los flujos en un bloque finally o use try‑with‑resources. Esto previene fugas de descriptores de archivo que pueden bloquear servicios de larga duración.

```java
public class ResourceManagedPreviewGenerator implements AutoCloseable {
    private final ExecutorService executor;
    private final PreviewCache cache;
    
    public ResourceManagedPreviewGenerator() {
        this.executor = Executors.newFixedThreadPool(4);
        this.cache = new PreviewCache();
    }
    
    @Override
    public void close() {
        executor.shutdown();
        try {
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                executor.shutdownNow();
            }
        } catch (InterruptedException e) {
            executor.shutdownNow();
            Thread.currentThread().interrupt();
        }
        
        cache.clear();
    }
}
```

## Solución de problemas comunes

### Problema 1: Error “Could not load document”

**Síntomas:** Excepción al intentar cargar ciertos tipos de documento.  

**Soluciones**  
1. Verifique que el documento no esté corrupto.  
2. Compruebe si el formato de archivo es compatible.  
3. Asegúrese de que los permisos del archivo sean correctos.  
4. Valide que la ruta del archivo exista.

```java
private boolean isDocumentValid(String filePath) {
    File file = new File(filePath);
    if (!file.exists()) {
        logger.error("Document file does not exist: {}", filePath);
        return false;
    }
    
    if (!file.canRead()) {
        logger.error("Cannot read document file: {}", filePath);
        return false;
    }
    
    return true;
}
```

### Problema 2: Calidad de vista previa deficiente

**Síntomas:** Las vistas previas generadas son borrosas o pixeladas.  

**Soluciones**  
- Verifique la calidad del documento fuente.  
- Ajuste la configuración del formato de salida (use PNG para calidad sin pérdida).  
- Asegúrese de contar con recursos del sistema adecuados durante la conversión.

### Problema 3: Generación lenta de vistas previas

**Síntomas:** La generación de vistas previas lleva demasiado tiempo para documentos grandes.  

**Soluciones**  
- Implemente límites de páginas para vistas previas iniciales.  
- Use procesamiento asíncrono (vea el ejemplo `ExecutorService`).  
- Añada indicadores de progreso para la retroalimentación del usuario.  
- Cachee vistas previas de acceso frecuente.

## Alternativas a GroupDocs.Comparison

Aunque GroupDocs.Comparison es excelente para la generación de vistas previas de documentos, podría considerar alternativas:

- **Apache PDFBox** (solo PDF, código abierto)  
- **iText** (Comercial, características extensas de PDF)  
- **ImageIO con bibliotecas Office** (Mayor control, mayor complejidad de configuración)

## Conclusión

Ahora ha aprendido cómo **create pdf preview java** usando GroupDocs.Comparison. Esta solución ofrece:

- Soporte para múltiples formatos de documento (PDF, Word, Excel, PowerPoint)  
- Generación de vistas previas de alta calidad con opciones configurables  
- Manejo de errores y gestión de recursos listo para producción  
- Arquitectura escalable adecuada para aplicaciones empresariales  

### Próximos pasos

1. **Implementar caché** – Añada caché Redis o basada en archivos para vistas previas de acceso frecuente.  
2. **Añadir seguimiento de progreso** – Muestre a los usuarios el progreso de la generación de vistas previas para documentos grandes.  
3. **Optimizar para móvil** – Cree vistas previas responsivas para aplicaciones móviles.  
4. **Monitorear rendimiento** – Añada métricas y monitoreo para rastrear el rendimiento del sistema.

¿Listo para implementar la generación de vistas previas de documentos en su aplicación Java? Comience con una pequeña prueba de concepto y expanda gradualmente la funcionalidad según sus requisitos específicos.

## Preguntas frecuentes

**Q:** ¿Qué formatos de documento admite este generador de vistas previas de documentos Java?  
**A:** GroupDocs.Comparison admite más de 50 formatos de documento, incluidos PDF, DOCX, XLSX, PPTX, TXT, HTML y muchos más. Consulte la [documentación](https://docs.groupdocs.com/comparison/java/) para obtener una lista completa.

**Q:** ¿Cómo genero miniaturas de documentos solo de la primera página?  
**A:** Use `previewOptions.setPageNumbers(new int[]{1})` para generar una vista previa solo de la primera página. Esto es perfecto para la creación de miniaturas en navegadores de documentos.

**Q:** ¿Puedo personalizar el formato y la calidad de la imagen de salida?  
**A:** Sí, puede configurar el formato de salida mediante el delegado `CreatePageStream`. La biblioteca admite principalmente el formato PNG, que brinda una excelente calidad para vistas previas de documentos.

**Q:** ¿Cómo manejo archivos PDF muy grandes sin quedarme sin memoria?  
**A:** Procese documentos grandes en lotes especificando rangos de páginas, implemente una limpieza adecuada de recursos con try‑with‑resources y considere aumentar el tamaño del heap de la JVM con el parámetro `-Xmx`.

**Q:** ¿Hay una forma de generar vistas previas de forma asíncrona?  
**A:** ¡Absolutamente! Use `CompletableFuture.runAsync()` o `ExecutorService` para generar vistas previas en hilos en segundo plano. Esto evita bloquear el hilo principal de su aplicación.

**Q:** ¿Cómo soluciono los errores “License not found”?  
**A:** Asegúrese de que su archivo de licencia esté en el classpath, verifique que la licencia no haya expirado y compruebe que está usando el tipo de licencia correcto para su versión de GroupDocs.Comparison.

### Recursos adicionales

- **Documentación**: [GroupDocs.Comparison Java Documentation](https://docs.groupdocs.com/comparison/java/)  
- **Referencia API**: [Complete API Reference](https://reference.groupdocs.com/comparison/java/)  
- **Descargar última versión**: [GroupDocs.Comparison Downloads](https://releases.groupdocs.com/comparison/java/)  
- **Comprar licencia**: [Buy GroupDocs.Comparison License](https://purchase.groupdocs.com/buy)  
- **Probar gratis**: [Download Free Trial](https://releases.groupdocs.com/comparison/java/)  
- **Obtener soporte**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/comparison)  
- **Licencia temporal**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**Última actualización:** 2026-05-26  
**Probado con:** GroupDocs.Comparison 25.2  
**Autor:** GroupDocs  

---

## Tutoriales relacionados

- [Java Document Preview Generation - Complete GroupDocs.Comparison Tutorial](/comparison/java/preview-generation/)  
- [compare pdf java – Java Document Comparison Tutorial – Complete Guide to Loading & Comparing Documents](/comparison/java/document-loading/)  
- [GroupDocs.Comparison Java Licensing Setup Guide - Complete Configuration Tutorial](/comparison/java/licensing-configuration/)