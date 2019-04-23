---
title: 'Instrukcje: Dodawanie pozycji Menu skrótów do typu elementu projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 7de1bf04137c0e799e19e658307d630ec3fa6a78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068746"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Instrukcje: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu SharePoint, można dodać element menu skrótów do elementu projektu. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksploratora rozwiązań**.

 W następujących krokach założono, że swój własny typ elementu projektu programu SharePoint został już zdefiniowany. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Aby dodać element menu skrótów do typu elementu niestandardowego projektu

1. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody usługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji, uchwyt <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenia *projectItemTypeDefinition* parametru.

2. W sieci programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzeń, Dodaj nowy <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiekt <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> lub <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> zbiór parametr argumenty zdarzenia.

3. W <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> programu obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektów, wykonywanie zadań, o których chcesz wykonać, gdy użytkownik wybierze danego elementu menu skrótów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać element menu kontekstowego do typu elementu niestandardowego projektu. Gdy użytkownik otwiera menu skrótów elementu projektu w **Eksploratora rozwiązań** i wybiera **zapisać wiadomość do okna danych wyjściowych** elementu menu programu Visual Studio wyświetla komunikat w **dane wyjściowe**  okna.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 W tym przykładzie używa usługi projektu programu SharePoint do zapisu do wiadomości **dane wyjściowe** okna. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga projekt biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Wdrożenia elementu projektu
 Aby włączyć innych deweloperzy mogą używać element projektu, należy utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Aby wdrożyć elementu projektu, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu, szablon i inne pliki, które chcesz rozesłać za pomocą elementu projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
