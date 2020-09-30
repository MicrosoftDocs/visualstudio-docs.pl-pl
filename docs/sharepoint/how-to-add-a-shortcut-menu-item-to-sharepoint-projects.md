---
title: 'Instrukcje: Dodawanie elementu menu skrótów do projektów programu SharePoint | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ea862eb21aaee75499f3b1bac7007063227150e2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585852"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Instrukcje: Dodawanie elementu menu skrótów do projektów programu SharePoint
  Możesz dodać element menu skrótów do dowolnego projektu programu SharePoint. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że już utworzono rozszerzenie projektu. Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Aby dodać element menu skrótów do projektów programu SharePoint

1. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzenie parametru *projectService* .

2. W programie obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> zdarzenia Dodaj nowy <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiekt do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> kolekcji lub z <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> parametrem argumenty zdarzenia.

3. W programie <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektu wykonaj zadania, które chcesz wykonać, gdy użytkownik kliknie element menu skrótów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać element menu skrótów do węzłów projektu programu SharePoint w **Eksplorator rozwiązań**. Gdy użytkownik kliknie prawym przyciskiem myszy węzeł projektu i kliknie element menu **Zapisz wiadomość do okno dane wyjściowe** , program Visual Studio wyświetli komunikat w oknie **danych wyjściowych** . Ten przykład używa usługi projektu programu SharePoint, aby wyświetlić komunikat. Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga projektu biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Zwiększ projekty programu SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Instrukcje: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
