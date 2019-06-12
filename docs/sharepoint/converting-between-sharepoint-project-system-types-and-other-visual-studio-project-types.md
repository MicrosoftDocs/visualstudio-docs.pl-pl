---
title: 'Konwertuj: Typami systemu projektu programu SharePoint z innych typów'
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
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836002"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio
  W niektórych przypadkach może być obiekt w systemie projektu programu SharePoint i chcesz korzystać z funkcji odpowiedni obiekt w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, lub na odwrót. W takich przypadkach można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metody usługi projektu programu SharePoint, aby przekonwertować obiekt do innego obiektu modelu.

 Na przykład, Niewykluczone, że <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt, ale chcesz użyć metod, które są dostępne tylko na <xref:EnvDTE.Project> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> obiektu. W takim przypadku można użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodę, aby przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do <xref:EnvDTE.Project> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Aby uzyskać więcej informacji na temat modelu obiektu automatyzacji programu Visual Studio i model obiektów integracji programu Visual Studio, zobacz [omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Konwersje typów
 W poniższej tabeli wymieniono typy, które tej metody można konwertować między systemu projektu programu SharePoint i innych modeli obiektów programu Visual Studio.

|Typ systemu projektu SharePoint|Odpowiadające typy w modele obiektów automatyzacji i integracji|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> lub<br /><br /> Żadnego interfejsu w modelu obiektów integracji programu Visual Studio, który jest implementowany przez obiekt COM dla projektu. Te interfejsy zawierają <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (lub interfejs pochodny) i <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Aby uzyskać listę główny interfejsy, które są implementowane w projektach, zobacz [podstawowe składniki modelu projektu](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> lub<br /><br /> A<xref:System.UInt32> określająca (nazywane również VSITEMID) elementu członkowskiego projektu w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> zawierający go. Ta wartość może być przekazywany do *itemid* parametru niektórych <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metody.|

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób używania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodę, aby przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt <xref:EnvDTE.Project>.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Ten przykład wymaga:

- Rozszerzenie systemu projektu programu SharePoint, która zawiera odwołanie do *EnvDTE.dll* zestawu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Kod, który rejestruje `projectService_ProjectAdded` metody, aby obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzenia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Aby uzyskać przykład, zobacz [jak: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Zobacz także

- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Instrukcje: Pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
