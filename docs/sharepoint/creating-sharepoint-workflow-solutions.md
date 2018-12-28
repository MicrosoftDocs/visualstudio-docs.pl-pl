---
title: Tworzenie rozwiązań przepływu pracy programu SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0dd8a1339dddc52326bf7b0e42d52c1eaa53e6cf
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802501"
---
# <a name="create-sharepoint-workflow-solutions"></a>Tworzenie rozwiązań przepływu pracy SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] udostępnia narzędzia pomocne podczas tworzenia niestandardowych przepływów pracy, które zarządzać cyklem życia dokumentami i elementami listy w witrynie sieci Web programu SharePoint. Podane elementy obejmują projektanta, zestaw formantów działania i niezbędne odwołania do zestawu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera również **Kreator ustawień niestandardowych SharePoint**, aby ułatwić tworzenie i Konfigurowanie przepływów pracy.

Aby uzyskać więcej informacji na temat programu SharePoint, zobacz [Microsoft produktów i technologii SharePoint](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Przepływy pracy w programie SharePoint
 Po dodaniu przepływu pracy do biblioteki programu SharePoint lub listy można wymusić proces biznesowy na wszystkich elementach w bibliotece lub na liście. Przepływ pracy zawiera opis akcji, które system lub użytkowników, należy wykonać dla każdego elementu, takie jak wysyłanie element które mają być edytowane, a następnie sprawdzono. Te akcje, znane jako *działania*, są blokami konstrukcyjnymi przepływu pracy.

 Możesz utworzyć przepływów pracy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i wdróż je w witrynie sieci Web programu SharePoint. Po wdrożeniu przepływu pracy programu SharePoint, należy ją skojarzyć z biblioteki lub listy. Może następnie być uruchamiany automatycznie przez proces lub ręcznie przez użytkownika. Aby uzyskać więcej informacji na temat operacji przepływu pracy, zobacz [tworzenie przepływów pracy programu SharePoint przy użyciu programu Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Tworzenie niestandardowych przepływów pracy programu SharePoint
 Dwa projekty przepływu pracy programu SharePoint są dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **Sekwencyjny przepływ pracy** i **stanu przepływu pracy komputera**.

 A *sekwencyjnego przepływu pracy* reprezentuje serię kroków. Kroki są wykonywane jedna po drugiej, do momentu ukończenia ostatniego działania. Sekwencyjne przepływy pracy są zawsze ściśle sekwencyjnego w ich realizacji. Może odbierać zdarzenia zewnętrzne, a także obejmują przepływów logiki równoległej, na kolejność wykonywania mogą się nieznacznie różnić. Na poniższej ilustracji przedstawiono przykład sekwencyjnego przepływu pracy.

 ![Sekwencyjny przepływ pracy](../sharepoint/media/sp-sequential.png "sekwencyjnego przepływu pracy")

 A *przepływ pracy automatu stanów* reprezentuje zestaw stany, przejścia i akcje. Kroki opisane w przepływ pracy automatu stanów są wykonywane asynchronicznie. Oznacza to, ich nie są zawsze wykonywane po kolei, ale zamiast tego są wyzwalane przez działania i stanów. Jednego stanu jest przypisany jako stan początkowy, a następnie na podstawie zdarzenia, przejście zostanie podjęta inny stan. Automatu stanów może mieć stan końcowy, który określa koniec przepływu pracy. Na poniższym diagramie przedstawiono przykład przepływ pracy automatu stanów.

 ![Stan przepływu pracy komputera](../sharepoint/media/sp-state.png "stanu przepływu pracy komputera")

 Aby uzyskać więcej informacji na temat typów przepływu pracy, zobacz [typy przepływów pracy](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Za pomocą Kreatora
 Po utworzeniu projektu przepływu pracy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy najpierw określić jego ustawień **Kreator ustawień niestandardowych SharePoint**. Kreator używa tych ustawień, aby utworzyć projekt w **Eksploratora rozwiązań**. Ten projekt zawiera plik kodu, kilka plików, które są używane do wdrażania przepływu pracy, a odwołuje się do zestawów, które są wymagane do utworzenia niestandardowych przepływu pracy programu SharePoint.

 Po utworzeniu przepływu pracy, można zmodyfikować jego właściwości w oknie dialogowym właściwości. Mimo że większość właściwości przepływu pracy można zmienić bezpośrednio w oknie dialogowym właściwości, niektóre wymagają kliknij przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) do modyfikowanie ich wartości. Kliknięcie tego przycisku powoduje ponowne uruchomienie **Kreator ustawień niestandardowych SharePoint**. Po wprowadzeniu właściwości wartość zmiany, wybierz **Zakończ** przycisk, aby zakończyć je.

> [!NOTE]
>  **Przepływu pracy typu** właściwość jest tylko do odczytu i nie można jej zmienić. Jeśli chcesz zmienić typ przepływu pracy, należy utworzyć inny przepływ pracy.

## <a name="design-a-sharepoint-workflow"></a>Projekt przepływu pracy programu SharePoint
 Po zdefiniowaniu wszystkich czynności w procesie biznesowym za pomocą [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta przepływu pracy do projektowania przepływu pracy programu SharePoint. Aby otworzyć projektanta, kliknij dwukrotnie Workflow1.cs lub Workflow1.vb w **Eksploratora rozwiązań**, lub Otwórz menu skrótów dla jednej z tych plików, a następnie wybierz **Otwórz**.

### <a name="activities"></a>Kategoria Activities
 Aby zaprojektować przepływ pracy, należy dodać działania z **przybornika** do *harmonogram przepływu pracy* w projektancie. Harmonogram przepływu pracy zawiera sekwencję działań w kolejności, że powinno być przeprowadzane.

 Istnieją dwa typy działań:

- *Proste działania* wykonać pojedynczą jednostkę pracy, takich jak "Opóźnij przez 1 dzień" lub "uruchomić usługi sieci Web".

- *Działań złożonych* zawierają inne działania; na przykład warunkowego działanie może zawierać dwie gałęzie.

  Oba rodzaje działań są dostępne w **przybornika**.

  Działania mogą mieć właściwości, metody i zdarzenia. Użyj **właściwości** okna do ustawiania właściwości działania.

  Można również utworzyć niestandardowe działanie. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowego przepływu pracy działania witryny](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Działania są pogrupowane w następującej karcie we **przybornika**:

- **Przepływ pracy programu SharePoint**

- **Windows Workflow 3.0**

- **Windows Workflow 3.5**

  Nie wszystkie działania przepływu pracy podstawowej są obsługiwane przez program SharePoint. Aby uzyskać więcej informacji, zobacz [działań dla Windows SharePoint przegląd usług przepływu pracy](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>Działania przepływu pracy programu SharePoint
 **Przepływu pracy programu SharePoint** karty zawierają wyspecjalizowanych działań do użycia w [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Te działania upraszczającego i usprawniającego rozwoju cyklu życia dokumentu w przepływach pracy. Aby uzyskać więcej informacji o działaniach na liście **przepływu pracy programu SharePoint** kartę, zobacz [działań dla Windows SharePoint przegląd usług przepływu pracy](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Działania przepływu pracy Windows
 **Windows Workflow** karty zawierają działania, które są dostarczane przez [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Te działania można użyć do tworzenia harmonogramów przepływu pracy dla każdego rodzaju aplikacji przepływu pracy Windows.

 Aby uzyskać więcej informacji o działaniach na liście **przepływy pracy Windows** kartę, zobacz [działania programu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=156096). Aby uzyskać więcej informacji na temat programu Windows Workflow Foundation, zobacz [Windows Workflow Foundation — omówienie](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Praca z działaniami w Projektancie
 Harmonogram przepływu pracy może zawierać kombinację działań przepływu pracy Windows i działań przepływu pracy programu SharePoint.

 Projektant wyświetla podpowiedzi wizualne, które ułatwią Ci położenie i działania jest prawidłowo skonfigurowane. Przeciągnij lub skopiuj działania na harmonogram przepływu pracy, Projektant wyświetla ikony zielony znak plus (+), które przedstawiają prawidłowe lokalizacje dla tego działania w przepływie pracy. Nie możesz umieścić działania w lokalizacji, w którym nie jest prawidłowy. Na przykład nie możesz umieścić działania wysyłania, jako pierwsze działanie w gałęzi działania nasłuchiwania. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów programu SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Zbieranie informacji podczas przepływu pracy
 Możesz zbierać dane od użytkowników na wstępnie zdefiniowanym czasie w przepływie pracy. Może zbierać informacje za pomocą formularzy i właściwości elementu.

### <a name="forms"></a>Formularze
 Formularze są takie jak okna dialogowe, zawierające pytania i umożliwiają użytkownikom udzielić odpowiedzi.

 Istnieją cztery rodzaje formularzy, które mogą być używane w przepływie pracy:

- Skojarzenie

- Inicjowania

- Modyfikacja

- Zadanie

  Z tych opcji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obejmuje szablony elementów dla formularzy skojarzenia i inicjacji. Przykładem *formularza skojarzenia* jest taki, który umożliwia administratorowi zainstalowanie przepływu pracy wprowadź parametry, które odnoszą się do przepływu pracy, takie jak limit wydatków dla przepływu pracy wydatków. Przykładem *formularza inicjowania* to taki, który umożliwia użytkownikowi wydatków przepływu pracy wprowadź kwotę poświęcony do przepływu pracy. Aby uzyskać więcej informacji na temat tego rodzaju formularzy zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Właściwości elementu.
 Może również zbierać informacje od użytkowników za pomocą właściwości elementu w bibliotece programu SharePoint lub na liście. Pliku głównego kodu (Workflow1.cs lub Workflow1.vb) oświadcza, wystąpienie klasy Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties o nazwie `workflowProperties`. Użyj `workflowProperties` obiekt, aby uzyskać dostęp do właściwości biblioteki lub listy w kodzie. Aby uzyskać przykład, zobacz [instruktażu: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Debugowanie szablonu przepływu pracy programu SharePoint
 Możesz debugować projekt przepływu pracy programu SharePoint takie same jak można debugować innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty oparte na sieci Web. Po uruchomieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] korzysta z ustawień, które są określone w **Kreator ustawień niestandardowych SharePoint** Otwórz odpowiednią witrynę sieci Web programu SharePoint i automatycznie skojarzenia szablonu przepływu pracy za pomocą odpowiedniej biblioteki lub listy. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dołącza również [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuger [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] procesu o nazwie *w3wp.exe*.

 Aby przetestować przepływ pracy, należy uruchomić go ręcznie. Aby uzyskać więcej informacji, zobacz sekcję "Debugowanie przepływów pracy" w [debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugowaniem aplikacji sieci Web, zobacz [debugowanie aplikacji sieci web i skryptu](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Wdrażanie szablonu przepływu pracy programu SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Wdrażanie projektów przepływu pracy programu SharePoint, podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [rozwiązań pakietu i wdrożenia programu SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importowanie globalnie wielokrotnych przepływów danych
 Oprócz tworzenia przepływów danych wielokrotnego użytku specyficzne dla lokacji, programu SharePoint Designer umożliwia tworzenie *globalnie wielokrotnych przepływów danych*, które są przepływy pracy, które mogą być używane przez wszystkie witryny programu SharePoint. Projekt Importowanie przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aktualnie nie importuje globalny wielokrotnych przepływów danych. Jednak można albo użyj programu SharePoint Designer do konwertowania do wielokrotnego użytku globalnego przepływu pracy do przepływu pracy wielokrotnego użytku, lub importowanie przepływu pracy jako nieprzekonwertowane deklaracyjnego przepływu pracy. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Prowadzi użytkownika krok po kroku proces tworzenia i debugowania prostego [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przepływu pracy.|
|[Przewodnik: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Prowadzi użytkownika krok po kroku do tworzenia zaawansowanych funkcji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przepływu pracy wykonaj z formularzy skojarzenia i inicjacji.|
|[Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Opiera się na temat [instruktażu: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) przez dodanie dodatkowych *.aspx* strona aplikacji, zawierający raporty dotyczące danych wprowadzanych do przepływu pracy.|
|[Przewodnik: Utwórz niestandardową witrynę działanie przepływu pracy](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Pokazuje, jak wykonać dwa kluczowe zadania: Utwórz poziomie witryny przepływu pracy i utworzyć działanie niestandardowego przepływu pracy.|
|[Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Pokazuje, jak zaimportować deklaratywne przepływów danych wielokrotnego użytku, utworzone w programie SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)