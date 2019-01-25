---
title: 'Instrukcje: Wykonywania kodu w trakcie kroków wdrożeniowych | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d2c36ce055816f712b4d38bca42a8af9c75921da
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871068"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Instrukcje: Uruchamianie kodu, gdy są wykonywane kroki związane z wdrażaniem
  Jeśli chcesz wykonać dodatkowe zadania dla kroku wdrożenia w projekcie programu SharePoint, możesz obsłużyć zdarzenia, które są wywoływane przez elementów projektu programu SharePoint przed i po programu Visual Studio wykonuje każdy krok wdrażania. Aby uzyskać więcej informacji, zobacz [rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Aby uruchomić kod, gdy są wykonywane kroki związane z wdrażaniem  
  
1.  Tworzenie rozszerzenia elementu projektu, rozszerzenia projektu lub definicji typu elementu projektu. Więcej informacji znajduje się w następujących tematach:  
  
    -   [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Do rozszerzenia obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzenia elementu projektu lub rozszerzenia projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu (w definicji typu elementu projektu).  
  
3.  W przypadku programów obsługi, użyj <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> i <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametry, aby uzyskać informacje na temat kroku wdrażania. Na przykład można określić kroku wdrożenia, który jest wykonywany i tego, czy rozwiązanie jest wdrożony lub wycofany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób obsługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzenia do rozszerzenia dla elementu projektu wystąpienia listy. To rozszerzenie zapisuje komunikat dodatkowe do **dane wyjściowe** okna, gdy pula aplikacji jest odtwarzana programu Visual Studio podczas wdrażania i wycofywanie rozwiązania.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład wymaga odwołania do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Instrukcje: Uruchamianie kodu, podczas projektu programu SharePoint jest wdrożony lub wycofany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
