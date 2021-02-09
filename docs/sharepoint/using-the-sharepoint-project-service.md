---
title: Korzystanie z usługi projektu SharePoint | Microsoft Docs
description: Użyj usługi projektu programu SharePoint do wykonywania zadań związanych z systemem projektu. Wyświetl listę funkcji usługi projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5366be3ed60da9225eaf10b19f58ccd77bffbb90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892193"
---
# <a name="use-the-sharepoint-project-service"></a>Korzystanie z usługi projektu SharePoint
  System projektu programu SharePoint zawiera usługę projektu, której można użyć do wykonywania zadań związanych z systemem projektu. Usługa projektu jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektem.

 Dostęp do usługi projektu SharePoint można uzyskać w dowolnym rozszerzeniu narzędzi programu SharePoint. Możesz również uzyskać do niego dostęp w innych typach rozszerzeń programu Visual Studio, takich jak dodatki i pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [How to: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Funkcje usługi projektu
 Poniższa tabela zawiera listę zadań, które można wykonać przy użyciu usługi projektu SharePoint oraz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> metody lub właściwości, które mają być używane do wykonywania poszczególnych zadań.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Uzyskaj dostęp do dowolnego projektu programu SharePoint, który jest otwarty w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> wartość.|
|Dostęp do wszystkich dostępnych typów elementów projektu programu SharePoint (w tym wbudowanych i niestandardowych typów elementów projektu).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> wartość.|
|Uzyskaj dostęp do wszystkich kroków wdrożenia dostępnych dla projektów programu SharePoint (w tym wbudowanych i niestandardowych kroków wdrażania).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> wartość.|
|Zdarzenia dostępu, które są zgłaszane, gdy kod refaktoryzacji dewelopera w projekcie programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> wartość.|
|Wykonaj niestandardowe *polecenie programu SharePoint* , które wywołuje model obiektów programu SharePoint Server. Aby uzyskać więcej informacji na temat poleceń programu SharePoint, zobacz [wywołanie do modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> wartość.|
|Przekonwertuj typ w systemie projektu SharePoint na typ w modelu obiektów automatyzacji programu Visual Studio lub modelu obiektów integracji i odwrotnie. Aby uzyskać więcej informacji, zobacz [konwertowanie między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Method.|
|Napisz komunikaty do okna **danych wyjściowych** lub okna **Lista błędów** w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> wartość.|
|Uzyskaj dostęp do innych usług, które są dostępne w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> wartość.|
|Pobierz ścieżkę do folderu instalacji lokalnej witryny programu SharePoint, która jest używana do debugowania rozwiązania.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> wartość.|
|Ustal, [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] czy [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] na komputerze jest zainstalowany.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> wartość.|
|Sprawdź poprawność funkcji lub pakietu w rozwiązaniu programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> wartość.|

## <a name="see-also"></a>Zobacz też
- [Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Instrukcje: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Instrukcje: Uzyskiwanie usługi z obiektu DTE](/previous-versions/bb166401(v=vs.140))