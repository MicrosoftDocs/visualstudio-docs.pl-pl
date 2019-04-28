---
title: Opcje debugowania Azure usługi w chmurze | Dokumentacja firmy Microsoft
description: Debugowanie usług Azure cloud services
services: visual-studio-online
documentationcenter: n/a
author: mikejo
manager: douge
editor: ''
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.service: visual-studio-online
ms.devlang: multiple
ms.topic: article
ms.tgt_pltfrm: multiple
ms.workload: na
origin.date: 03/18/2017
ms.date: 05/11/2018
ms.author: v-junlch
ms.openlocfilehash: 3b489b97551e5b5522cb58868b34dee4d9e5fb7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963653"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Informacje dotyczące różnych sposobów debugowania usługi w chmurze platformy Azure
Ten artykuł zawiera łącza do różnych sposobów debugowanie usługi w chmurze platformy Azure. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Debugowanie usługi w chmurze platformy Azure w programie Visual Studio
Możesz zaoszczędzić czas i pieniądze za pomocą usługi Azure compute emulatora do debugowania na maszynie lokalnej usługi w chmurze. Debugowanie usługi lokalnie przed przystąpieniem do wdrażania, może zwiększyć niezawodność i wydajność bez konieczności płacenia za czas obliczeń. Jednak niektóre błędy mogą wystąpić tylko w przypadku korzystania z usługi w chmurze na platformie Azure. Błędy występujące tylko w przypadku korzystania z usługi w chmurze na platformie Azure może być debugowany, należy włączyć zdalne debugowanie po opublikowaniu usługi, a następnie dołączanie debugera do wystąpienia roli. Aby uzyskać więcej informacji, zobacz [debugowanie usługi w chmurze na komputerze lokalnym](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Używanie funkcji IntelliTrace 
Jeśli używasz programu Visual Studio Enterprise do zapisania ról docelowych programu .NET Framework 4.5, można włączyć funkcji IntelliTrace w czasie wdrażania usługi w chmurze platformy Azure z programu Visual Studio. IntelliTrace zawiera dziennik, który za pomocą programu Visual Studio umożliwia debugowanie aplikacji, tak jakby były uruchamiane na platformie Azure. Aby uzyskać więcej informacji, zobacz [debugowanie opublikowanych usług w chmurze za pomocą IntelliTrace i Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Debugowanie zdalne 
Aby umożliwić zdalne debugowanie usług w chmurze w czasie, podczas wdrażania usługi w chmurze z programu Visual Studio. Jeśli chcesz włączyć zdalne debugowanie dla wdrożenia zdalnego debugowania są instalowane na maszynach wirtualnych, które są uruchamiane każde wystąpienie roli. Te usługi — takich jak `msvsmon.exe` — nie wpływa na wydajność lub powodować dodatkowych kosztów. Aby uzyskać więcej informacji, zobacz [debugowanie usługi w chmurze na platformie Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Następne kroki
- [Debugowanie usługi w chmurze platformy Azure lub maszynie Wirtualnej w programie Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) — Dowiedz się, szczegóły dotyczące debugowania usług Azure cloud services.

<!-- Update_Description: update metedata properties -->