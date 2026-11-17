# Sorpresas inflacionarias y volatilidad del S&P Merval (Argentina, 2021-2025)

Código de replicación del trabajo final integrador. Analiza si las sorpresas en el dato mensual de inflación (IPC de INDEC frente a la mediana del REM del BCRA) afectan el nivel de los retornos y la volatilidad condicional del índice S&P Merval, con 60 publicaciones entre febrero de 2021 y enero de 2026.

## Informe de resultados

El informe compilado (metodología, tablas y figuras) puede verse en: https://TU_USUARIO.github.io/sorpresas-merval/

## Archivos

| Archivo | Lenguaje | Qué hace |
|---|---|---|
| `sorpresas_merval_v2.ipynb` | Python | Construye la base de datos: lee las series de precios, el IPC, el REM y las variables de contexto; calcula las sorpresas y los retornos anormales acumulados, y exporta tres CSV. |
| `Sorpresas_Merval_v2.Rmd` | R Markdown | Lee los CSV, estima el AR(1)-GARCH(1,1)-t y las regresiones del trabajo, y genera las tablas y figuras. |
| `index.html` | HTML | Informe compilado a partir del Rmd. |

## Flujo

```
Fuentes  →  sorpresas_merval_v2.ipynb  →  base_eventos_v2.csv
                                           merval_diario_v2.csv
                                           tabla_yahoo_vs_bloomberg.csv
                                                     ↓
                                     Sorpresas_Merval_v2.Rmd  →  Tablas 1-11, Figuras 1-2
```

## Datos

Los datos no se incluyen en este repositorio. Los precios de Bloomberg no pueden redistribuirse por su licencia. Para correr el código hacen falta, en una carpeta `datos/`:

| Archivo | Fuente |
|---|---|
| `datos bloomberg/Merval cierre.xlsx` | Bloomberg (PX_LAST) |
| `datos bloomberg/{GGAL, BMA, YPFD, PAMP, CEPU, TXAR, ALUA}-ARS-COMPLETO.xlsx` | Bloomberg (PX_LAST) |
| `datos bloomberg/CCL_GGAL.xlsx` | Bloomberg (GGAL en BYMA y ADR en NYSE) |
| `datos bloomberg/historico_vix.xlsx` | Yahoo Finance (^VIX) |
| `historico-relevamiento-expectativas-mercado.xlsx` | BCRA, Relevamiento de Expectativas de Mercado |
| `EMBI 2020-2026.xlsx` | Ámbito |
| `Dolar BNA.xlsx` | Banco de la Nación Argentina |

El IPC se descarga directamente del sitio de INDEC y el Merval de Yahoo Finance (^MERV) se usa para completar la serie de Bloomberg.

## Replicación

1. Colocar los archivos de datos en `datos/` (o definir la variable de entorno `RUTA_DATOS` con otra ruta, terminada en `/`).
2. Ejecutar `sorpresas_merval_v2.ipynb` (Python 3 con pandas, numpy, openpyxl y yfinance; funciona en Google Colab).
3. Dejar los tres CSV generados en la misma carpeta de datos y compilar `Sorpresas_Merval_v2.Rmd` desde RStudio (Knit). Paquetes de R: dplyr, tidyr, purrr, tibble, ggplot2, knitr, kableExtra, lmtest, sandwich, broom, car, rugarch, xts, quantreg y MASS.

El notebook se muestra con las salidas de su última ejecución.
