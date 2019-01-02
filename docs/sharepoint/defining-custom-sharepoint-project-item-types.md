---
title: Definiowanie typów elementów projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4b678d0a4a148bbd8a7414c8a7585b50fbc9c01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855169"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definiowanie niestandardowych typów elementów projektu SharePoint
  Zdefiniuj nowy typ elementu projektu programu SharePoint utworzyć nowy typ elementu projektu programu SharePoint. Na przykład programu Visual Studio nie ma elementów projektu programu SharePoint do dodawania pól lub akcje niestandardowe w witrynie programu SharePoint. Można zdefiniować własne typy elementów projektu programu SharePoint do tworzenia pól, akcje niestandardowe lub inne składniki programu SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Zadania do definiowania typów elementów projektu SharePoint
 Aby zdefiniować typ elementu niestandardowego projektu, tworzenie zestawu rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Podczas definiowania typu elementu niestandardowego projektu, można również dodać następujące funkcje do elementu projektu:  
  
- Dodaj element menu skrótów do elementu projektu. Element menu pojawia się po otwarciu menu skrótów dla elementu projektu w **Eksploratora rozwiązań** przez kliknięcie prawym przyciskiem myszy element projektu lub wybierając go, a następnie wybierając **Shift** +  **F10** kluczy. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
- Dodawanie właściwości niestandardowych do elementu projektu. Właściwość pojawia się w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  Aby umożliwić innym deweloperom używanie element projektu w programie Visual Studio, Utwórz plik spdata i Utwórz szablon elementu lub szablon projektu, który jest skojarzony z elementem projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Zrozumienie relacji między typów elementów projektu i wystąpienia elementów projektu
 Podczas definiowania typu elementu projektu SharePoint, programu Visual Studio wczytuje Twojego rozszerzenia, gdy element projektu o skojarzony typ zostanie dodany do projektu programu SharePoint. Na przykład, jeśli zdefiniujesz nowe **Akcja niestandardowa** typu elementu projektu, Visual Studio wczytuje Twojego rozszerzenia, gdy użytkownik doda **Akcja niestandardowa** element projektu do projektu. Visual Studio używa tego samego wystąpienia rozszerzenia dla wszystkich wystąpień tego typu elementu skojarzonego projektu. W poprzednim przykładzie, jeśli użytkownik doda sekundy **Akcja niestandardowa** element projektu do projektu, to samo wystąpienie elementu rozszerzenia jest używany do dostosowywania drugiego elementu projektu.  
  
 Dostęp do określonego wystąpienia typu elementu projektu, obsługę jednej z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia *projectItemTypeDefinition* parametru w danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Na przykład, aby określić, kiedy niestandardowego typu elementu projektu zostanie dodany do projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Instrukcje: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
