---
title: 'Diseño para un idioma: QnA Maker'
description: El recurso de QnA Maker y todas las bases de conocimiento dentro de ese recurso admiten solo un idioma. Solo debe ser un idioma para proporcionar los mejores resultados de respuesta para las consultas.
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: conceptual
ms.date: 01/27/2020
ms.openlocfilehash: e09e15f71b0574a5612e7f9bacd8aaa4739a441c
ms.sourcegitcommit: ef69245ca06aa16775d4232b790b142b53a0c248
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2020
ms.locfileid: "91777010"
---
# <a name="design-knowledge-base-for-content-language"></a>Diseño de una base de conocimiento para el idioma del contenido

El recurso de QnA Maker y todas las bases de conocimiento dentro de ese recurso admiten solo un idioma. Solo debe ser un idioma para proporcionar los mejores resultados de respuesta para las consultas.

## <a name="single-language-per-resource"></a>Un solo idioma por recurso

Consideraciones de QnA Maker para la compatibilidad con idiomas:

* Un servicio de QnA Maker y todas sus bases de conocimiento solo admiten un idioma.
* El idioma se establece de forma explícita cuando se crea la primera base de conocimiento del servicio.
* El idioma se determina a partir de los archivos y las direcciones URL que se agregan al crear la base de conocimiento.
* No se puede cambiar el idioma de ninguna otra base de conocimiento en el servicio.
* El servicio de Cognitive Search (clasificador n.º 1) y el servicio de QnA Maker (clasificador n.º 2) usan el idioma para generar la mejor respuesta de una consulta.

## <a name="supporting-multiple-languages"></a>Compatibilidad con varios idiomas

Si necesita admitir un sistema de base de conocimiento que incluye varios idiomas, puede elegir uno de los siguientes métodos:

* Usar el [servicio de traducción de texto](../../translator/translator-info-overview.md) para traducir una pregunta a un solo idioma antes de enviarla a la base de conocimiento. Esto le permite concentrarse en la calidad de un solo idioma, así como en la calidad de las preguntas y respuestas alternativas.
* Crear un recurso de QnA Maker (y una base de conocimiento dentro de ese recurso) para cada idioma. Esta opción le permite administrar preguntas alternativas independientes y textos de respuesta con más matices para cada idioma. De este modo, obtiene mucha más flexibilidad, aunque tiene un costo de mantenimiento mucho mayor cuando las preguntas o respuestas son distintas en todos los idiomas.

Consulte los [idiomas admitidos](../overview/language-support.md) en QnA Maker.

### <a name="support-each-language-with-a-qna-maker-resource"></a>Inclusión de un recurso de QnA Maker para cada idioma

* Cree un recurso de QnA Maker para cada idioma
* Agregue solo archivos y direcciones URL para ese idioma
* Use una convención de nomenclatura para que el recurso identifique el idioma. Por ejemplo, `qna-maker-fr` es para todas las bases de conocimiento de documentos en francés

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre los [conceptos](query-knowledge-base.md) para consultar la base de conocimiento y obtener una respuesta.