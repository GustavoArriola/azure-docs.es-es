---
title: Copia de una instantánea en una cuenta de almacenamiento de otra región mediante la CLI
description: 'Ejemplo de script de la CLI de Azure: exportación o copia de instantánea como un VHD a una cuenta de almacenamiento en misma suscripción o en una diferente'
documentationcenter: storage
author: ramankumarlive
manager: kavithag
ms.service: virtual-machines
ms.subservice: disks
ms.devlang: azurecli
ms.topic: sample
ms.workload: infrastructure
ms.date: 05/19/2017
ms.author: ramankum
ms.custom: mvc,seodec18
ms.openlocfilehash: e59386acdf4590100e59fe49142715ea26b8d6d6
ms.sourcegitcommit: 5ed504a9ddfbd69d4f2d256ec431e634eb38813e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89321946"
---
# <a name="exportcopy-a-snapshot-to-a-storage-account-in-different-region-with-cli"></a>Exportación o copia de una instantánea administrada como un VHD a una cuenta de almacenamiento en una región diferente con la CLI

Este script exporta una instantánea administrada a una cuenta de almacenamiento en otra región. En primer lugar, genera el identificador URI de SAS de la instantánea y, luego, lo usa para copiarlo en una cuenta de almacenamiento en una región diferente. Use este script para mantener una copia de seguridad de los discos administrados en una región distinta para la recuperación ante desastres. 


[!INCLUDE [sample-cli-install](../../../includes/sample-cli-install.md)]

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="sample-script"></a>Script de ejemplo

[!code-azurecli[main](../../../cli_scripts/virtual-machine/copy-snapshots-to-storage-account/copy-snapshots-to-storage-account.sh "Copy snapshot")]


## <a name="script-explanation"></a>Explicación del script

Este script usa los siguientes comandos para generar el identificador URI de SAS para una instantánea administrada y copia la instantánea en una cuenta de almacenamiento usando el URI de SAS. Cada comando de la tabla crea un vínculo a documentación específica del comando.

| Get-Help | Notas |
|---|---|
| [az snapshot grant-access](/cli/azure/snapshot) | Genera la SAS de solo lectura que se usa para copiar el archivo de VHD subyacente a una cuenta de almacenamiento o descargarlo localmente.  |
| [az storage blob copy start](/cli/azure/storage/blob/copy) | Copia un blob de forma asincrónica desde una cuenta de almacenamiento a otra. |

## <a name="next-steps"></a>Pasos siguientes

[Crear un disco administrado a partir de un VHD](virtual-machines-cli-sample-create-managed-disk-from-vhd.md?toc=%2fcli%2fmodule%2ftoc.json)

[Crear una máquina virtual a partir de un disco administrado](virtual-machines-linux-cli-sample-create-vm-from-managed-os-disks.md?toc=%2fcli%2fmodule%2ftoc.json)

Para más información sobre la CLI de Azure, consulte la [documentación de la CLI de Azure](/cli/azure).

Encontrará más ejemplos de scripts de la CLI de máquina virtual y discos administrados en la [documentación de Azure sobre máquinas virtuales Linux](../linux/cli-samples.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
