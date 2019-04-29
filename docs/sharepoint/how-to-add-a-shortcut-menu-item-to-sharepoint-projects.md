---
title: 'Instrukcje: Dodawanie pozycji Menu skrótów do projektów SharePoint | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 5b5db3fe3aaf8dc57c7df6a63810106ae9fb30fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967125"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Instrukcje: Dodawanie pozycji menu skrótów do projektów SharePoint
  Do każdego projektu programu SharePoint, można dodać element menu skrótów. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**.

 W następujących krokach założono, że utworzono już rozszerzenia projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Aby dodać element menu skrótów do projektów SharePoint

1. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody usługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji, uchwyt <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzenia *projectService* parametru.

2. W sieci programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzeń, Dodaj nowy <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiekt <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> lub <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> zbiór parametr argumenty zdarzenia.

3. W <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> programu obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektów, wykonywanie zadań, o których chcesz wykonać, gdy użytkownik kliknie danego elementu menu skrótów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób dodawania pozycji menu skrótów do węzłów projektu programu SharePoint w **Eksploratora rozwiązań**. Gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu i klika pozycję **zapisać wiadomość do okna danych wyjściowych** elementu menu programu Visual Studio wyświetla komunikat w **dane wyjściowe** okna. W tym przykładzie użyto usługi projektu programu SharePoint, aby wyświetlić wiadomość. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga projekt biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Instrukcje: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
