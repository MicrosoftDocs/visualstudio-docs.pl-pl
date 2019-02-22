---
title: Korzystanie z usługi projektu SharePoint | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dfb7592fb2cec05da1bd72bd69a76e9a3b270db
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619982"
---
# <a name="use-the-sharepoint-project-service"></a>Korzystanie z usługi projektu SharePoint
  Systemu projektu programu SharePoint zawiera usługa projektu, która służy do wykonywania zadań związanych z system projektu. Usługa projektu jest <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu.

 Dostępne usługi projektu programu SharePoint w wszelkich rozszerzeń narzędzi programu SharePoint. Można także przejść w innych rodzajów rozszerzeń programu Visual Studio, takich jak dodatki i pakiety VSPackages. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Funkcje usługi projektu
 Poniższa tabela zawiera listę zadań, które można wykonać przy użyciu usługi projektu programu SharePoint i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> metody lub właściwości służące do wykonania poszczególnych zadań.

|Zadanie|Element członkowski do użycia|
|----------|-------------------|
|Dostęp do każdego projektu programu SharePoint, która jest otwarta w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> Właściwość.|
|Dostęp do wszystkich typów elementów projektu SharePoint, które są dostępne (w tym typów elementów projektu wbudowanych i niestandardowych).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> Właściwość.|
|Dostęp do wszystkich kroków wdrażania, które są dostępne dla projektów programu SharePoint (w tym kroki wdrażania wbudowanych i niestandardowych).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> Właściwość.|
|Zdarzenia dostępu, które są wywoływane, gdy deweloper refactors kodu w projekcie programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> Właściwość.|
|Wykonywanie niestandardowej *polecenia SharePoint* wywołująca w modelu obiektów serwera SharePoint. Aby uzyskać więcej informacji na temat poleceń programu SharePoint, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Właściwość.|
|Konwertowanie typu w systemie projektu programu SharePoint do typu w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji i na odwrót. Aby uzyskać więcej informacji, zobacz [konwersji między typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Metoda.|
|Zapisywanie komunikatów **dane wyjściowe** okna lub **lista błędów** okna w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> Właściwość.|
|Dostęp do innych usług, które są dostępne w programie Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> Właściwość.|
|Pobierz ścieżkę do folderu instalacji lokalnej witryny programu SharePoint, która jest używana do debugowania rozwiązania.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> Właściwość.|
|Określić, czy [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] lub [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] jest zainstalowany na komputerze.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> Właściwość.|
|Sprawdź poprawność funkcji lub pakietu w rozwiązaniu programu SharePoint.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> Właściwość.|

## <a name="see-also"></a>Zobacz także
- [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Instrukcje: Pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Instrukcje: Pobierz usługę z obiektu DTE](https://msdn.microsoft.com/library/bb166401.aspx)
