---
title: Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bec1627af7bbef1c3fcd264f2d74aca86d1cfad4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639339"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Omówienie modelu programowania programu SharePoint rozszerzeń narzędzi
  Po utworzeniu rozszerzeń dla narzędzi SharePoint w programie Visual Studio, należy rozpocząć od implementacja interfejsów rozszerzeń, które są udostępniane przez narzędzia programu SharePoint. W większości przypadków będzie również użyć innych typów dostarczonych przez narzędzia programu SharePoint do zaimplementowania funkcji w rozszerzeniu. W niektórych przypadkach można także użyć typów w innych modeli obiektów, dostarczone przez program Visual Studio i programu SharePoint. Konieczne jest zrozumienie przeznaczenia każdego z tych modeli obiektów oraz wiedzieć, jak za ich pomocą ze sobą tworzenia rozszerzeń dla narzędzi SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Rozszerzanie narzędzi SharePoint poprzez implementację rozszerzalności interfejsów
 Visual Studio używa Managed Extensibility Framework (MEF) w programie .NET Framework 4, aby zapewnić modelu rozszerzalności dla narzędzi SharePoint. MEF jest interfejs API (zaimplementowanych w zestawie System.ComponentModel.Composition), umożliwia aplikacjom udostępnianie punkty rozszerzeń i wykrycie i załadowanie rozszerzenia w czasie wykonywania. Aby uzyskać więcej informacji na temat MEF, zobacz [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).

 Aby rozszerzyć narzędzia programu SharePoint, zaimplementuj jeden lub więcej interfejsów rozszerzeń, które są dostępne w programie Visual Studio. Należy również zastosować <xref:System.ComponentModel.Composition.ExportAttribute>, oraz dodatkowe SharePoint specyficzne dla narzędzia atrybutów w razie potrzeby implementacji interfejsu. Poniższa tabela zawiera listę interfejsów, które można zaimplementować w celu rozszerzenia narzędzi programu SharePoint.

|Interface|Opis|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implementuje ten interfejs do definiowania nowego typu elementu projektu programu SharePoint. Aby uzyskać przykład, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implementuje ten interfejs w celu rozszerzania typu elementu projektu programu SharePoint, która jest już zainstalowana w programie Visual Studio. Aby uzyskać przykład, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implementuje ten interfejs, aby rozszerzyć projektów programu SharePoint. Aby uzyskać przykład, zobacz [jak: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implementuje ten interfejs do definiowania nowego kroku wdrożenia, które mogą być wykonywane, gdy element projektu programu SharePoint jest wdrożony lub wycofany. Aby uzyskać przykład, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implementuje ten interfejs, aby rozszerzyć istniejący węzeł w obszarze **połączeń SharePoint** w węźle **Eksploratora serwera** okna. Aby uzyskać przykład, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implementuje ten interfejs do definiowania nowego typu węzeł w węźle **połączeń SharePoint** w węźle **Eksploratora serwera** okna. Aby uzyskać przykład, zobacz [jak: Rozszerzanie węzła SharePoint w Eksploratorze serwera](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implementuje ten interfejs zdefiniowanie funkcji niestandardowe reguły sprawdzania poprawności. Aby uzyskać przykład, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implementuje ten interfejs, aby zdefiniować niestandardowy pakiet regułę sprawdzania poprawności. Aby uzyskać przykład, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 Po zaimplementowaniu rozszerzenia narzędzi programu SharePoint, należy wdrożyć zestawu rozszerzeń w pakiecie Visual Studio rozszerzenia (VSIX), aby umożliwić programowi Visual Studio wykrycie i załadowanie rozszerzenia. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Zrozumienie modeli obiektów, używanych w rozszerzeń narzędzi SharePoint
 Istnieje kilka modeli obiektów, których można użyć podczas tworzenia rozszerzeń dla narzędzi SharePoint:

-   *Modelu obiektów programu SharePoint narzędzia*. Ten model obiektów zapewnia rozszerzalność interfejsów, które implementują do tworzenia rozszerzenia narzędzi programu SharePoint i innych powiązanych typów.

-   *Visual Studio Automatyzacja i integracja modele do obiektów*. Te modele obiektów umożliwia dostęp do funkcji programu Visual Studio, które wykraczają poza zakres modelu obiektów przy użyciu narzędzi programu SharePoint.

    > [!NOTE]
    >  Możesz przekonwertować niektóre obiekty w modelu obiektu narzędzi programu SharePoint do obiektów w automatyzacji programu Visual Studio i modeli obiektów integracji i odwrotnie, korzystając z usługi projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [konwersji między typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

-   *Modele obiektów serwera i klienta programu SharePoint*. Użyj tych modeli obiektów, do modyfikowania witryny programu SharePoint lub odbierać dane z witryny programu SharePoint z kontekstu rozszerzenia narzędzi programu SharePoint.

### <a name="sharepoint-tools-object-model"></a>Model obiektów programu SharePoint narzędzia
 Każdego rozszerzenia narzędzi programu SharePoint używa typów w modelu obiektów programu SharePoint narzędzia do definiowania zachowania podstawowych i funkcji rozszerzenia. W poniższych tabelach opisano przestrzenie nazw, które mają zostać uwzględnione w tym modelu obiektu assemby, który je zawiera.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Zawiera typy, które służą do rozszerzania i automatyzacji systemu projektu programu SharePoint. Na przykład można rozszerzyć wbudowane projekty programu SharePoint i elementy projektu, lub możesz utworzyć własne elementy projektu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Zawiera typy, które służą do rozszerzenia procesu wdrażania projektów programu SharePoint, takich jak tworzenie własnych kroki wdrażania i konfiguracji wdrażania. Aby uzyskać więcej informacji, zobacz [pakowaniem i wdrażaniem SharePoint rozszerzyć](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Zawiera typy, które służą do rozszerzenia węzłów w ramach **połączeń SharePoint** w węźle **Eksploratora serwera** oknie lub do definiowania nowych typów węzłów. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Zawiera typy, które umożliwiają dostęp do definicji funkcji w projekcie programu SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Zawiera typy, które umożliwiają dostęp do definicji pakietów w rozwiązaniu programu SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Zawiera typy, które służy do dostosowywania funkcji i zachowania poprawności pakietu dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Zawiera typy, które służą do tworzenia niestandardowych *poleceń programu SharePoint*. Polecenie programu SharePoint jest metodą, która wywołuje w modelu obiektów serwera SharePoint z rozszerzenia narzędzi programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Przestrzeń nazw|Opis|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Zawiera typy, które można użyć, aby uzyskać informacje o wbudowanych **Eksploratora serwera** węzły, które reprezentują poszczególne składniki w witrynie programu SharePoint, takich jak węzeł, który reprezentuje listę, pole lub typ zawartości. Aby uzyskać więcej informacji, zobacz [rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Model obiektowy automatyzacji w usłudze Visual Studio
 Modelu obiektu automatyzacji programu Visual Studio udostępnia interfejsy API, które można użyć do zautomatyzowania projektów programu Visual Studio i środowiska IDE. Wykonywanie zadań związanych z projektem, które nie są specyficzne dla projektów programu SharePoint lub wykonywać inne zadania automatyzacji ogólnej w programie Visual Studio, należy użyć modelu obiektów programu Visual Studio. Tradycyjnie ten model obiektów jest często używane w dodatkach programu Visual Studio i makra, ale można go także użyć w rozszerzenia narzędzi programu SharePoint.

 Główna część modelu obiektu automatyzacji programu Visual Studio jest zdefiniowany w *EnvDTE.dll* zestawu. *EnvDTE\\<version>.dll* zestawy oferowanie dodatkowych funkcji, która została wprowadzona w określonych wersjach programu Visual Studio. Te zestawy są dołączone do programu Visual Studio.

 Aby uzyskać więcej informacji na temat modelu obiektu automatyzacji, zobacz [odwołanie do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Model obiektu integracji programu Visual Studio
 Integracja object model zawiera interfejsy API, które można użyć, aby dodać funkcje do programu Visual Studio, tworząc *pakietu VSPackage*. Pakietu VSPackage jest moduł, który rozszerza środowiska IDE programu Visual Studio, zapewniając niestandardowe funkcje, takie jak okna narzędzi, edytory, projektantów, usług i projektów.

 Jeśli chcesz dodać nową funkcję programu Visual Studio, która będzie służyć za pomocą wbudowanych narzędzi programu SharePoint, można użyć modelu obiektów integracji. Na przykład jeśli utworzysz niestandardowego elementu projektu programu SharePoint, która reprezentuje akcję niestandardową dla witryny programu SharePoint, można utworzyć również pakietu VSPackage, który implementuje projektanta dla akcji niestandardowej. Projektant można skojarzyć z akcji niestandardowej, przez dodawanie pozycji menu skrótów do elementu projektu, która reprezentuje akcję niestandardową w **Eksploratora rozwiązań**. Można otworzyć projektanta, otwierając jego menu skrótów (klikając prawym przyciskiem myszy niestandardowej akcji elementu projektu lub wybierając je, a następnie wybierając **Shift**+**F10** kluczy), a następnie wybierając **Otwórz**.

 Ten model obiektu jest zdefiniowana w zbiór zestawów, które są dołączone do zestawu SDK programu Visual Studio. Niektóre główne zestawy w modelu obiektowego *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll*, i  *Microsoft.VisualStudio.OLE.Interop.dll*.

 Aby uzyskać więcej informacji na temat integracji modelu obiektów zobacz [omówienie modelu automatyzacji](../extensibility/internals/automation-model-overview.md) i [odwołanie do zestawu SDK programu Visual Studio](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>Modeli obiektów SharePoint
 Rozszerzenia narzędzi programu SharePoint można użyć interfejsów API programu SharePoint, do modyfikowania witryny programu SharePoint lub odbierać dane z witryny programu SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zapewnia dwa różne modele obiektów: modelu obiektów serwera i modelu obiektów klienta.

 W modelu obiektu, albo w rozszerzenia narzędzi programu SharePoint mogą używać interfejsów API, ale każdy model obiektu ma niektóre zalety i wady w kontekście rozszerzenia narzędzi programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Model obiektów|Opis|
|------------------|-----------------|
|Model obiektu serwera|W modelu obiektów serwera zapewnia dostęp do wszystkich funkcji [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ujawnić programowo. Ten model obiektów jest przeznaczony do użycia przez rozwiązania programu SharePoint, które są uruchamiane na serwerze programu SharePoint. Większość tego modelu obiektu jest zdefiniowana w *Microsoft.SharePoint.dll* zestawu. Aby uzyskać więcej informacji na temat modelu obiektów serwera, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).|
|Model obiektu klienta|Model obiektu klienta jest podzbiorem modelu obiektów serwera, który może służyć do współdziałania z danymi programu SharePoint z klientem zdalnym lub serwera. Zaprojektowano go w celu zminimalizowania liczby rund, które muszą być wykonane w celu wykonywania typowych zadań. Większość client object model jest zdefiniowana w *Microsoft.SharePoint.Client.dll* i *Microsoft.SharePoint.Client.Runtime.dll* zestawów. Aby uzyskać więcej informacji na temat modelu obiektów klienta, zobacz [zarządzane Client Object Model](http://go.microsoft.com/fwlink/?LinkId=177797).|

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
