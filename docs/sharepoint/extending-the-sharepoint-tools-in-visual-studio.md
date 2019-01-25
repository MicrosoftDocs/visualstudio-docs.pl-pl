---
title: Rozszerzanie narzędzi SharePoint w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7d70d9b5bac260dc0731d06ebb11780114f0edf5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867172"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Rozszerzanie narzędzi SharePoint w programie Visual Studio
  Narzędzia programu SharePoint w programie Visual Studio wymagań wiele scenariuszy programowania aplikacji. Jednak można wykryć przypadki, w którym nie zapewniają funkcji, które wymagają zostanie lub innym deweloperom. W takich przypadkach można rozszerzyć narzędzia programu SharePoint do tworzenia potrzebne funkcje.

## <a name="how-to-extend-the-sharepoint-tools"></a>Jak Rozszerzanie narzędzi SharePoint
 Możesz rozszerzyć systemu projektu programu SharePoint i **połączeń SharePoint** w węźle **Eksploratora serwera** okna.

### <a name="extend-the-sharepoint-project-system"></a>Rozszerzanie systemu projektu SharePoint
 Visual Studio zawiera zestaw szablonów projektów i szablonów elementów, które umożliwia tworzenie rozwiązań programu SharePoint. Na przykład istnieją szablony dla odbiorcy zdarzeń, definicje list, przepływów pracy i składniki Web Part. Jednakże można także zdefiniować własne typy elementów projektu programu SharePoint do tworzenia składników programu SharePoint, takich jak pola lub akcje niestandardowe. Można również utworzyć rozszerzenia dla typów elementów projektu SharePoint, które są już zainstalowane w programie Visual Studio, a następnie można utworzyć rozszerzenia dla projektów programu SharePoint.

 Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera
 W programie Visual Studio, można użyć **połączeń SharePoint** w węźle **Eksploratora serwera** okna, aby wyświetlić wiele składników w jednej lub więcej lokalnych witryn programu SharePoint w hierarchicznym widoku drzewa. Można także rozszerzyć **połączeń SharePoint** węzła w następujący sposób:

- Przez dodanie własnych węzłów. Jest to przydatne, jeśli chcesz wyświetlić składniki witryny programu SharePoint, które nie są wyświetlane domyślnie.

- Rozszerzając istniejących węzłów. Na przykład można dodać nowego węzła podrzędnego do istniejącego węzła lub można dodać element menu skrótów dla węzła i wykonywać zadania, gdy deweloper kliknie element menu.

  Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Wymagania dotyczące komputera rozwoju
 Aby utworzyć rozszerzeń dla narzędzi SharePoint, komputer deweloperski musi spełniać te same wymagania dotyczące tworzenia rozwiązań programu SharePoint w Visual Studio.

 Firma Microsoft zaleca również zainstalowanie [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Zestaw SDK zawiera szablony projektów i narzędzi, które służą do rozszerzenia programu Visual Studio. W szczególności zestaw SDK zawiera szablon projektu, który umożliwia łatwe tworzenie pakietu Visual Studio rozszerzenia (VSIX). Pakiety VSIX są preferowanym sposobem wdrażania rozszerzeń programu Visual Studio w programie Visual Studio. Wszystkie rozszerzenia narzędzi programu SharePoint musi zostać wdrożony za pomocą pakietów VSIX. Wszystkie przewodniki w tej dokumentacji założono, że [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] zainstalowane.

 Aby zainstalować program Visual Studio SDK, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Aby uzyskać więcej informacji na temat rozszerzeń programu Visual Studio, zobacz [Rozpoczynanie tworzenia rozszerzeń programu Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Zobacz także

- [Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Odwołanie &#40;rozszerzalność narzędzi SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)