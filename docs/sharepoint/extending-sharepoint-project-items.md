---
title: Rozszerzanie elementów projektu programu SharePoint | Microsoft Docs
description: Przejrzyj zadania rozszerzające elementy projektu programu SharePoint. Zrozumienie, jak są powiązane rozszerzenia elementów projektu i wystąpienia elementów projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e8486120b0f08077bc30c2a5177a8aba915c37f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948677"
---
# <a name="extend-sharepoint-project-items"></a>Zwiększ elementy projektu SharePoint
  Utwórz rozszerzenie elementu projektu, gdy chcesz dodać funkcję do typu elementu projektu programu SharePoint, który jest już zainstalowany w programie Visual Studio. Na przykład można utworzyć rozszerzenie dla wbudowanego **odbiorcy zdarzeń** lub **definicji listy** elementów projektu w programie Visual Studio lub można utworzyć rozszerzenie dla niestandardowego typu elementu projektu. Można również utworzyć rozszerzenie dla wszystkich typów elementów projektu programu SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Zadania rozszerzania elementów projektu programu SharePoint
 Aby rozszerzać element projektu, skompiluj zestaw rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejs. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Rozszerzając element projektu, można również dodać następujące funkcje do elementu projektu:

- Dodaj element menu skrótów do elementu projektu. Element menu pojawia się po otwarciu menu skrótów dla elementu projektu w **Eksplorator rozwiązań**. Aby otworzyć menu skrótów, kliknij prawym przyciskiem myszy element projektu lub wybierz go, a następnie wybierz klawisze **SHIFT** + **F10** . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie elementu menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Dodaj właściwość niestandardową do elementu projektu. Właściwość pojawia się w oknie **Właściwości** po wybraniu elementu projektu w **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Aby zapoznać się z przewodnikiem, który pokazuje, jak utworzyć, wdrożyć i przetestować rozszerzenie elementu projektu, zobacz [Przewodnik: rozszerzanie typu elementu projektu programu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Zrozumienie relacji między rozszerzeniami elementów projektu i wystąpieniami elementów projektu
 Gdy tworzysz rozszerzenie elementu projektu, program Visual Studio ładuje rozszerzenie, gdy element projektu skojarzonego typu jest dodawany do projektu programu SharePoint. Jeśli na przykład utworzysz rozszerzenie dla elementów projektu **odbiorcy zdarzeń** , program Visual Studio ładuje rozszerzenie, gdy użytkownik doda element projektu **odbiorcy zdarzeń** do projektu. Program Visual Studio używa tego samego wystąpienia rozszerzenia dla wszystkich wystąpień skojarzonego typu elementu projektu. W poprzednim przykładzie, jeśli użytkownik doda drugi element projektu **odbiorcy zdarzeń** do projektu, to to samo wystąpienie rozszerzenia służy do dostosowywania drugiego elementu projektu.

 Aby uzyskać dostęp do konkretnego wystąpienia typu elementu projektu, który jest rozszerzany, należy obsłużyć jedno z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzeń parametru *projectItemType* w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody. Na przykład, aby określić, kiedy element projektu typu, który ma zostać rozszerzony, jest dodawany do projektu, obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzenie. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identyfikatory dla elementów projektu programu SharePoint
 Każdy element projektu programu SharePoint ma odpowiedni identyfikator ciągu. Należy znać identyfikator elementu projektu, jeśli chcesz wykonać następujące zadania:

- Utwórz rozszerzenie dla elementu projektu. W takim przypadku należy przekazać identyfikator elementu projektu, który ma zostać rozbudowany do konstruktora <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Aby utworzyć rozszerzenie dla wszystkich typów elementów projektu, należy przekazać **\\** * wartość ciągu.

- Programowo Dodaj element projektu do projektu. W takim przypadku należy przekazać identyfikator dla elementu projektu do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metody.

  W poniższej tabeli przedstawiono identyfikatory elementów projektu programu SharePoint, które są dołączone do programu Visual Studio.

|Nazwa elementu projektu|Identyfikator ciągu|
|-----------------------|-----------------------|
|Model Data Catalog firmy|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Typ zawartości|Microsoft. VisualStudio. SharePoint. ContentType|
|Odbiorca zdarzeń|Microsoft. VisualStudio. SharePoint. EventHandler|
|Pusty element|Microsoft. VisualStudio. SharePoint. Genericelement|
|Definicja listy<br /><br /> Definicja listy z typu zawartości|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Wystąpienie listy|Microsoft. VisualStudio. SharePoint. ListInstance|
|Moduł|Microsoft. VisualStudio. SharePoint. module|
|Sekwencyjny przepływ pracy<br /><br /> Przepływ pracy automatu Stanów|Microsoft. VisualStudio. SharePoint. Workflow|
|Definicja lokacji|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Wizualny składnik Web Part|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Web Part|Microsoft. VisualStudio. SharePoint. WebPart|
|Formularz skojarzenia przepływu pracy|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie elementu menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
