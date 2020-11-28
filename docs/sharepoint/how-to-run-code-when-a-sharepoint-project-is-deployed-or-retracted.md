---
title: Uruchom kod, gdy projekt programu SharePoint jest wdrażany lub wycofywany
titleSuffix: ''
description: Dowiedz się, jak uruchomić kod, gdy projekt programu SharePoint jest wdrażany lub wycofywany, aby można było obsługiwać zdarzenia, które są wywoływane przez program Visual Studio.
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
ms.openlocfilehash: 24e6536dc5fdc62bb3b1c32bbd7c379fcef1f8cd
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304486"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Instrukcje: uruchamianie kodu, gdy projekt SharePoint jest wdrażany lub wycofywany
  Jeśli chcesz wykonać dodatkowe zadania, gdy projekt programu SharePoint jest wdrażany lub wycofywany, można obsługiwać zdarzenia, które są wywoływane przez program Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Aby uruchomić kod, gdy projekt programu SharePoint jest wdrażany lub wycofywany

1. Utwórz rozszerzenie elementu projektu, rozszerzenie projektu lub definicję nowego typu elementu projektu. Aby uzyskać więcej informacji, zobacz następujące tematy:

   - [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. W rozszerzeniu, uzyskaj dostęp do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Aby uzyskać więcej informacji, zobacz [How to: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Obsłuż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> zdarzenia i usługi projektu.

4. W programach obsługi zdarzeń Użyj <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parametru, aby uzyskać informacje o bieżącej sesji wdrażania. Można na przykład określić, który projekt znajduje się w bieżącej sesji wdrożenia i czy jest wdrażany czy wycofywany.

   Poniższy przykład kodu demonstruje, jak obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> zdarzenia i w rozszerzeniu projektu. To rozszerzenie zapisuje dodatkowy komunikat do okna **dane wyjściowe** po uruchomieniu i zakończeniu wdrażania dla projektu programu SharePoint.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Instrukcje: uruchamianie kodu po wykonaniu kroków wdrożenia](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
