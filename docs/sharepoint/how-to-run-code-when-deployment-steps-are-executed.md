---
title: 'Instrukcje: uruchamianie kodu po wykonaniu kroków wdrożenia | Microsoft Docs'
description: Uruchom kod, aby obsłużyć zdarzenia, które są wywoływane przez elementy projektu programu SharePoint przed i po wykonaniu kroku wdrożenia przez program Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 00b921d8500c95ebbb771b5c0b5817db87b7c6ca
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304451"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Instrukcje: uruchamianie kodu po wykonaniu kroków wdrożenia
  Jeśli chcesz wykonać dodatkowe zadania dla kroku wdrożenia w projekcie programu SharePoint, możesz obsłużyć zdarzenia, które są wywoływane przez elementy projektu programu SharePoint przed i po wykonaniu każdego kroku wdrożenia przez program Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie pakietów i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Uruchamianie kodu po wykonaniu kroków wdrożenia

1. Utwórz rozszerzenie elementu projektu, rozszerzenie projektu lub definicję nowego typu elementu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:

    - [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. W rozszerzeniu obsługa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzeń i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> obiektu (w rozszerzeniu elementu projektu lub rozszerzenia projektu) lub <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> obiektu (w definicji nowego typu elementu projektu).

3. W programach obsługi zdarzeń Użyj <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> parametrów i, <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> Aby uzyskać informacje o kroku wdrożenia. Można na przykład określić, który krok wdrożenia ma być wykonywany i czy rozwiązanie jest wdrażane czy wycofywane.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> zdarzenia i w rozszerzeniu elementu projektu wystąpienia listy. To rozszerzenie zapisuje dodatkowy komunikat do okna **dane wyjściowe** , gdy program Visual Studio odtwarza pulę aplikacji podczas wdrażania i wycofywania rozwiązania.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Instrukcje: uruchamianie kodu, gdy projekt SharePoint jest wdrażany lub wycofywany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
