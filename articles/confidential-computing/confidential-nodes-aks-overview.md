---
title: Nodos de computación confidencial en Azure Kubernetes Service, versión preliminar pública
description: Nodos de computación confidencial en Azure Kubernetes Service
services: virtual-machines
author: agowdamsft
ms.service: container-service
ms.topic: overview
ms.date: 9/22/2020
ms.author: amgowda
ms.openlocfilehash: ae3090689f9999c9ea6aa65447dadbdd7b0b2026
ms.sourcegitcommit: eb6bef1274b9e6390c7a77ff69bf6a3b94e827fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2020
ms.locfileid: "90998544"
---
# <a name="confidential-computing-nodes-on-azure-kubernetes-service-public-preview"></a>Nodos de computación confidencial en Azure Kubernetes Service, versión preliminar pública

La [computación confidencial de Azure](overview.md) permite proteger los datos confidenciales mientras estén en uso. Las infraestructuras subyacentes protegen estos datos no solo de otras aplicaciones, sino también de los administradores y proveedores de servicios en la nube. 

## <a name="overview"></a>Información general

Azure Kubernetes Service permite agregar [nodos de computación confidencial de DCsv2](confidential-computing-enclaves.md) en Intel SGX. Estos nodos ejecutan cargas de trabajo confidenciales en un entorno de ejecución de confianza (TEE) basado en hardware. Para ello, permiten que el código de nivel de usuario asigne regiones privadas de la memoria. Estas regiones se denominan enclaves. Los enclaves están diseñados para proteger el código y los datos de los procesos que se ejecutan con privilegios más elevados. El modelo de ejecución de SGX elimina las capas intermedias del sistema operativo invitado y de hipervisor. Esto permite ejecutar aplicaciones de contenedor directamente sobre la CPU sin perder el bloque de memoria especial cifrado. 


![Información general del nodo de SGX](./media/confidential-nodes-aks-overview/sgxaksnode.jpg)

## <a name="aks-confidential-nodes-features"></a>Características de los nodos confidenciales de AKS

- Aislamiento de contenedores en el nivel de proceso y basado en hardware mediante un entorno de ejecución de confianza (TEE) de SGX 
- Clústeres de grupos de nodos heterogéneos (mezcla de grupos de nodos confidenciales y no confidenciales)
- Programación de pods basada en memoria caché de página cifrada (EPC)
- Controlador SGX DCAP preinstalado
- Revisión de Intel FSGS preinstalada
- Admite el escalado automático de clústeres y la escalabilidad horizontal automática de pods en función del consumo de CPU
- Asistente de atestación fuera del proceso a mediante DaemonSet de AKS
- Compatibilidad con contenedores Linux mediante los nodos de trabajo de máquina virtual de Ubuntu 18.04 Gen 2

## <a name="aks-provided-daemon-sets"></a>DaemonSet proporcionados por AKS

#### <a name="sgx-device-plugin"></a>SGX Device Plugin <a id="sgx-plugin"></a>

SGX Device Plugin implementa la interfaz del complemento de dispositivos Kubernetes para la memoria EPC. De hecho, este complemento hace que la memoria EPC sea un tipo de recurso adicional en Kubernetes. Los usuarios pueden especificar límites en este recurso tal como lo harían en cualquier otro. Además de la función de programación, el complemento del dispositivo ayuda a asignar los permisos del controlador de dispositivos de SGX a los contenedores de cargas de trabajo confidenciales. Para ver un ejemplo de la implementación basada en memoria de EPC (`kubernetes.azure.com/sgx_epc_mem_in_MiB`) consulte [aquí](https://github.com/azure-samples/confidential-computing/blob/main/containersamples/helloworld/helloworld.yaml)

#### <a name="sgx-quote-helper-service"></a>Servicio SGX Quote Helper<a id="sgx-quote"></a>

Las aplicaciones de enclave que realizan la atestación remota necesitan generar una cita. La cita proporciona una prueba criptográfica de la identidad y del estado de la aplicación, así como el entorno en que se ejecuta el enclave. La generación de una cita utiliza determinados componentes de software de confianza de Intel, que forman parte de los componentes de software de plataforma (PSW/DCAP) de SGX. Este PSW se empaqueta como un DaemonSet que se ejecuta por nodo. Para aprovecharlo, se puede solicitar la cita de atestación de las aplicaciones de enclave. El uso del servicio proporcionado por AKS le ayudará a mantener mejor la compatibilidad entre el PSW y otros componentes de software del host. [Más información](confidential-nodes-out-of-proc-attestation.md) sobre su uso y detalles de las características.

## <a name="programming--application-models"></a>Modelos de programación y de aplicación

### <a name="confidential-containers"></a>Contenedores confidenciales

Los [contenedores confidenciales](confidential-containers.md) ejecutan programas existentes y el entorno de ejecución de la mayoría de los **lenguajes de programación comunes** (Python, Node, Java, etc.), junto con las dependencias de sus bibliotecas existentes, sin necesidad de modificar ni volver a compilar el código fuente. Este modelo es el más rápido para la confidencialidad habilitada mediante los proyectos de código abierto y los asociados de Azure. Las imágenes de contenedor creadas para ejecutarse en los enclaves seguro se denominan contenedores confidenciales.

### <a name="enclave-aware-containers"></a>Contenedores compatibles con enclave

AKS admite aplicaciones que están programadas para ejecutarse en nodos confidenciales y usan un **conjunto de instrucciones especiales** que se ponen a disposición mediante los SDK y los marcos de trabajo. Este modelo de aplicación proporciona el máximo control a las aplicaciones con la mínima base de computación de confianza (TCB). [Más información](enclave-aware-containers.md) sobre contenedores compatibles con el enclave.

## <a name="next-steps"></a>Pasos siguientes

[Implementación de un clúster de AKS con nodos de computación confidencial](./confidential-nodes-aks-get-started.md)

[Inicio rápido con ejemplos de contenedores confidenciales](https://github.com/Azure-Samples/confidential-container-samples)

[Lista de SKU de DCsv2](https://docs.microsoft.com/azure/virtual-machines/dcv2-series)

<!-- LINKS - external -->
[Azure Attestation]: https://docs.microsoft.com/en-us/azure/attestation/


<!-- LINKS - internal -->
[DC Virtual Machine]: /confidential-computing/virtual-machine-solutions