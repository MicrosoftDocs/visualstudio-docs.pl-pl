---
title: 'Instrukcje: Tworzenie rozszerzenia elementu projektu programu SharePoint | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 52d2cb187b4c119c17d87e089bdd7e2055556b90
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864774"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint
  Tworzenie rozszerzenia elementu projektu, jeśli chcesz dodać funkcje do elementu projektu programu SharePoint, która jest już zainstalowana w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [elementów projektu programu SharePoint z rozszerzenia](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Aby utworzyć rozszerzenie elementu projektu  
  
1.  Utwórz projekt biblioteki klas.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu.  
  
4.  Dodaj następujące atrybuty do klasy:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Ten atrybut umożliwia środowisku Visual Studio wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> typu konstruktora atrybutu.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. W rozszerzenia elementu projektu ten atrybut identyfikuje element projektu, który ma zostać rozszerzony. Przekaż identyfikator elementu projektu do konstruktora atrybutu. Aby uzyskać listę identyfikatorów elementów projektu, które są dołączone do programu Visual Studio, zobacz [elementów projektu programu SharePoint z rozszerzenia](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody, użyj członkowie *projectItemType* parametru do określania zachowania Twojego rozszerzenia. Ten parametr jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu, który zapewnia dostęp do zdarzenia, zdefiniowany w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfejsów. Aby uzyskać dostęp do konkretnego wystąpienia typu elementu projektu, rozszerzania, obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> zdarzeniach, takich jak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć proste rozszerzenie elementu projektu odbiorcy zdarzeń. Każdorazowo użytkownik dodaje element projektu odbiorcy zdarzeń do projektu programu SharePoint, to rozszerzenie zapisuje komunikat do **dane wyjściowe** okna i **lista błędów** okna.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 W tym przykładzie używa usługi projektu programu SharePoint do zapisu do wiadomości **dane wyjściowe** okna i **lista błędów** okna. Aby uzyskać więcej informacji, zobacz [korzystania z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie elementów projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
