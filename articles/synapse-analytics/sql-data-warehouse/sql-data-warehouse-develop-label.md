---
title: Uso de etiquetas para instrumentar consultas
description: Sugerencias para usar etiquetas para instrumentar las consultas en el grupo de SQL de Synapse para el desarrollo de soluciones.
services: synapse-analytics
author: XiaoyuMSFT
manager: craigg
ms.service: synapse-analytics
ms.topic: conceptual
ms.subservice: sql-dw
ms.date: 04/17/2018
ms.author: xiaoyul
ms.reviewer: igorstan
ms.custom: seo-lt-2019
ms.openlocfilehash: 91b6dac5fba4bb8dfd8cf4a3bb4e5952f8388bb5
ms.sourcegitcommit: 4a7a4af09f881f38fcb4875d89881e4b808b369b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2020
ms.locfileid: "89459154"
---
# <a name="using-labels-to-instrument-queries-in-synapse-sql-pool"></a>Uso de etiquetas para instrumentar consultas en el grupo de SQL de Synapse

En este artículo se incluyen sugerencias para desarrollar soluciones que usan etiquetas para instrumentar consultas en el grupo de SQL.

Sugerencias para usar etiquetas para instrumentar las consultas en Azure Synapse Analytics para el desarrollo de soluciones.

## <a name="what-are-labels"></a>¿Qué son las etiquetas?

El grupo de SQL admite un concepto conocido como etiquetas de consulta. Antes de entrar en materia, vamos a ver un ejemplo:

```sql
SELECT *
FROM sys.tables
OPTION (LABEL = 'My Query Label')
;
```

Esta última línea etiqueta la cadena "Mi etiqueta de consulta" a la consulta. Esta etiqueta es útil porque la etiqueta se puede consultar a través de las DMV.

La consulta de etiquetas proporciona un mecanismo para buscar consultas problemáticas y ayudar a identificar el progreso a través de una ejecución de ETL.

Una buena convención de nomenclatura realmente ayuda en este caso. Por ejemplo, que la etiqueta empiece por algo como PROYECTO, PROCEDIMIENTO, INSTRUCCIÓN o COMENTARIO identifica de forma única la consulta entre todo el código de control del código fuente.

La consulta siguiente usa una vista de administración dinámica para buscar por etiqueta:

```sql
SELECT  *
FROM    sys.dm_pdw_exec_requests r
WHERE   r.[label] = 'My Query Label'
;
```

> [!NOTE]
> Es esencial que encierre entre corchetes o comillas dobles la etiqueta de la palabra al consultar. La etiqueta es una palabra reservada y provoca un error cuando no se delimita.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más sugerencias sobre desarrollo, vea la [información general sobre desarrollo](sql-data-warehouse-overview-develop.md).
