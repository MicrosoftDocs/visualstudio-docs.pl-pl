---
title: Projekty programu SharePoint i szablony elementów projektu | Microsoft Docs
description: Przejrzyj opisy dostępnego projektu programu SharePoint oraz szablonów elementów projektu i sposobu ich użycia.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6cbcc4d0bc99ce7ab495e0a24591b145c58f377
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95970374"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Projekty programu SharePoint i szablony elementów projektu
  W poniższych sekcjach opisano dostępne projekty programu SharePoint i szablony elementów projektu oraz sposób ich użycia.

## <a name="project-and-project-item-templates-overview"></a>Przegląd szablonów elementów projektu i projektu
 Podczas tworzenia nowego projektu programu SharePoint w programie Visual Studio, projekt programu SharePoint jest dodawany do rozwiązania wraz ze wszystkimi elementami projektu wymaganymi przez ten typ projektu. Na przykład, jeśli tworzysz projekt składnika Web Part Silverlight, Visual Studio utworzy rozwiązanie, które zawiera element projektu Visual Web Part i element projektu aplikacji Silverlight wraz ze wszystkimi plikami wymaganymi przez te elementy projektu. Szablony elementów projektu służą do dodawania elementów projektu do istniejącego projektu programu SharePoint, takich jak dodawanie odbiorcy zdarzeń, kolumna witryny lub lista.

 Aby uzyskać informacje na temat podstaw programu SharePoint, zobacz [bloki konstrukcyjne programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Użytkownicy zaawansowani mogą tworzyć niestandardowe szablony projektu i elementów projektu. Aby uzyskać więcej informacji, zobacz Rozpoznaj [system projektu programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Szablony projektów
 Poniżej znajduje się lista szablonów projektów programu SharePoint. Aby wyświetlić szablony projektu programu SharePoint w programie Visual Studio, w oknie dialogowym **Nowy projekt** rozwiń węzeł **SharePoint** w obszarze **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010**.

### <a name="sharepoint-2010-project"></a>Projekt 2010 programu SharePoint
 Zawartość *projektu programu sharepoint 2010* jest uwzględniona w każdym szablonie projektu programu SharePoint. Projekt programu SharePoint 2010 zawiera:

- Plik projektu.

- Strona właściwości projektu.

- Folder **odwołań** wymienia wszystkie odwołania do zestawu w projekcie.

- Folder **funkcji** , który zawiera plik konfiguracji *funkcji* służący do wdrażania funkcji na serwerze programu SharePoint.

- Folder **pakietu** zawierający plik *Package. Package* używany do wdrożenia rozwiązania w programie SharePoint.

- Plik Key. snk (klucza o silnej nazwie), który jest używany do podpisywania zestawu silną nazwą, aby zwiększyć bezpieczeństwo.

### <a name="sharepoint-2010-silverlight-web-part"></a>Składnik Web Part Silverlight programu SharePoint 2010
 Projekty *składnika Web Part programu sharepoint 2010 Silverlight* umożliwiają tworzenie części sieci Web dla programu SharePoint, w których są wyświetlane aplikacje Silverlight. Podczas tworzenia projektu można określić, czy dodać do niego nową aplikację Silverlight, czy też odwołać się do istniejącej. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [Przewodnik: Tworzenie składnika Web Part programu Silverlight wyświetlającego dane OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Wizualny składnik Web Part programu SharePoint 2010
 Projekt *wizualnego składnika Web Part programu SharePoint 2010* zawiera plik definicji *Elements.xml* , element **składnika Web Part** i element **kontrolki użytkownika** . Wygląd wizualnego składnika Web Part można zaprojektować, przeciągając lub kopiując kontrolki z przybornika programu Visual Studio na powierzchnię kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie składnika Web Part programu SharePoint przy użyciu projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloku konstrukcyjnego: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importuj pakiet rozwiązań programu SharePoint 2010
 *Importuj projekty pakietu rozwiązań programu sharepoint 2010* umożliwiają zaimportowanie całej istniejącej witryny programu SharePoint 2010 lub jej części do programu Visual Studio, która została wyeksportowana do pliku rozwiązania programu SharePoint (*wsp*). Po zaimportowaniu do programu Visual Studio można dostosować jego elementy i wdrożyć je ponownie. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importuj przepływ pracy wielokrotnego użytku programu SharePoint 2010
 *Importuj projekty przepływu pracy do wielokrotnego użytku programu sharepoint 2010* umożliwiają zaimportowanie, deklaratywnego przepływu pracy utworzonego w programie SharePoint Designer 2010 do programu Visual Studio. Przepływ pracy jest eksportowany z witryny programu SharePoint jako plik *. wsp* . Po zaimportowaniu do programu Visual Studio można je dostosować, dodać do niego kod, a następnie wdrożyć w witrynie programu SharePoint. Aby uzyskać więcej informacji, zobacz [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Szablony elementów projektu
 Poniżej znajduje się lista szablonów elementów projektu programu SharePoint. Szablony elementów projektu umożliwiają dodanie plików do rozwiązania SharePoint w celu obsługi funkcji programu SharePoint, takich jak kolumny, listy i typy zawartości witryny. Na przykład dodanie kolumny witryny do rozwiązania powoduje dodanie projektu kolumny witryny, który zawiera plik definicji *Elements.xml* . Dodanie wizualnego składnika Web Part powoduje dodanie projektu wizualnego składnika Web Part do rozwiązania, które zawiera plik *Elements.xml* , element kontrolki użytkownika i element wizualnego składnika Web Part.

 Aby wyświetlić szablony elementów projektu programu SharePoint, w **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu programu SharePoint, a następnie wybierz **Dodaj**, **nowy element**. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz **2010**.

### <a name="application-page-farm-solution-only"></a>Strona aplikacji (tylko rozwiązanie farmy)
 **Strona aplikacji (tylko rozwiązanie farmy)** umożliwia zaprojektowanie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci Web dla witryny programu SharePoint. Strony aplikacji mogą być używane tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md) i [aplikacji _layouts typ strony](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Model łączności danych firmowych (tylko rozwiązanie farmy)
 Element **model łączności danych firmowych (tylko rozwiązanie farmy)** umożliwia integrowanie danych firmowych z programem SharePoint. Dane biznesowe mogą pochodzić z aplikacji serwera zaplecza, takich jak [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] firma Siebel i Service Advertising Protocol (SAP). Modele łączności danych firmowych mogą być używane tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [How to: Create a BDC model](../sharepoint/how-to-create-a-bdc-model.md)( [instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)) oraz [nowości: usługi łączności biznesowej](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Typ zawartości
 Elementy *typu zawartości* umożliwiają tworzenie niestandardowych typów zawartości na podstawie istniejącego typu zawartości (podstawowej), takiego jak dokument, anons lub zadanie. Niestandardowy typ zawartości zapewnia te same atrybuty i pola co podstawowy typ zawartości wraz ze zdefiniowanymi kolumnami witryny (polami). Na przykład można utworzyć niestandardowy typ zawartości kontaktu oparty na podstawowym typie zawartości kontaktu, który znajduje się w programie SharePoint. Typ zawartości można dostosować, zmieniając istniejące kolumny lokacji lub dodając więcej kolumn lokacji do tych, które są już zawarte w podstawowym typie zawartości.

> [!NOTE]
> Ze względu na ograniczenie programu SharePoint nie można utworzyć typu zawartości rozwiązania farmy na podstawie typu zawartości rozwiązania w trybie piaskownicy.

 Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [blok konstrukcyjny: typ zawartości](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Pusty element
 *Puste elementy* są najczęściej używane do definiowania elementów projektu programu SharePoint, które nie mają szablonu projektu lub elementu projektu w programie Visual Studio. Po dodaniu pustego elementu do projektu, węzeł o nazwie EmptyElement [x] (gdzie [x] jest tworzony unikatowy numer \) . EmptyElement [x] zawiera pojedynczy plik o nazwie *Elements.xml.* Instrukcje służą [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] do definiowania żądanych elementów w *Elements.xml*.

### <a name="event-receiver"></a>Odbiorca zdarzeń
 *Odbiorcy zdarzeń* obsługują zdarzenia dla elementów w witrynie programu SharePoint, na przykład gdy element zostanie dodany do listy, gdy element sieci Web zostanie usunięty lub gdy przepływ pracy został uruchomiony. Szablon elementu projektu odbiorcy zdarzeń umożliwia obsługę

- Wyświetl listę zdarzeń

- Zdarzenia elementu listy

- Wyświetl listę zdarzeń poczty e-mail

- Zdarzenia sieci Web

- Wyświetl listę zdarzeń przepływu pracy

  Element projektu odbiorcy zdarzeń tworzy folder **odbiorcy zdarzeń** z pojedynczym plikiem klasy, który zawiera programy obsługi zdarzeń dla wszystkich zdarzeń, które zostały określone podczas tworzenia projektu w **Kreatorze dostosowywania programu SharePoint**. Klasa odbiorcy zdarzeń może obsługiwać zdarzenia występujące w witrynie programu SharePoint, gdy elementy takie jak pliki, pola, elementy, listy, załączniki, składniki Web Part i przepływy pracy są dodawane, aktualizowane, usuwane lub usuwane. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md) i [bloku konstrukcyjnego: obsługa zdarzeń](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>Lista
 Lista jest wystąpieniem podstawowej definicji listy programu SharePoint do wielokrotnego użytku, takiej jak kalendarz lub lista zadań. Po dodaniu listy do rozwiązania Projektant list umożliwia dodawanie kolumn do listy i tworzenie niestandardowych kolumn list. Obejmuje to kolumny witryny z typów zawartości. Można określić *Widok* listy, który określa kolumny, które będą widoczne na liście. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloków konstrukcyjnych: list i bibliotek dokumentów](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Moduł
 *Moduły* (nie należy mylić z [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułami) zawierają wszystkie pliki, które mają zostać wdrożone na serwerze programu SharePoint, takie jak obrazy lub notatki. Element projektu modułu zawiera węzeł **modułu** . Węzeł modułu zawiera dwa szablony elementów projektu: plik definicji XML, który działa jako manifest dla modułu i plik *sample.txt* , plik zastępczy. Aby uzyskać więcej informacji, zobacz [używanie modułów do dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md) i [modułów](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sekwencyjny przepływ pracy (tylko rozwiązanie farmy)
 *Sekwencyjny przepływ pracy* to seria kroków logiki biznesowej wykonanych w sekwencji, do momentu zakończenia ostatniego kroku. Sekwencyjne przepływy pracy są używane do zarządzania procesami, które obejmują elementy programu SharePoint, takie jak listy i dokumenty. Można tworzyć przepływy pracy na poziomie witryny (globalnym) lub na poziomie listy (lokalne), a także określić, czy przepływ pracy jest uruchamiany automatycznie, czy ręcznie. Tego elementu projektu można używać tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))i [nowości: usprawnienia przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Składnik Web Part Silverlight
 Elementy projektu *składnika Web Part Silverlight* umożliwiają tworzenie części sieci Web dla programu SharePoint, w których są wyświetlane aplikacje Silverlight. Po dodaniu tego elementu projektu do rozwiązania możesz zdecydować, czy dodać nową aplikację Silverlight lub odwołać się do istniejącej aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [Przewodnik: Tworzenie składnika Web Part programu Silverlight wyświetlającego dane OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Kolumna witryny
 *Kolumna witryny*, znana także jako *pole*, jest jednym z najbardziej podstawowych elementów, które można dodać do projektu programu SharePoint. Kolumna witryny reprezentuje typ danych, taki jak numer telefonu, komentarz tekstowy lub nazwa miasta kontaktu na liście kontaktów. Aby uzyskać więcej informacji, zobacz [Tworzenie kolumn witryn, typów zawartości i list dla programu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) i [kolumn](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definicja witryny (tylko rozwiązanie farmy)
 Elementy projektu *definicji witryny* zawierają folder definicji lokacji zawierający następujące pliki:

- Domyślna strona. aspx używana jako domyślna strona sieci Web witryny.

- Plik *onet.xml* , który definiuje składniki witryny.

- Plik XML temp w sieci Web, który określa konfiguracje definicji lokacji, które są wyświetlane w sekcji **Wybór szablonu** na stronie **Nowa witryna programu SharePoint** .

  Po dodaniu definicji lokacji należy dodać kod i pliki w celu wprowadzenia funkcji. Tego elementu projektu można używać tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie definicji witryny dla programu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) i [definicji lokacji i konfiguracji](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>Przepływ pracy automatu Stanów (tylko rozwiązanie farmy)
 *Przepływ pracy automatu Stanów* to zestaw Stanów, przejść i akcji logiki biznesowej. Kroki w przepływie pracy automatu stanów nie są wykonywane w kolejności; Zamiast tego są one wyzwalane przez akcje i Stany. Przepływy pracy automatu Stanów są skojarzone z elementami programu SharePoint, takimi jak listy i dokumenty, podobnie jak sekwencyjny przepływ pracy. Po ponownym uruchomieniu można tworzyć przepływy pracy na poziomie witryny (globalnym) lub na poziomie listy (lokalne). Możesz również wybrać, czy przepływ pracy jest uruchamiany automatycznie, czy ręcznie. Tego elementu projektu można używać tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))i [nowości: usprawnienia przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Kontrolka użytkownika (tylko rozwiązanie farmy)
 *Kontrolka użytkownika* to niestandardowa kontrolka wielokrotnego użytku, do której można dodać inne kontrolki ASP.NET i kontrolki programu SharePoint. Kontrolkę użytkownika można dodać do stron aplikacji i składników Web Part, które są uruchamiane w programie SharePoint. Tego elementu projektu można używać tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolek wielokrotnego użytku dla składniki Web Part lub stron aplikacji](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Wizualny składnik Web Part
 Element projektu *wizualnego składnika Web Part* zawiera plik definicji *Elements.xml* , element **składnika Web Part** i element **kontrolki użytkownika** . Wygląd wizualnego składnika Web Part można zaprojektować, przeciągając lub kopiując kontrolki z przybornika programu Visual Studio na powierzchnię kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie składnika Web Part programu SharePoint przy użyciu projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloku konstrukcyjnego: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web Part
 *Składnik Web Part* to formant po stronie serwera, który działa na specjalnym typie strony nazywanej stroną części sieci Web. Są to bloki konstrukcyjne stron, które są wyświetlane w witrynie programu SharePoint. Element składnika Web Part zawiera pliki, które umożliwiają projektowanie części sieci Web dla witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie składnika Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md) i [bloku konstrukcyjnego programu SharePoint: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produkty i technologie programu SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
