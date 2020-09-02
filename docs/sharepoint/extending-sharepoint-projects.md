---
title: Rozszerzanie projektów programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967484"
---
# <a name="extend-sharepoint-projects"></a>Zwiększ projekty programu SharePoint
  Utwórz rozszerzenie projektu, jeśli chcesz dostosować funkcje na poziomie projektu dla projektów programu SharePoint. Na przykład możesz dodać niestandardowe właściwości projektu lub odpowiedzieć na zdarzenia na poziomie projektu, które są wywoływane, gdy użytkownik opracowuje rozwiązanie SharePoint w programie Visual Studio.

## <a name="create-project-extensions"></a>Tworzenie rozszerzeń projektu
 Aby rozszerzać element projektu, skompiluj zestaw rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejs. Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Podczas tworzenia rozszerzenia projektu można także dodać następujące funkcje do projektów programu SharePoint:

- Dodaj element menu skrótów. Element menu pojawia się po otwarciu menu skrótów dla węzła projektu programu SharePoint w **Eksplorator rozwiązań** przez kliknięcie prawym przyciskiem myszy węzła lub wybranie go, a następnie wybranie klawiszy **SHIFT** + **F10** . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie elementu menu skrótów do projektów programu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Dodaj właściwość niestandardową. Właściwość pojawia się w oknie **Właściwości** w przypadku wybrania projektu programu SharePoint w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Aby zapoznać się z przewodnikiem, który pokazuje, jak utworzyć, wdrożyć i przetestować rozszerzenie projektu, zobacz [Przewodnik: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Zrozumienie relacji między rozszerzeniami projektu i wystąpieniami projektu
 Podczas tworzenia rozszerzenia projektu rozszerzenie jest ładowane, gdy dowolny rodzaj projektu programu SharePoint jest otwarty w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera kilka szablonów projektu programu SharePoint, takich jak definicje list, typy zawartości i odbiorcy zdarzeń. Istnieje jednak tylko jeden typ projektu programu SharePoint. Typy projektów, które pojawiają się w oknie dialogowym **Nowy projekt** , są tylko szablonami, które łączą się z co najmniej jednym elementem projektu programu SharePoint. Ponieważ istnieje tylko jeden typ projektu programu SharePoint, rozszerzenia utworzone dla jednego projektu są stosowane do wszystkich projektów programu SharePoint. Nie można na przykład utworzyć rozszerzenia, które ma zastosowanie tylko do projektu **typu zawartości** .

 Aby uzyskać dostęp do określonego wystąpienia projektu, należy obsłużyć jedno z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> zdarzeń parametru *projectService* w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody. Na przykład, aby określić, kiedy projekt programu SharePoint jest dodawany do rozwiązania, należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzenie. Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Instrukcje: Dodawanie elementu menu skrótów do projektów programu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Instrukcje: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Przewodnik: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
