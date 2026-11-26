# ¿Dónde rinde más tu dinero? Precios de la canasta básica en México (Profeco + INPC, 2026)

Proyecto TECNOLOCHICAS _Procesamiento de datos con Python_.
Autora: Nailea Tania Castro Vazquez

---

## 1. Introducción

Los precios de los productos básicos cambian según la tienda, la ciudad y la época del año. La inflación oficial (INPC) resume esos cambios en un solo número nacional, pero no muestra cuánto varía el precio de un mismo producto entre una cadena comercial y otra.

Este proyecto analiza datos abiertos del gobierno de México para comparar precios **del mismo producto** entre cadenas y estados, y contrastar su evolución durante 2026 con la inflación oficial.

Para comparar de forma justa, se construye un **índice de precio relativo**: el precio de un producto en una tienda dividido entre la mediana del mismo producto (misma presentación y marca) en todo el país, multiplicado por 100. Un índice de 100 es el precio típico, 90 es un 10% más barato y 110 un 10% más caro.

## 2. Problemática

Las familias y las autoridades no tienen una vista clara de dónde son más caros los productos básicos, qué tan lejos están esos precios de la inflación oficial y cómo cambian durante el año. Comparar el "precio promedio" global no sirve, porque los productos están en escalas muy distintas (un electrodoméstico y un litro de aceite no son comparables). Esto dificulta decidir dónde comprar y detectar aumentos injustificados.

**Importancia.** El gasto en alimentos y productos básicos pesa mucho en el presupuesto de los hogares, y los datos de Profeco son públicos pero muy extensos y con problemas de calidad, por lo que rara vez se aprovechan completos. Un análisis reproducible puede ayudar a comprar mejor y a entender dónde se concentran las diferencias de precio.

## 3. Pregunta de investigación

**Pregunta central:** ¿Qué cadenas comerciales y estados tienen los precios más altos en productos básicos y cómo se compara la evolución de esos precios con la inflación oficial (INPC) durante 2026?

**Preguntas secundarias:**

1. ¿Las diferencias de precio de un mismo producto son mayores entre cadenas o entre estados?
2. ¿Qué tipo de tienda (supermercado, bodega, tienda de conveniencia) tiene los precios más altos?
3. ¿Los precios de Profeco siguen la tendencia mensual del INPC?
4. ¿Hay estacionalidad en algunos productos?

## 4. Origen de los datos

| Fuente                                                             | Contenido                                                                                         | Periodo                  | Acceso                                                      |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- | ------------------------ | ----------------------------------------------------------- |
| **Profeco**, _Quién es Quién en los Precios_                       | Precio de cada producto por tienda, municipio y estado. 20 archivos CSV (2 por mes, `Q1` y `Q2`). | Enero a octubre de 2026  | https://datos.profeco.gob.mx/index.php#tab-quien-precios    |
| **INEGI**, Índice Nacional de Precios al Consumidor (INPC) mensual | Índice nacional de precios y su variación                                                         | Hasta septiembre de 2026 | Datos abiertos de INEGI (archivo incluido en `datos/inpc/`) |

Los archivos de Profeco pesan unos 3.6 GB en total, por lo que **no se incluyen en este repositorio** (carpeta `datos/crudos/`, ignorada por Git). Para reproducir el análisis, descárgalos del enlace anterior y colócalos en esa carpeta. Se estima que suman más de 10 millones de registros. Los datos se actualizan periódicamente, por lo que no son un conjunto estático.

## 5. Objetivo del análisis

**Objetivo general:** Analizar los precios de productos básicos en México durante 2026 con datos abiertos de Profeco e INEGI, para identificar diferencias por cadena y estado y compararlas con la inflación oficial.

**Objetivos específicos:**

1. Explorar y limpiar los 20 archivos de Profeco con un proceso reproducible (duplicados, faltantes, errores de captura y formato).
2. Construir un índice de precio relativo que permita comparar productos de forma justa.
3. Comparar los precios entre cadenas comerciales y entre estados.
4. Contrastar la evolución mensual de los precios con la variación del INPC (enero a septiembre de 2026).
5. Presentar los hallazgos en un informe y una presentación con recomendaciones.

## 6. Hipótesis

Las hipótesis se plantean a partir de una exploración preliminar con la primera quincena de julio de 2026 y se probarán con los 10 meses de datos.

- **H1.** Las diferencias de precio de un mismo producto son mayores **entre cadenas comerciales** que **entre estados**.
- **H2.** Las tiendas de conveniencia (por ejemplo, Oxxo y Minisuper) tienen índices de precio más altos que los supermercados y bodegas para los mismos productos básicos.
- **H3.** La evolución mensual del índice de precios de Profeco sigue la misma tendencia que la variación del INPC entre enero y septiembre de 2026.
- **H4.** Los precios de los útiles escolares aumentan en las quincenas de regreso a clases (agosto) respecto a los meses anteriores.

## Estructura del repositorio

```
precios-canasta-basica-mx/
├── README.md
├── notebooks/          ← exploración, limpieza y análisis
├── src/                ← funciones reutilizables de limpieza
├── datos/
│   ├── crudos/         ← archivos de Profeco (no se suben a GitHub)
│   ├── inpc/           ← INPC mensual (INEGI)
│   └── procesados/     ← resultados resumidos y muestra limpia
└── docs/               ← informe y presentación
```

## Estado del proyecto

- [x] Planteamiento del problema
- [ ] Exploración y limpieza de los datos
- [ ] Análisis y contraste de hipótesis
- [ ] Informe y presentación
