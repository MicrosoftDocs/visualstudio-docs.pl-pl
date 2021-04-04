---
title: Dodaj element menu skrótów do niestandardowego typu elementu projektu SharePoint
titleSuffix: ''
description: Dowiedz się, jak dodać element menu skrótów do niestandardowego typu elementu projektu programu SharePoint. Element menu pojawia się po kliknięciu prawym przyciskiem myszy elementu projektu w Eksplorator rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3e4523d0f992ed72c9af2eb7e542f902578f9338
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215386"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Instrukcje: Dodawanie elementu menu skrótów do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu programu SharePoint można dodać element menu skrótów do elementu projektu. Element menu jest wyświetlany, gdy użytkownik kliknie prawym przyciskiem myszy element projektu w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że masz już zdefiniowany własny typ elementu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Aby dodać element menu skrótów do niestandardowego typu elementu projektu

1. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenie parametru *ProjectItemTypeDefinition* .

2. W programie obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> zdarzenia Dodaj nowy <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiekt do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> kolekcji lub z <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> parametrem argumenty zdarzenia.

3. W programie <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> obsługi zdarzeń dla nowego <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> obiektu wykonaj zadania, które chcesz wykonać, gdy użytkownik wybierze element menu skrótów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać element menu kontekstowego do niestandardowego typu elementu projektu. Gdy użytkownik otwiera menu skrótów z elementu projektu w **Eksplorator rozwiązań** i wybiera element menu **zapisz wiadomość do okno dane wyjściowe** , program Visual Studio wyświetli komunikat w oknie **danych wyjściowych** .

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 W tym przykładzie za pomocą usługi projektu SharePoint można napisać komunikat do okna **dane wyjściowe** . Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga projektu biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-project-item"></a>Wdróż element projektu
 Aby umożliwić innym deweloperom korzystanie z elementu projektu, Utwórz szablon projektu lub szablon elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Aby wdrożyć element projektu, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu, szablonu i innych plików, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
