---
title: 'Instrukcje: pobieranie usługi projektu SharePoint | Microsoft Docs'
description: Dowiedz się, jak uzyskać dostęp do usługi projektu programu SharePoint w rozszerzeniach systemu projektu, rozszerzeniach Eksplorator serwera lub innych rozszerzeniach programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ef53a0328fe8427b356132fe878b52a3e504ea9a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214463"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Instrukcje: pobieranie usługi projektu SharePoint
  Dostęp do usługi projektu SharePoint można uzyskać w następujących typach rozwiązań:

- Rozszerzenie systemu projektu programu SharePoint, takie jak rozszerzenie projektu, rozszerzenie elementu projektu lub definicja typu elementu projektu. Aby uzyskać więcej informacji na temat tych typów rozszerzeń, zobacz [Rozszerzanie systemu projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Rozszerzenie węzła **połączenia programu SharePoint** w **Eksplorator serwera**. Aby uzyskać więcej informacji na temat tych typów rozszerzeń, zobacz [rozszerzanie węzła połączeń SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Inny typ rozszerzenia programu Visual Studio, na przykład pakietu VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Pobieranie usługi w rozszerzeniach systemu projektu
 W dowolnym rozszerzeniu systemu projektu SharePoint można uzyskać dostęp do usługi projektu przy użyciu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu.

 Możesz również pobrać usługę projektu, korzystając z poniższych procedur.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Aby pobrać usługę w rozszerzeniu projektu

1. W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodę.

2. Użyj parametru *projectService* , aby uzyskać dostęp do usługi.

     Poniższy przykład kodu demonstruje, jak za pomocą usługi projektu napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** w prostym rozszerzeniu projektu.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Aby uzyskać więcej informacji na temat tworzenia rozszerzeń projektu, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Aby pobrać usługę w rozszerzeniu elementu projektu

1. W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodę.

2. Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> właściwości *projectItemType* parametru, aby pobrać usługę.

     Poniższy przykład kodu demonstruje, jak za pomocą usługi projektu napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** w prostym rozszerzeniu elementu projektu **definicji listy** .

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet2":::

     Aby uzyskać więcej informacji na temat tworzenia rozszerzeń elementów projektu, zobacz [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Aby pobrać usługę w definicji typu elementu projektu

1. W implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu Znajdź <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodę.

2. Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> właściwości *typeDefinition* parametru, aby pobrać usługę.

     Poniższy przykład kodu demonstruje, jak za pomocą usługi projektu napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** w prostej definicji typu elementu projektu.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet3":::

     Aby uzyskać więcej informacji na temat definiowania typów elementów projektu, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Pobieranie usługi przy użyciu rozszerzeń Eksplorator serwera
 W rozszerzeniu węzła **połączenia programu SharePoint** w **Eksplorator serwera** można uzyskać dostęp do usługi projektu przy użyciu <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Aby pobrać usługę z rozszerzenia Eksplorator serwera

1. Pobierz <xref:System.IServiceProvider> obiekt z <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu w rozszerzeniu.

2. Użyj <xref:System.IServiceProvider.GetService%2A> metody, aby zażądać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu.

     Poniższy przykład kodu demonstruje, jak za pomocą usługi projektu napisać komunikat do okna **danych wyjściowych** i okna **Lista błędów** z menu skrótów, które rozszerzenie dodaje do listy węzłów w **Eksplorator serwera**.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Aby uzyskać więcej informacji na temat rozszerzania węzła **połączenia programu SharePoint** w **Eksplorator serwera**, zobacz [How to: rozszerzanie węzła programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Pobieranie usługi z innych rozszerzeń programu Visual Studio
 Usługę projektu można pobrać w pakietu VSPackage lub w dowolnym rozszerzeniu programu Visual Studio, który ma dostęp do <xref:EnvDTE80.DTE2> obiektu w modelu obiektów automatyzacji, takiego jak Kreator szablonu projektu implementujący <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejs.

 W pakietu VSPackage można zażądać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu za pomocą jednej z następujących metod:

- <xref:System.IServiceProvider.GetService%2A>Metoda zarządzanego pakietu VSPackage, która pochodzi od <xref:Microsoft.VisualStudio.Shell.Package> klasy. Aby uzyskać więcej informacji, zobacz [How to: get a Service](../extensibility/how-to-get-a-service.md).

- Metoda statyczna <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> . Aby uzyskać więcej informacji, zobacz [Korzystanie z GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  W rozszerzeniu programu Visual Studio, które ma dostęp do <xref:EnvDTE80.DTE2> obiektu, można zażądać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu za pomocą <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody <xref:Microsoft.VisualStudio.Shell.ServiceProvider> obiektu. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie usługi z poziomu obiektu DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Zobacz też
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)
- [Instrukcje: korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
