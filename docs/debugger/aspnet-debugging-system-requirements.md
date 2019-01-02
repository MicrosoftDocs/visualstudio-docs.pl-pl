---
title: 'Debugowanie ASP.NET: Wymagania systemowe | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 334f2887b85cf0c58ace27cfca65984b29067246
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824041"
---
# <a name="aspnet-debugging-system-requirements"></a>Debugowanie ASP.NET: Wymagania systemowe
W tym temacie opisano wymagania dotyczące oprogramowania i zabezpieczeń dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debugowania scenariuszy:  
  
- Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i aplikacji sieci Web, uruchom na tym samym komputerze. Istnieją dwie wersje tego scenariusza:  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod znajduje się w systemie plików.  
  
  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Kod znajduje się w witrynie sieci Web usług IIS.  
  
- Zdalne debugowanie, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] działa na komputerze klienckim i debugować aplikację internetową, która jest uruchomiona na komputerze serwera zdalnego.  
  
## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń  
 Zdalne debugowanie lokalne i zdalne komputery muszą należeć do Instalatora domeny lub grupy roboczej.  
  
 Aby debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy (obsługiwanych przez pulę aplikacji), musi mieć uprawnienia do debugowania tego procesu. Domyślnie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji przed ich usług IIS 6.0, Uruchom jako **ASPNET** użytkownika. W usługach IIS 6.0 i IIS 7.0 **Usługa sieciowa** konta jest ustawieniem domyślnym. Jeśli proces roboczy jest uruchomione jako **ASPNET**, lub jako **Usługa sieciowa**, musi mieć uprawnienia administratora, aby go debugować.

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2, firma Microsoft zaleca użycie [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako tożsamość, dla każdej puli aplikacji.
  
 Nazwa [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy zmienia się przez scenariusz debugowania i wersję usług IIS. Aby uzyskać więcej informacji, zobacz [jak: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Można zmienić użytkownika konta, do którego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces działa, edytując plik machine.config na serwerze, na którym działa program IIS. Najlepszym sposobem, w tym celu jest użycie **Internet Information Services (IIS) Manager**. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Jeśli zmienisz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego w ramach własnego konta użytkownika, nie masz uprawnienia administratora na serwerze, na którym działa program IIS.  
  
> [!CAUTION]
>  Zanim będzie można zmienić [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] do uruchamiania przy użyciu innego konta, procesu roboczego należy wziąć pod uwagę ewentualne konsekwencje Jeśli [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego powinien stać się celem ataku podczas pracy w ramach tego konta. Konta użytkowników ASPNET i usługa sieci uruchomić z minimalnymi uprawnieniami, zmniejszając ryzyko uszkodzenia, jeśli proces jest włamania. Jeśli musisz zmienić [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces uruchamiany w kontekście konta mającego większe uprawnienia potencjalne szkody jest większa.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Instrukcje: Uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)