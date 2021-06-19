---
title: Zmienianie projektu przy użyciu wizualizacji i modelowania
description: Dowiedz się więcej na temat narzędzi do wizualizacji i modelowania w Visual Studio oraz sposobu używania tych narzędzi do zmiany projektu.
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
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05cdd769a59c4101fbc05a7e51893752e2532f42
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385828"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania

Upewnij się, że system oprogramowania spełnia potrzeby użytkowników, korzystając z narzędzi do wizualizacji i modelowania w Visual Studio.
Użyj narzędzi, takich jak mapy kodu, diagramy zależności i diagramy klas, aby:

Aby sprawdzić, które wersje Visual Studio obsługują poszczególne narzędzia, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

- Wyjaśnienie wymagań użytkowników i procesów biznesowych.

- Wizualizowanie i eksplorowanie istniejącego kodu.

- Opisz zmiany w istniejącym systemie.

- Sprawdź, czy system spełnia jego wymagania.

- Utrzymuj spójność kodu z projektem.

Ten przewodnik:

- Opisuje, jak te narzędzia mogą być korzystne dla projektu oprogramowania.

- W przykładzie pokazano, jak można korzystać z tych narzędzi, niezależnie od podejścia programistycznego.

Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które obsługują, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Omówienie scenariusza

W tym scenariuszu opisano scenariusze z cyklu życia tworzenia oprogramowania dwóch fikcyjnych firm: Lunch Now i Lucerne Publishing. Lunch Now oferuje internetową usługę dostarczania obiadów w Seattle. Klienci mogą zamówić i zapłacić za nie w witrynie internetowej Lunch Now. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji w celu dostarczenia. Lucerne Publishing, firma w Nowym Jorku, prowadzi kilka firm zarówno poza, jak i w Internecie. Na przykład uruchamiają witrynę internetową, w której klienci mogą publikować recenzje restauracji.

Lucerne niedawno nabyła obiad teraz i chce wprowadzić następujące zmiany:

- Zintegruj swoje witryny internetowe, dodając możliwości przeglądu restauracji do aplikacji Dinner Now.

- Zastąp system płatności Dinner Now systemem Lucerne.

- Rozwiń usługę Lunch Now w całym regionie.

Program Dinner Now korzysta z programowania SCRUM i e Wy. Mają bardzo duże pokrycie testów i bardzo mało nieobsługiwanego kodu. Minimalizują one ryzyko, tworząc małe, ale robocze wersje systemu, a następnie dodając funkcje przyrostowo. Opracowują kod w krótkich i częstych iteracjach. Dzięki temu mogą pewnie korzystać ze zmian, często refaktoryzować kod i unikać "dużego projektu z góry".

Lucerne utrzymuje znacznie większą i złożoną kolekcję systemów, z których część ma ponad 40 lat. Są bardzo ostrożnie wprowadzać zmiany ze względu na złożoność i zakres starszego kodu. Są one zgodne z bardziej rygorystycznym procesem tworzenia, preferując projektowanie szczegółowych rozwiązań oraz dokumentowania projektu i zmian zachodzące podczas opracowywania.

Oba zespoły używają diagramów modelowania w Visual Studio, aby ułatwić im opracowywanie systemów spełniających potrzeby użytkowników. Używają one Team Foundation Server razem z innymi narzędziami, aby ułatwić im planowanie i organizowanie pracy oraz zarządzanie nimi.

Aby uzyskać więcej informacji na Team Foundation Server, zobacz:

- [Planowanie i śledzenie pracy](#plan-and-track-work)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Role diagramów architektury i modelowania w programie tworzenia oprogramowania

W poniższej tabeli opisano role, które te narzędzia mogą odgrywać na wielu i różnych etapach cyklu życia tworzenia oprogramowania:

|Narzędzie/rola|Modelowanie wymagań użytkownika|Modelowanie procesów biznesowych|Projektowanie architektury & systemowego|Wizualizacja kodu & eksploracji|Weryfikacja|
|------|-|-|-|-|-|
|diagram języka Domain-Specific (DSL)|Tak|Tak|Tak|||
|Diagram zależności, walidacja warstwy|||Tak|Tak|Tak|
|Mapa kodu|||Tak|Tak|Tak|
|Projektant klas (oparte na kodzie)||||Tak||

Aby narysować diagramy zależności, należy utworzyć projekt modelowania w ramach istniejącego lub nowego rozwiązania. Te diagramy należy utworzyć w projekcie modelowania.
Elementy na diagramach zależności znajdują się w projekcie modelowania, ale nie są przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieją poza projektem modelowania.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba zespoły używają również weryfikacji zależności, aby upewnić się, że kod w trakcie opracowywania pozostaje zgodny z projektem. Zobacz:

- [Zachowanie spójności kodu z projektem](#ValidatingCode)

- [Opisywanie architektury logicznej: diagramy zależności](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Niektóre wersje aplikacji Visual Studio weryfikację zależności i wersje tylko do odczytu map kodu do wizualizacji i modelowania. Aby sprawdzić, które wersje usługi Visual Studio obsługują tę funkcję, zobacz Obsługa wersji dla [architektury i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="understand-and-communicate-information-about-the-system"></a>Zrozumienie i komunikowanie informacji o systemie

Nie ma zalecanej kolejności używania Visual Studio modelowania, więc można ich używać zgodnie z potrzebami lub podejściem. Zazwyczaj zespoły ponownie poszukaj swoich modeli iteracyjnie i często w całym projekcie. Każdy diagram ma konkretne mocne strony, które pomagają zrozumieć, opisać i przekazać różne aspekty systemu w trakcie opracowywania.

Lunch Now i Lucerne komunikują się ze sobą i z uczestnikami projektu przy użyciu diagramów jako wspólnego języka. Na przykład w przypadku usługi Dinner Now do wykonania tych zadań używane są diagramy:

- Wizualizowanie istniejącego kodu.

- Komunikowanie się z Lucernem na temat nowych lub zaktualizowanych historii użytkownika.

- Zidentyfikuj zmiany wymagane do obsługi nowych lub zaktualizowanych historii użytkownika.

Lucerne używa diagramów do wykonywania tych zadań:

- Dowiedz się więcej o procesie biznesowym Lunch Now.

- Zrozumienie projektu systemu.

- Komunikuj się z usługą Lunch Now, aby przekazać nowe lub zaktualizowane wymagania użytkownika.

- Udokumentuj aktualizacje systemu.

Diagramy są zintegrowane z Team Foundation Server dzięki czemu zespoły mogą łatwiej planować i śledzić swoją pracę oraz zarządzać nimi. Na przykład używają modeli, aby identyfikować przypadki testowe i zadania programowe oraz szacować swoją pracę. Lucerne łączy elementy Team Foundation Server z elementami modelu, dzięki czemu mogą monitorować postęp i upewnić się, że system spełnia wymagania użytkowników. Na przykład łączy przypadki użycia z elementami pracy przypadków testowych, dzięki czemu mogą zobaczyć, że przypadki użycia są spełnione, gdy wszystkie testy zostaną spełnione.

Zanim zespoły zaewidencjują swoje zmiany, weryfikują kod względem testów i projektu, uruchamiając kompilacje, które obejmują walidację zależności i testy automatyczne. Dzięki temu można mieć pewność, że zaktualizowany kod nie jest w konflikcie z projektem i nie działa wcześniej.

### <a name="identify-changes-to-the-existing-system"></a>Identyfikowanie zmian w istniejącym systemie

Obiad Teraz musi oszacować koszt spełniania nowego wymagania. Zależy to częściowo od tego, jak ta zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie tego, jeden z deweloperów aplikacji Dinner Now tworzy te mapy i diagramy na pomocą istniejącego kodu:

|**Mapa lub diagram**|**Seriale**|
|-|-|
|*Mapa kodu*<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład obiad teraz może rozpocząć się od przejrzenia map kodu zestawu, aby zapoznać się z omówieniem zestawów i ich zależności. Mogą oni przejść do szczegółów map, aby eksplorować przestrzenie nazw i klasy w tych zestawach.<br /><br /> Lunch Now może również tworzyć mapy, aby eksplorować konkretne obszary i inne rodzaje relacji w kodzie. Używają Eksplorator rozwiązań do znalezienia i wybrania obszarów i relacji, które ich interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [How to: Add Class Diagrams to Projects (Projektant klas).](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje swój zakres, aby skoncentrować się na obszarach, na które będzie miał wpływ nowy scenariusz. Te obszary są zaznaczone i wyróżnione na mapie:

 ![Wykres zależności przestrzeni nazw](../modeling/media/namespace_reviewsystem.png)

 **Mapa kodu przestrzeni nazw**

 Deweloper rozszerza wybrane przestrzenie nazw, aby wyświetlić ich klasy, metody i relacje:

 ![Wykres zależności rozszerzonej przestrzeni nazw](../modeling/media/dep_reviewsystem.png)

 **Rozwinięta mapa kodu przestrzeni nazw z widocznymi linkami międzygrupowych**

 Deweloper analizuje kod, aby znaleźć objęte klasy i metody. Aby zobaczyć skutki każdej zmiany w ich przypadku, ponownie wygeneruj mapy kodu po każdej zmianie. Zobacz [Wizualizacja kodu](../modeling/visualize-code.md).

 Aby opisać zmiany w innych częściach systemu, takich jak składniki lub interakcje, zespół może narysować te elementy na tablicach. Mogą one również rysować następujące diagramy w Visual Studio, aby szczegóły mogły być przechwytywane, zarządzane i zrozumiałe dla obu zespołów:

|**Diagramy**|**Opisuje**|
|-|-|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [How to: Add Class Diagrams to Projects (Projektant klas).](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|Istniejące klasy w kodzie.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Zachowanie spójności kodu z projektem
 Obiad Teraz musi upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą diagramy zależności, które opisują warstwy funkcjonalności w systemie, określają dozwolone zależności między nimi i kojarzą artefakty rozwiązania z tymi warstwami.

|**Diagram**|**Opisuje**|
|-|-|
|*Diagram zależności*<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikowanie kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|Architektura logiczna kodu.<br /><br /> Diagram zależności organizuje i mapuje artefakty w rozwiązaniu Visual Studio do grup abstrakcyjnych nazywanych *warstwami*. Te warstwy identyfikują role, zadania lub funkcje, które te artefakty wykonują w systemie.<br /><br /> Diagramy zależności są przydatne do opisywania zamierzonego projektu systemu i sprawdzania poprawności zmieniającego się kodu względem tego projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksplorator rozwiązań, map kodu, Widok klasy i przeglądarki obiektów. Aby narysować nowe warstwy, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu zależności, a następnie kliknij polecenie **Generuj zależności.** Aby określić zamierzone zależności, należy narysować nowe zależności.|

Na przykład na poniższym diagramie zależności opisano zależności między warstwami i liczbę artefaktów skojarzonych z każdą warstwą:

![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności**

Aby upewnić się, że konflikty z projektem nie wystąpią podczas tworzenia kodu, zespoły wykorzystują weryfikację zależności w kompilacjach uruchamianych na Azure DevOps. Tworzą również niestandardowe zadanie MSBuild, aby wymagać weryfikacji zależności w operacjach zaewidencjncji. Raporty kompilacji są zbierane w celu zbierania błędów walidacji.

Zobacz:

- [Korzystanie z projektanta wizualnego](/azure/devops/pipelines/get-started-designer)

- [Kontrola kontroli wersji serwera Team](/azure/devops/pipelines/build/triggers)

- [Zadania kompilacji i wydania](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Ogólne porady dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów połączonych liniami. Dla każdego typu diagramu przybornik udostępnia różne rodzaje węzłów i linii.

   Aby otworzyć przybornik, w menu **Widok** kliknij pozycję **Przybornik**.

- Aby utworzyć węzeł, przeciągnij go z przybornika do diagramu. Niektóre rodzaje węzłów należy przeciągać na istniejące węzły. Na przykład na diagramie składników należy dodać nowy port do istniejącego składnika.

- Aby utworzyć linię lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródłowy, a następnie kliknij węzeł docelowy. Niektóre wiersze można tworzyć tylko między określonymi rodzajami węzłów. Gdy przenosisz wskaźnik na możliwe źródło lub obiekt docelowy, wskaźnik wskazuje, czy można utworzyć połączenie.

### <a name="plan-and-track-work"></a>Planowanie i śledzenie pracy

Visual Studio modelowania są zintegrowane z Team Foundation Server, dzięki czemu można łatwiej planować i śledzić pracę oraz zarządzać nimi. Oba zespoły używają modeli, aby identyfikować przypadki testowe i zadania programowe oraz szacować swoją pracę. Lucerna tworzy i łączy elementy Team Foundation Server z elementami modelu, takimi jak przypadki użycia lub składniki. Ułatwia to monitorowanie postępu i śledzenie pracy z powrotem do wymagań użytkowników. Dzięki temu mogą upewnić się, że ich zmiany nadal spełniają te wymagania.

W trakcie pracy zespoły aktualizują swoje elementy robocze, aby odzwierciedlały czas spędzony na zadaniach. Ponadto monitorują i raportują stan swojej pracy przy użyciu następujących Team Foundation Server funkcji:

- Raporty *dziennego spadku,* które pokazują, czy zostaną ukończone planowane prace w oczekiwanym czasie. Generują one inne podobne raporty z Team Foundation Server, aby śledzić postęp usterek.

- Arkusz *iteracji,* który używa programu Microsoft Excel, aby pomóc zespołowi w monitorowaniu i równoważeniu obciążenia między jego członkami. Ten arkusz jest połączony z Team Foundation Server i umożliwia dyskusję podczas regularnych spotkań z postępami.

- Pulpit *nawigacyjny dewelopera,* który używa projektu pakietu Office, aby informować zespół o ważnych informacjach o projekcie.

Zobacz:

- [Informacje o narzędziach Agile i zarządzaniu projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Wykresy, pulpity nawigacyjne i widżety (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Tworzenie listy prac i zadań przy użyciu projektu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Testowanie, weryfikowanie i sprawdzanie kodu

Gdy zespoły ukończą każde zadanie, sprawdzają swój kod w kontroli źródła i otrzymują przypomnienia od Team Foundation Server, jeśli o tym zapomnią. Zanim Team Foundation Server zaakceptuje swoje zaewidencje, zespoły uruchamiają testy jednostkowe i weryfikację zależności, aby zweryfikować kod pod względem przypadków testowych i projektu. Używają one Team Foundation Server do regularnego uruchamiania kompilacji, zautomatyzowanych testów jednostkowych i walidacji zależności. Pomaga to upewnić się, że kod spełnia następujące kryteria:

- Działa.

- Nie powoduje to przerwania wcześniej pracy kodu.

- Nie powoduje konfliktu z projektem.

Lunch Now zawiera dużą kolekcję testów automatycznych, których Lucerne może użyć ponownie, ponieważ prawie wszystkie nadal mają zastosowanie. Lucerne może również tworzyć te testy i dodawać nowe, aby obejmować nowe funkcje. Obie używają również Visual Studio do uruchamiania testów ręcznych.

Aby upewnić się, że kod jest zgodny z projektem, zespoły konfigurują swoje kompilacje w Azure DevOps, aby uwzględnić weryfikację zależności. Jeśli wystąpią konflikty, zostanie wygenerowany raport ze szczegółami.

Zobacz:

- [Testowanie aplikacji](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Korzystanie z kontroli wersji](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizowanie systemu przy użyciu wizualizacji i modelowania

Lucerne i Lunch Now muszą zintegrować swoje systemy płatności. W poniższych sekcjach przedstawiono diagramy modelowania w Visual Studio ułatwić im wykonanie tego zadania:

- [Wizualizacja istniejącego kodu: mapy kodu](#VisualizeCode)

- [Definiowanie słownika typów: diagramy klas](#DefineClasses)

- [Opisywanie architektury logicznej: diagramy zależności](#DescribeLayers)

Zobacz:

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a> Wizualizacja istniejącego kodu: mapy kodu

Mapy kodu pokazują bieżącą organizację i relacje w kodzie. Elementy są reprezentowane przez *węzły* na mapie, a relacje są reprezentowane przez *łącza*. Mapy kodu mogą ułatwić wykonywanie następujących rodzajów zadań:

- Eksploruj nieznany kod.

- Dowiedz się, gdzie i w jaki sposób proponowana zmiana może wpłynąć na istniejący kod.

- Znajdowanie obszarów złożoności, naturalnych zależności lub wzorców albo innych obszarów, które mogą skorzystać z ulepszeń.

Na przykład obiad musi oszacować koszt aktualizacji składnika PaymentProcessing. Zależy to częściowo od tego, jak ta zmiana wpłynie na inne części systemu. Aby ułatwić im zrozumienie tego, jeden z deweloperów aplikacji Dinner Now generuje mapy kodu na podstawie kodu i dostosowuje fokus zakresu na obszarach, na które może mieć wpływ zmiana.

Na poniższej mapie przedstawiono zależności między klasą PaymentProcessing i innymi wybranymi częściami systemu Lunch Now:

![Wykres zależności dla systemu płatności Lunch Now](../modeling/media/dep_dnpayment.png)

**Mapa kodu systemu płatności Lunch Now**

Deweloper eksploruje mapę, rozwijając klasę PaymentProcessing i wybierając jej składowe, aby zobaczyć potencjalne obszary, których dotyczy problem:

![Metody wewnątrz paymentProcessing i zależności](../modeling/media/depgraph_expandeddn.png)

**Metody wewnątrz klasy PaymentProcessing i ich zależności**

Generują następującą mapę dla systemu płatności Lucerne, aby sprawdzić jego klasy, metody i zależności. Zespół widzi, że system Lucerne może również wymagać pracy w celu interakcji z innymi częściami programu Lunch Now:

![Wykres zależności dla systemu płatności Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mapa kodu dla systemu płatności Lucerne**

Oba zespoły współpracują ze sobą, aby określić zmiany, które są wymagane do zintegrowania tych dwóch systemów. Decydują się na refaktoryzowanie kodu, aby ułatwić jego aktualizację. Klasa PaymentApprover zostanie przeniesiena do przestrzeni nazw DinnerNow.Business i będzie wymagać pewnych nowych metod. Klasy Lunch Now, które obsługują transakcje, będą mieć własną przestrzeń nazw. Zespoły tworzą elementy robocze i używają ich do planowania, organizowania i śledzenia swojej pracy. Elementy robocze są łączyć z elementami modelu tam, gdzie jest to przydatne.

Po reorganizacji kodu zespoły generują nową mapę kodu, aby zobaczyć zaktualizowaną strukturę i relacje:

![Wykres zależności ze zreorganizowany kod](../modeling/media/depgraph_integrated.png)

**Mapa kodu ze zreorganizowany kod**

Ta mapa pokazuje, że klasa PaymentApprover znajduje się teraz w przestrzeni nazw DinnerNow.Business i ma kilka nowych metod. Klasy transakcji Lunch Now mają teraz własną przestrzeń nazw PaymentSystem, co ułatwia późniejsze radzenie sobie z tym kodem.

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu

- Aby uzyskać szybki przegląd kodu źródłowego, wykonaj następujące kroki, aby wygenerować mapę kodu:

     W menu **Architektura** kliknij pozycję **Generuj mapę kodu dla rozwiązania.**

     Aby uzyskać szybki przegląd skompilowanego kodu, utwórz pustą mapę kodu, a następnie przeciągnij pliki zestawu lub pliki binarne na powierzchnię mapy.

- Aby eksplorować określony kod lub elementy rozwiązania, użyj Eksplorator rozwiązań, aby wybrać elementy i relacje, które chcesz zwizualizować. Następnie możesz wygenerować nową mapę lub dodać wybrane elementy do istniejącej mapy. Zobacz [Mapowanie zależności między rozwiązaniami.](../modeling/map-dependencies-across-your-solutions.md)

- Aby ułatwić eksplorowanie mapy, należy zmienić układ tak, aby odpowiadał rodzajom zadań, które chcesz wykonać.

     Aby na przykład zwizualizować warstwy w kodzie, wybierz układ drzewa. Zobacz [Przeglądanie i ponowne rozmieszczanie map kodu.](../modeling/browse-and-rearrange-code-maps.md)

#### <a name="summary-strengths-of-code-maps"></a>Podsumowanie: Silne strony map kodu
 Mapy kodu ułatwiają:

- Dowiedz się więcej o organizacji i relacjach w istniejącym kodzie.

- Identyfikowanie obszarów, na które może mieć wpływ proponowana zmiana.

- Znajdowanie obszarów złożoności, wzorców, warstw lub innych obszarów, które można ulepszyć, aby ułatwić konserwację, zmianę i ponowne używanie kodu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opisuje**|
|-|-|
|Diagram zależności|Architektura logiczna systemu. Użyj weryfikacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikację istniejących lub zamierzonych zależności, utwórz mapę kodu i pogrupuj powiązane elementy. Aby utworzyć diagram zależności, zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)|
|Diagram klas (oparty na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Aby zwizualizować i zmodyfikować istniejącą klasę w kodzie, użyj Projektant klas.<br /><br /> Zobacz [How to: Add Class Diagrams to Projects (Projektant klas) (2.3.0:](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)dodawanie diagramów klas do projektów Projektant klas).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Definiowanie słownika typów: diagramy klas
 Diagramy klas definiują jednostki, terminy lub koncepcje, które uczestniczą w systemie, i ich relacje ze sobą. Na przykład można użyć tych diagramów podczas opracowywania do opisania atrybutów i operacji dla każdej klasy, niezależnie od ich języka implementacji lub stylu.

 Aby pomóc Lucernie opisać i omówić jednostki, które uczestniczą w przypadku użycia płatności procesu, narysują następujący diagram klas:

 ![Przetwarzanie jednostek płatności na diagramie klas](../modeling/media/uml_payentities.png)

 **Przetwarzanie jednostek płatności na diagramie klas**

 Na tym diagramie widać, że klient może mieć wiele zamówień i różne sposoby płacenia za zamówienia. Konta BankAccount i CreditCard dziedziczą po płatności.

 Podczas opracowywania Lucerne używa następującego diagramu klas do opisania i omówienia szczegółów każdej klasy:

 ![Przetwarzanie szczegółów jednostki płatności na diagramie klas](../modeling/media/uml_payment.png)

 **Przetwarzanie szczegółów płatności na diagramie klas**

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas

Diagram klas ma następujące główne funkcje:

- Typy, takie jak klasy, interfejsy i wyliczenia:

  - Klasa *to* definicja obiektów, które mają określone cechy strukturalne lub behawioralne.

  - Interfejs  definiuje część widocznego na zewnątrz zachowania obiektu.

  - *Wyliczenie* to klasyfikator, który zawiera listę wartości literałów.

- *Atrybuty to* wartości pewnego typu, które opisują każde wystąpienie *klasyfikatora*. Klasyfikator to ogólna nazwa typów, składników, przypadków użycia, a nawet aktorów.

- *Operacje* to metody lub funkcje, które mogą wykonywać wystąpienia klasyfikatora.

- Skojarzenie wskazuje pewien rodzaj relacji między dwoma klasyfikatorami. 

  - *Agregacja* to skojarzenie, które wskazuje współwłasność między klasyfikatorami.

  - *Kompozycja* to skojarzenie, które wskazuje na relację całościową między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, ustaw właściwość **Agregacja** dla skojarzenia. **Udostępnione** — agregacje, **a złożone** — kompozycje.

- Zależność *wskazuje,* że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- Uogólnienie *wskazuje,* że określony klasyfikator dziedziczy część jego definicji z klasyfikatora ogólnego. Realizacja *wskazuje,* że klasa implementuje operacje i atrybuty oferowane przez interfejs.

     Aby utworzyć te relacje, użyj **narzędzia dziedziczenia.** Alternatywnie realizacja może być reprezentowana jako *lizak*.

- *Pakiety* to grupy klasyfikatorów, skojarzeń, linii życia, składników i innych pakietów. *Relacje* importu wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

Jako punkt wyjścia do eksplorować i omawiać istniejące klasy, możesz użyć Projektant klas do tworzenia diagramów klas z kodu.

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Podsumowanie: Silne strony diagramów klas
 Diagramy klas ułatwiają definiowanie:

- Wspólny słownik terminów, których należy używać podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [Wymagania użytkownika modelu.](../modeling/model-user-requirements.md)

- Typy używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje między typami, takie jak zależności. Można na przykład pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Diagram zależności|Zdefiniuj architekturę logiczną systemu w odniesieniu do klas.<br /><br /> Użyj weryfikacji zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Weryfikowanie kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa kodu|Wizualizowanie organizacji i relacji w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i metody, utwórz mapę kodu, która pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> Opisywanie architektury logicznej: diagramy zależności
 Diagramy zależności opisują architekturę logiczną systemu, organizując artefakty w rozwiązaniu w abstrakcyjne grupy lub *warstwy*. Artefakty mogą być wieloma rzeczami, takimi jak przestrzenie nazw, projekty, klasy, metody itp. Warstwy reprezentują i opisują role lub zadania wykonywane przez artefakty w systemie. Możesz również uwzględnić walidację warstwy w operacjach kompilacji i zaewidencjiowania, aby upewnić się, że kod pozostaje zgodny z jego projektem.

 Aby zachować spójność kodu z projektem, program Dinner Now i Lucerne używają następującego diagramu zależności do weryfikowania kodu w jego rozwoju:

 ![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności dla obiadu teraz zintegrowane z Lucerne**

 Warstwy na tym diagramie są linkami do odpowiednich artefaktów rozwiązania Dinner Now i Lucerne. Na przykład warstwa Biznesowa łączy się z przestrzenią nazw DinnerNow.Business i jej członkami, które teraz zawierają klasę PaymentApprover. Warstwa Dostępu do zasobów łączy się z przestrzenią nazw DinnerNow.Data. Strzałki lub zależności *określają,* że tylko warstwa Biznesowa może korzystać z funkcji w warstwie Dostęp do zasobów. Gdy zespoły aktualizują swój kod, walidacja warstwy jest regularnie wykonywana w celu wychwytania konfliktów w ich przypadku i szybkiego rozwiązywania ich przez zespoły.

 Zespoły współpracują ze sobą w celu przyrostowej integracji i testowania obu systemów. Najpierw upewniają się, że paymentApprover i pozostała część usługi Dinner Now działają ze sobą pomyślnie, zanim zajmieją się usługą PaymentProcessing.

 Na poniższej mapie kodu przedstawiono nowe wywołania między usługami Dinner Now i PaymentApprover:

 ![Zaktualizowano wykres zależności za pomocą zintegrowanego systemu](../modeling/media/depgraph_intsystem.png)

 **Mapa kodu ze zaktualizowanymi wywołaniami metod**

 Po potwierdzeniu, że system działa zgodnie z oczekiwaniami, program Dinner Now dodaje komentarze do kodu PaymentProcessing. Raporty weryfikacji warstwy są czyste, a wynikowa mapa kodu pokazuje, że nie istnieją już zależności PaymentProcessing:

 ![Wykres zależności bez paymentProcessing](../modeling/media/depgraph_nomore.png)

 **Mapa kodu bez przetwarzania płatności**

#### <a name="drawing-a-dependency-diagram"></a>Rysowanie diagramu zależności

Diagram zależności ma następujące główne funkcje:

- *Warstwy* opisują logiczne grupy artefaktów.

- Link *jest* skojarzeniem między warstwą i artefaktem.

     Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksplorator rozwiązań, mapy kodu, Widok klasy lub przeglądarki obiektów. Aby narysować nowe warstwy, a następnie połączyć je z artefaktami, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

     Liczba w warstwie pokazuje liczbę artefaktów połączonych z warstwą. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami itp. Podczas interpretowania liczby artefaktów w warstwie należy pamiętać o następujących elementy:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

       Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby wyświetlić artefakty połączone z warstwą, kliknij prawym przyciskiem myszy zależność, a następnie kliknij polecenie Wyświetl linki, **aby** otworzyć **Eksploratora warstwy.**

- Zależność *wskazuje,* że jedna warstwa może używać funkcji w innej warstwie, ale nie na odwrót. Zależność *dwukierunkowa wskazuje,* że jedna warstwa może używać funkcji w innej warstwie i na odwrót.

     Aby wyświetlić istniejące zależności na diagramie zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij pozycję **Generuj zależności**. Aby opisać zamierzone zależności, narysuj nowe zależności.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)

- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Podsumowanie: Silne strony diagramów zależności

Diagramy zależności ułatwiają:

- Opis architektury logicznej systemu zgodnie z funkcjonalnością jego artefaktów.

- Upewnij się, że kod w trakcie opracowywania jest zgodny z określonym projektem.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Mapa kodu|Wizualizowanie organizacji i relacji w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, wygeneruj mapę kodu, a następnie pogrupuj elementy na mapie jako potencjalne warstwy. Przeciągnij grupy z mapy do diagramu zależności.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i ponowne rozmieszczanie map kodu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|-|-|
|**Fora**|- [Visual Studio Visualization & Modeling Tools](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modeling SDK (Narzędzia DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Używanie modeli w programie Agile Development](/previous-versions/ff398061(v=vs.140))
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)