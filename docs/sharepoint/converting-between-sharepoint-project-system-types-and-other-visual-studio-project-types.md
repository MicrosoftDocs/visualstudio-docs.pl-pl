---
title: 'Konwertuj: typy systemu projektu SharePoint na/z innych typów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea60a8df5bc0bcd033c60a83d742ed3249cc53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836002"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio
  W niektórych przypadkach może istnieć obiekt w systemie projektu programu SharePoint i chcesz użyć funkcji odpowiedniego obiektu w modelu obiektów automatyzacji programu Visual Studio lub modelu obiektów integracji lub na odwrót. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metody usługi projektu SharePoint do przekonwertowania obiektu na inny model obiektu.

 Na przykład może istnieć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt, ale chcesz użyć metod, które są dostępne tylko dla <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> obiektu lub. W takim przypadku można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metody do przekonwertowania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> na <xref:EnvDTE.Project> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Aby uzyskać więcej informacji na temat modelu obiektów automatyzacji programu Visual Studio i modelu obiektów integracji programu Visual Studio, zobacz [Omówienie modelu programowania rozszerzeń narzędzi programu SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Typy konwersji
 W poniższej tabeli wymieniono typy, które ta metoda może konwertować między systemem projektu SharePoint a innymi modelami obiektów programu Visual Studio.

|Typ systemu projektu SharePoint|Odpowiednie typy w modelach obiektów automatyzacji i integracji|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> lub<br /><br /> Dowolny interfejs w modelu obiektów integracji programu Visual Studio, który jest implementowany przez obiekt modelu COM dla projektu. Te interfejsy obejmują <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (lub interfejs pochodny), i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Aby uzyskać listę głównych interfejsów, które są implementowane przez projekty, zobacz [podstawowe składniki modelu projektu](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> lub<br /><br /> <xref:System.UInt32>Wartość (zwana również VSITEMID), która identyfikuje element członkowski projektu w, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> który zawiera. Tę wartość można przesłać do parametru *ItemId* niektórych <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metod.|

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób użycia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metody do konwersji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu na <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Ten przykład wymaga:

- Rozszerzenie systemu projektu programu SharePoint, które ma odwołanie do zestawu *EnvDTE.dll* . Aby uzyskać więcej informacji, zobacz Rozpoznaj [system projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Kod, który rejestruje `projectService_ProjectAdded` metodę, aby obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Aby zapoznać się z przykładem, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Zobacz też

- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Instrukcje: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
