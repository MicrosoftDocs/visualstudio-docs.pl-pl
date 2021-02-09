---
title: 'Debugowanie ASP.NET: Wymagania systemowe | Microsoft Docs'
description: Zapoznaj się z wymaganiami dotyczącymi oprogramowania i zabezpieczeń na potrzeby debugowania lokalnego ASP.NET, w którym program Visual Studio i aplikacja internetowa działają na tym samym komputerze, i zdalne debugowanie.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 8ab32e855ee93ceb328bc33340597ce65e3ee871
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866102"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Debugowanie: wymagania systemu
W tym temacie opisano wymagania dotyczące oprogramowania i zabezpieczeń dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] scenariuszy debugowania:

- Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aplikacja sieci Web jest uruchamiana na tym samym komputerze. Istnieją dwie wersje tego scenariusza:

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kod znajduje się w systemie plików.

  - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Kod znajduje się w witrynie sieci Web usług IIS.

- Zdalne debugowanie, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] działa na komputerze klienckim i debuguje aplikację sieci Web, która jest uruchomiona na komputerze serwera zdalnego.

## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń
 W przypadku zdalnego debugowania na komputerach lokalnych i zdalnych musi znajdować się konfiguracja domeny lub Konfiguracja grupy roboczej.

 Aby debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy (hostowany przez pulę aplikacji), musisz mieć uprawnienia do debugowania tego procesu. Domyślnie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje przed usługami IIS 6,0 są uruchamiane jako użytkownik **ASPNET** . W usługach IIS 6,0 i IIS 7,0 konto **usługi sieciowej** jest domyślnie. Jeśli proces roboczy jest uruchomiony jako **ASPNET** lub jako **Usługa sieciowa**, musisz mieć uprawnienia administratora, aby go debugować.

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2 zaleca się użycie [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako tożsamości dla każdej puli aplikacji.

 Nazwa [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego zależy od scenariusza debugowania i wersji usług IIS. Aby uzyskać więcej informacji, zobacz [How to: find a Name the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 Można zmienić konto użytkownika, na którym [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] działa proces roboczy, edytując plik machine.config na serwerze z uruchomionymi usługami IIS. Najlepszym sposobem jest użycie **menedżera Internet Information Services (IIS)**. Aby uzyskać więcej informacji, zobacz [jak: uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 Jeśli zmienisz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy na uruchomiony przy użyciu własnego konta użytkownika, nie musisz być administratorem na serwerze, na którym są uruchomione usługi IIS.

> [!CAUTION]
> Przed zmianą [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego w celu uruchomienia go przy użyciu innego konta należy wziąć pod uwagę ewentualne konsekwencje, jeśli [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy powinien zostać zaatakowana podczas działania w ramach tego konta. Konta użytkowników ASPNET i NETWORK SERVICE działają z minimalnymi uprawnieniami, co zmniejsza możliwą szkodę, jeśli proces jest zaatakowana. Jeśli musisz zmienić [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, aby był uruchamiany na koncie, które ma większe uprawnienia, to potencjalne uszkodzenie jest większe.

## <a name="see-also"></a>Zobacz też

- [Debuguj aplikacje ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instrukcje: uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)