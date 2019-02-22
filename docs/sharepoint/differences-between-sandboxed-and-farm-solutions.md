---
title: Różnice między piaskownicy oraz rozwiązaniami farmy | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596650"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Różnice między piaskownicy oraz rozwiązaniami farmy
  Podczas kompilowania rozwiązania programu SharePoint, wdraża ją do serwera programu SharePoint i debuger dołącza do debugowania. Proces używany do debugowania rozwiązania zależy od ustawienia właściwości rozwiązanie w trybie piaskownicy: rozwiązanie w trybie piaskownicy lub rozwiązaniu farmy.

 Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Rozwiązania farmy
 Rozwiązania farmy, które są hostowane w procesie roboczym usług IIS (W3WP.exe), uruchomić kod, który może mieć wpływ na całej farmy. Podczas debugowania projektu programu SharePoint, w których właściwość rozwiązanie w trybie piaskownicy ma wartość "rozwiązania farmy" puli aplikacji usług IIS systemu odtwarza przed SharePoint wycofuje lub wdraża funkcję tak, aby zwolnić wszystkie pliki zablokowane przez proces roboczy usług IIS. Tylko puli aplikacji usług IIS obsługujących adres URL witryny projektu programu SharePoint zostanie odtworzona.

## <a name="sandboxed-solutions"></a>Rozwiązania piaskownicy
 Rozwiązania w trybie piaskownicy, które znajdują się w programie SharePoint użytkownika kodu rozwiązania procesu roboczego (SPUCWorkerProcess.exe), uruchomić kod, który tylko może mieć wpływ na zbiorze witryn rozwiązania. Ponieważ rozwiązania w trybie piaskownicy nie są uruchamiane w proces roboczy usług IIS, pula aplikacji usług IIS ani na serwerze usług IIS nie wymaga ponownego uruchomienia. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger do procesu SPUCWorkerProcess, wyzwalającego automatycznie usługa SPUserCodeV4 w programie SharePoint i kontroli. Nie jest konieczne do SPUCWorkerProcess w procesie roboczym do załadowania najnowszej wersji rozwiązania.

## <a name="either-type-of-solution"></a>Dowolnego typu rozwiązania
 Za pomocą dowolnego typu rozwiązania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] również dołącza debuger do przeglądarki, aby włączyć debugowanie skryptów po stronie klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa tego skryptu w aparacie, w tym celu debugowania. Aby włączyć debugowanie skryptów, możesz zmienić ustawienie domyślnej przeglądarki po wyświetleniu monitu.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger tylko procesy W3WP lub SPUCWorkerProcess uruchomione bieżącej lokacji. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza również zarządzane modelu COM Plus i aparaty debugowania przepływów pracy.

## <a name="see-also"></a>Zobacz także
- [Debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)
