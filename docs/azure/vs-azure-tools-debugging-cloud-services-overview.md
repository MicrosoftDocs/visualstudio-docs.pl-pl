---
title: Opcje debugowania usług Azure Cloud Services | Microsoft Docs
description: Debugowanie usług Azure Cloud Services
author: mikejo5000
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 2471b79c7401d63b9655586fc4745d3977d37275
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844232"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Informacje dotyczące różnych sposobów debugowania usługi w chmurze platformy Azure
Ten artykuł zawiera linki do różnych sposobów debugowania usługi w chmurze platformy Azure.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Debugowanie usługi w chmurze platformy Azure w programie Visual Studio
Możesz zaoszczędzić czas i pieniądze, korzystając z emulatora obliczeń platformy Azure w celu debugowania usługi w chmurze na komputerze lokalnym. Przez debugowanie usługi lokalnie przed jej wdrożeniem można zwiększyć niezawodność i wydajność bez płacenia za czas obliczeń. Niektóre błędy mogą jednak wystąpić tylko w przypadku uruchomienia usługi w chmurze na platformie Azure. Błędy występujące tylko w przypadku uruchomienia usługi w chmurze na platformie Azure mogą być debugowane przez włączenie debugowania zdalnego podczas publikowania usługi, a następnie dołączenie debugera do wystąpienia roli. Aby uzyskać więcej informacji, zobacz [debugowanie usługi w chmurze na komputerze lokalnym](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Używanie funkcji IntelliTrace
Jeśli używasz Visual Studio Enterprise do zapisywania ról przeznaczonych dla .NET Framework 4,5, możesz włączyć IntelliTrace w czasie wdrażania usługi w chmurze platformy Azure z poziomu programu Visual Studio. IntelliTrace zawiera dziennik, którego można użyć w programie Visual Studio do debugowania aplikacji tak, jakby była uruchomiona na platformie Azure. Aby uzyskać więcej informacji, zobacz [debugowanie opublikowanej usługi w chmurze za pomocą IntelliTrace i programu Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Debugowanie zdalne
Podczas wdrażania usługi w chmurze z poziomu programu Visual Studio można włączyć debugowanie zdalne w usługach w chmurze. W przypadku wybrania opcji włączenia debugowania zdalnego dla wdrożenia usługi zdalnego debugowania są instalowane na maszynach wirtualnych, na których działa każde wystąpienie roli. Te usługi — takie jak `msvsmon.exe` -nie wpływają na wydajność ani nie powodują dodatkowych kosztów. Aby uzyskać więcej informacji, zobacz [debugowanie usługi w chmurze na platformie Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Następne kroki
- [Debugowanie usługi w chmurze lub maszyny wirtualnej platformy Azure w programie Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) — Poznaj szczegóły dotyczące debugowania usług Azure Cloud Services.
