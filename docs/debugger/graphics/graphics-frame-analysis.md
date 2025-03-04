---
title: Análisis de fotogramas de gráficos | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6df598717685d3f198b61e4a750c3133e50f5a2d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388724"
---
# <a name="graphics-frame-analysis"></a>Análisis de fotograma de gráficos
Use el Análisis de fotogramas de gráficos en el Analizador de gráficos de Visual Studio para analizar y optimizar el rendimiento de la representación de su juego o aplicación Direct3D.

## <a name="frame-analysis"></a>Análisis de fotogramas
 El análisis de fotogramas usa la misma información que se captura en un archivo de registro de gráficos para fines de diagnóstico, pero la usa para resumir el rendimiento de la representación. La información sobre el rendimiento no se registra en el archivo de registro durante la captura, sino que se genera más adelante, durante el análisis de fotogramas, mediante el control del tiempo de los eventos y la recopilación de estadísticas mientras se reproduce el fotograma. Este enfoque tiene más ventajas que recopilar la información sobre el rendimiento durante la captura:

- El análisis de fotogramas puede sacar la media de los resultados de varias reproducciones del mismo fotograma para garantizar que el resumen del rendimiento sea sólido estadísticamente.

- El análisis de fotogramas puede generar información sobre rendimiento para configuraciones de hardware y dispositivos diferentes al que capturó la información.

- El análisis de fotogramas puede generar nuevos resúmenes de rendimiento a partir de información capturada anteriormente; por ejemplo, cuando los controladores de GPU se optimizan o exponen características de depuración adicionales.

  Además de estas ventajas, el análisis de fotogramas puede cambiar la manera de representar el fotograma durante la reproducción para que pueda presentar información sobre cómo los cambios pueden afectar al rendimiento de la representación de una aplicación. Puede usar esta información para decidir entre las posibles estrategias de optimización sin tener que implementar todas ellas y, luego, capturar y comparar todos los resultados por su cuenta.

  Aunque el análisis de fotogramas está diseñado principalmente para ayudarle a conseguir un rendimiento de la representación más rápido, también le puede ayudar a conseguir una mejor calidad visual para un objetivo de rendimiento determinado o reducir el consumo de energía de la GPU.

  Para ver una demostración de lo que puede hacer el análisis de fotogramas de la aplicación, puede ver el [análisis de fotogramas de gráficos de Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) vídeo de Channel 9.

## <a name="using-frame-analysis"></a>Uso de Análisis de fotogramas
 Antes de usar el Análisis de fotogramas, debe capturar la información de gráficos de su aplicación mientras se ejecuta, al igual que haría al usar cualquiera de las demás herramientas del Analizador de gráficos. Luego, en la ventana del documento de registro de gráficos (.vsglog), seleccione la pestaña **Análisis de fotogramas**.

 ![Seleccione la pestaña análisis de fotogramas.](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")

 Al completarse el análisis, se muestran los resultados. La parte superior de la pestaña de análisis de fotogramas muestra la escala de tiempo y la tabla de resumen. La parte inferior muestra las tablas de detalles. Si se generan errores o advertencias durante la reproducción, se resumen encima de la escala de tiempo. Desde allí, puede seguir los vínculos para obtener más información sobre los errores y las advertencias.

### <a name="interpreting-results"></a>Interpretación de los resultados
 Al interpretar los resultados de cada variante, puede deducir información útil sobre el rendimiento de la representación y el comportamiento de la aplicación. Para obtener más información sobre variantes de interpretación, vea [Variantes](#Variants) más adelante en este artículo.

 Algunos resultados indican directamente cómo la variante afecta al rendimiento de la representación:

- Si la variante Bilinear Texture Filtering muestra aumentos del rendimiento, al usar el filtrado de textura bilineal en la aplicación conseguirá un aumento del rendimiento parecido.

- Si la variante 1x1 Viewport muestra aumentos del rendimiento, reducir el tamaño de los objetivos de representación en su aplicación mejorará su rendimiento de la representación.

- Si la variante BC Texture Compression muestra aumentos del rendimiento, usar la compresión de textura BC en su aplicación mostrará aumentos del rendimiento parecidos.

- Si la variante 2xMSAA tiene casi el mismo rendimiento que la variante 0xMSAA, puede activar 2xMSAA en su aplicación para mejorar la calidad de la representación sin que repercuta en el rendimiento.

  Hay otros resultados que pueden sugerir implicaciones más profundas y sutiles sobre el rendimiento de la aplicación:

- Si la variante 1x1 Viewport muestra un gran aumento del rendimiento, es posible que la aplicación consuma más tasa de relleno de textura que la disponible. Si esta variante no muestra aumentos del rendimiento, es probable que la aplicación procese demasiados vértices.

- Si la variante 16bpp Render Target Format muestra un aumento significativo del rendimiento, es probable que la aplicación consuma demasiado ancho de banda de memoria.

- Si la variante Half/Quarter Texture Dimensions muestra un aumento significativo del rendimiento, es probable que las texturas ocupen demasiada memoria, consuman demasiado ancho de banda o utilicen la caché de texturas de forma ineficaz. Si esta variante no muestra cambios en el rendimiento, es probable que pueda usar texturas más grandes y detalladas sin que ello perjudique al rendimiento.

  Si hay disponibles contadores de hardware, puede usarlos para recopilar información muy detallada sobre por qué el rendimiento de la representación de la aplicación puede verse afectado. Todos los dispositivos de nivel de características 9.2 y superiores admiten las consultas de oclusión de profundidad (contador de **píxeles ocluidos**) y las marcas de tiempo. Puede que estén disponibles otros contadores de hardware, en función de si el fabricante de la GPU implementó los contadores de hardware y los expuso en el controlador. Puede usar estos contadores para confirmar la causa precisa de los resultados que se muestran en la tabla de resumen, por ejemplo, puede determinar si el sobredibujo es un factor examinando el porcentaje de píxeles que se ocluyeron en la prueba de profundidad.

### <a name="timeline-and-summary-table"></a>Escala de tiempo y Tabla de resumen
 De manera predeterminada, la Escala de tiempo y la Tabla de resumen se muestran, pero las otras secciones están contraídas.

#### <a name="timeline"></a>Escala de tiempo
 La escala de tiempo muestra una vista general de los cronometrajes de llamada a draw relativos a otro. Como las barras más largas se corresponden con tiempos de dibujo más prolongados, puede usarlo para ubicar rápidamente en el fotograma las llamadas a draw más caras. Cuando el fotograma capturado contiene una gran cantidad de llamadas a draw, se combinan varias llamadas a draw en una barra cuya longitud sea la suma de esas llamadas a draw.

 ![La escala de tiempo muestra draw&#45;llamar a los costos. ](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")

 Puede colocar el puntero en una barra para ver a qué evento de llamada a draw corresponde. Al seleccionar la barra, la lista de eventos se sincroniza con este evento.

#### <a name="table"></a>Tabla
 La tabla de números de debajo de la escala de tiempo muestra el rendimiento relativo de cada variante de representación para cada llamada a draw con respecto a la representación predeterminada de la aplicación. Cada columna muestra una variante de representación diferente y cada fila representa una llamada a draw diferente que está identificada en la columna del punto de conexión izquierdo; desde aquí puede seguir un vínculo al evento de la ventana de Lista de eventos gráficos.

 ![La tabla de resumen muestra diferentes variaciones. ](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")

 La segunda columna por la izquierda de la Tabla de resumen muestra el tiempo de representación de línea base de la aplicación, es decir, el tiempo que tarda la representación predeterminada de la aplicación en completar la llamada a draw. Las columnas restantes muestran el rendimiento relativo de cada variante de representación como un porcentaje de la línea base para que sea más fácil ver si el rendimiento mejora. Los porcentajes superiores al 100 por cien han tardado más que la línea base, es decir, el rendimiento ha empeorado, y los inferiores al 100 por cien han tardado menos: el rendimiento ha mejorado.

 Los valores del control de tiempo absoluto de la línea base y relativo de las variantes de representación realmente son meros promedios de varias ejecuciones, cinco de manera predeterminada. Este promedio ayuda a garantizar que los datos de control de tiempo son fiables y coherentes. Puede colocar el puntero en todas las celdas de la tabla para examinar los valores de tiempo mínimo, máximo, promedio y la mediana que se han observado cuando se han generado los resultados de esta llamada a draw y variante de representación. También se muestra el control de tiempo de línea base.

#### <a name="hot-draw-calls"></a>Llamadas a draw "activas"
 Para llamar la atención sobre llamadas a draw que consumen una mayor proporción del tiempo de representación general o que puedan ser inusualmente lentas por motivos que se pueden evitar, la fila que contiene estas llamadas a draw "activas" se sombrea en rojo cuando su control del tiempo de la línea base es superior a una desviación estándar más larga que el promedio de tiempo de la línea base de todas las llamadas a draw del fotograma.

 ![Esta llamada DrawIndexed tiene variantes activas e inactivos. ](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")

#### <a name="statistical-significance"></a>Significación estadística
 Para llamar la atención sobre las variantes de representación que son más significativas, el Análisis de fotogramas determina la significación estadística de cada variante de representación y muestra las más significativas en negrita. Muestra en verde las que mejoran el rendimiento y en rojo las que lo emporan. Muestra resultados que no son estadísticamente significativos como tipo normal.

 ![La relevancia estadística de la llamada a Draw](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")

 Para determinar la importancia estadística, análisis de fotogramas usa la [prueba t de Student](http://www.wikipedia.org/wiki/Student%27s_t-test).

### <a name="details-table"></a>Tabla de detalles
 Debajo de la Tabla de resumen está la Tabla de detalles, que está contraída de manera predeterminada. El contenido de la Tabla de detalles depende de la plataforma de hardware de la máquina de reproducción. Para obtener información sobre las plataformas de hardware admitidas, vea [Compatibilidad de hardware](#HardwareSupport).

#### <a name="platforms-that-do-not-support-hardware-counters"></a>Plataformas que no admiten contadores de hardware
 La mayoría de plataformas no admiten completamente contadores GPU de hardware, entre los que se incluyen todas las GPU ofrecidas actualmente por Intel, AMD y nVidia. Cuando no se pueden recopilar contadores de hardware, solo se muestra la Tabla de detalles, que contiene el control de tiempo absoluto promedio de todas las variantes.

 ![La tabla de detalles y algunas variantes de reproducción. ](media/pix_frame_analysis_details.png "pix_frame_analysis_details")

#### <a name="platforms-that-support-hardware-counters"></a>Plataformas que admiten contadores de hardware
 Para las plataformas que admiten contadores GPU de hardware, el SoC nVidia T40 SOC y todos los SoC Qualcomm, por ejemplo, se muestran varias Tablas de detalles, una para cada variante. Cada contador de hardware disponible se recopila para cada variante de representación y se muestra en su propia Tabla de detalles.

 ![Cuando se admita, se muestran los contadores de hardware. ](media/pix_frame.png "pix_frame")

 La información de contador de hardware ofrece una vista muy detallada del comportamiento específico de la plataforma de hardware para cada llamada a draw, que le puede ayudar a identificar la causa de los cuellos de botella en el rendimiento de manera muy precisa.

> [!NOTE]
> Cada plataforma de hardware admite contadores diferentes, no hay ninguno que sea estándar. Únicamente el fabricante de la GPU determina los contadores y lo que representan.

### <a name="marker-regions-and-events"></a>Regiones de marcadores y eventos
 El Análisis de fotogramas admite marcadores y grupos de eventos definidos por el usuario. Se muestran en la tabla de resumen y en las tablas de detalles.

 Puede usar las API ID3DUserDefinedAnnotation o la familia de API D3DPERF_ heredada para crear marcadores y grupos. Al usar la familia de API D3DPERF_, puede asignar a cada marcador y grupo un color que el Análisis de fotogramas muestra como una banda coloreada en las filas que contienen el marcador de evento o los marcadores de inicio/fin de grupo de evento y sus contenidos. Esta característica le puede ayudar a identificar rápidamente eventos de representación o grupos de eventos importantes.

### <a name="warnings-and-errors"></a>Advertencias y errores
 En ocasiones, el análisis de fotogramas finaliza con advertencias o errores, que se resumen encima de la escala de tiempo y se detallan al final de la pestaña Análisis de fotogramas.

 Normalmente, las advertencias y los errores solo se presentan con fines informativos y no requieren ninguna intervención.

 Las advertencias normalmente indican que no hay compatibilidad de hardware pero se puede solucionar el problema, que no se pueden obtener los contadores de hardware o que algún dato de rendimiento puede no ser fiable, por ejemplo, cuando se influye en él para solucionar el problema.

 Los errores suelen indicar que la implementación del análisis de fotogramas tiene errores, que un controlador tiene errores, que no se admite el hardware y no se encuentra ninguna solución alternativa o que la aplicación trata de hacer algo que la reproducción no admite.

### <a name="retries"></a>Reintentos
 Si la GPU se somete a una transición de estado de energía durante el análisis de fotogramas, debe repetir el pase del análisis afectado, dado que la velocidad del reloj de la GPU cambió y, con ello, invalidó los resultados de los intervalos relativos.

 El Análisis de fotogramas limita el número de reintentos a 10. Si su plataforma tiene una gestión de la energía o un canalizador del reloj agresivos, es posible que el Análisis de fotogramas no se ejecute correctamente e informe de un error porque haya superado el límite de reintentos. Tal vez pueda mitigar el problema restaurando la limitación de la velocidad del reloj y la administración de energía de la plataforma de modo que sean menos agresivas, si la plataforma lo permite.

## <a name="HardwareSupport"></a> Compatibilidad de hardware

### <a name="timestamps-and-occlusion-queries"></a>Marcas de tiempo y consultas de oclusión
 Las marcas de tiempo se admiten en todas las plataformas que admiten el Análisis de fotogramas. Las consultas de oclusión de profundidad, necesarias para el contador de píxeles ocluidos, se admiten en las plataformas que admiten el nivel de características 9.2 o superiores.

> [!NOTE]
> Aunque las marcas de tiempo se admiten en todas las plataformas que admiten el análisis de fotogramas, la precisión y la coherencia de las marcas de tiempo varía de una plataforma a otra.

### <a name="gpu-counters"></a>Contadores de GPU
 La compatibilidad de los contadores de hardware de GPU depende del hardware.

 El Análisis de fotogramas no recopila contadores de Intel, AMD ni nVidia, ya que ninguna GPU ofrecida actualmente por estas marcas admite los contadores de hardware de GPU de manera fiable. Sin embargo, el análisis de fotogramas recopila contadores de hardware de la GPU siguiente, que forma confiable es compatible con:

- nVidia T40 (Tegra4)

  Ninguna otra plataforma que admita el Análisis de fotogramas recopila contadores de hardware de GPU.

> [!NOTE]
> Dado que los contadores de hardware de GPU son recursos de hardware, puede que la recopilación del conjunto completo de contadores de hardware de cada variante de representación requiera varios pases. Por esto, no se especifica el orden en el que se recopilan los contadores de la GPU.

## <a name="unsupported-scenarios"></a>Escenarios no admitidos
 Algunas maneras de usar el análisis de fotogramas no se admiten o simplemente son una mala idea.

### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Reproducción de capturas de alto nivel en dispositivos inferiores
 En el Analizador de gráficos, cuando reproduce un archivo de registro de gráficos que usa un nivel superior al que admite la máquina de reproducción, recurre a WARP automáticamente. En el Análisis de fotogramas no se recurre a WARP explícitamente y se genera un error. WARP es útil para examinar la corrección de la aplicación Direct3D, pero no para examinar su rendimiento.

> [!NOTE]
> Aunque sea importante tener en cuenta los problemas de nivel de características, puede capturar y reproducir archivos de registro de gráficos en diferentes configuraciones y dispositivos de hardware. El registro de gráficos puede reproducirse siempre que el archivo de registro no contenga ninguna API o usar niveles de características que no se admiten en la máquina de reproducción.

### <a name="direct3d-10-and-lower"></a>Direct3D 10 e inferiores
 Si su aplicación llama a la API Direct3D 10, el Análisis de fotogramas no la reconocerá ni la incluirá en el perfil, aunque otras herramientas del Analizador de gráficos la reconozcan y la usen.

> [!NOTE]
> Esto se aplica solo a las llamadas de la API Direct3D que utilice, no a los niveles de características.

### <a name="warp"></a>WARP
 El Análisis de fotogramas está diseñado para perfilar y mejorar el rendimiento de la representación en hardware real. Ejecutar análisis de fotogramas en dispositivos WARP no se puede evitar, pero no es normalmente la pena dado si WARP se ejecuta en una CPU es más lento que incluso la menos GPU modernas y que el rendimiento de WARP puede variar enormemente según la CPU se ejecuta en.

## <a name="Variants"></a> Variantes
 Cada cambio que el Análisis de fotogramas realiza en la manera en que se representa un fotograma durante la reproducción se conoce como *variante*. Las variantes que el Análisis de fotogramas examina corresponden a cambios comunes relativamente fáciles que puede realizar para mejorar el rendimiento de la representación o la calidad visual de la aplicación, por ejemplo, reducir el tamaño de las texturas, usar compresión de textura o permitir diferentes tipos de suavizado de contorno. Las variantes reemplazan el contexto de representación y los parámetros habituales de la aplicación. A continuación, se muestra un resumen:

|Variante|Descripción|
|-------------|-----------------|
|**Tamaño de ventanilla 1x1**|Reduce las dimensiones de la ventanilla de todos los objetivos de representación a 1x1 píxeles.<br /><br /> Para más información, vea [1x1 Viewport Size Variant](1x1-viewport-size-variant.md) (Variante de tamaño de ventanilla 1x1).|
|**0x MSAA**|Deshabilita el suavizado de contorno de muestras múltiples (MSAA) en todos los objetivos de representación.<br /><br /> Para más información, vea [0x/2x/4x MSAA Variants](0x-2x-4x-msaa-variants.md) (Variantes de MSAA 0x/2x/4x).|
|**2x MSAA**|Habilita dos veces el suavizado de contorno de muestras múltiples (MSAA) en todos los objetivos de representación.<br /><br /> Para más información, vea [0x/2x/4x MSAA Variants](0x-2x-4x-msaa-variants.md) (Variantes de MSAA 0x/2x/4x).|
|**4x MSAA**|Habilita cuatro veces el suavizado de contorno de muestras múltiples (MSAA) en todos los objetivos de representación.<br /><br /> Para más información, vea [0x/2x/4x MSAA Variants](0x-2x-4x-msaa-variants.md) (Variantes de MSAA 0x/2x/4x).|
|**Filtro de textura de punto**|Establece el modo de filtro en `DXD11_FILTER_MIN_MAG_MIP_POINT` (filtro de textura de punto) para todas las muestras de textura adecuadas.<br /><br /> Para obtener más información, consulte [punto, bilineal, trilineal y anisotrópico variantes de filtrado de textura](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Filtro de textura bilineal**|Establece el modo de filtro en `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtro de textura bilineal) para todas las muestras de textura adecuadas.<br /><br /> Para obtener más información, consulte [punto, bilineal, trilineal y anisotrópico variantes de filtrado de textura](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Filtro de textura trilineal**|Establece el modo de filtro en `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtro de textura trilineal) para todas las muestras de textura adecuadas.<br /><br /> Para obtener más información, consulte [punto, bilineal, trilineal y anisotrópico variantes de filtrado de textura](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Filtro de textura anisotrópico**|Establece el modo de filtro en `DXD11_FILTER_ANISOTROPIC` y `MaxAnisotropy` en `16` (16 veces el filtro de textura anisotrópico) para todas las muestras de textura adecuadas.<br /><br /> Para obtener más información, consulte [punto, bilineal, trilineal y anisotrópico variantes de filtrado de textura](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|
|**Formato de destino de presentación 16bpp**|Establece el formato de píxeles en `DXGI_FORMAT_B5G6R5_UNORM` (16 bpp, formato 565) para todos los objetivos de representación y superficies del búfer.<br /><br /> Para obtener más información, vea [16bpp Render Target Format Variant](16bpp-render-target-format-variant.md) (Variante de formato de destino de representación 16bpp).|
|**Generación de asignación de MIP**|Habilita la asignación de MIP en todas las texturas que no son objetivos de representación.<br /><br /> Para obtener más información, vea [Mip-map Generation Variant](mip-map-generation-variant.md) (Variante Generación de asignación de MIP).|
|**Dimensiones de textura media**|Reduce las dimensiones de la textura en todas las texturas que no son objetivos de representación a la mitad del tamaño original de cada dimensión. Por ejemplo, una textura de 256x128 se reduce a 128x64 elementos de textura.<br /><br /> Para obtener más información, vea [Half/Quarter Texture Dimensions Variant](half-quarter-texture-dimensions-variant.md) (Variante de dimensiones de textura media o un cuarto).|
|**Dimensiones de textura un cuarto**|Reduce las dimensiones de la textura en todas las texturas que no son objetivos de representación a un cuarto del tamaño original de cada dimensión. Por ejemplo, una textura de 256x128 se reduce a 64x32 elementos de textura.<br /><br /> Para obtener más información, vea [Half/Quarter Texture Dimensions Variant](half-quarter-texture-dimensions-variant.md) (Variante de dimensiones de textura media o un cuarto).|
|**Compresión de textura BC**|Habilita la compresión de bloque en todas las texturas que tengan una variante de formato de píxel de B8G8R8X8, B8G8R8A8 o R8G8B8A8. Las variantes de formato B8G8R8X8 se comprimen mediante BC1; las variantes de formato B8G8R8A8 y R8G8B8A8 se comprimen mediante BC3.<br /><br /> Para obtener más información, vea [BC Texture Compression Variant](bc-texture-compression-variant.md) (Variante de compresión de textura BC).|

 El resultado de la mayoría de las variantes es descriptivo: "reducir el tamaño de la textura a la mitad es un 25 por ciento más rápido" o "habilitar dos veces el MSAA es solo un 2 por ciento más lento". Otras variantes pueden requerir más interpretación, por ejemplo, si la variante que cambia las dimensiones de la ventanilla a 1x1 muestra un gran aumento del rendimiento, puede indicar que la representación tiene un cuello de botella por una tasa de relleno de texturas baja; si no hay un cambio importante en el rendimiento, puede indicar que la representación tiene un cuello de botella por un procesamiento de vértice.