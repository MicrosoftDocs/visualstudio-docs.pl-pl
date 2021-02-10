---
title: Różnice między rozwiązaniami w trybie piaskownicy a farmą | Microsoft Docs
description: Zapoznaj się z różnicami między rozwiązaniami w trybie piaskownicy a farmą. Dowiedz się, jak program Visual Studio podejścia do debugowania z dowolnego typu rozwiązania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cea66f313a8c6c8ad7fc390a3ca126d92139725c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948781"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Różnice między rozwiązaniami w trybie piaskownicy a farmą
  Podczas kompilowania rozwiązania programu SharePoint jest wdrażany na serwerze programu SharePoint, a debuger dołącza do jego debugowania. Proces używany do debugowania rozwiązania zależy od ustawienia właściwości rozwiązanie w trybie piaskownicy: rozwiązanie w trybie piaskownicy lub rozwiązanie farmy.

 Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Rozwiązania farmy
 Rozwiązania farmy, które są hostowane w procesie roboczym usług IIS (W3WP.exe), uruchamiają kod, który może mieć wpływ na całą farmę. Podczas debugowania projektu programu SharePoint, którego właściwość rozwiązanie w trybie piaskownicy jest ustawiona na "rozwiązanie farmy", Pula aplikacji usług IIS systemu jest odtwarzana przed wycofaniem lub wdrożeniem funkcji przez program SharePoint w celu zwolnienia plików zablokowanych przez proces roboczy usług IIS. Odtworzony jest tylko pula aplikacji IIS obsługująca adres URL witryny projektu programu SharePoint.

## <a name="sandboxed-solutions"></a>Rozwiązania w trybie piaskownicy
 Rozwiązania w trybie piaskownicy, które są hostowane w procesie roboczym rozwiązania kodu użytkownika programu SharePoint (SPUCWorkerProcess.exe), uruchamiają kod, który może mieć wpływ tylko na zbiór witryn tego rozwiązania. Ponieważ rozwiązania w trybie piaskownicy nie są uruchamiane w procesie roboczym usług IIS, nie trzeba ponownie uruchamiać puli aplikacji IIS ani serwera usług IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger do procesu SPUCWorkerProcess, który usługa SPUserCodeV4 w programie SharePoint automatycznie wyzwala i kontroluje. Proces SPUCWorkerProcess nie jest konieczny do odzyskania w celu załadowania najnowszej wersji rozwiązania.

## <a name="either-type-of-solution"></a>Oba typy rozwiązań
 Każdy typ rozwiązania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza również debuger do przeglądarki, aby włączyć debugowanie skryptu po stronie klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] w tym celu używa aparatu debugowania skryptów. Aby włączyć debugowanie skryptów, należy zmienić domyślne ustawienia przeglądarki po wyświetleniu monitu.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza debuger tylko do procesów W3WP lub SPUCWorkerProcess, w których działa bieżąca lokacja. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza także zarządzane aparaty debugowania modelu COM Plus i przepływu pracy.

## <a name="see-also"></a>Zobacz też
- [Debuguj rozwiązania programu SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md)
