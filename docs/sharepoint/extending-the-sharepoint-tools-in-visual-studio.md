---
title: Rozszerzanie narzędzi programu SharePoint w programie Visual Studio | Microsoft Docs
description: Rozwiń narzędzia programu SharePoint w programie Visual Studio. Zwiększ system projektu programu SharePoint. Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a921f45ea151ce7ee3313dba47e81a5acc86063d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672629"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Poszerzanie narzędzi programu SharePoint w programie Visual Studio
  Narzędzia programu SharePoint w programie Visual Studio spełniają wymagania wielu scenariuszy tworzenia aplikacji. Można jednak odkryć przypadki, w których nie udostępniają one funkcji, które są wymagane przez użytkownika lub innych deweloperów. W takich przypadkach można rozwinąć narzędzia programu SharePoint w celu utworzenia potrzebnych funkcji.

## <a name="how-to-extend-the-sharepoint-tools"></a>Jak rozłożyć narzędzia programu SharePoint
 W oknie **Eksplorator serwera** można rozwinąć System projektu programu SharePoint i węzeł **połączenia programu SharePoint** .

### <a name="extend-the-sharepoint-project-system"></a>Poszerzanie systemu projektu SharePoint
 Program Visual Studio zawiera zestaw szablonów projektu i szablonów elementów, których można użyć do tworzenia rozwiązań programu SharePoint. Na przykład istnieją szablony dla odbiorców zdarzeń, definicje list, przepływy pracy i składniki Web Part. Można jednak definiować własne typy elementów projektu programu SharePoint do tworzenia składników programu SharePoint, takich jak pola lub akcje niestandardowe. Można również tworzyć rozszerzenia dla typów elementów projektu programu SharePoint, które są już zainstalowane w programie Visual Studio, i można tworzyć rozszerzenia dla projektów programu SharePoint.

 Aby uzyskać więcej informacji, zobacz Rozpoznaj [system projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera
 W programie Visual Studio można użyć węzła **połączenia programu SharePoint** w oknie **Eksplorator serwera** , aby wyświetlić wiele składników jednej lub wielu lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Możesz również zwiększyć węzeł **połączenia SharePoint** w następujący sposób:

- Dodając własne węzły. Jest to przydatne, jeśli chcesz wyświetlać składniki witryn programu SharePoint, które nie są wyświetlane domyślnie.

- Rozszerzając istniejące węzły. Na przykład można dodać nowy węzeł podrzędny do istniejącego węzła lub dodać element menu skrótów do węzła i wykonać zadania, gdy deweloper kliknie element menu.

  Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Wymagania dotyczące komputera deweloperskiego
 Aby można było tworzyć rozszerzenia dla narzędzi programu SharePoint, komputer deweloperski musi spełniać te same wymagania dotyczące tworzenia rozwiązań programu SharePoint w programie Visual Studio.

 Zalecamy również zainstalowanie programu [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . Zestaw SDK zawiera szablony i narzędzia projektu, których można użyć do rozszerania programu Visual Studio. W szczególności zestaw SDK zawiera szablon projektu, którego można użyć do łatwego tworzenia pakietu Visual Studio Extension (VSIX). Pakiety VSIX są preferowanym sposobem wdrożenia rozszerzeń programu Visual Studio w programie Visual Studio. Wszystkie rozszerzenia narzędzi programu SharePoint muszą zostać wdrożone przy użyciu pakietów VSIX. We wszystkich przewodnikach w tej dokumentacji założono, że [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] zainstalowano program.

 Aby zainstalować zestaw Visual Studio SDK, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Aby uzyskać więcej informacji na temat rozszerzeń programu Visual Studio, zobacz [Rozpoczynanie tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Zobacz także

- [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Koncepcje programowania i funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Dokumentacja &#40;rozszerzalności narzędzi programu SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)