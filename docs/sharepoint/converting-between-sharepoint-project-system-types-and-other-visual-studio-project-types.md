---
title: 'Konwertuj: typy systemu projektu SharePoint na/z innych typów'
titleSuffix: ''
description: Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio. Zobacz listę zawierającą szczegóły typów, które mogą być konwertowane.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 973c3d4b3c4fa2dc602e45736dc3a2d2f23c7616
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215295"
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

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs" id="Snippet2":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb" id="Snippet2":::

 Ten przykład wymaga:

- Rozszerzenie systemu projektu programu SharePoint, które ma odwołanie do zestawu *EnvDTE.dll* . Aby uzyskać więcej informacji, zobacz Rozpoznaj [system projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Kod, który rejestruje `projectService_ProjectAdded` metodę, aby obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> zdarzenie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu. Aby zapoznać się z przykładem, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Zobacz też

- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Instrukcje: pobieranie usługi projektu SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Omówienie modelu programowania rozszerzeń narzędzi SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
