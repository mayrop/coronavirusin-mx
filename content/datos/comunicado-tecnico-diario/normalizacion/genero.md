---
author: "Mayra Valdes"
date: 2020-04-10
linktitle: Normalización de la columna Género (Sexo Masculino/Femenino)
title: Normalización del Género
weight: 2
lang:
    en: /en/data/cases-tables/normalization/gender/
bookToc: false
---

## Formato
El formato de género para la columna _Sexo_ tendrá un valor de `M` para el sexo Masculino, y `F` para el sexo femenino.

## Inconsistencias de formato de la columna Sexo
Al parecer las columnas de Sexo no son consistentes, al tener diferentes valores:
```r
> table(rows$Sexo)
        F         M  FEMENINO MASCULINO 
    32830     32347     22507     22453 
```

La columna `Sexo_Normalizado` tiene el sexo normalizado a `F` y `M`:
```r
> table(rows$Sexo_Normalizado)
    F     M 
55337 54800 
```

Podemos comprobar que esta inconsistencia empezó a partir del 6 de Abril tanto en las tablas de positivos como en las de sospechosos:
```r
rows %>%
+   dplyr::filter(Sexo %in% c("MASCULINO", "FEMENINO")) %>%
+   dplyr::pull(File_Id) %>%
+   unique()
[1] "positivos_2020_04_06"   "positivos_2020_04_07"   "positivos_2020_04_08"  
[4] "positivos_2020_04_09"   "sospechosos_2020_04_06" "sospechosos_2020_04_07"
[7] "sospechosos_2020_04_08" "sospechosos_2020_04_09"
```

