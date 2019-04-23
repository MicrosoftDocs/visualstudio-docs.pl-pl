---
title: 'ASP.NET Debugging: Wymagania systemowe | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 523764ae5cd787fd4b52650e894eb086ae4adb0c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097131"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Debugging: Wymagania systemowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano wymagania dotyczące oprogramowania i zabezpieczeń dla [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] debugowania scenariuszy:  
  
- Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i aplikacji sieci Web, uruchom na tym samym komputerze. Istnieją dwie wersje tego scenariusza:  
  
    - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Kod znajduje się w systemie plików.  
  
    - [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Kod znajduje się w witrynie sieci Web usług IIS.  
  
- Zdalne debugowanie, w którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] działa na komputerze klienckim i debugować aplikację internetową, która jest uruchomiona na komputerze serwera zdalnego.  
  
## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń  
 Zdalne debugowanie lokalne i zdalne komputery muszą należeć do Instalatora domeny lub grupy roboczej.  
  
 Aby debugować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego musi mieć uprawnienia do debugowania tego procesu. Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacje są uruchamiane jako **ASPNET** użytkownika. Jeśli proces roboczy jest uruchomione jako **ASPNET**, lub jako **Usługa sieciowa**, musi mieć uprawnienia administratora, aby go debugować.  
  
 Nazwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy zmienia się przez scenariusz debugowania i wersję usług IIS. Aby uzyskać więcej informacji, zobacz [jak: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Można zmienić użytkownika konta, do którego [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces działa, edytując plik machine.config na serwerze, na którym działa program IIS. Najlepszym sposobem, w tym celu jest użycie **Internet Information Services (IIS) Manager**. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Jeśli zmienisz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego w ramach własnego konta użytkownika, nie masz uprawnienia administratora na serwerze, na którym działa program IIS.  
  
> [!CAUTION]
>  Zanim będzie można zmienić [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] do uruchamiania przy użyciu innego konta, procesu roboczego należy wziąć pod uwagę ewentualne konsekwencje Jeśli [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego powinien stać się celem ataku podczas pracy w ramach tego konta. Konta użytkowników ASPNET i usługa sieci uruchomić z minimalnymi uprawnieniami, zmniejszając ryzyko uszkodzenia, jeśli proces jest włamania. Jeśli musisz zmienić [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces uruchamiany w kontekście konta mającego większe uprawnienia potencjalne szkody jest większa.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Instrukcje: Uruchamianie procesu roboczego z konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
