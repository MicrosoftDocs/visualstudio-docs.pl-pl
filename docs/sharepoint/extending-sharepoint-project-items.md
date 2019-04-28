---
title: Rozszerzanie pozycji projektu SharePoint | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967399"
---
# <a name="extend-sharepoint-project-items"></a>Rozszerzanie elementów projektu programu SharePoint
  Tworzenie rozszerzenia elementu projektu, jeśli chcesz dodać funkcje do typu elementu projektu programu SharePoint, która jest już zainstalowana w programie Visual Studio. Na przykład można utworzyć rozszerzenia dla wbudowanej **odbiorcy zdarzeń** lub **definicji listy** elementy projektu w programie Visual Studio lub można utworzyć rozszerzenia dla typu elementu niestandardowego projektu. Można również utworzyć rozszerzenia dla wszystkich typów elementów projektu programu SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Zadania dla rozszerzanie pozycji projektu SharePoint
 Tworzenie zestawu rozszerzeń programu Visual Studio, który implementuje rozszerzenie elementu projektu, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Rozszerzenie elementu projektu, można również dodać następujące funkcje do elementu projektu:

- Dodaj element menu skrótów do elementu projektu. Element menu pojawia się po otwarciu menu skrótów dla elementu projektu w **Eksploratora rozwiązań**. Otwórz menu skrótów, klikając prawym przyciskiem myszy element projektu lub wybierając je, a następnie wybierając **Shift**+**F10** kluczy. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie pozycji menu skrótów do rozszerzenia elementu projektu programu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Dodawanie właściwości niestandardowych do elementu projektu. Właściwość pojawia się w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Aby uzyskać wskazówki, które pokazuje, jak tworzenie, wdrażanie i testowanie rozszerzenia elementu projektu, zobacz [instruktażu: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Zrozumienie relacji między rozszerzenia elementu projektu i wystąpienia elementów projektu
 Podczas tworzenia rozszerzenia elementu projektu programu Visual Studio wczytuje Twojego rozszerzenia, gdy element projektu o skojarzony typ zostanie dodany do projektu programu SharePoint. Na przykład, jeśli tworzysz rozszerzenie **odbiorcy zdarzeń** elementów projektu programu Visual Studio wczytuje Twojego rozszerzenia, gdy użytkownik doda **odbiorcy zdarzeń** element projektu do projektu. Visual Studio używa tego samego wystąpienia rozszerzenia dla wszystkich wystąpień tego typu elementu skojarzonego projektu. W poprzednim przykładzie, jeśli użytkownik doda sekundy **odbiorcy zdarzeń** element projektu do projektu, to samo wystąpienie elementu rozszerzenia jest używany do dostosowywania drugiego elementu projektu.

 Dostęp do określonego wystąpienia typu elementu projektu, rozszerzania, obsługiwać jeden z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia *projectItemType* parametru w danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody. Na przykład, aby określić, kiedy rozszerzania typu elementu projektu jest dodawany do projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> zdarzeń. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identyfikatory elementów projektu programu SharePoint
 Każdy element projektu programu SharePoint ma odpowiedni identyfikator ciągu. Identyfikator elementu projektu musisz wiedzieć, aby wykonać następujące zadania:

- Tworzenie rozszerzenia elementu projektu. W takim przypadku należy przekazać identyfikator dla elementu projektu, który ma zostać rozszerzony do konstruktora <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby utworzyć rozszerzenie elementu projektu wszystkie typy, należy przekazać **\\*** wartość ciągu.

- Programowe Dodawanie elementu projektu do projektu. W takim przypadku należy przekazać identyfikator dla elementu projektu, aby <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> metody.

  Poniższa tabela zawiera listę identyfikatorów dla elementów projektu programu SharePoint, które są dołączone do programu Visual Studio.

|Nazwa elementu projektu|Identyfikator ciągu|
|-----------------------|-----------------------|
|Model katalogu danych biznesowych|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|
|Typ zawartości|Microsoft.VisualStudio.SharePoint.ContentType|
|Odbiorcy zdarzeń|Microsoft.VisualStudio.SharePoint.EventHandler|
|Pusty Element|Microsoft.VisualStudio.SharePoint.GenericElement|
|Definicja listy<br /><br /> Definicja listy z typu zawartości|Microsoft.VisualStudio.SharePoint.ListDefinition|
|Wystąpienia listy|Microsoft.VisualStudio.SharePoint.ListInstance|
|Moduł|Microsoft.VisualStudio.SharePoint.Module|
|Sekwencyjny przepływ pracy<br /><br /> Przepływ pracy automatu stanów|Microsoft.VisualStudio.SharePoint.Workflow|
|Definicji witryny|Microsoft.VisualStudio.SharePoint.SiteDefinition|
|Wizualny składnik Web Part|Microsoft.VisualStudio.SharePoint.VisualWebPart|
|Web Part|Microsoft.VisualStudio.SharePoint.WebPart|
|Formularz skojarzenia przepływu pracy|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie pozycji menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
