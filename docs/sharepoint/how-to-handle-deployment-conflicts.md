---
title: 'Instrukcje: Obsługa konfliktów wdrożenia | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd28e7a9f0fc04a704d6d3600fb80390d9509de1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863048"
---
# <a name="how-to-handle-deployment-conflicts"></a>Instrukcje: Obsługa konfliktów wdrożenia
  Możesz podać kod do obsługi konflikty wdrażania dla elementu projektu programu SharePoint. Na przykład można określić, czy wszystkie pliki w bieżącym elemencie projektu już istnieje w lokalizacji wdrożenia, a następnie usunąć wdrożonych plików, przed wdrożeniem bieżącego elementu projektu. Aby uzyskać więcej informacji na temat konflikty wdrażania zobacz [rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Do obsługi konfliktów wdrożenia  
  
1.  Tworzenie rozszerzenia elementu projektu, rozszerzenia projektu lub definicji typu elementu projektu. Więcej informacji znajduje się w następujących tematach:  
  
    -   [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Do rozszerzenia obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> zdarzenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzenia elementu projektu lub rozszerzenia projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu (w definicji typu elementu projektu).  
  
3.  W procedurze obsługi zdarzeń Ustal, czy niezgodności elementu projektu, który jest wdrażany z wdrożonym rozwiązaniem w witrynie programu SharePoint, na podstawie kryteriów, które są stosowane do danego scenariusza. Możesz użyć <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> właściwość parametru argumenty zdarzeń do analizowania elementu projektu, który jest wdrażany, na które można analizować plików w lokalizacji wdrożenia, wywołując polecenie programu SharePoint, które są definiowane w tym celu.  
  
     Dla wielu typów konfliktów najpierw warto określić kroku wdrożenia, który jest wykonywany. Można to zrobić za pomocą <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> właściwość parametru argumenty zdarzeń. Mimo że zazwyczaj warto wykrywanie konfliktów podczas wbudowane <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> kroku wdrożenia można sprawdzić konflikty podczas którykolwiek z kroków wdrażania.  
  
4.  Jeśli istnieje konflikt, użyj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> właściwość argumenty zdarzenia, aby utworzyć nowy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiektu. Ten obiekt reprezentuje konflikt wdrażania. W przypadku wywołania do <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metody również określić metodę, która jest wywoływana, aby rozwiązać konflikt.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje podstawowy proces obsługi konflikt wdrażania w rozszerzenia elementu projektu dla elementów projektu definicji listy. Aby obsłużyć konflikt wdrożenia do innego typu elementu projektu, przekazać inny ciąg do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby uzyskać więcej informacji, zobacz [elementów projektu programu SharePoint z rozszerzenia](../sharepoint/extending-sharepoint-project-items.md).  
  
 Dla uproszczenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> programu obsługi zdarzeń w tym przykładzie przyjęto założenie, że istnieje konflikt wdrażania (czyli zawsze dodaje nowy <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiektu) i `Resolve` metoda po prostu zwraca **true** z informacją, że Konflikt został rozwiązany. W przypadku rzeczywistych swoje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> obsługi zdarzenia czy najpierw ustalić, czy istnieje konflikt między plik w bieżącym elemencie projektów i plików w lokalizacji wdrożenia, a następnie dodaj <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> obiektu tylko, jeśli istnieje konflikt. Na przykład, można na przykład `e.ProjectItem.Files` właściwości programu obsługi zdarzeń do przeanalizowania plików w elementu projektu, a może wywołać polecenie programu SharePoint do przeanalizowania plików w lokalizacji wdrożenia. Podobnie w przypadku rzeczywistych `Resolve` metoda może wywoływać polecenia programu SharePoint, aby rozwiązać konflikt w witrynie programu SharePoint. Aby uzyskać więcej informacji na temat tworzenia poleceń programu SharePoint, zobacz [jak: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Rozszerzanie elementów projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Instrukcje: Uruchamianie kodu, gdy są wykonywane kroki związane z wdrażaniem](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Instrukcje: Tworzenie polecenia SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
