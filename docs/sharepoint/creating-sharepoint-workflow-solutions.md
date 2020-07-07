---
title: Tworzenie rozwiązań przepływu pracy programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c787009577735213437140513ec095f81c3f43b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015288"
---
# <a name="create-sharepoint-workflow-solutions"></a>Tworzenie rozwiązań przepływu pracy programu SharePoint

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera narzędzia ułatwiające tworzenie niestandardowych przepływów pracy, które zarządzają cyklem życia dokumentów i elementów listy w witrynie sieci Web programu SharePoint. Dostarczone elementy obejmują projektanta, zestaw kontrolek działania oraz niezbędne odwołania do zestawu. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]zawiera także **Kreatora dostosowania programu SharePoint**, który ułatwia tworzenie i Konfigurowanie przepływów pracy.

Aby uzyskać więcej informacji na temat programu SharePoint, zobacz [produkty i technologie programu Microsoft SharePoint](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Przepływy pracy w programie SharePoint
 Po dodaniu przepływu pracy do biblioteki lub listy programu SharePoint należy wymusić proces biznesowy dla wszystkich elementów w bibliotece lub liście. Przepływ pracy zawiera opis akcji, które system lub użytkownicy muszą wykonać na każdym z elementów, takich jak wysyłanie elementu do edycji, a następnie przeglądanie. Te akcje, nazywane *działaniami*, są blokami konstrukcyjnymi przepływu pracy.

 Możesz tworzyć przepływy pracy programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i wdrażać je w witrynie sieci Web programu SharePoint. Po wdrożeniu przepływu pracy w programie SharePoint należy skojarzyć go z biblioteką lub listą. Następnie można uruchomić go automatycznie, przez proces lub ręcznie przez użytkownika. Aby uzyskać więcej informacji na temat operacji przepływu pracy, zobacz [opracowywanie przepływów pracy programu SharePoint przy użyciu programu Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Tworzenie niestandardowych przepływów pracy programu SharePoint
 W programie dostępne są dwa projekty przepływu pracy programu SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] : **sekwencyjny przepływ pracy** i **przepływ pracy automatu Stanów**.

 *Sekwencyjny przepływ pracy* reprezentuje serię kroków. Kroki są wykonywane jeden po drugim do momentu zakończenia ostatniego działania. Sekwencyjne przepływy pracy są zawsze ściśle sekwencyjne w ich wykonaniu. Ponieważ mogą odbierać zewnętrzne zdarzenia i obejmować równoległe przepływy logiczne, Dokładna kolejność wykonywania może się różnić. Na poniższej ilustracji przedstawiono przykład sekwencyjnego przepływu pracy.

 ![Sekwencyjny przepływ pracy](../sharepoint/media/sp-sequential.png "Sekwencyjny przepływ pracy")

 *Przepływ pracy automatu Stanów* reprezentuje zestaw Stanów, przejść i akcji. Kroki w przepływie pracy automatu Stanów są wykonywane asynchronicznie. Oznacza to, że nie są one wykonywane jeden po drugim, ale zamiast tego są wyzwalane przez akcje i Stany. Jeden stan jest przypisywany jako stan początkowy, a następnie na podstawie zdarzenia następuje przejście do innego stanu. Komputer stanu może mieć stan końcowy, który określa koniec przepływu pracy. Na poniższym diagramie przedstawiono przykładowy przepływ pracy automatu Stanów.

 ![Przepływ pracy automatu Stanów](../sharepoint/media/sp-state.png "Przepływ pracy automatu Stanów")

 Aby uzyskać więcej informacji na temat typów przepływów pracy, zobacz [Typy przepływów pracy](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Korzystanie z Kreatora
 Podczas tworzenia projektu przepływu pracy programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] należy najpierw określić jego ustawienia w **Kreatorze dostosowywania programu SharePoint**. Kreator używa tych ustawień do tworzenia projektu w **Eksplorator rozwiązań**. Ten projekt zawiera plik kodu, kilka plików, które są używane do wdrożenia przepływu pracy, oraz odwołania do zestawów, które są wymagane do utworzenia niestandardowego przepływu pracy programu SharePoint.

 Po utworzeniu przepływu pracy można zmodyfikować jego właściwości w okno Właściwości. Chociaż większość właściwości przepływu pracy można zmienić bezpośrednio w okno Właściwości, niektóre wymagają kliknięcia przycisku wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")), aby zmienić ich wartości. Ten przycisk powoduje ponowne uruchomienie **Kreatora dostosowania programu SharePoint**. Po zmianie wartości właściwości wybierz przycisk **Zakończ** , aby zakończyć.

> [!NOTE]
> Właściwość **typu przepływu pracy** jest tylko do odczytu i nie można jej zmienić. Jeśli chcesz zmienić typ przepływu pracy, musisz utworzyć inny przepływ pracy.

## <a name="design-a-sharepoint-workflow"></a>Projektowanie przepływu pracy programu SharePoint
 Po zdefiniowaniu wszystkich kroków w procesie biznesowym [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] można zaprojektować przepływ pracy programu SharePoint za pomocą projektanta przepływu pracy. Aby otworzyć projektanta, kliknij dwukrotnie pozycję Workflow1.cs lub Workflow1. vb w **Eksplorator rozwiązań**lub Otwórz menu skrótów dla jednego z tych plików, a następnie wybierz polecenie **Otwórz**.

### <a name="activities"></a>Działania
 Aby zaprojektować przepływ pracy, należy dodać działania z **przybornika** do *harmonogramu przepływu pracy* w projektancie. Harmonogram przepływu pracy zawiera sekwencję działań w kolejności, w jakiej powinny być wykonywane.

 Istnieją dwa typy działań:

- *Proste działania* wykonują pojedynczą jednostkę pracy, na przykład "opóźnienie przez 1 dzień" lub "Uruchamianie usługi sieci Web".

- *Działania złożone* zawierają inne działania; na przykład działanie warunkowe może zawierać dwie gałęzie.

  Oba rodzaje działań są dostępne w **przyborniku**.

  Działania mogą mieć właściwości, metody i zdarzenia. Użyj okna **Właściwości** , aby ustawić właściwości działania.

  Możesz również utworzyć niestandardowe działanie. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego działania przepływu pracy w witrynie](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Działania są zorganizowane na następujących kartach w **przyborniku**:

- **Przepływ pracy programu SharePoint**

- **Windows Workflow 3.0**

- **Windows Workflow 3.5**

  Nie wszystkie działania podstawowe przepływów pracy są obsługiwane przez program SharePoint. Aby uzyskać więcej informacji, zobacz temat [działania przepływu pracy dla programu Windows SharePoint Services — Omówienie](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>Działania związane z przepływem pracy programu SharePoint
 Karty **przepływu pracy programu SharePoint** zawierają wyspecjalizowane działania do użycia w programie [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] . Te działania upraszczają i usprawniają opracowywanie przepływów pracy związanych z cyklem życia dokumentów. Aby uzyskać więcej informacji na temat działań wymienionych na karcie **przepływ pracy programu SharePoint** , zobacz temat [działania przepływu pracy dla programu Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Działania przepływu pracy systemu Windows
 Karty **przepływu pracy systemu Windows** zawierają działania, które są dostarczane przez [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] . Te działania mogą służyć do tworzenia harmonogramów przepływu pracy dla dowolnego rodzaju aplikacji Windows Workflow.

 Aby uzyskać więcej informacji na temat działań wymienionych na karcie **przepływy pracy systemu Windows** , zobacz [Windows Workflow Foundation działania](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Aby uzyskać więcej informacji na temat Windows Workflow Foundation, zobacz [Windows Workflow Foundation Omówienie](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Praca z działaniami w projektancie
 Harmonogram przepływu pracy może zawierać kombinację działań przepływu pracy w systemie Windows i działań przepływu pracy programu SharePoint.

 Projektant wyświetla podpowiedzi wizualizacji, aby pomóc w poprawnym pozycjonowaniu i konfigurowaniu działań. Podczas przeciągania lub kopiowania działania do harmonogramu przepływu pracy, w projektancie są wyświetlane ikony zielony znak plus (+) pokazujące prawidłowe lokalizacje tego działania w przepływie pracy. Nie można umieścić działania w lokalizacji, w której będzie ona nieprawidłowa. Na przykład nie można umieścić działania wysyłania jako pierwszego działania w rozgałęzieniu działania listen. Aby uzyskać więcej informacji, zobacz [Centrum deweloperów programu SharePoint Designer](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Zbierz informacje podczas przepływu pracy
 Możesz chcieć zbierać informacje od użytkowników we wstępnie zdefiniowanym czasie w przepływie pracy. Informacje można zbierać przy użyciu formularzy lub właściwości elementów.

### <a name="forms"></a>Formularze
 Formularze są podobne do okien dialogowych, które zawierają pytania i umożliwiają użytkownikom udzielanie odpowiedzi.

 Istnieją cztery typy formularzy, które mogą być używane w przepływie pracy:

- Skojarzenie

- Rozpoczęcie

- Modyfikowanie

- Zadanie

  Z tych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementów, obejmują szablony elementu dla formularzy skojarzenia i inicjowania. Przykładem *formularza skojarzenia* jest taki, który pozwala administratorowi na instalowanie przepływu pracy wprowadzić parametry, które odnoszą się do przepływu pracy, na przykład limit wydatków dla przepływu pracy. Przykładem *formularza inicjowania* jest taki, który umożliwia użytkownikowi przepływu pracy wydatków wprowadzanie ilości, która pozostała w przepływie pracy. Aby uzyskać więcej informacji na temat tych typów formularzy, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Właściwości elementu
 Możesz również zbierać informacje od użytkowników, używając właściwości elementu w bibliotece lub liście programu SharePoint. Plik głównego kodu (Workflow1.cs lub Workflow1. vb) deklaruje wystąpienie klasy Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. WorkflowProperties o nazwie `workflowProperties` . Użyj `workflowProperties` obiektu, aby uzyskać dostęp do właściwości biblioteki lub listy w kodzie. Aby zapoznać się z przykładem, zobacz [Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Debugowanie szablonu przepływu pracy programu SharePoint
 Można debugować projekt przepływu pracy programu SharePoint w taki sam sposób, jak debugowanie innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów opartych na sieci Web. Po uruchomieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa ustawień określonych w **Kreatorze dostosowania programu SharePoint** , aby otworzyć odpowiednią witrynę sieci Web programu SharePoint i automatycznie skojarzyć szablon przepływu pracy z odpowiednią biblioteką lub listą. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]dołącza także [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debuger do [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] procesu o nazwie *w3wp.exe*.

 Aby przetestować przepływ pracy, należy uruchomić go ręcznie. Aby uzyskać więcej informacji, zobacz sekcję "Debugowanie przepływów pracy" w artykule [Debugowanie rozwiązań programu SharePoint](../sharepoint/debugging-sharepoint-solutions.md). Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugowania aplikacji sieci Web, zobacz [debugowanie aplikacji sieci Web i skryptów](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Wdrażanie szablonu przepływu pracy programu SharePoint
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Projekty przepływu pracy programu SharePoint wdrażają się podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty programu SharePoint. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importowanie przepływów pracy wielokrotnego użytku, które można ponownie wykorzystać
 Oprócz tworzenia przepływów pracy wielokrotnego użytku specyficznych dla lokacji, program SharePoint Designer umożliwia tworzenie *globalnych przepływów pracy wielokrotnego użytku*, które są przepływami pracy, które mogą być używane przez dowolną witrynę programu SharePoint. Projekt zaimportuj przepływ pracy wielokrotnego użytku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obecnie nie importuje globalnie dostępnych przepływów pracy wielokrotnego użytku. Można jednak użyć programu SharePoint Designer do przekonwertowania globalnego przepływu pracy wielokrotnego użytku do przepływu pracy wielokrotnego użytku lub zaimportowania przepływu pracy jako nieskonwertowanego deklaracyjnego przepływu pracy. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Prowadzi Cię krok po kroku przez tworzenie i debugowanie prostego [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przepływu pracy.|
|[Przewodnik: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Prowadzi krok po kroku, aby utworzyć pełniejszy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przepływ pracy uzupełniający przy użyciu formularzy skojarzenia i inicjowania.|
|[Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Kompilacje w [przewodniku: tworzenie przepływu pracy z formularzami skojarzenia i inicjacji](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) przez dodanie dodatkowej strony aplikacji *. aspx* , która raportuje dane wprowadzone do przepływu pracy.|
|[Przewodnik: Tworzenie niestandardowego działania przepływu pracy witryny](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Pokazuje, jak wykonywać dwa kluczowe zadania: tworzenie przepływu pracy na poziomie witryny i tworzenie niestandardowego działania przepływu pracy.|
|[Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Demonstruje sposób importowania deklaratywnych przepływów pracy wielokrotnego użytku utworzonych w programie SharePoint Designer 2010 do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)