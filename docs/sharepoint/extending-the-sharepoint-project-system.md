---
title: Rozszerzanie systemu projektu programu SharePoint | Microsoft Docs
description: Zwiększ system projektu programu SharePoint. Dowiedz się, jak rozłożyć system projektu programu SharePoint. Informacje o typowych zadaniach programistycznych.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c017217f66e38eed6248b90efaeabce0efaa9c70
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672551"
---
# <a name="extend-the-sharepoint-project-system"></a>Poszerzanie systemu projektu SharePoint
  Rozwiązania programu SharePoint można tworzyć przy użyciu zestawu szablonów projektu i szablonów elementów w programie Visual Studio. Te szablony spełniają wymagania wielu scenariuszy programistycznych, ale mogą zostać wykryte sytuacje, w których nie zapewniają potrzebnych funkcji. W takich przypadkach można rozszerzyć system projektu programu SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Przegląd systemu projektu programu SharePoint
 System projektu programu SharePoint jest oparty na podstawowym składniku *elementów projektu programu SharePoint*. Element projektu programu SharePoint reprezentuje pojedyncze dostosowanie programu SharePoint, takie jak definicja listy, składnik Web Part lub typ zawartości.

 Projekt programu SharePoint jest projektem programu Visual Studio, który zawiera co najmniej jeden element projektu programu SharePoint. Projekty programu SharePoint zawierają również dodatkowe składniki, które definiują sposób grupowania elementów projektu w funkcje i pakiety do wdrożenia.

 Aby uzyskać więcej informacji na temat zawartości elementów projektu programu SharePoint i projektów programu SharePoint, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Jak zwiększyć system projektu programu SharePoint
 System projektu programu SharePoint można rozłożyć na następujące sposoby:

- Zdefiniuj własne typy elementów projektu programu SharePoint i skojarz je z nowymi szablonami elementów lub szablonami projektu w programie Visual Studio. Na przykład można zdefiniować typ elementu projektu programu SharePoint do tworzenia niestandardowej akcji lub pola. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Zwiększ typy elementów projektu programu SharePoint, które są już zainstalowane w programie Visual Studio. Na przykład można dodać element menu skrótów do elementu projektu w **Eksplorator rozwiązań** i dostosować element projektu, gdy deweloper wybierze element menu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając elementy projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Rozszerzając projekty programu SharePoint. Można na przykład dodać procedury obsługi zdarzeń w celu wykonywania określonych zadań, gdy elementy są dodawane lub usuwane z projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [rozszerzając projekty programu SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Zwiększ zachowanie pakowania i wdrażania elementów projektu programu SharePoint i projektów programu SharePoint. Można na przykład utworzyć własne kroki wdrażania, które mają zostać wykonane podczas wdrażania lub wycofywania projektu, lub wykonać dodatkowe zadania niestandardowe, gdy program Visual Studio wykonuje pewne kroki wdrożenia. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Typowe zadania programistyczne
 W rozszerzeniach systemu projektu programu SharePoint można wykonać następujące typowe zadania:

- Zapisz dane niestandardowego ciągu z elementami projektu i w kilku różnych typach plików projektu. Aby uzyskać więcej informacji, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Przekonwertuj obiekt w systemie projektu SharePoint na odpowiedni obiekt w modelu obiektów automatyzacji programu Visual Studio lub modelu obiektów integracji lub odwrotnie. Aby uzyskać więcej informacji, zobacz [skonwer między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Zobacz także
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Zwiększ projekty programu SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
