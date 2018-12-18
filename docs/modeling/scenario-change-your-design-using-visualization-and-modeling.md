---
title: 'Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc8066148b2c8612b3a07922e15422022b8c9c4d
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967509"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania

Upewnij się, że oprogramowanie systemu spełnia wymagania użytkowników przy użyciu wizualizacji i modelowania narzędzi w programie Visual Studio.
Użyj narzędzi takich jak mapy kodu, diagramów zależności i diagramy klas do:

Aby zobaczyć, które wersje programu Visual Studio obsługuje każde narzędzie, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Wyjaśnij procesy biznesowe i wymagania użytkowników.

- Wizualizacja i eksploracja istniejącego kodu.

- Opisz zmiany w istniejącym systemie.

- Sprawdź, czy system spełnia wymagania.

- Utrzymuj spójność kodu z projektem.

W tym instruktażu:

- W tym artykule opisano te narzędzia zyska projektem oprogramowania.

- Pokazano, jak może użyć tych narzędzi, niezależnie od tego, daną metodę rozwoju w przykładowym scenariuszu.

Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które wspierają, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Omówienie scenariusza

W tym scenariuszu opisano odcinki z cyklu rozwoju oprogramowania dwóch fikcyjnych spółek: Dinner Now i Lucerne Publishing. Dinner Now zapewnia terenie Seattle usługę dostarczania posiłków opartą na sieci Web. Klienci mogą posiłki i zapłacić za w witrynie internetowej firmy Dinner Now. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji do dostarczenia. Lucerna Publishing, firma w Nowym Jorku, prowadzi kilka działalności zarówno off, jak i w sieci Web. Na przykład uruchamiają witryny sieci Web, których klienci mogą ogłaszać opinie o restauracjach.

Lucerna niedawno nabyła obiad teraz i chce wprowadzić następujące zmiany:

- Integrowanie ich witryn sieci Web przez dodanie możliwości przeglądu restauracji na obiad teraz.

- Zamień na systemu płatności Dinner Now system firmy Lucerne.

- Rozwinięcie węzła usługi Dinner Now całego regionu.

Dinner Now używa SCRUM i eXtreme Programming. Mają bardzo wysokie pokrycie testu i bardzo mało nieobsługiwanego kodu. Firma minimalizuje ryzyko tworząc małe, ale działające wersje systemu, a następnie stopniowo dodając nowe funkcje. Firma opracowuje swój kod w krótkich i częstych iteracjach. Pozwala to wykorzystać pewne zmiany, często refaktoryzować kod i unikać "na początku związanych z dużymi projektami".

Lucerna zachowuje zdecydowanie większą i bardzien złożoną kolekcję systemów, z których niektóre mają więcej niż 40 lat. Są one wyjątkową ostrożność podczas wprowadzania zmian z powodu złożoności i zakresu starszego kodu. Stosują bardziej rygorystyczny proces tworzenia oprogramowania, preferując projektowanie szczegółowych rozwiązań i dokumentowanie projektu oraz zmian, które występują podczas pracy.

Oba zespoły korzystają z diagramów modelowania w programie Visual Studio, aby ułatwić opracowanie systemów spełniających potrzeby użytkowników. Używają serwera Team Foundation Server oraz innymi narzędziami, aby pomóc im planowania, organizowania i zarządzania pracą.

Aby uzyskać więcej informacji na temat serwera Team Foundation Server zobacz:

- [Planowanie i śledzenie pracy](#planning-and-tracking-work)

- [Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu zaktualizowanego](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> Role architektury i diagramów modelowania w tworzeniu oprogramowania

W poniższej tabeli opisano role, które mogą pełnić te narzędzia wielu i różnych etapach cyklu życia tworzenia oprogramowania:

||**Modelowanie wymagań użytkowników**|**Modelowanie procesów biznesowych**|**Architektura i projektowanie**|**Kod — Wizualizacja i eksploracja**|**Weryfikacja**|
|------|-|-|-|-|-|
|Diagram języka specyficznego dla domeny (DSL)|Tak|Tak|Tak|||
|Diagram zależności, sprawdzanie poprawności warstwy|||Tak|Tak|Tak|
|Mapy kodu|||Tak|Tak|Tak|
|Projektant klasy (oparty na kodzie)||||Tak||

Aby narysować diagramy zależności, należy utworzyć projekt modelowania jako część nowego lub istniejącego rozwiązania. Te diagramy należy utworzyć w projekcie modelowania.
Elementy na diagramach zależności znajdują się w projekcie modelowania, ale nie są one przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieje poza projektem modelowania.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba zespoły korzystają również weryfikacji zależności, aby upewnić się, że opracowywany kod pozostaje zgodny z projektem. Zobacz:

- [Zachowywanie kodu zgodnie z projektem](#ValidatingCode)

- [Opisz logiczną architekturę: diagramy zależności](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Niektóre wersje programu Visual Studio Obsługa weryfikacji zależności i wersje tylko do odczytu map kodów wizualizacji i modelowania. Aby zobaczyć, jakie wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługę wersji narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Zrozumienie i przekazywania informacji o systemie

Nie ma żadnej zalecanej kolejności przy użyciu programu Visual Studio, modelowanie diagramów, aby można było ich używać stosownie do potrzeb lub podejścia. Zwykle zespoły wracają do swoich modeli wielokrotnie i często w całym projekcie. Każdy diagram oferuje szczególne zalety, aby ułatwić zrozumienie, opisać i zakomunikować różne aspekty systemu w fazie projektowania.

Dinner Now i Lucerne komunikują się ze sobą i z udziałowcami projektu za pomocą diagramów oraz ich wspólnego języka. Na przykład Dinner Now używa diagramów do wykonywania następujących zadań:

- Wizualizacja istniejącego kodu.

- Komunikować się z usługą Lucerne o nowych lub zaktualizowanych przypadków użycia.

- Zidentyfikuj zmiany, które są wymagane do obsługi nowych lub zaktualizowanych przypadków użycia.

Lucerna używa diagramów do wykonywania następujących zadań:

- Więcej informacji na temat procesu biznesowego obiad teraz.

- Omówienie konstrukcji systemu.

- Komunikuj się z firmą Dinner Now w kwestii nowych lub uaktualnionych wymagań użytkownika.

- Dokumentowanie aktualizacji systemu.

Diagramy są zintegrowane z programem Team Foundation Server, dzięki czemu zespoły mogą planowanie, zarządzanie i łatwiej śledzić ich pracę. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych i do szacowania pracy. Lucerna łaczy Team Foundation Server elementy robocze z elementów modelu tak aby monitorować postęp i upewnij się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia z elementami roboczymi przypadków testowych można zobaczyć, że przypadki użycia są spełnione, gdy kod przechodzi wszystkie testy.

Zanim zespoły zaewidencjonują zmiany, sprawdzają poprawność kodu w stosunku do testów i projektu uruchamiając kompilacje, które obejmują weryfikacji zależności oraz zautomatyzowanych testów. Dzięki temu, upewnij się, że zaktualizowany kod nie są w konflikcie z projektowaniem i przerwać wcześniej działające funkcje.

### <a name="identify-changes-to-the-existing-system"></a>Identyfikuj zmiany w istniejącym systemie

Dinner Now musi oszacować koszty realizacji nowego wymagania. Zależy to częściowo ile ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów Dinner Now tworzy te mapy i diagramy z istniejącego kodu:

|**Mapa lub diagramu**|**Pokazuje**|
|-|-|
|*Mapy kodu*<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład Dinner Now może rozpocząć od przejrzenia mapy kodu zestawu omówienie zestawów i ich zależności. Może przechodzić do mapy do zbadania przestrzeni nazw i klas w tych zestawach.<br /><br /> Dinner Now, można również utworzyć mapy na zbadanie szczególnych obszarów i innych rodzajów relacji w kodzie. Używają Eksploratora rozwiązań, aby znaleźć i wybrać obszary i relacje, które ich interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje jego zakres, aby skupić się na obszarach, których dotyczy nowy scenariusz. Te obszary zaznaczone i wyróżnione na mapie:

 ![Wykres zależności Namespace](../modeling/media/namespace_reviewsystem.png)

 **Mapy kodu Namespace**

 Deweloper rozwija wybrane obszary nazw, aby zobaczyć ich klasy, metody i relacje:

 ![Wykres zależności przestrzeni nazw rozwinięty](../modeling/media/dep_reviewsystem.png)

 **Rozwinięty obszar nazw mapy kodu z widoczny aż linki międzygrupowe**

 Deweloper bada kod, aby znaleźć dotyczy klasy i metody. Aby zobaczyć skutki każdej zmiany, jak wprowadzisz je, ponowne generowanie mapy kodu po każdej zmianie. Zobacz [tworzenie wizualizacji kodu](../modeling/visualize-code.md).

 Aby opisać zmiany dotyczące innych części systemu, takie jak składniki lub interakcje, zespół może narysować je na tablicach. Dzięki temu szczegółowe informacje mogą być przechwytywane, zarządzane i rozpoznawane przez oba zespoły może również narysować następujące diagramy w programie Visual Studio:

|**Diagramy**|**W tym artykule opisano**|
|-|-|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Istniejące klasy w kodzie.|

### <a name="ValidatingCode"></a> Utrzymuj spójność kodu z projektem
 Dinner Now, musisz upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą diagramów zależności, które opisują warstwy funkcji w systemie, określa dozwolone zależności między nimi i kojarzy artefakty rozwiązania z tymi warstwami.

|**Diagram**|**W tym artykule opisano**|
|-|-|
|*Diagram zależności*<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram zależności organizuje i mapuje artefakty w rozwiązaniu Visual Studio, grup abstrakcyjnych nazywanych *warstwy*. Te warstwy określają role, zadania lub funkcje, które te artefakty pełnią w systemie.<br /><br /> Diagramy warstwy są przydatne do opisywania zamierzonego projektu systemu i sprawdzenia poprawności zmian kodu w stosunku do projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klas i przeglądarki obiektów. Aby narysować nowe warstwy, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu warstwy, a następnie kliknij przycisk **Wygeneruj zależności**. Aby określić zależności zamierzone, narysuj nowe.|

 Na przykład poniższy diagram zależności opisuje zależności między warstwami i liczbą artefaktów, które są skojarzone z poszczególnymi warstwami:

 ![Diagram zależności systemu płatności zintegrowane](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności**

Aby upewnić się, że nie występują konflikty z projektem podczas programowania kodu, zespoły sprawdzają weryfikacji zależności w kompilacjach, które są uruchamiane na DevOps platformy Azure. Tworzą one równie niestandardowe zadanie platformy MSBuild, aby wymagać weryfikacji zależności w swoich operacjach ewidencjonowania. Używają raportów z kompilacji do zbierania błędów sprawdzania poprawności.

Zobacz:

- [Użyj wizualnego projektanta](/azure/devops/pipelines/get-started-designer)

- [TFVC zaewidencjonowania](/azure/devops/pipelines/build/triggers#gated)

- [Kompiluj i wdrażaj zadania](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Ogólne porady dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów, które są połączone liniami. Dla każdego typu diagramu Przybornik zawiera różne rodzaje węzłów i wierszy.

     Aby otworzyć przybornik, na **widoku** menu, kliknij przycisk **przybornika**.

- Aby utworzyć węzeł, przeciągnij je z przybornika do diagramu. Niektóre rodzaje węzłów muszą zostać przeciągnięte do istniejących węzłów. Na przykład na diagramie składników nowy port musi być dodany do istniejącego składnika.

- Aby utworzyć linię lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródła, a następnie kliknij węzeł docelowy. Niektóre linie mogą być tworzone tylko między pewnymi rodzajami węzłów. Gdy przesuniesz wskaźnik nad możliwe źródło lub docelowej kursor wskazuje, czy można utworzyć połączenie.

### <a name="plan-and-track-work"></a>Planowanie i śledzenie pracy

Diagramy modelowania w usłudze Visual Studio są zintegrowane z programem Team Foundation Server, aby zaplanować, zarządzanie i łatwiej śledzić pracę. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych i do szacowania pracy. Lucerna tworzy i łaczy Team Foundation Server elementy robocze z elementami modelu, takie jak przypadki użycia lub składniki. Pomoże im to monitorować ich postęp i śledzić ich pracę odpowiednio do wymagań użytkowników. Pomoże im to upewnić się, że ich zmiany w dalszym ciągu spełniają te wymagania.

Jako postępem prac zespoły aktualizują elementy robocze, aby odzwierciedlić czas poświęcony na ich zadań. Ponadto monitorują i raportują stan swojej pracy, korzystając z następujących funkcji serwera Team Foundation Server:

- Codzienne *Raporty postępu* które pokazują, czy zostaną zakończone planowaną pracę w oczekiwanym czasie. Generują inne podobne raporty z Team Foundation Server w celu śledzenia postępu usterek.

- *Arkusz iteracji* który używa programu Microsoft Excel, aby pomóc zespołowi w monitorowaniu i równoważeniu obciążenia pracą poszczególnych członków. Ten arkusz jest połączony z serwerem Team Foundation Server i dostarcza tematy do dyskusji podczas regularnie odbywanych spotkań.

- A *pulpit nawigacyjny prac rozwojowych* używający Office Project do informowania zespołu o ważnych projektów.

Zobacz:

- [Narzędzia Agile i Zwinne Zarządzanie projektami — informacje](/azure/devops/boards/backlogs/overview?view=vsts)

- [Wykresy, pulpitów nawigacyjnych i widżetów (usługom DevOps platformy Azure)](/azure/devops/report/dashboards/overview?view=vsts)

- [Tworzenie zaległości i zadań za pomocą programu Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="TestValidateCheckInCode"></a> Testowanie, sprawdzanie poprawności i ewidencjonują kod

Jak wykonania poszczególne zadania zespoły ewidencjonują kod do kontroli źródła i otrzymują przypomnienia z Team Foundation Server, jeśli zapomną. Zanim Team Foundation Server zaakceptuje ewidencjonowania, zespoły uruchamiają testy jednostkowe i weryfikacja zależności, aby sprawdzić kod w oparciu o przypadki testowe i projekt. Używają programu Team Foundation Server do uruchamiania kompilacji, testów automatycznych jednostkowych i regularnie weryfikacji zależności. Dzięki temu, upewnij się, że dany kod spełnia następujące kryteria:

- To działa.

- Nie zprzerywa wcześniej działającego kodu.

- Nie powoduje konfliktu z projektem.

Dinner Now ma duży zbiór zautomatyzowanych testów, których może korzystać Lucerne, ponieważ prawie wszystkie nadal obowiązują. Lucerna można tworzyć na tych testach i dodać nowe na pokrycie nowej funkcje. Obie używają Visual Studio do uruchomienia testów ręcznych.

Aby upewnić się, że kod odpowiada wymaganiom projektu, zespoły konfigurują swoje kompilacje w DevOps platformy Azure, aby uwzględnić weryfikacji zależności. Jeśli wystąpią konflikty, raport jest generowany ze szczegółami.

Zobacz:

- [Testowanie aplikacji](/azure/devops/test/overview?view=vsts)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Korzystanie z kontroli wersji](http://go.microsoft.com/fwlink/?LinkID=525605)

- [Potoki usługi Azure](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizowanie systemu przy użyciu wizualizacji i modelowania

Lucerna i obiad teraz muszą zintegrować swoje systemy płatności. Poniższe sekcje pokazują, że diagramy modelowania w programie Visual Studio pomagają w wykonaniu tego zadania:

- [Wizualizacja istniejącego kodu: Map kodu](#VisualizeCode)

- [Definiuj słownik typów: diagramy klas](#DefineClasses)

- [Opisz logiczną architekturę: diagramy zależności](#DescribeLayers)

Zobacz:

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="VisualizeCode"></a> Wizualizacja istniejącego kodu: Map kodu

Mapy kodu pokazują bieżącą organizacją i relacje w kodzie. Elementy są reprezentowane przez *węzłów* na mapie, a relacje są reprezentowane przez *łącza*. Mapy kodu może pomóc Ci realizować następujące rodzaje zadań:

- Poznawanie nieznanego kodu.

- Dowiedz się, gdzie i w jaki sposób proponowana zmiana może mieć wpływ na istniejący kod.

- Znajdowanie obszarów złożoności, naturalnych zależności lub wzorców albo innych obszarów, które mogą skorzystać na poprawie.

Na przykład Dinner Now musi oszacować koszt aktualizacji składnika PaymentProcessing. Zależy to częściowo ile ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów Dinner Now generuje mapy kodu z kodu i dopasowuje obszarem zakresu obszarów, które mogą mieć wpływ zmiany.

Poniższe mapy przedstawia zależności między klasą PaymentProcessing i innymi częściami systemu firmy Dinner Now, które zostaną wyświetlone jako zaznaczone:

![Wykres zależności dla systemu płatności Dinner Now](../modeling/media/dep_dnpayment.png)

**Mapę kodu dla systemu płatności Dinner Now**

Deweloper bada mapy, rozwijając klasę PaymentProcessing i wybierając jej elementy członkowskie, aby zobaczyć obszary, które potencjalnie dotyczą zmiany:

![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph_expandeddn.png)

**Metody wewnątrz klasy PaymentProcessing i ich zależności**

Generują poniższe mapy dla systemu płatności firmy Lucerne sprawdzić jej klas, metod i zależności. Zespół widzi, że system firmy Lucerne może również wymagać pracy nad interakcją z innymi częściami firmy Dinner now:

![Wykres zależności dla systemu płatności Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mapy kodu dla systemu płatności Lucerne**

Oba zespoły współpracują ze sobą w celu określenia zmian, które są wymagane do zintegrowania dwóch systemów. One decyduje się o zrefaktoryzować część kodu, czemu będzie łatwiejszy do aktualizacji. Klasa PaymentApprover zostanie przeniesione do obszaru nazw DinnerNow.Business i będzie wymagać pewnych nowych metod. Klasy firmy Dinner Now, które obsługują transakcje, będą miały własny obszar nazw. Zespoły tworzą i używanie elementów roboczych do planowania, organizowania i śledzenia swojej pracy. Łączą elementy robocze z elementami modelu, gdzie jest to użyteczne.

Po reorganizacji kodu zespoły generują nowej mapy kodu, aby zobaczyć zaktualizowaną strukturę i relacje:

![Wykres zależności z kodem zreorganizowanym](../modeling/media/depgraph_integrated.png)

**Mapy kodu z kodem zreorganizowanym**

Ta mapa pokazuje, że klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow.Business i ma kilka nowych metod. Klasy transakcji firmy Dinner Now mają teraz własne obszar nazw PaymentSystem, dzięki czemu łatwiej radzenia sobie z tym kodem później.

#### <a name="creating-a-code-map"></a>Tworzenie Map kodu

- Aby uzyskać szybki przegląd kodu źródłowego wykonaj następujące kroki, aby wygenerować mapę kodu:

     Na **architektury** menu, kliknij przycisk **Generuj mapę kodu dla rozwiązania**.

     Aby uzyskać szybki przegląd skompilowanego kodu Utwórz mapę kodów puste, a następnie przeciągnij pliki zestawu lub pliki binarne do powierzchni mapy.

- Aby poznać konkretny kod lub elementy rozwiązania, użyj Eksploratora rozwiązań, aby wybrać elementy i relacje, które mają być wyświetlane. Możesz następnie wygenerować nowej mapy lub Dodaj wybrane elementy do istniejącej mapy. Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

- Aby ułatwić zrozumienie mapy, można zmienić układ, aby go do rodzaju zadań, które chcesz wykonać.

     Na przykład do zwizualizowania warstw w kodzie, wybierz układ drzewa. Zobacz [przeglądanie i zmianę położenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: Zalety map kodu
 Mapy kodu ułatwiają:

- Więcej informacji o organizacji i relacjach w istniejącym kodzie.

- Zidentyfikuj obszary, które mogą mieć wpływ proponowana zmiana.

- Znajdowanie obszarów złożoności, wzorów, warstwy lub innych obszarów, które można poprawić, aby ułatwić utrzymania, zmieniać i ponownego użycia kodu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**W tym artykule opisano**|
|-|-|
|Diagram zależności|Logiczna architektura systemu. Użyj weryfikacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących dependencys lub dependencys zamierzony, utwórz mapę kodu i pogrupować pokrewne elementy. Aby utworzyć diagram zależności, zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)|
|Diagram klasy (oparty na kodzie)|Istniejące klasy w kodzie dla konkretnego projektu.<br /><br /> Wizualizację i modyfikowanie istniejącej klasy w kodzie, za pomocą projektanta klas.<br /><br /> Zobacz [porady: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DefineClasses"></a> Definiuj słownik typów: diagramy klas
 Diagramy klas określają podmioty, terminy i pojęcia, które uczestniczą w systemie oraz ich wzajemne relacje. Na przykład służy tych diagramów podczas programowania do opisania atrybutów i operacji dla każdej klasy, niezależnie od ich implementacji języka i stylu.

 Aby pomóc firmie Lucerne opisać i omówić podmioty, które uczestniczą w przypadku użycia przetwarzanie płatności, można narysować Poniższy diagram klasy:

 ![Jednostki procesu płatności na diagramie klasy](../modeling/media/uml_payentities.png)

 **Jednostki procesu płatności na diagramie klasy**

 Ten diagram przedstawia to, że klient może mieć wiele zamówień i płacić za zamówienia na różne sposoby. BankAccount i CreditCard dziedziczy płatności.

 Podczas programowania Lucerne używa poniższego diagramu klas do opisania i omówienia szczegółów każdej klasy:

 ![Szczegóły procesu płatności jednostek na diagramie klasy](../modeling/media/uml_payment.png)

 **Szczegóły procesu płatności na diagramie klasy**

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas

Diagram klas ma następujące cechy główne:

- Typy takie jak klasy, interfejsy i wyliczenia:

    - A *klasy* jest definicji obiektów, które mają szczególne strukturalnych szczególnymi cechami strukturalnymi i.

    - *Interfejsu* definiuje część widocznych zewnętrznych zachowań obiektu.

    - *Wyliczenie* jest klasyfikatorem, który zawiera listę wartości literałów.

- *Atrybuty* to wartości pewnego typu, opisujące każde wystąpienie *klasyfikatora*. Klasyfikator to ogólna nazwa dla typów, składników, przypadków użycia i nawet aktorów.

- *Operacje* są metodami lub funkcjami, które mogą wykonywać wystąpienia klasyfikatora.

- *Skojarzenia* oznacza pewnego rodzaju relację między dwoma klasyfikatorami.

  - *Agregacji* jest skojarzeniem, które wskazuje wspólną własność między klasyfikatorami.

  - A *kompozycji* to skojarzenie ukazujące relacje między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, ustaw **agregacji** właściwości skojarzenia. **Udostępnione** pokazuje agregacje i **złożonego** — kompozycje.

- A *zależności* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- A *Generalizacja* wskazuje, że dany Klasyfikator dziedziczy część jego definicji od klasyfikatora ogólnego. A *realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.

     Aby utworzyć te relacje, należy użyć **dziedziczenia** narzędzia. Alternatywnie, realizacja może być reprezentowana jako *interfejsu typu lizak*.

- *Pakiety* są grupami klasyfikatorów, skojarzeń, linii życia, składników i innych pakietów. *Importuj* relacji wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

Jako punktu wyjścia do badania i omawiania istniejących klas można użyć projektanta klas do tworzenia diagramów klas z kodu.

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: Zalety diagramów klas
 Diagramy klas pomagają określić:

- Wspólny Słownik terminów do wykorzystania podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).

- Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje, takie jak zależności między typami. Na przykład można pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Diagram zależności|Definiuj logiczną architekturę systemu, w odniesieniu do klasy.<br /><br /> Użyj weryfikacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|
|Mapy kodu|Umożliwia wizualizację organizacji i relacjach w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metod, utwórz mapę kodu, pokazujący te elementy.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a> Opisz logiczną architekturę: diagramy zależności
 Diagramy zależności opisują architekturę logiczną systemu organizowania artefaktów w Twoich rozwiązaniach w abstrakcyje grupy, lub *warstwy*. Artefakty mogą być różne, takie jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy przedstawiają i opisują role lub zadania, które te artefakty pełnią w systemie. Można także dodać sprawdzanie poprawności warstwy w kompilacji i ewidencjonowaniu operacji, aby upewnić się, że kod pozostaje zgodny z jego zamysłem.

 Aby zachować zgodność kodu z projektem, firmy Dinner Now i Lucerne umożliwia Poniższy diagram zależności sprawdzenie ich kodu jest opracowywany:

 ![Diagram zależności systemu płatności zintegrowane](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności na obiad teraz zintegrowany z Lucerną**

 Warstwy na tym diagramie połączyć odpowiednie artefakty rozwiązania firmy Dinner Now i Lucerne. Na przykład warstwa biznesowa łączy do nazw DinnerNow.Business i jej elementów członkowskich, które obejmują teraz klasa PaymentApprover. Linki warstwy dostępu do zasobów z obszarem nazw DinnerNow.Data. Strzałki, lub *zależności*, określić, że tylko warstwa biznesowa może używać funkcji w warstwie dostępu do zasobów. Jako że zespoły aktualizują kod, sprawdzanie poprawności warstwy odbywa się regularnie pozwala na wychwytywanie konfliktów w momencie ich wystąpienia i pomagają zespołom niezwłoczne ich rozwiązywanie.

 Zespoły współpracują ze sobą nad stopniową integracją i testowaniem tych dwóch systemów. One najpierw upewnij się, że PaymentApprover i pozostała część Dinner Now dobrze ze sobą pomyślnie przed mają do czynienia PaymentProcessing.

 Poniższe mapy kodu pokazuje nowe wywołania między Dinner Now a PaymentApprover:

 ![Wykres zależności zaktualizowane przy użyciu zintegrowanego systemu](../modeling/media/depgraph_intsystem.png)

 **Mapy kodu ze zaktualizowanymi wywołaniami metod**

 Po potwierdzeniu, że system działa zgodnie z oczekiwaniami, Dinner Now komentuje kod PaymentProcessing. Raporty sprawdzania poprawności warstwy są czyste, a wynikowy mapy kodu pokazuje, że istnieje nie więcej zależności klasy PaymentProcessing:

 ![Wykres zależności bez PaymentProcessing](../modeling/media/depgraph_nomore.png)

 **Mapy kodu bez PaymentProcessing**

#### <a name="drawing-a-dependency-diagram"></a>Rysowanie diagramu zależności

Diagram zależności ma następujące cechy główne:

- *Warstwy* opis grupy logicznej artefaktów.

- A *łącze* jest skojarzeniem między warstwą i artefaktem.

     Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klas lub przeglądarki obiektów. Aby narysować nowe warstwy i łączyć je w artefakty, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

     Liczba na warstwie pokazuje liczbę artefaktów, które są połączone z warstwą. Te artefakty mogą być przestrzenie nazw, projekty, klasy, metody i tak dalej. Interpretując liczbę artefaktów na warstwie, pamiętaj o następujących kwestiach:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

       Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby zobaczyć artefakty, które są połączone z warstwą, kliknij prawym przyciskiem myszy zależności, a następnie kliknij przycisk **Wyświetl łącza** otworzyć **Eksplorator warstw**.

- A *zależności* wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie, ale nie odwrotnie. A *zależność dwukierunkowa* wskazuje, że jedna warstwę może korzystać z funkcji w innej warstwie i odwrotnie.

     Aby wyświetlić istniejące zależności na diagram zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij przycisk **Wygeneruj zależności**. Aby opisać zależności zamierzone, narysuj nowe.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)

- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Podsumowanie: Zalety diagramów zależności

Diagramy zależności ułatwiają:

- Opisz logiczną architekturę systemu zgodnie z funkcji jego artefaktów.

- Upewnij się, że kod w opracowaniu odpowiada określonemu projektowi.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Mapy kodu|Umożliwia wizualizację organizacji i relacjach w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, Generuj mapę kodu, a następnie zgrupuj elementy na mapie jako potencjalne warstwy. Przeciągnij grupy z mapy na diagram zależności.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Łącza**|
|-|-|
|**Fora**|- [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Zobacz także

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Używaj modeli w Agile development](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
