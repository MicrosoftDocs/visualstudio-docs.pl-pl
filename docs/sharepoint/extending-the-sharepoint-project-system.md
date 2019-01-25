---
title: Rozszerzanie systemu projektu programu SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9f461cae21dfd43bb8fb1d78af65e0ea234d0100
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869268"
---
# <a name="extend-the-sharepoint-project-system"></a>Rozszerzanie systemu projektu SharePoint
  Możesz tworzyć rozwiązania programu SharePoint przy użyciu zestawu szablonów elementów i szablonów projektu w programie Visual Studio. Te szablony wymagań wiele scenariuszy programowania, ale można wykryć niektórych przypadkach, gdy nie zapewniają funkcji, która jest wymagana. W takich przypadkach można rozszerzyć systemu projektu programu SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Omówienie systemu projektu SharePoint
 System projektu programu SharePoint opiera się na podstawowym składnikiem *elementów projektu programu SharePoint*. Element projektu programu SharePoint reprezentuje pojedynczy dostosowywania programu SharePoint, takich jak definicji listy, składnik Web Part lub typu zawartości.  
  
 Projekt SharePoint jest projekt programu Visual Studio, który zawiera jeden lub więcej elementów projektu programu SharePoint. Projekty programu SharePoint zawiera również dodatkowe składniki, które definiują, jak elementy projektu są grupowane w funkcji i pakietów dla wdrożenia.  
  
 Aby uzyskać więcej informacji o zawartości elementów projektu programu SharePoint i projektów programu SharePoint, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Jak rozszerzyć systemu projektu SharePoint
 Możesz rozszerzyć systemu projektu programu SharePoint w następujący sposób:  
  
-   Definiowanie własnych typów elementów projektu programu SharePoint i skojarzyć je z nowych szablonów elementów i szablonów projektu w programie Visual Studio. Na przykład można zdefiniować typ elementu projektu programu SharePoint do tworzenia akcji niestandardowej lub pola. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Rozszerz typów elementów projektu SharePoint, które są już zainstalowane w programie Visual Studio. Na przykład można dodać element menu skrótów do elementu projektu w **Eksploratora rozwiązań** i dostosowywanie elementu projektu, gdy deweloper wybierze element menu. Aby uzyskać więcej informacji, zobacz [elementów projektu programu SharePoint z rozszerzenia](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Rozszerzanie projektów SharePoint. Na przykład można dodać procedury obsługi zdarzeń do wykonywania określonych zadań, gdy elementy są dodawane lub usuwane z projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [projektów SharePoint rozszerzyć](../sharepoint/extending-sharepoint-projects.md).  
  
-   Rozszerzanie pakowania i wdrażania zachowanie elementów projektu programu SharePoint i projektów programu SharePoint. Na przykład można utworzyć własne kroki wdrażania do wykonania podczas wdrażania lub wycofać projektu lub można wykonywać dodatkowe zadania niestandardowe podczas Visual Studio wykonuje pewne kroki wdrażania. Aby uzyskać więcej informacji, zobacz [pakowaniem i wdrażaniem SharePoint rozszerzyć](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Typowe zadania rozwoju
 W rozszerzeniach systemu projektu programu SharePoint, można wykonywać następujące typowe zadania:  
  
-   Zapisz niestandardowy ciąg danych, z elementami projektu i w kilku różnych typach plików projektu. Aby uzyskać więcej informacji, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Konwertowanie obiektu w systemie projektu programu SharePoint do odpowiedniego obiektu w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, lub na odwrót. Aby uzyskać więcej informacji, zobacz [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Zobacz także
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Rozszerzanie elementów projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
