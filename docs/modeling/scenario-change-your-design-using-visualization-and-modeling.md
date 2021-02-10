---
title: Zmienianie projektu przy użyciu wizualizacji i modelowania
description: Poznaj narzędzia do wizualizacji i modelowania w programie Visual Studio oraz sposób używania tych narzędzi do zmiany projektu.
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79f131276172a9df91dd8408149fae66a2f28ca9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938047"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania

Upewnij się, że system oprogramowania spełnia potrzeby użytkowników, korzystając z narzędzi do wizualizacji i modelowania w programie Visual Studio.
Użyj narzędzi, takich jak mapy kodu, diagramy zależności i diagramy klas, aby:

Aby sprawdzić, które wersje programu Visual Studio obsługują poszczególne narzędzia, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Wyjaśnij wymagania użytkowników i procesy biznesowe.

- Wizualizuj i Eksploruj istniejący kod.

- Opisz zmiany w istniejącym systemie.

- Sprawdź, czy system spełnia wymagania.

- Zachowaj spójność kodu z projektem.

Ten przewodnik:

- Opisuje, jak te narzędzia mogą korzystać z projektu oprogramowania.

- Pokazuje, w jaki sposób można korzystać z tych narzędzi, niezależnie od podejścia programistycznego, z przykładowym scenariuszem.

Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które są przez nie obsługiwane, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Omówienie scenariusza

W tym scenariuszu opisano odcinki cykli rozwoju oprogramowania dwóch fikcyjnych firm: obiad teraz i publikowanie z lucerny. Zapraszamy teraz usługa dostarczania posiłków opartych na sieci Web w Seattle. Klienci mogą zamówić posiłki i uregulować je w witrynie internetowej obiadu teraz. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji na potrzeby dostawy. Publikowanie Lucerny, firma w Nowym Jorku, uruchamia kilka firm zarówno w sieci Web, jak i w Internecie. Na przykład uruchamiają witryny sieci Web, w których klienci mogą publikować przeglądy restauracji.

Przede wszystkim uzyskano obiad i chcemy wprowadzić następujące zmiany:

- Zintegruj swoje witryny sieci Web, dodając do obiadu teraz funkcje przeglądu restauracji.

- Zastąp teraz system płatności z tytułu obiadu w systemie z systemem Lucerny.

- Rozwiń usługę z obiadem teraz w całym regionie.

Obiad obejmuje teraz programowanie SCRUM i eXtreme. Mają bardzo duże pokrycie testów i bardzo mały nieobsługiwany kod. Minimalizują one ryzyko, tworząc małe, ale działające wersje systemu, a następnie zwiększając przyrost funkcji. Opracowują swój kod w krótkich i częstych iteracjach. Dzięki temu mogą one często polegać na zmianie, niewielkim kodzie i uniknięciu "Big Design" na początku.

Lucerny, w której znajduje się znacznie większa i złożona kolekcja systemów, a niektóre z nich są starsze niż 40 lat. Są one bardzo ostrożne w przypadku wprowadzania zmian ze względu na złożoność i zakres starszego kodu. Są one zgodne z bardziej rygorystycznym procesem opracowywania, ale przed projektowaniem szczegółowych rozwiązań i udokumentowaniem projektu oraz zmian, które wystąpiły podczas opracowywania.

Oba zespoły używają diagramów modelowania w programie Visual Studio, aby ułatwić im opracowywanie systemów spełniających potrzeby użytkowników. Używają Team Foundation Server wraz z innymi narzędziami, aby ułatwić im planowanie i organizowanie pracy oraz zarządzanie nimi.

Aby uzyskać więcej informacji na temat Team Foundation Server, zobacz:

- [Planowanie i śledzenie pracy](#plan-and-track-work)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Role architektury i diagramy modelowania w programowaniu oprogramowania

W poniższej tabeli opisano role, które te narzędzia mogą odtwarzać na różnych etapach cyklu tworzenia oprogramowania:

|Narzędzie/rola|Modelowanie wymagań użytkownika|Modelowanie procesów firmy|Projekt architektury systemowej &|Wizualizacja kodu & Eksploracja|Weryfikacja|
|------|-|-|-|-|-|
|Diagram języka Domain-Specific (DSL)|Tak|Tak|Tak|||
|Diagram zależności, walidacja warstwy|||Tak|Tak|Tak|
|Mapa kodu|||Tak|Tak|Tak|
|Projektant klas (oparty na kodzie)||||Tak||

Aby rysować diagramy zależności, należy utworzyć projekt modelowania w ramach istniejącego rozwiązania lub nowego. Te diagramy muszą zostać utworzone w projekcie modelowania.
Elementy na diagramach zależności znajdują się w projekcie modelowania, ale nie są one przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieją poza projektem modelowania.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba zespoły używają również walidacji zależności, aby upewnić się, że kod w trakcie tworzenia nadal jest zgodny z projektem. Zobacz:

- [Zachowywanie spójności kodu w projekcie](#ValidatingCode)

- [Opisywanie architektury logicznej: diagramy zależności](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Niektóre wersje programu Visual Studio obsługują weryfikację zależności i wersje tylko do odczytu map kodu do wizualizacji i modelowania. Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Zrozumienie i przekazywanie informacji o systemie

Nie ma określonej kolejności na potrzeby używania diagramów modelowania programu Visual Studio, dzięki czemu można ich używać w zależności od potrzeb lub podejścia. Zwykle zespoły ponownie odwiedzają swoje modele iteracyjnie i często w całym projekcie. Każdy diagram oferuje szczególne zalety, które ułatwiają zrozumienie, opisywanie i komunikowanie różnych aspektów systemu w trakcie opracowywania.

Obiady teraz i lucerny ze sobą komunikują się z innymi uczestnikami projektu, korzystając ze diagramów jako ich wspólnego języka. Na przykład obiad używa teraz diagramów do wykonywania następujących zadań:

- Wizualizuj istniejący kod.

- Komunikuj się z usługami w ramach platformy Lucerny, aby poznać nowe lub zaktualizowane historie użytkownika.

- Zidentyfikuj zmiany, które są wymagane do obsługi nowych lub zaktualizowanych historii użytkownika.

W przypadku korzystania z diagramów z wykresów:

- Poznaj proces biznesowy obiadu teraz.

- Zapoznaj się z projektowaniem systemu.

- Skontaktuj się z obiadem teraz o nowych lub zaktualizowanych wymaganiach użytkownika.

- Aktualizacje dokumentów do systemu.

Diagramy są zintegrowane z Team Foundation Server, dzięki czemu zespoły mogą łatwiej planować i śledzić swoją służbę oraz zarządzać nią. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych i szacowania ich pracy. Linki lucerny Team Foundation Server elementy robocze do elementów modelu, dzięki czemu mogą monitorować postęp i upewnić się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia z elementami roboczymi przypadku testowego, dzięki czemu mogą zobaczyć, że przypadki użycia są spełnione, gdy wszystkie testy zostały zakończone pomyślnie.

Zanim zespoły zaewidencjonują zmiany, sprawdzają poprawność kodu względem testów i projektu, uruchamiając kompilacje, które obejmują weryfikację zależności i testy automatyczne. Pomaga to upewnić się, że zaktualizowany kod nie powoduje konfliktu z projektem i przerwaniem wcześniej działającej funkcjonalności.

### <a name="identify-changes-to-the-existing-system"></a>Identyfikowanie zmian w istniejącym systemie

Kolacja teraz musi oszacować koszt zaspokajania nowego wymagania. Jest to zależne od tego, jak bardzo zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie, jeden z obiadów teraz tworzy te mapy i diagramy z istniejącego kodu:

|**Mapa lub diagram**|**Seriale**|
|-|-|
|*Mapa kodu*<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład możesz zacząć od obiadu, przeglądając mapy kodu zestawu, aby zapoznać się z omówieniem zestawów i ich zależnościami. Mogą przechodzić do szczegółów map, aby eksplorować przestrzenie nazw i klasy w tych zestawach.<br /><br /> Na obiad teraz można również tworzyć mapy umożliwiające Eksplorowanie określonych obszarów i innych rodzajów relacji w kodzie. Używają oni Eksplorator rozwiązań, aby znajdować i wybierać obszary i relacje, które je interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje swój zakres, aby skoncentrować się na obszarach, na które wpłynie nowy scenariusz. Obszary te są wybrane i wyróżnione na mapie:

 ![Wykres zależności przestrzeni nazw](../modeling/media/namespace_reviewsystem.png)

 **Mapa kodu przestrzeni nazw**

 Deweloper rozszerza wybrane przestrzenie nazw, aby zobaczyć ich klasy, metody i relacje:

 ![Wykres zależności rozwiniętej przestrzeni nazw](../modeling/media/dep_reviewsystem.png)

 **Rozwinięta Mapa kodu przestrzeni nazw z widocznymi łączami między grupami**

 Deweloper bada kod w celu znalezienia odpowiednich klas i metod. Aby zobaczyć efekty każdej zmiany w miarę ich tworzenia, należy ponownie wygenerować mapy kodu po każdej zmianie. Zobacz [wizualizowanie kodu](../modeling/visualize-code.md).

 Aby opisać zmiany w innych częściach systemu, takich jak składniki lub interakcje, zespół może narysować te elementy w tablicach. Mogą również narysować następujące diagramy w programie Visual Studio, aby szczegóły mogły być przechwytywane, zarządzane i zrozumiałe dla obu zespołów:

|**Schematów**|**Szczegół**|
|-|-|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Istniejące klasy w kodzie.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Zachowaj spójność kodu z projektem
 Teraz należy upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą one diagramy zależności opisujące warstwy funkcji w systemie, określają dozwolone zależności między nimi i kojarzą artefakty rozwiązań z tymi warstwami.

|**4b**|**Szczegół**|
|-|-|
|*Diagram zależności*<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Sprawdzanie poprawności kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram zależności organizuje i mapuje artefakty w rozwiązaniu programu Visual Studio do grup abstrakcyjnych nazywanych *warstwami*. Te warstwy identyfikują role, zadania lub funkcje, które te artefakty pełnią w systemie.<br /><br /> Diagramy zależności są przydatne do opisywania zamierzonego projektu systemu i weryfikowania rozwoju kodu względem tego projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksplorator rozwiązań, map kodu, Widok klasy i Przeglądarka obiektów. Aby narysować nowe warstwy, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu zależności, a następnie kliknij polecenie **Generuj zależności**. Aby określić zamierzone zależności, narysuj nowe zależności.|

Na przykład poniższy diagram zależności opisuje zależności między warstwami i liczbą artefaktów, które są skojarzone z każdą warstwą:

![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności**

Aby upewnić się, że konflikty z projektem nie wystąpią podczas tworzenia kodu, zespoły korzystają z walidacji zależności w kompilacjach uruchamianych w usłudze Azure DevOps. Tworzy również niestandardowe zadanie programu MSBuild, aby wymagać weryfikacji zależności w ramach operacji zaewidencjonowania. Wykorzystują one raporty kompilacji do zbierania błędów walidacji.

Zobacz:

- [Korzystanie z projektanta wizualnego](/azure/devops/pipelines/get-started-designer)

- [Ewidencjonowanie warunkowe TFVC](/azure/devops/pipelines/build/triggers)

- [Zadania kompilacji i wydawania](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Ogólne porady dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów, które są połączone liniami. Dla każdego typu diagramu Przybornik zawiera różne rodzaje węzłów i linii.

   Aby otworzyć przybornik, w menu **Widok** kliknij polecenie **Przybornik**.

- Aby utworzyć węzeł, przeciągnij go z przybornika do diagramu. Niektóre rodzaje węzłów muszą być przeciągane do istniejących węzłów. Na przykład na diagramie składników należy dodać nowy port do istniejącego składnika.

- Aby utworzyć wiersz lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródłowy, a następnie kliknij węzeł docelowy. Niektóre linie mogą być tworzone tylko między pewnymi rodzajami węzłów. Gdy przesuwasz wskaźnik nad możliwym źródłem lub obiektem docelowym, wskaźnik wskazuje, czy można utworzyć połączenie.

### <a name="plan-and-track-work"></a>Planowanie i śledzenie pracy

Diagramy modelowania programu Visual Studio są zintegrowane z Team Foundation Server, dzięki czemu można łatwiej planować i zarządzać nimi. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz szacowania ich pracy. Lucerny tworzy i łączy Team Foundation Server elementów roboczych z elementami modelu, takimi jak przypadki użycia lub składniki. Ułatwia to monitorowanie postępów i śledzenie ich pracy z powrotem do wymagań użytkowników. Dzięki temu można upewnić się, że ich zmiany będą nadal spełniały te wymagania.

W miarę postępów prac zespoły aktualizują swoje elementy robocze, aby odzwierciedlały czas spędzony na wykonywaniu zadań. Umożliwiają również monitorowanie i zgłaszanie stanu pracy przy użyciu następujących funkcji Team Foundation Server:

- Codzienne *nagrywanie raportów* pokazujących, czy ukończy planowaną pracę w oczekiwanym czasie. Generują one inne podobne raporty z Team Foundation Server, aby śledzić postęp błędów.

- *Arkusz iteracji* , który używa programu Microsoft Excel, aby pomóc zespołowi monitorować i zrównoważyć obciążenie między jego członkami. Ten arkusz jest połączony z Team Foundation Server i umożliwia skoncentrowanie się na dyskusjach podczas zwykłych spotkań z postępem.

- *Pulpit nawigacyjny programistyczny* , który używa programu Office Project do informowania zespołu o ważnych informacjach o projekcie.

Zobacz:

- [Informacje o narzędziach Agile i zarządzaniu projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Wykresy, pulpity nawigacyjne i widżety (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Tworzenie zaległości i zadań przy użyciu projektu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Testowanie, sprawdzanie poprawności i ewidencjonowanie kodu

Gdy zespoły ukończyją każde zadanie, sprawdzają swój kod w kontroli źródła i odbierają przypomnienia z Team Foundation Server, jeśli zapomnieć. Zanim Team Foundation Server zaakceptuje zaewidencjonowania, zespoły uruchomią testy jednostkowe i walidację zależności w celu zweryfikowania kodu względem ich przypadków testowych i projektu. Używają Team Foundation Server do uruchamiania kompilacji, zautomatyzowanych testów jednostkowych i weryfikacji zależności regularnie. Pomaga to upewnić się, że kod spełnia następujące kryteria:

- Działa.

- Nie powoduje przerwania działania kodu.

- Nie powoduje konfliktu z projektem.

Obiad ma teraz dużą kolekcję zautomatyzowanych testów, które mogą być ponownie używane przez Lucerny, ponieważ niemal wszystkie nadal mają zastosowanie. W ramach tych testów można także skompilować te testy i dodać nowe, aby uwzględnić nowe funkcje. Oba te programy również używają programu Visual Studio do uruchamiania testów ręcznych.

Aby upewnić się, że kod jest zgodny z projektem, zespoły konfigurują kompilacje w usłudze Azure DevOps w celu uwzględnienia walidacji zależności. Jeśli wystąpią konflikty, raport zostanie wygenerowany ze szczegółowymi informacjami.

Zobacz:

- [Testowanie aplikacji](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Użyj kontroli wersji](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizowanie systemu przy użyciu wizualizacji i modelowania

Lucerny i obiady teraz muszą zintegrować swoje systemy płatności. W poniższych sekcjach przedstawiono diagramy modelowania w programie Visual Studio, które ułatwiają wykonywanie tego zadania:

- [Wizualizowanie istniejącego kodu: mapy kodu](#VisualizeCode)

- [Definiowanie słownika typów: diagramy klas](#DefineClasses)

- [Opisywanie architektury logicznej: diagramy zależności](#DescribeLayers)

Zobacz:

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a> Wizualizowanie istniejącego kodu: mapy kodu

Mapy kodu pokazują bieżącą organizację i relacje w kodzie. Elementy są reprezentowane przez *węzły* na mapie, a relacje są reprezentowane przez *linki*. Mapy kodu mogą pomóc w wykonywaniu następujących rodzajów zadań:

- Eksploruj nieznany kod.

- Zapoznaj się z miejscem i sposobem, w jaki proponowana zmiana może mieć wpływ na istniejący kod.

- Znajdź obszary złożoności, zależności naturalne lub wzorce lub inne obszary, które mogą korzystać z poprawy.

Na przykład obiad będzie teraz musiał oszacować koszt aktualizowania składnika PaymentProcessing. Jest to zależne od tego, jak bardzo zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie tego, jeden z obiadów obecnie deweloperów generuje mapy kodu z kodu i dostosowuje fokus zakresu w obszarach, na które mogą mieć wpływ zmiany.

Poniższa mapa przedstawia zależności między klasą PaymentProcessing i innymi częściami systemu obiadu teraz, które zostały wyświetlone:

![Wykres zależności dla systemu płatności z obiadem teraz](../modeling/media/dep_dnpayment.png)

**Mapa kodu dla systemu płatności z obiadem teraz**

Deweloper eksploruje mapę przez rozwijanie klasy PaymentProcessing i wybieranie jej elementów członkowskich, aby zobaczyć obszary, które mogą mieć wpływ:

![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph_expandeddn.png)

**Metody wewnątrz klasy PaymentProcessing i ich zależności**

Generują następujące mapy dla systemu płatności z lucerny, aby sprawdzić jej klasy, metody i zależności. Zespół widzi, że system lucerny, może również wymagać pracy w celu współdziałania z innymi częściami obiadu:

![Wykres zależności dla systemu płatności z lucerny](../modeling/media/depgraph_lucernepay.png)

**Mapa kodu dla systemu płatności z lucerny**

Oba zespoły współpracują ze sobą, aby określić zmiany, które są wymagane do integracji dwóch systemów. Użytkownik zdecyduje się na refaktoryzację pewnego kodu, aby ułatwić jego aktualizację. Klasa PaymentApprover zostanie przeniesiona do przestrzeni nazw DinnerNow. Business i będzie wymagała nowych metod. Klasy obiadu teraz, które obsługują transakcje, będą miały własny obszar nazw. Zespoły tworzą i wykorzystują elementy robocze do planowania, organizowania i śledzenia pracy. Łączą elementy robocze z elementami modelu, w których są użyteczne.

Po rozpoczęciu restrukturyzacji kodu zespoły generują nową mapę kodu, aby wyświetlić zaktualizowaną strukturę i relacje:

![Wykres zależności z rezorganizowanym kodem](../modeling/media/depgraph_integrated.png)

**Mapa kodu z rezorganizowanym kodem**

Ta mapa pokazuje, że Klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow. Business i ma kilka nowych metod. Klasy transakcji obiadu teraz mają swoją własną przestrzeń nazw PaymentSystem, co ułatwia objęcie tego kodu w późniejszym czasie.

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu

- Aby uzyskać szybki przegląd kodu źródłowego, wykonaj następujące kroki, aby wygenerować mapę kodu:

     W menu **Architektura** kliknij polecenie **Generuj mapę kodu dla rozwiązania**.

     Aby zapoznać się z krótkim omówieniem skompilowanego kodu, Utwórz pustą mapę kodu, a następnie przeciągnij pliki zestawu lub pliki binarne na powierzchnię mapy.

- Aby poznać określony kod lub elementy rozwiązania, użyj Eksplorator rozwiązań, aby zaznaczyć elementy i relacje, które chcesz wizualizować. Następnie można wygenerować nową mapę lub dodać wybrane elementy do istniejącej mapy. Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

- Aby ułatwić Eksplorowanie mapy, należy zmienić układ tak, aby odpowiadał rodzajom zadań, które chcesz wykonać.

     Na przykład w celu wizualizowania warstw w kodzie wybierz układ drzewa. Zobacz [przeglądanie i zmiana kolejności map kodu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: zalety map kodu
 Mapy kodu pomagają Ci:

- Poznaj organizację i relacje w istniejącym kodzie.

- Zidentyfikuj obszary, na które może mieć wpływ proponowana zmiana.

- Znajdź obszary złożoności, wzorce, warstwy lub inne obszary, które można ulepszyć, aby ułatwić przechowywanie, zmianę i ponowne użycie kodu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Szczegół**|
|-|-|
|Diagram zależności|Logiczna architektura systemu. Użyj walidacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących zależności lub zamierzonych zależności, Utwórz mapę kodu i pogrupuj powiązane elementy. Aby utworzyć diagram zależności, zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)|
|Diagram klas (oparty na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Aby wizualizować i modyfikować istniejącą klasę w kodzie, użyj Projektant klas.<br /><br /> Zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Definiowanie słownika typów: diagramy klas
 Diagramy klas definiują jednostki, terminy lub koncepcje, które uczestniczą w systemie i ich relacji ze sobą. Na przykład można użyć tych diagramów podczas programowania, aby opisać atrybuty i operacje dla każdej klasy, niezależnie od ich języka lub stylu implementacji.

 Aby pomóc lucerny opisać i omówić jednostki, które uczestniczą w przypadku użycia w procesie płatności, narysujemy następujący Diagram klas:

 ![Przetwarzanie jednostek płatności na diagramie klas](../modeling/media/uml_payentities.png)

 **Przetwarzanie jednostek płatności na diagramie klas**

 Ten diagram pokazuje, że klient może mieć wiele zamówień i różne sposoby płacenia za zamówienia. BankAccount i CreditCard są dziedziczone z płatności.

 Podczas opracowywania, w przypadku korzystania z poniższych diagramów klas, w celu opisania szczegółów poszczególnych klas i omówienia ich:

 ![Przetwarzanie szczegółów jednostki płatniczej na diagramie klas](../modeling/media/uml_payment.png)

 **Przetwarzanie szczegółów płatności na diagramie klas**

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas

Diagram klas ma następujące główne funkcje:

- Typy takie jak klasy, interfejsy i wyliczenia:

  - *Klasa* jest definicją obiektów, które mają określone charakterystyki strukturalne lub behawioralne.

  - *Interfejs* definiuje część widocznego na zewnątrz zachowania obiektu.

  - *Wyliczenie* jest klasyfikatorem zawierającym listę wartości literału.

- *Atrybuty* są wartościami określonego typu, które opisują każde wystąpienie *klasyfikatora*. Klasyfikator to ogólna nazwa dla typów, składników, przypadków użycia, a nawet aktorów.

- *Operacje* to metody lub funkcje, które mogą wykonywać wystąpienia klasyfikatora.

- *Skojarzenie* wskazuje rodzaj relacji między dwoma klasyfikatorami.

  - *Agregacja* to skojarzenie wskazujące wspólną własność między klasyfikatorami.

  - *Kompozycja* to skojarzenie, które wskazuje całość relacji między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, należy ustawić właściwość **agregacji** skojarzenia. W obszarze **udostępnione** są wyświetlane agregacje i **złożone** kompozycje.

- *Zależność* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- *Generalizacja* wskazuje, że określony klasyfikator dziedziczy część swojej definicji z klasyfikatora ogólnego. *Realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.

     Aby utworzyć te relacje, użyj narzędzia **dziedziczenie** . Alternatywnie realizacja może być reprezentowana jako *lizak*.

- *Pakiety* są grupami klasyfikatora, skojarzeniami, liniami życia, składnikami i innymi pakietami. Relacje *importu* wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

Jako punkt początkowy do eksplorowania i omawiania istniejących klas można użyć Projektant klas do tworzenia diagramów klas na podstawie kodu.

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: zalety diagramów klas
 Diagramy klas ułatwiają Definiowanie:

- Typowy słownik terminów do użycia podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [wymagania dotyczące modelu użytkownika](../modeling/model-user-requirements.md).

- Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje, takie jak zależności, między typami. Można na przykład pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-|-|
|Diagram zależności|Zdefiniuj architekturę logiczną systemu, która odnosi się do klas.<br /><br /> Użyj walidacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Sprawdzanie poprawności kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metody, Utwórz mapę kodu, która pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> Opisywanie architektury logicznej: diagramy zależności
 Diagramy zależności opisują architekturę logiczną systemu przez organizowanie artefaktów w rozwiązaniu do grup abstrakcyjnych lub *warstw*. Artefakty mogą mieć wiele rzeczy, takich jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy reprezentują i opisują role lub zadania wykonywane przez artefakty w systemie. Możesz również uwzględnić walidację warstwy w operacjach kompilacji i zaewidencjonowania, aby upewnić się, że kod pozostaje zgodny z projektem.

 Aby zachować kod spójny z projektem, obiad teraz i Lucerny, użyj następującego diagramu zależności, aby zweryfikować swój kod w miarę rozwoju:

 ![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności dla obiadu teraz zintegrowany z usługami Lucerny**

 Warstwy na tym diagramie łączą się z odpowiednimi artefaktami rozwiązań na obiad teraz i Lucerny. Na przykład warstwa biznesowa łączy się z przestrzenią nazw DinnerNow. Business i jej członkami, która teraz zawiera klasę PaymentApprover. Warstwa dostępu do zasobów łączy się z przestrzenią nazw DinnerNow. Data. Strzałki lub *zależności* określają, że tylko warstwa biznesowa może korzystać z funkcji w warstwie dostępu do zasobów. Gdy zespoły aktualizują swój kod, sprawdzanie poprawności warstwy jest wykonywane regularnie, aby przechwytywać konflikty w miarę ich występowania, a także ułatwić zespołom ich natychmiastowe rozwiązanie.

 Zespoły współpracują ze sobą w celu przyrostowego integrowania i testowania dwóch systemów. Najpierw należy upewnić się, że PaymentApprover i pozostała część obiadu teraz współpracują ze sobą, zanim zadbają o PaymentProcessing.

 Poniższa mapa kodu przedstawia nowe wywołania między obiadem teraz i PaymentApprover:

 ![Zaktualizowany wykres zależności z systemem zintegrowanym](../modeling/media/depgraph_intsystem.png)

 **Mapa kodu ze zaktualizowanymi wywołaniami metod**

 Po upewnieniu się, że system działa zgodnie z oczekiwaniami, obiad teraz oznacza kod PaymentProcessing. Raporty sprawdzania poprawności warstwy są czyste, a powstająca Mapa kodu wskazuje, że nie ma więcej zależności PaymentProcessing:

 ![Wykres zależności bez PaymentProcessing](../modeling/media/depgraph_nomore.png)

 **Mapa kodu bez PaymentProcessing**

#### <a name="drawing-a-dependency-diagram"></a>Rysowanie diagramu zależności

Diagram zależności ma następujące główne funkcje:

- *Warstwy* opisują logiczne grupy artefaktów.

- *Łącze* jest skojarzeniem między warstwą a artefaktem.

     Aby utworzyć warstwy na podstawie artefaktów, przeciągnij elementy z Eksplorator rozwiązań, mapy kodu Widok klasy lub Przeglądarka obiektów. Aby narysować nowe warstwy, a następnie połączyć je z artefaktami, Użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

     Liczba na warstwie pokazuje liczbę artefaktów, które są połączone z warstwą. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami i tak dalej. Podczas interpretacji liczby artefaktów na warstwie należy pamiętać o następujących kwestiach:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

       Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby wyświetlić artefakty, które są połączone z warstwą, kliknij prawym przyciskiem myszy zależność, a następnie kliknij przycisk **Wyświetl linki** , aby otworzyć **Eksploratora warstw**.

- *Zależność* wskazuje, że jedna warstwa może korzystać z funkcjonalności w innej warstwie, ale nie odwrotnie. *Zależność dwukierunkowa* wskazuje, że jedna warstwa może korzystać z funkcjonalności w innej warstwie i odwrotnie.

     Aby wyświetlić istniejące zależności na diagramie zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Generuj zależności**. Aby opisać zamierzone zależności, narysuj nowe.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)

- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Podsumowanie: zalety diagramów zależności

Diagramy zależności pomagają:

- Opisz logiczną architekturę systemu w zależności od funkcjonalności jego artefaktów.

- Upewnij się, że kod w obszarze programowanie jest zgodny z określonym projektem.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**4b**|**Opis**|
|-|-|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, wygeneruj mapę kodu, a następnie Grupuj elementy na mapie jako potencjalną warstwę. Przeciągnij grupy z mapy do diagramu zależności.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|-|-|
|**Fora**|- [Wizualizacja programu Visual Studio & narzędzia do modelowania](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Wizualizacja & modelowania SDK (narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Używanie modeli w programowaniu Agile](/previous-versions/ff398061(v=vs.140))
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)