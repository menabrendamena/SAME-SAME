# Same Same. Cuaderno de modelación y datos de origen

Validador de equivalencias de formulación entre productos labiales de gama alta y alternativas de gama económica, construido sobre listas de ingredientes en nomenclatura INCI, con precio de referencia en pesos mexicanos.

El sistema responde una sola pregunta: si la base química de una alternativa accesible sostiene la equivalencia que se le atribuye frente a un producto de gama alta. A esa respuesta le añade cuánto se ahorra. No evalúa tono ni desempeño en uso.

Este repositorio contiene el cuaderno de punta a punta y los insumos de origen que ese cuaderno consume. La aplicación web que publica los resultados vive en [menabrendamena/interfaz-same-same](https://github.com/menabrendamena/interfaz-same-same).

## Cómo ejecutar el cuaderno

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/menabrendamena/same-same/blob/main/same_same_cuaderno_final.ipynb)

El cuaderno corre de principio a fin en Google Colab sin configuración previa y sin archivos adjuntos. La celda de configuración del entorno clona este mismo repositorio dentro de la sesión, de modo que todos los insumos quedan disponibles por ruta relativa. No hay rutas locales ni montajes de unidades.

Ejecución recomendada: `Entorno de ejecución`, `Ejecutar todas`. El cuaderno fija las semillas aleatorias y declara las versiones de las bibliotecas en la sección 2, de modo que una segunda corrida reproduce los mismos valores.

## Estructura del cuaderno

| Sección | Contenido |
|---|---|
| 1 | Planteamiento del problema y estrategia analítica |
| 2 | Configuración del entorno, semillas y reproducibilidad |
| 3 | Adquisición de datos por extracción estructurada |
| 4 y 5 | Descripción, control de integridad y diagnóstico de valores ausentes |
| 6 | Limpieza y construcción de la unidad de análisis |
| 7 y 8 | Análisis exploratorio y tratamiento de valores extremos |
| 9 | Derivación de la aptitud vegana desde la propia fórmula |
| 10 | Ingeniería de variables funcionales |
| 11 | Capa de presentación: nombre comercial y línea |
| 12 | Verdad de referencia y bandera de trato ético |
| 13 | Modelo de similitud, selección de hiperparámetros y evaluación |
| 14 | Política de acierto por línea comercial |
| 15 | Escala, etiquetas, explicación, arquetipos y flujo de inferencia |
| 16 | Precios de referencia en pesos mexicanos |
| 17 | Exportación y verificación de los artefactos de la aplicación |
| 18 y 19 | Conclusiones, siguientes pasos y referencias |

## Insumos de este repositorio

| Archivo | Contenido |
|---|---|
| `catalogo_urls_labiales.csv` | Universo de fichas de producto localizadas, con marca, gama y estado de extracción |
| `productos_inci.csv` | Lista INCI completa por producto, en el orden de declaración publicado |
| `producto_ingrediente.csv` | Relación producto a ingrediente, una fila por posición declarada |
| `producto_funcion.csv` | Relación producto a función cosmética declarada por ingrediente |
| `cobertura_marcas.csv` | Cobertura alcanzada por marca frente al universo esperado |
| `descartes_zona_ajena.csv` | Fichas descartadas por no corresponder a productos labiales, con el motivo |
| `curados/revision_nombres_01b.csv` | Resolución manual de nombres comerciales ambiguos |
| `curados/lista_dupes.xlsx` | Equivalencias documentadas en comunidades, con su origen |
| `curados/pares_extraccion_temptalia.xlsx` | Pares obtenidos de la fuente editorial de referencia |
| `curados/pares_enlace_pendiente_revisado.csv` | Pares cuyo enlace al catálogo requirió revisión manual |
| `curados/observaciones_precios.csv` | Precios consultados en minoristas con operación en México |

La carpeta `curados/` reúne los insumos que exigieron criterio humano y quedaron documentados fila por fila. El resto se obtuvo por extracción automatizada.

## Qué produce la ejecución

El cuaderno escribe sus salidas en `salidas_same_same/`, separadas en tres carpetas: `extraccion/` con los datos normalizados, `analitico/` con la base de fórmulas, las variables funcionales y la evaluación del modelo, y `app/` con los nueve artefactos que consume la aplicación web.

Resultado del modelo sobre el catálogo final: 645 fórmulas, de las cuales 147 son de gama alta y 498 económicas, agrupadas en 548 líneas comerciales de veinte marcas con presencia en México, y un vocabulario de comparación de 359 ingredientes.

## Fuentes

Listas de ingredientes publicadas por el repositorio INKEEDecoder. Equivalencias documentadas en comunidades y en una fuente editorial especializada. Clasificación de crueldad animal contrastada entre PETA y Cruelty-Free Kitty. Precios consultados en minoristas con operación en México en una sola fecha de corte.

## Alcance

Proyecto académico de análisis de formulación cosmética. Sin relación comercial con ninguna de las marcas citadas. Los precios son de referencia y no constituyen una oferta de venta.
