---
title: Definiowanie niestandardowych typów elementów projektu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5f32abba4c4cbdeab59ed66e38019d913e704e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580787"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definiowanie niestandardowych typów elementów projektu SharePoint
  Zdefiniuj nowy typ elementu projektu programu SharePoint, gdy chcesz utworzyć nowy rodzaj elementu projektu programu SharePoint. Na przykład program Visual Studio nie zawiera elementów projektu programu SharePoint do dodawania pól lub akcji niestandardowych do witryny programu SharePoint. Można definiować własne typy elementów projektu programu SharePoint do tworzenia pól, akcji niestandardowych lub innych typów składników programu SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Zadania definiowania typów elementów projektu SharePoint
 Aby zdefiniować niestandardowy typ elementu projektu, skompiluj zestaw rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejs. Aby uzyskać więcej informacji, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Podczas definiowania niestandardowego typu elementu projektu można również dodać następujące funkcje do elementu projektu:

- Dodaj element menu skrótów do elementu projektu. Element menu pojawia się po otwarciu menu skrótów dla elementu projektu w **Eksplorator rozwiązań** przez kliknięcie prawym przyciskiem myszy elementu projektu lub wybranie go, a następnie wybranie klawiszy **SHIFT** + **F10** . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie elementu menu skrótów do niestandardowego typu elementu projektu programu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Dodaj właściwość niestandardową do elementu projektu. Właściwość pojawia się w oknie **Właściwości** po wybraniu elementu projektu w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu programu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Aby umożliwić innym deweloperom używanie elementu projektu w programie Visual Studio, Utwórz plik. spdata i Utwórz szablon elementu lub szablon projektu, który jest skojarzony z elementem projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Zrozumienie relacji między typami elementów projektu i wystąpieniami elementów projektu
 Podczas definiowania typu elementu projektu SharePoint program Visual Studio ładuje rozszerzenie, gdy element projektu skojarzonego typu zostanie dodany do projektu programu SharePoint. Na przykład, jeśli zdefiniujesz nowy typ elementu projektu **akcji niestandardowej** , program Visual Studio ładuje rozszerzenie, gdy użytkownik doda niestandardowy element projektu **akcji** do projektu. Program Visual Studio używa tego samego wystąpienia rozszerzenia dla wszystkich wystąpień skojarzonego typu elementu projektu. W poprzednim przykładzie, jeśli użytkownik doda drugi element projektu **akcji niestandardowej** do projektu, to to samo wystąpienie rozszerzenia służy do dostosowywania drugiego elementu projektu.

 Aby uzyskać dostęp do określonego wystąpienia typu elementu projektu, należy obsłużyć jedno z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzeń parametru *ProjectItemTypeDefinition* w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Na przykład, aby określić, kiedy element projektu typu niestandardowego zostanie dodany do projektu, obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzenie. Aby uzyskać więcej informacji, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie elementu menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Przewodnik: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
