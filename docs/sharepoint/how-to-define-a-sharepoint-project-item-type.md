---
title: 'Instrukcje: Definiowanie typu elementu projektu programu SharePoint | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: bfb04256a1bb8aacb062f30839566b75b599a3a3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872030"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Instrukcje: Definiowanie typu elementu projektu SharePoint
  Definiowanie typu elementu projektu, gdy chcesz utworzyć niestandardowego elementu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu programu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Aby zdefiniować typ elementu projektu  
  
1.  Utwórz projekt biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu.  
  
4.  Dodaj następujące atrybuty do klasy:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> typu konstruktora atrybutu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W definicji typu elementu projektu ten atrybut określa identyfikator ciągu dla nowego elementu projektu. Zalecane jest użycie formatu *nazwa firmy*. *Nazwa funkcji* pomaga zapewnić, że wszystkie elementy projektu mają unikatową nazwę.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Ten atrybut Określa ikonę do wyświetlenia dla tego elementu projektu w **Eksploratora rozwiązań**. Ten atrybut jest opcjonalny; Jeśli nie miała zastosowanie do klasy, Visual Studio Wyświetla domyślną ikonę element projektu. Jeśli ten atrybut jest ustawiony, należy przekazać w pełni kwalifikowaną nazwę ikony lub mapy bitowej, który jest wbudowany w zestaw.  
  
5.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody, użyj członkowie *projectItemTypeDefinition* parametru do określania zachowania typu elementu projektu. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu, który zapewnia dostęp do zdarzenia, zdefiniowany w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsów. Aby uzyskać dostęp do konkretnego wystąpienia typu elementu projektu, obsługę <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzeniach, takich jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak zdefiniować typ elementu prostego projektu. Ten typ elementu projektu zapisuje komunikat do **dane wyjściowe** okna i **lista błędów** okna, gdy użytkownik doda tego typu elementu projektu do projektu.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 W tym przykładzie używa usługi projektu programu SharePoint do zapisu do wiadomości **dane wyjściowe** okna i **lista błędów** okna. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Wdrożenia elementu projektu  
 Aby włączyć innych deweloperzy mogą używać element projektu, należy utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Aby wdrożyć elementu projektu, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu, szablon i inne pliki, które chcesz rozesłać za pomocą elementu projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla programu SharePoint narzędzia w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Instrukcje: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
