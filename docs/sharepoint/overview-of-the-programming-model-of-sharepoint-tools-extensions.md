---
title: Omówienie modelu programowania rozszerzeń narzędzi SharePoint
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d2f7b56b372f1f083b441a5d3e6045ffc7aff7ed
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585735"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Omówienie modelu programowania rozszerzeń narzędzi SharePoint
  Po utworzeniu rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio Zacznij od zaimplementowania jednego lub większej liczby interfejsów rozszerzalności, które są udostępniane przez narzędzia programu SharePoint. W większości przypadków do zaimplementowania funkcji w rozszerzeniu są również używane inne typy udostępniane przez narzędzia programu SharePoint. W niektórych scenariuszach można także używać typów w innych modelach obiektów udostępnianych przez program Visual Studio i program SharePoint. Musisz zrozumieć przeznaczenie każdego z tych modeli obiektów i wiedzieć, jak z nich korzystać, aby utworzyć rozszerzenia dla narzędzi programu SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Rozszerzanie narzędzi programu SharePoint przez implementację interfejsów rozszerzalności
 Program Visual Studio używa Managed Extensibility Framework (MEF) w .NET Framework 4, aby zapewnić model rozszerzalności dla narzędzi programu SharePoint. MEF to interfejs API (zaimplementowany w zestawie System. ComponentModel. kompozycji), który umożliwia aplikacjom udostępnianie punktów rozszerzalności oraz odnajdywanie i ładowanie rozszerzeń w czasie wykonywania. Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).

 Aby rozszerzać narzędzia programu SharePoint, zaimplementuj jeden lub więcej interfejsów rozszerzalności, które są udostępniane przez program Visual Studio. W <xref:System.ComponentModel.Composition.ExportAttribute> razie potrzeby do implementacji interfejsu należy również zastosować i dodatkowe atrybuty specyficzne dla narzędzi programu SharePoint. Poniższa tabela zawiera listę interfejsów, które można zaimplementować w celu rozbudowania narzędzi programu SharePoint.

|Interfejs|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Zaimplementuj ten interfejs, aby zdefiniować nowy typ elementu projektu programu SharePoint. Aby zapoznać się z przykładem, zobacz [How to: Zdefiniuj typ elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Zaimplementuj ten interfejs, aby zwiększyć typ elementu projektu programu SharePoint, który jest już zainstalowany w programie Visual Studio. Aby zapoznać się z przykładem, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Zaimplementuj ten interfejs, aby rozłożyć projekty programu SharePoint. Aby zapoznać się z przykładem, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Zaimplementuj ten interfejs, aby zdefiniować nowy krok wdrożenia, który można wykonać, gdy element projektu programu SharePoint zostanie wdrożony lub wycofany. Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Zaimplementuj ten interfejs, aby zwiększyć istniejący węzeł w węźle **połączenia programu SharePoint** w oknie **Eksplorator serwera** . Aby zapoznać się z przykładem, zobacz [How to: rozszerzając węzeł programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Zaimplementuj ten interfejs, aby zdefiniować nowy typ węzła w węźle **połączenia programu SharePoint** w oknie **Eksplorator serwera** . Aby zapoznać się z przykładem, zobacz [How to: rozszerzając węzeł programu SharePoint w Eksplorator serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Zaimplementuj ten interfejs, aby zdefiniować regułę walidacji niestandardowej funkcji. Aby zapoznać się z przykładem, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Zaimplementuj ten interfejs, aby zdefiniować niestandardową regułę walidacji pakietu. Aby zapoznać się z przykładem, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 Po wdrożeniu rozszerzenia narzędzi programu SharePoint należy wdrożyć zestaw rozszerzeń w pakiecie Visual Studio Extension (VSIX), aby umożliwić programowi Visual Studio odnalezienie i załadowanie rozszerzenia. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Zrozumienie modeli obiektów używanych w rozszerzeniach narzędzi programu SharePoint
 Istnieje kilka modeli obiektów, których można użyć podczas tworzenia rozszerzeń dla narzędzi programu SharePoint:

- *Model obiektów narzędzi programu SharePoint*. Ten model obiektów udostępnia interfejsy rozszerzalności, które są implementowane w celu tworzenia rozszerzeń narzędzi SharePoint i innych powiązanych typów.

- *Modele obiektów automatyzacji i integracji programu Visual Studio*. Te modele obiektów umożliwiają dostęp do funkcji programu Visual Studio, które wykraczają poza zakres modelu obiektów narzędzi programu SharePoint.

    > [!NOTE]
    > Niektóre obiekty w modelu obiektów narzędzi SharePoint można przekonwertować na obiekty w ramach modeli obiektów automatyzacji i integracji programu Visual Studio, a na odwrót — za pomocą usługi projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [konwertowanie między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *Serwer programu SharePoint i modele obiektów klienta*. Użyj tych modeli obiektów, aby zmodyfikować witrynę programu SharePoint lub pobrać dane z witryny programu SharePoint z kontekstu rozszerzenia narzędzi programu SharePoint.

### <a name="sharepoint-tools-object-model"></a>Model obiektów narzędzi SharePoint
 Każde rozszerzenie narzędzia programu SharePoint używa typów w modelu obiektów narzędzi programu SharePoint do definiowania podstawowego zachowania i funkcjonalności rozszerzenia. W poniższych tabelach opisano przestrzenie nazw, które są uwzględnione w tym modelu obiektów, przez zestaw, który je zawiera.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Zawiera typy, które służą do rozszerania i automatyzowania systemu projektu programu SharePoint. Na przykład można rozbudować wbudowane projekty programu SharePoint i elementy projektu, a także utworzyć własne elementy projektu. Aby uzyskać więcej informacji, zobacz Rozpoznaj [system projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Zawiera typy, które służą do rozbudowania procesu wdrażania dla projektów programu SharePoint, takie jak tworzenie własnych kroków wdrożenia i konfiguracji wdrożenia. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Zawiera typy, które służą do rozszerania węzłów w węźle **połączenia SharePoint** w oknie **Eksplorator serwera** lub do definiowania nowych typów węzłów. Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Zawiera typy, które są używane w celu uzyskania dostępu do definicji funkcji w projekcie programu SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Zawiera typy, które są używane w celu uzyskania dostępu do definicji pakietu w rozwiązaniu programu SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Zawiera typy, które służą do dostosowania funkcji i zachowania walidacji pakietu dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Zawiera typy, których można użyć do tworzenia niestandardowych *poleceń programu SharePoint*. Polecenie programu SharePoint to metoda, która wywołuje model obiektów programu SharePoint Server z rozszerzenia narzędzi programu SharePoint. Aby uzyskać więcej informacji, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Zawiera typy, których można użyć w celu uzyskania informacji na temat wbudowanych węzłów **Eksplorator serwera** , które reprezentują poszczególne składniki w witrynie programu SharePoint, takie jak węzeł, który reprezentuje listę, pole lub typ zawartości. Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [węzeł połączenia SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Model obiektów automatyzacji programu Visual Studio
 Model obiektów automatyzacji programu Visual Studio udostępnia interfejsy API, których można używać do automatyzowania projektów programu Visual Studio i środowiska IDE. Model obiektów programu Visual Studio służy do wykonywania zadań związanych z projektem, które nie są specyficzne dla projektów programu SharePoint, ani do wykonywania innych ogólnych zadań automatyzacji w programie Visual Studio. Tradycyjnie ten model obiektów jest często używany w dodatkach i makrach programu Visual Studio, ale można go również użyć w rozszerzeniach narzędzi programu SharePoint.

 Główna część modelu obiektów automatyzacji programu Visual Studio jest definiowana w zestawie *EnvDTE.dll* . Zestawy *EnvDTE \\ \<version> . dll* oferują dodatkowe funkcje, które zostały wprowadzone w określonych wersjach programu Visual Studio. Te zestawy są dołączone do programu Visual Studio.

 Aby uzyskać więcej informacji na temat modelu obiektów automatyzacji, zobacz [Dokumentacja zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Model obiektów integracji programu Visual Studio
 Model obiektów integracji udostępnia interfejsy API, których można użyć do dodawania funkcji do programu Visual Studio przez utworzenie *pakietu VSPackage*. Pakietu VSPackage to moduł, który rozszerza środowisko IDE programu Visual Studio, dostarczając niestandardowe funkcje, takie jak okna narzędzi, edytory, projektanci, usługi i projekty.

 Możesz użyć modelu obiektów integracji, jeśli chcesz dodać nową funkcję programu Visual Studio, która będzie używana z wbudowanymi narzędziami programu SharePoint. Na przykład jeśli utworzysz niestandardowy element projektu programu SharePoint, który reprezentuje akcję niestandardową dla witryny programu SharePoint, możesz również utworzyć pakietu VSPackage, który implementuje projektanta dla akcji niestandardowej. Możesz skojarzyć projektanta z akcją niestandardową, dodając element menu skrótów do elementu projektu, który reprezentuje akcję niestandardową w **Eksplorator rozwiązań**. Możesz otworzyć projektanta, otwierając jego menu skrótów (klikając prawym przyciskiem myszy element projektu akcji niestandardowej lub wybierając go, a następnie wybierając klawisze **SHIFT** + **F10** ), a następnie wybierając **Otwórz**.

 Ten model obiektów jest zdefiniowany w zestawie zestawów, które są zawarte w zestawie SDK programu Visual Studio. Niektóre główne zestawy w tym modelu obiektów obejmują *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*i *Microsoft.VisualStudio.OLE.Interop.dll*.

 Aby uzyskać więcej informacji na temat modelu obiektów integracji, zobacz [Omówienie modelu automatyzacji](../extensibility/internals/automation-model-overview.md) i [Informacje o zestawie SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>Modele obiektów programu SharePoint
 Rozszerzenia narzędzi SharePoint mogą używać interfejsów API programu SharePoint do modyfikowania witryny programu SharePoint lub pobierania danych z witryny programu SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] udostępniamy dwa różne modele obiektów: model obiektów serwera i model obiektów klienta.

 Można używać interfejsów API w obu modelach obiektów w rozszerzeniu narzędzi programu SharePoint, ale każdy model obiektów ma pewne korzyści i wady w kontekście rozszerzeń narzędzi programu SharePoint. Aby uzyskać więcej informacji, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Model obiektów|Opis|
|------------------|-----------------|
|Model obiektów serwera|Model obiektów serwera zapewnia dostęp do wszystkich funkcji, które można [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] programistycznie uwidocznić. Ten model obiektów jest przeznaczony do użycia przez rozwiązania programu SharePoint, które działają na serwerze programu SharePoint. Większość tego modelu obiektów jest definiowana w zestawie *Microsoft.SharePoint.dll* . Aby uzyskać więcej informacji na temat modelu obiektów serwera, zobacz [Korzystanie z modelu obiektów po stronie serwera programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Model obiektów klienta|Model obiektów klienta jest podzbiorem modelu obiektów serwera, który może służyć do współdziałania z danymi programu SharePoint ze zdalnego klienta lub serwera. Zaprojektowano w celu zminimalizowania liczby rejsów, które muszą zostać wykonane w celu wykonywania typowych zadań. Większość modelu obiektów klienta jest definiowana w zestawach *Microsoft.SharePoint.Client.dll* i *Microsoft.SharePoint.Client.Runtime.dll* . Aby uzyskać więcej informacji na temat modelu obiektów klienta, zobacz [model obiektów klienta zarządzanego](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>Zobacz też
- [Poszerzanie narzędzi programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
