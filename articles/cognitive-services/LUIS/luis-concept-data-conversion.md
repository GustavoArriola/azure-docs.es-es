---
title: 'Conversión de datos: LUIS'
titleSuffix: Azure Cognitive Services
description: Obtenga información sobre cómo se pueden modificar las expresiones antes de las predicciones en Language Understanding (LUIS).
services: cognitive-services
manager: nitinme
ms.custom: seodec18
ms.service: cognitive-services
ms.subservice: language-understanding
ms.topic: conceptual
ms.date: 07/29/2019
ms.openlocfilehash: b305be693f59b65a62570f656a0132f4f03cf099
ms.sourcegitcommit: f5580dd1d1799de15646e195f0120b9f9255617b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2020
ms.locfileid: "91541805"
---
# <a name="convert-data-format-of-utterances"></a>Conversión del formato de datos de expresiones
LUIS proporciona las siguientes conversiones de una expresión de usuario antes de la predicción.

* Conversión de voz en texto mediante el servicio [Speech de Cognitive Services](../Speech-Service/overview.md).

## <a name="speech-to-text"></a>Conversión de voz en texto

La conversión de voz en texto se proporciona como una integración con LUIS.

### <a name="intent-conversion-concepts"></a>Conceptos de la conversión en intención
La conversión de voz en texto en LUIS permite enviar expresiones de voz a un punto de conexión y recibir una respuesta de predicción de LUIS. El proceso consiste en integrar el servicio [Speech](https://docs.microsoft.com/azure/cognitive-services/Speech) con LUIS. Más información sobre la conversión de voz en intención con un [tutorial](../speech-service/how-to-recognize-intents-from-speech-csharp.md).

### <a name="key-requirements"></a>Requisitos principales
No es necesario crear una clave de **Bing Speech API** para esta integración. Para esta integración, solo servirá una clave de **Language Understanding** creada en Azure Portal. No utilice la clave de inicio de LUIS.

### <a name="pricing-tier"></a>Nivel de precios
Esta integración usa otro modelo de [precios](luis-limits.md#key-limits) distinto de los planes de tarifa habituales de Language Understanding.

### <a name="quota-usage"></a>Uso de cuota
Vea los [Límites clave](luis-limits.md#key-limits) para obtener información.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Extracción de datos](luis-concept-data-extraction.md)

