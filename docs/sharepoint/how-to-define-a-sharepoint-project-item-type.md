---
title: 'Instrukcje: Definiowanie typu elementu projektu SharePoint | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae709bf2d81e2b8b00dc984602c0426fdf272ebd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016856"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Instrukcje: Definiowanie typu elementu projektu SharePoint
  Zdefiniuj typ elementu projektu, gdy chcesz utworzyć niestandardowy element projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Aby zdefiniować typ elementu projektu

1. Utwórz projekt biblioteki klas.

2. Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. kompozycji

3. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejs.

4. Dodaj następujące atrybuty do klasy:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia programowi Visual Studio odnajdywanie i ładowanie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Typ do konstruktora atrybutu.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W definicji typu elementu projektu ten atrybut określa identyfikator ciągu dla nowego elementu projektu. Zalecamy użycie formatu *Nazwa firmy*. *nazwa funkcji* , która pomaga upewnić się, że wszystkie elementy projektu mają unikatową nazwę.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Ten atrybut określa ikonę, która ma być wyświetlana dla tego elementu projektu w **Eksplorator rozwiązań**. Ten atrybut jest opcjonalny; Jeśli nie zastosujesz go do swojej klasy, program Visual Studio wyświetli domyślną ikonę dla elementu projektu. W przypadku ustawienia tego atrybutu należy przekazać w pełni kwalifikowaną nazwę ikony lub mapy bitowej osadzonej w zestawie.

5. W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody należy użyć elementów członkowskich parametru *ProjectItemTypeDefinition* , aby zdefiniować zachowanie typu elementu projektu. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektem, który zapewnia dostęp do zdarzeń zdefiniowanych w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsie i. Aby uzyskać dostęp do określonego wystąpienia typu elementu projektu, należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzenia, takie jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje sposób definiowania prostego typu elementu projektu. Ten typ elementu projektu zapisuje komunikat do okna **danych wyjściowych** i okna **Lista błędów** , gdy użytkownik doda element projektu tego typu do projektu.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 W tym przykładzie za pomocą usługi projektu programu SharePoint można napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** . Aby uzyskać więcej informacji, zobacz [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-project-item"></a>Wdróż element projektu
 Aby umożliwić innym deweloperom korzystanie z elementu projektu, Utwórz szablon projektu lub szablon elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Aby wdrożyć element projektu, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu, szablonu i innych plików, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie elementu menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
