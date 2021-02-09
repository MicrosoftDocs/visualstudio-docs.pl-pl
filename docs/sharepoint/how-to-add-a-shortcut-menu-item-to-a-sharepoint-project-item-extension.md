---
title: Dodaj element menu skrótów do rozszerzenia elementu projektu SharePoint
titleSuffix: ''
description: Dodaj element menu skrótów do istniejącego elementu projektu programu SharePoint przy użyciu rozszerzenia elementu projektu w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: eba366ecf777697a0c63999d8addf099fecca976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923609"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Instrukcje: Dodawanie elementu menu skrótów do rozszerzenia elementu projektu SharePoint
  Element menu skrótów można dodać do istniejącego elementu projektu programu SharePoint za pomocą rozszerzenia elementu projektu. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że już utworzono rozszerzenie elementu projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Aby dodać element menu skrótów do rozszerzenia elementu projektu

1. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenie parametru *projectItemType* .

2. W programie obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenia Dodaj nowy <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiekt do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> kolekcji lub z <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> parametrem argumenty zdarzenia.

3. W programie <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektu wykonaj zadania, które chcesz wykonać, gdy użytkownik kliknie element menu skrótów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać element menu skrótów do elementu projektu odbiorcy zdarzeń. Gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksplorator rozwiązań** i kliknie element menu **napisz wiadomość do okno dane wyjściowe** , program Visual Studio wyświetli komunikat w oknie **danych wyjściowych** .

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 W tym przykładzie za pomocą usługi projektu SharePoint można napisać komunikat do okna **dane wyjściowe** . Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga projektu biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
