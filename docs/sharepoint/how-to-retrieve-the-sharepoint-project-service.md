---
title: 'Instrukcje: Pobieranie usługi projektu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dfd18de91848c8aabbdabc91fd37763418bb938a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891605"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Instrukcje: Pobieranie usługi projektu SharePoint
  Aby uzyskać dostęp z usługi projektu programu SharePoint w następujących rozwiązań:  
  
-   Rozszerzenie systemu projektu programu SharePoint, takich jak rozszerzenie projektu, rozszerzenie elementu projektu lub definicji typu elementu projektu. Aby uzyskać więcej informacji na temat tych typów rozszerzeń zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Rozszerzenie **połączeń SharePoint** w węźle **Eksploratora serwera**. Aby uzyskać więcej informacji na temat tych typów rozszerzeń zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Inny typ rozszerzenia programu Visual Studio, takie jak pakietu VSPackage.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Pobieranie usługi w rozszerzeniach systemu projektu  
 Wszystkie rozszerzenia systemu projektu programu SharePoint, mieli dostęp do usługi projektu za pomocą <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu.  
  
 Za pomocą poniższych procedur, można także pobrać z usługi projektu.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Można pobrać usługi w rozszerzeniu projektu  
  
1.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu, odszukaj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody.  
  
2.  Użyj *projectService* parametru, aby uzyskać dostęp do usługi.  
  
     Poniższy przykład kodu pokazuje, jak korzystać z usługi projektu do zapisywania komunikatów **dane wyjściowe** okna i **lista błędów** okna w rozszerzeniu prostego projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Aby uzyskać więcej informacji na temat tworzenia projektu rozszerzenia zobacz [jak: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Aby pobrać usługę w rozszerzenia elementu projektu  
  
1.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfejsu, odszukaj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody.  
  
2.  Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> właściwość *projectItemType* parametru, aby pobrać usługę.  
  
     Poniższy przykład kodu pokazuje, jak korzystać z usługi projektu do zapisywania komunikatów **dane wyjściowe** okna i **lista błędów** okna proste rozszerzenie **definicji listy** elementu projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Aby uzyskać więcej informacji na temat tworzenia rozszerzenia elementu projektu, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Aby pobrać usługę w definicji typu elementu projektu  
  
1.  W danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu, odszukaj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody.  
  
2.  Użyj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> właściwość *typeDefinition* parametru, aby pobrać usługę.  
  
     Poniższy przykład kodu pokazuje, jak korzystać z usługi projektu do zapisywania komunikatów **dane wyjściowe** okna i **lista błędów** okna w definicji typu elementu prostego projektu.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Aby uzyskać więcej informacji na temat definiowania typów elementów projektu, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Pobieranie usługi w rozszerzenia Eksploratora serwera  
 W rozszerzeniu **połączeń SharePoint** w węźle **Eksploratora serwera**, uzyskać dostęp do usługi projektu za pomocą <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Można pobrać usługi w rozszerzeniu Eksploratora serwera  
  
1.  Pobierz <xref:System.IServiceProvider> obiektu z <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> obiektu w rozszerzeniu.  
  
2.  Użyj <xref:System.IServiceProvider.GetService%2A> metodę, aby zażądać <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu.  
  
     Poniższy przykład kodu pokazuje, jak korzystać z usługi projektu do zapisywania komunikatów **dane wyjściowe** okna i **lista błędów** okna w menu skrótów, które rozszerzenie dodaje do listy węzłów w **Eksploratora serwera**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Aby uzyskać więcej informacji o rozszerzaniu **połączeń SharePoint** w węźle **Eksploratora serwera**, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Pobieranie usługi w inne rozszerzenia programu Visual Studio  
 Możesz pobrać z usługi projektu pakietu VSPackage lub rozszerzenia programu Visual Studio, które ma dostęp do <xref:EnvDTE80.DTE2> obiektu w modelu obiektu automatyzacji, takie jak Kreator szablonu projektu, który implementuje <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfejsu.  
  
 W VSPackage, możesz poprosić o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu przy użyciu jednej z następujących metod:  
  
- <xref:System.IServiceProvider.GetService%2A> Metoda zarządzanego pakietu VSPackage, który pochodzi od klasy <xref:Microsoft.VisualStudio.Shell.Package> klasy. Aby uzyskać więcej informacji, zobacz [jak: Usługi](../extensibility/how-to-get-a-service.md).  
  
- Statyczne <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody. Aby uzyskać więcej informacji, zobacz [GetGlobalService użyj](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
  W rozszerzeniu Visual Studio, który ma dostęp do <xref:EnvDTE80.DTE2> obiektu, możesz poprosić o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> obiektu za pomocą <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metody <xref:Microsoft.VisualStudio.Shell.ServiceProvider> obiektu. Aby uzyskać więcej informacji, zobacz [pobierania usługi z obiektu DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Zobacz także
 [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Instrukcje: Uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)   
 [Instrukcje: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)  
