---
title: 'Debugowanie ASP.NET: Wymagania systemowe | Microsoft Docs'
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 78f947c7ab9fcc1031d457526240ecdd7e9119a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745809"
---
# <a name="aspnet-debugging-system-requirements"></a>ASP.NET Debugowanie: wymagania systemu
W tym temacie opisano wymagania dotyczące oprogramowania i zabezpieczeń dotyczące [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] scenariuszy debugowania:

- Debugowanie lokalne, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i aplikacja sieci Web działa na tym samym komputerze. Istnieją dwie wersje tego scenariusza:

  - Kod [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] znajduje się w systemie plików.

  - Kod [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] znajduje się w witrynie sieci Web usług IIS.

- Zdalne debugowanie, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] działa na komputerze klienckim i debuguje aplikację sieci Web, która jest uruchomiona na komputerze serwera zdalnego.

## <a name="security-requirements"></a>Wymagania dotyczące zabezpieczeń
 W przypadku zdalnego debugowania na komputerach lokalnych i zdalnych musi znajdować się konfiguracja domeny lub Konfiguracja grupy roboczej.

 Aby debugować proces roboczy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (hostowany przez pulę aplikacji), musisz mieć uprawnienia do debugowania tego procesu. Domyślnie aplikacje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] przed usługami IIS 6,0 są uruchamiane jako użytkownik **ASPNET** . W usługach IIS 6,0 i IIS 7,0 konto **usługi sieciowej** jest domyślnie. Jeśli proces roboczy jest uruchomiony jako **ASPNET**lub jako **Usługa sieciowa**, musisz mieć uprawnienia administratora, aby go debugować.

 > [!IMPORTANT]
 > Począwszy od systemu Windows Server 2008 R2 zaleca się użycie [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) jako tożsamości dla każdej puli aplikacji.

 Nazwa procesu roboczego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zależy od scenariusza debugowania i wersji usług IIS. Aby uzyskać więcej informacji, zobacz [How to: find a Name the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).

 Można zmienić konto użytkownika, na którym działa proces roboczy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], edytując plik Machine. config na serwerze z uruchomionymi usługami IIS. Najlepszym sposobem jest użycie **menedżera Internet Information Services (IIS)** . Aby uzyskać więcej informacji, zobacz [jak: uruchamianie procesu roboczego w ramach konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md).

 Jeśli zmienisz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy na uruchomiony przy użyciu własnego konta użytkownika, nie musisz być administratorem na serwerze, na którym są uruchomione usługi IIS.

> [!CAUTION]
> Przed zmianą procesu roboczego [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] na inny należy wziąć pod uwagę ewentualne konsekwencje, jeśli proces roboczy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] powinien zostać zaatakowana podczas działania w ramach tego konta. Konta użytkowników ASPNET i NETWORK SERVICE działają z minimalnymi uprawnieniami, co zmniejsza możliwą szkodę, jeśli proces jest zaatakowana. Jeśli musisz zmienić proces roboczy [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] na konto, które ma większe uprawnienia, potencjalne uszkodzenie jest większe.

## <a name="see-also"></a>Zobacz także

- [Debuguj aplikacje ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Instrukcje: uruchamianie procesu roboczego z konta użytkownika](../debugger/how-to-run-the-worker-process-under-a-user-account.md)