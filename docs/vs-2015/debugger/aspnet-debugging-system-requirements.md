---
title: 'Debugowanie ASP.NET: Wymagania systemowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826260"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Debugowanie: wymagania systemu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano wymagania dotyczące oprogramowania i zabezpieczeń dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] scenariuszy debugowania:  
  
- Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplikacja sieci Web jest uruchamiana na tym samym komputerze. Istnieją dwie wersje tego scenariusza:  
  
  - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Kod znajduje się w systemie plików.  

  - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Kod znajduje się w witrynie sieci Web usług IIS.  
  
- Zdalne debugowanie, w którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] działa na komputerze klienckim i debuguje aplikację sieci Web, która jest uruchomiona na komputerze serwera zdalnego.  
  
## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń  
 W przypadku zdalnego debugowania na komputerach lokalnych i zdalnych musi znajdować się konfiguracja domeny lub Konfiguracja grupy roboczej.  
  
 Aby debugować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy, musisz mieć uprawnienia do debugowania tego procesu. Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje są uruchamiane jako użytkownik **ASPNET** . Jeśli proces roboczy jest uruchomiony jako **ASPNET**lub jako **Usługa sieciowa**, musisz mieć uprawnienia administratora, aby go debugować.  
  
 Nazwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego zależy od scenariusza debugowania i wersji usług IIS. Aby uzyskać więcej informacji, zobacz [How to: find a Name the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Można zmienić konto użytkownika, na którym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] działa proces roboczy, edytując plik machine.config na serwerze z uruchomionymi usługami IIS. Najlepszym sposobem jest użycie **menedżera Internet Information Services (IIS)**. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Jeśli zmienisz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy na uruchomiony przy użyciu własnego konta użytkownika, nie musisz być administratorem na serwerze, na którym są uruchomione usługi IIS.  
  
> [!CAUTION]
> Przed zmianą [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego w celu uruchomienia go przy użyciu innego konta należy wziąć pod uwagę ewentualne konsekwencje, jeśli [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy powinien zostać zaatakowana podczas działania w ramach tego konta. Konta użytkowników ASPNET i NETWORK SERVICE działają z minimalnymi uprawnieniami, co zmniejsza możliwą szkodę, jeśli proces jest zaatakowana. Jeśli musisz zmienić [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy, aby był uruchamiany na koncie, które ma większe uprawnienia, to potencjalne uszkodzenie jest większe.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Instrukcje: uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
