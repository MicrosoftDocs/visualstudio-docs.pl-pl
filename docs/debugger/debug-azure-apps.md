---
title: Debugowanie usług platformy Azure | Microsoft Docs
description: Można debugować usługi platformy Azure za pomocą programu Visual Studio. Skorzystaj z linków w tym artykule, aby dowiedzieć się więcej na temat różnych sposobów wykonania tej czynności.
ms.custom: SEO-VS-2020
ms.date: 09/14/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
ms.assetid: 3d434de3-ee5f-419d-9a94-ac4ac02d635b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 36619ae1b1cfc1d380eb85a3e7a2273493ebaa13
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560372"
---
# <a name="debug-azure-services-in-visual-studio"></a>Debugowanie usług platformy Azure w programie Visual Studio

Możesz użyć programu Visual Studio do debugowania usług platformy Azure w różnych scenariuszach:

Aby debugować aplikację produkcyjną hostowaną w:

- Azure App Service, używając Visual Studio Enterprise, zobacz [debugowanie live ASP.NET Apps przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Azure App Service lub Service Fabric, za pomocą Application Insights, zobacz [debugowanie migawek na wyjątkach w aplikacjach .NET](/azure/application-insights/app-insights-snapshot-debugger).

- Maszyna wirtualna platformy Azure lub zestaw skalowania maszyn wirtualnych platformy Azure, zobacz [debugowanie usługi live ASP.NET Azure Virtual Machines and Virtual Machine Scale Sets przy użyciu Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md).

- Usługa Azure Kubernetes, zobacz [debugowanie live ASP.NET Azure Kubernetes Services przy użyciu Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md).

Do zdalnego debugowania:

- ASP.NET na serwerze IIS (Azure App Service lub maszynie wirtualnej platformy Azure), zobacz [zdalne debugowanie ASP.NET na platformie Azure](remote-debugging-azure.md).

- ASP.NET na platformie Azure Service Fabric, zobacz [debugowanie aplikacji zdalnej Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)

## <a name="see-also"></a>Zobacz także

- [Debugowanie w Visual Studio](../debugger/index.yml)
