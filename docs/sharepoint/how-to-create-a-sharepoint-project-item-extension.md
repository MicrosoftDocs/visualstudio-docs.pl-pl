---
title: 'Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint | Microsoft Docs'
description: Zapoznaj się z tematem jak utworzyć rozszerzenie elementu projektu, gdy chcesz dodać funkcję do elementu projektu programu SharePoint, który jest już zainstalowany w programie Visual Studio.
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
ms.openlocfilehash: 8f01d3c15490a19c8cb5071cf7677fcf2b2a5384
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216621"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint
  Utwórz rozszerzenie elementu projektu, gdy chcesz dodać funkcję do elementu projektu programu SharePoint, który jest już zainstalowany w programie Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając elementy projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Aby utworzyć rozszerzenie elementu projektu

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. kompozycji

3. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejs.

4. Dodaj następujące atrybuty do klasy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Typ do konstruktora atrybutu.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W rozszerzeniu elementu projektu ten atrybut identyfikuje element projektu, który ma zostać rozszerzona. Przekaż identyfikator elementu projektu do konstruktora atrybutu. Aby uzyskać listę identyfikatorów elementów projektu, które są dołączone do programu Visual Studio, zobacz sekcję [rozszerzając elementy projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md).

5. W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody należy użyć elementów członkowskich parametru *projectItemType* , aby zdefiniować zachowanie rozszerzenia. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektem, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsie i. Aby uzyskać dostęp do określonego wystąpienia typu elementu projektu, które są rozszerzane, należy obsługiwać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia, takie jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak utworzyć proste rozszerzenie dla elementu projektu odbiorcy zdarzeń. Za każdym razem, gdy użytkownik dodaje element projektu odbiorcy zdarzeń do projektu programu SharePoint, to rozszerzenie zapisuje komunikat do okna **danych wyjściowych** i okna **Lista błędów** .

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 W tym przykładzie za pomocą usługi projektu programu SharePoint można napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** . Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
