---
title: 'Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1400f6d5881d5340ec452297d3579306111391b6
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759735"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania

Upewnij się, że system oprogramowania spełnia potrzeby użytkowników przy użyciu narzędzi do wizualizacji i modelowania w programie Visual Studio.
Użyj narzędzi, takich jak mapy kodu, diagramy zależności i diagramy klas, aby:

Aby zobaczyć, które wersje programu Visual Studio obsługują każde narzędzie, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Wyjaśnij wymagania użytkowników i procesy biznesowe.

- Wizualizuj i eksploruj istniejący kod.

- Opis zmian w istniejącym systemie.

- Sprawdź, czy system spełnia jego wymagania.

- Zachowaj kod zgodny z projektem.

Ten przewodnik:

- W tym artykule opisano, jak te narzędzia mogą przynieść korzyści projektowi oprogramowania.

- Pokazuje, jak można użyć tych narzędzi, niezależnie od podejścia do programowania, z przykładowym scenariuszem.

Aby dowiedzieć się więcej o tych narzędziach i scenariuszach, które obsługują, zobacz:

- [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Omówienie scenariusza

W tym scenariuszu opisano epizody z cyklu życia tworzenia oprogramowania dwóch fikcyjnych firm: Dinner Now i Lucerne Publishing. Dinner Now zapewnia usługę dostarczania posiłków w Seattle w sieci Web. Klienci mogą zamówić posiłki i zapłacić za nie na stronie internetowej Obiad teraz. Zamówienia są następnie wysyłane do odpowiedniej lokalnej restauracji w celu dostarczenia. Lucerne Publishing, firma z Nowego Jorku, prowadzi kilka firm zarówno poza siecią, jak i w internecie. Na przykład prowadzą witrynę sieci Web, w której klienci mogą publikować recenzje restauracji.

Lucerna niedawno nabyte Obiad teraz i chce wprowadzić następujące zmiany:

- Zintegruj swoje strony internetowe, dodając możliwości przeglądu restauracji do Obiad teraz.

- Zamień system płatności Dinner Now na system Lucerny.

- Rozwiń usługę Obiad teraz w całym regionie.

Kolacja Teraz używa SCRUM i eXtreme Programming. Mają bardzo wysoki zasięg testu i bardzo mało nieobsługiwał kod. Minimalizują one ryzyko, tworząc małe, ale działające wersje systemu, a następnie dodając funkcje przyrostowo. Rozwijają swój kod za jący krótkie i częste iteracje. Dzięki temu mogą ogarniać zmiany pewnie, refaktoryzuje kod często i uniknąć "duży projekt z góry".

Lucerna utrzymuje znacznie większy i złożony zbiór systemów, z których niektóre mają ponad 40 lat. Są one bardzo ostrożne w wprowadzaniu zmian ze względu na złożoność i zakres starszego kodu. Postępują zgodnie z bardziej rygorystycznym procesem rozwoju, preferując projektowanie szczegółowych rozwiązań i dokumentowanie projektu i zmian, które zachodzą podczas opracowywania.

Oba zespoły używają diagramów modelowania w programie Visual Studio, aby pomóc im w opracowywaniu systemów spełniających potrzeby użytkowników. Używają team foundation server wraz z innymi narzędziami, aby pomóc im planować, organizować i zarządzać swoją pracą.

Aby uzyskać więcej informacji na temat programu Team Foundation Server, zobacz:

- [Planowanie i śledzenie pracy](#plan-and-track-work)

- [Testowanie, sprawdzanie poprawności i sprawdzanie zaktualizowanego kodu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Role diagramów architektury i modelowania w tworzeniu oprogramowania

W poniższej tabeli opisano role, które te narzędzia mogą odgrywać na wielu i różnych etapach cyklu życia tworzenia oprogramowania:

||**Modelowanie wymagań użytkownika**|**Modelowanie procesów biznesowych**|**Architektura systemu & projektowanie**|**Wizualizacja kodu & eksploracji**|**Weryfikacja**|
|------|-|-|-|-|-|
|Diagram języka specyficznego dla domeny (DSL)|Tak|Tak|Tak|||
|Diagram zależności, sprawdzanie poprawności warstwy|||Tak|Tak|Tak|
|Mapa kodu|||Tak|Tak|Tak|
|Projektant klas (oparty na kodzie)||||Tak||

Aby narysować diagramy zależności, należy utworzyć projekt modelowania jako część istniejącego rozwiązania lub nowego. Te diagramy muszą być tworzone w projekcie modelowania.
Elementy na diagramach zależności znajdują się w projekcie modelowania, ale nie są przechowywane we wspólnym modelu. Mapy kodu i diagramy klas .NET utworzone na podstawie kodu istnieją poza projektem modelowania.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba zespoły również użyć sprawdzania poprawności zależności, aby upewnić się, że kod w fazie rozwoju pozostaje zgodne z projektem. Zobacz:

- [Utrzymywanie kodu zgodnego z projektem](#ValidatingCode)

- [Opis architektury logicznej: diagramy zależności](#DescribeLayers)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Niektóre wersje programu Visual Studio obsługują sprawdzanie poprawności zależności i tylko do odczytu wersje map kodu do wizualizacji i modelowania. Aby zobaczyć, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa architektury i modelowania w wersji.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="understand-and-communicate-information-about-the-system"></a>Zrozumienie i przekazywanie informacji o systemie

Nie ma żadnych wymaganych kolejności przy użyciu diagramów modelowania programu Visual Studio, dzięki czemu można ich używać, ponieważ pasują one do twoich potrzeb lub podejścia. Zazwyczaj zespoły ponownie ich modele iteratively i często w całym projekcie. Każdy diagram oferuje szczególne mocne strony, które pomogą Ci zrozumieć, opisać i przekazać różne aspekty systemu w fazie opracowywania.

Dinner Now i Lucerna komunikują się ze sobą i z zainteresowanymi stronami projektu przy użyciu diagramów jako wspólnego języka. Na przykład obiad teraz używa diagramów do wykonywania tych zadań:

- Wizualizuj istniejący kod.

- Komunikuj się z Lucerny o nowych lub zaktualizowanych historiach użytkowników.

- Identyfikowanie zmian, które są wymagane do obsługi nowych lub zaktualizowanych wątków użytkownika.

Lucerna używa diagramów do wykonywania tych zadań:

- Dowiedz się więcej o procesie biznesowym Obiad teraz.

- Zrozumieć projekt systemu.

- Komunikuj się z obiadem teraz o nowych lub zaktualizowanych wymaganiach użytkownika.

- Aktualizacja dokumentu systemu.

Diagramy są zintegrowane z team foundation server, dzięki czemu zespoły mogą łatwiej planować, zarządzać i śledzić swoją pracę. Na przykład używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz do szacowania ich pracy. Lucerna łączy elementy robocze programu Team Foundation Server z elementami modelu, dzięki czemu mogą monitorować postęp i upewnić się, że system spełnia wymagania użytkowników. Na przykład łączą przypadki użycia do elementów roboczych sprawy testowej, dzięki czemu mogą zobaczyć, że przypadki użycia są spełnione, gdy wszystkie testy przechodzą.

Zanim zespoły zaewidencjonują swoje zmiany, sprawdzają poprawność kodu względem testów i projektu, uruchamiając kompilacje, które obejmują sprawdzanie poprawności zależności i testy automatyczne. Pomaga to upewnić się, że zaktualizowany kod nie powoduje konfliktu z projektem i przerywa wcześniej działające funkcje.

### <a name="identify-changes-to-the-existing-system"></a>Identyfikowanie zmian w istniejącym systemie

Obiad teraz musi oszacować koszt spełnienia nowego wymogu. Zależy to częściowo od tego, jak bardzo ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów obiad teraz tworzy te mapy i diagramy z istniejącego kodu:

|**Mapa lub diagram**|**Seriale**|
|-|-|
|*Mapa kodu*<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Dostosowywanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Zależności i inne relacje w kodzie.<br /><br /> Na przykład obiad teraz można rozpocząć od przeglądu map kodu zestawu dla przeglądu zestawów i ich zależności. Mogą one drążyć na mapach, aby eksplorować przestrzenie nazw i klasy w tych zestawach.<br /><br /> Obiad teraz można również utworzyć mapy do eksplorowania poszczególnych obszarów i innych rodzajów relacji w kodzie. Używają Eksploratora rozwiązań, aby znaleźć i wybrać obszary i relacje, które ich interesują.|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Istniejące klasy w kodzie|

 Na przykład deweloper tworzy mapę kodu. Dostosowuje swój zakres, aby skupić się na obszarach, które będą miały wpływ na nowy scenariusz. Te obszary są zaznaczone i wyróżnione na mapie:

 ![Wykres zależności obszaru nazw](../modeling/media/namespace_reviewsystem.png)

 **Mapa kodu obszaru nazw**

 Deweloper rozszerza wybrane przestrzenie nazw, aby wyświetlić ich klasy, metody i relacje:

 ![Wykres zależności rozwiniętego obszaru nazw](../modeling/media/dep_reviewsystem.png)

 **Mapa kodu rozszerzonej przestrzeni nazw z widocznymi łączami między grupami**

 Deweloper sprawdza kod, aby znaleźć których dotyczy problem klas i metod. Aby zobaczyć efekty każdej zmiany w miarę ich wprowadzania, ponownie wygeneruj mapy kodu po każdej zmianie. Zobacz [Wizualizuj kod](../modeling/visualize-code.md).

 Aby opisać zmiany w innych częściach systemu, takich jak składniki lub interakcje, zespół może narysować te elementy na tablicach. Mogą również rysować następujące diagramy w programie Visual Studio, dzięki czemu szczegóły mogą być przechwytywane, zarządzane i zrozumiałe dla obu zespołów:

|**Diagramy**|**Opisuje**|
|-|-|
|*Diagram klas oparty na kodzie*<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Istniejące klasy w kodzie.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Zachowaj spójność kodu z projektem
 Obiad teraz należy upewnić się, że zaktualizowany kod pozostaje zgodny z projektem. Tworzą diagramy zależności, które opisują warstwy funkcjonalności w systemie, określają dozwolone zależności między nimi i kojarzą artefakty rozwiązania z tymi warstwami.

|**Diagram**|**Opisuje**|
|-|-|
|*Diagram zależności*<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Sprawdzanie poprawności kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|Logiczna architektura kodu.<br /><br /> Diagram zależności organizuje i mapuje artefakty w rozwiązaniu programu Visual Studio na abstrakcyjne grupy zwane *warstwami.* Warstwy te identyfikują role, zadania lub funkcje, które te artefakty wykonują w systemie.<br /><br /> Diagramy zależności są przydatne do opisywania zamierzonego projektu systemu i sprawdzania poprawności rozwijającego się kodu względem tego projektu.<br /><br /> Aby utworzyć warstwy, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klasy i przeglądarki obiektów. Aby narysować nowe warstwy, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu.<br /><br /> Aby wyświetlić istniejące zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu zależności, a następnie kliknij polecenie **Generuj zależności**. Aby określić zamierzone zależności, narysuj nowe zależności.|

Na przykład na poniższym diagramie zależności opisano zależności między warstwami i liczbę artefaktów skojarzonych z każdą warstwą:

![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności**

Aby upewnić się, że konflikty z projektem nie występują podczas tworzenia kodu, zespoły używają sprawdzania poprawności zależności w kompilacjach, które są uruchamiane na platformie Azure DevOps. Tworzą również niestandardowe zadanie MSBuild, aby wymagać sprawdzania poprawności zależności w swoich operacjach ewidencjonowania. Używają raportów kompilacji do zbierania błędów sprawdzania poprawności.

Zobacz:

- [Korzystanie z projektanta wizualnego](/azure/devops/pipelines/get-started-designer)

- [Odprawa bramna TFVC](/azure/devops/pipelines/build/triggers)

- [Tworzenie i zwalnianie zadań](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Ogólne wskazówki dotyczące tworzenia i używania modeli

- Większość diagramów składa się z węzłów połączonych liniami. Dla każdego typu diagramu przybornik zawiera różne rodzaje węzłów i linii.

   Aby otworzyć przybornik, w menu **Widok** kliknij polecenie **Przybornik**.

- Aby utworzyć węzeł, przeciągnij go z przybornika do diagramu. Niektóre rodzaje węzłów muszą być przeciągane do istniejących węzłów. Na przykład na diagramie składników nowy port musi zostać dodany do istniejącego składnika.

- Aby utworzyć linię lub połączenie, kliknij odpowiednie narzędzie w przyborniku, kliknij węzeł źródłowy, a następnie kliknij węzeł docelowy. Niektóre wiersze mogą być tworzone tylko między określonymi rodzajami węzłów. Po przesunięciu wskaźnika nad możliwym źródłem lub obiektem docelowym wskaźnik wskazuje, czy można utworzyć połączenie.

### <a name="plan-and-track-work"></a>Planowanie i śledzenie pracy

Diagramy modelowania programu Visual Studio są zintegrowane z programem Team Foundation Server, dzięki czemu można łatwiej planować, zarządzać i śledzić pracę. Oba zespoły używają modeli do identyfikowania przypadków testowych i zadań programistycznych oraz do szacowania ich pracy. Lucerna tworzy i łączy elementy robocze programu Team Foundation Server z elementami modelu, takimi jak przypadki użycia lub składniki. Pomaga im to monitorować ich postępy i śledzić ich pracę z powrotem do wymagań użytkowników. Pomaga im to upewnić się, że ich zmiany nadal spełniają te wymagania.

W miarę postępu pracy zespoły aktualizują swoje elementy robocze, aby odzwierciedlić czas spędzony na swoich zadaniach. Monitorują również i zgłaszają stan swojej pracy przy użyciu następujących funkcji team foundation server:

- Codzienne *raporty wypalenia,* które pokazują, czy zakończą planowane prace w oczekiwanym czasie. Generują inne podobne raporty z Team Foundation Server do śledzenia postępu błędów.

- *Arkusz iteracji,* który używa programu Microsoft Excel, aby pomóc zespołowi monitorować i równoważyć obciążenie między jego członkami. Ten arkusz jest połączony z team foundation server i zapewnia fokus do dyskusji podczas regularnych spotkań postępu.

- *Pulpit nawigacyjny rozwoju,* który używa pakietu Office Project, aby informować zespół o ważnych informacjach o projekcie.

Zobacz:

- [Informacje o narzędziach Agile i agile project management](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Wykresy, pulpity nawigacyjne i widżety (usługi Azure DevOps)](/azure/devops/report/dashboards/overview?view=vsts)

- [Tworzenie zaległości i zadań przy użyciu programu Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a>Testowanie, sprawdzanie poprawności i sprawdzanie kodu

Gdy zespoły wykonają każde zadanie, sprawdzają swój kod w kontroli źródła i otrzymują przypomnienia z team foundation server, jeśli zapomną. Zanim Team Foundation Server zaakceptuje ich zaewidencjonowania, zespoły uruchamiają testy jednostkowe i sprawdzanie poprawności zależności, aby zweryfikować kod w ich przypadkach testowych i projekcie. Używają Team Foundation Server do regularnego uruchamiania kompilacji, automatycznych testów jednostkowych i sprawdzania poprawności zależności. Pomaga to upewnić się, że kod spełnia następujące kryteria:

- To działa.

- Nie łamie wcześniej działającego kodu.

- Nie jest to sprzeczne z projektem.

Obiad teraz ma duży zbiór zautomatyzowanych testów, które Lucerna może ponownie użyć, ponieważ prawie wszystkie nadal mają zastosowanie. Lucerna może również opierać się na tych testach i dodawać nowe, aby objąć nowe funkcje. Oba również używać programu Visual Studio do uruchamiania testów ręcznych.

Aby upewnić się, że kod jest zgodny z projektem, zespoły skonfigurować swoje kompilacje w usłudze Azure DevOps do uwzględnienia sprawdzania poprawności zależności. Jeśli wystąpią konflikty, raport jest generowany ze szczegółami.

Zobacz:

- [Testowanie aplikacji](/azure/devops/test/overview?view=vsts)

- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)

- [Korzystanie z kontroli wersji](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizowanie systemu za pomocą wizualizacji i modelowania

Lucerna i Obiad Teraz muszą zintegrować swoje systemy płatności. W poniższych sekcjach przedstawiono diagramy modelowania w programie Visual Studio, aby ułatwić wykonanie tego zadania:

- [Wizualizuj istniejący kod: Mapy kodu](#VisualizeCode)

- [Definiowanie glosariusza typów: diagramy klas](#DefineClasses)

- [Opis architektury logicznej: diagramy zależności](#DescribeLayers)

Zobacz:

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)

- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Wizualizuj istniejący kod: Mapy kodu

Mapy kodu pokazują bieżącą organizację i relacje w kodzie. Elementy są reprezentowane przez *węzły* na mapie, a relacje są reprezentowane przez *łącza*. Mapy kodu mogą pomóc w wykonaniu następujących rodzajów zadań:

- Zapoznaj się z nieznanym kodem.

- Dowiedz się, gdzie i jak proponowana zmiana może wpłynąć na istniejący kod.

- Znajdź obszary złożoności, naturalne zależności lub wzorców lub inne obszary, które mogą korzystać z poprawy.

Na przykład obiad teraz należy oszacować koszt aktualizacji PaymentProcessing składnika. Zależy to częściowo od tego, jak bardzo ta zmiana wpłynie na inne części systemu. Aby pomóc im to zrozumieć, jeden z deweloperów obiad teraz generuje mapy kodu z kodu i dostosowuje zakres fokus na obszarach, które mogą mieć wpływ zmiany.

Na poniższej mapie przedstawiono zależności między PaymentProcessing klasy i innych części systemu Obiad teraz, które pojawiają się wybrane:

![Wykres zależności dla systemu płatności Obiad teraz](../modeling/media/dep_dnpayment.png)

**Mapa kodu dla systemu płatności Obiad Teraz**

Deweloper eksploruje mapę, rozszerzając klasę PaymentProcessing i wybierając jej członków, aby zobaczyć obszary, których może dotyczyć:

![Metody wewnątrz PaymentProcessing i zależności](../modeling/media/depgraph_expandeddn.png)

**Metody wewnątrz klasy PaymentProcesssing i ich zależności**

Generują następującą mapę dla systemu płatności Lucerna, aby sprawdzić jego klasy, metody i zależności. Zespół widzi, że system Lucerny może również wymagać pracy do interakcji z innymi częściami Obiad teraz:

![Wykres zależności dla systemu płatności Lucerny](../modeling/media/depgraph_lucernepay.png)

**Mapa kodów dla systemu płatności Lucerna**

Oba zespoły współpracują ze sobą w celu określenia zmian, które są wymagane do integracji dwóch systemów. Decydują się na refaktoryzacji niektórych kodu, tak aby łatwiej będzie zaktualizować. PaymentApprover Klasa zostanie przeniesione do obszaru nazw DinnerNow.Business i będzie wymagać nowych metod. Dinner Now klasy, które obsługują transakcje będą miały własne obszaru nazw. Zespoły tworzą i używają elementów roboczych do planowania, organizowania i śledzenia ich pracy. Łączą elementy robocze z elementami modelu, gdzie jest to przydatne.

Po reorganizacji kodu zespoły generują nową mapę kodu, aby zobaczyć zaktualizowaną strukturę i relacje:

![Wykres zależności z zreorganizowanym kodem](../modeling/media/depgraph_integrated.png)

**Mapa kodu z zreorganizowanym kodem**

Ta mapa pokazuje, że PaymentApprover klasa jest teraz w DinnerNow.Business obszaru nazw i ma kilka nowych metod. Klasy transakcji Obiad teraz mają teraz własną przestrzeń nazw PaymentSystem, co ułatwia radzenie sobie z tym kodem później.

#### <a name="creating-a-code-map"></a>Tworzenie mapy kodu

- Aby uzyskać szybki przegląd kodu źródłowego, wykonaj następujące kroki, aby wygenerować mapę kodu:

     W menu **Architektura** kliknij polecenie **Generuj mapę kodu dla rozwiązania**.

     Aby uzyskać szybki przegląd skompilowanego kodu, utwórz pustą mapę kodu, a następnie przeciągnij pliki zestawu lub pliki binarne na powierzchnię mapy.

- Aby eksplorować określone elementy kodu lub rozwiązania, użyj Eksploratora rozwiązań, aby wybrać elementy i relacje, które chcesz wizualizować. Następnie można wygenerować nową mapę lub dodać wybrane elementy do istniejącej mapy. Zobacz [Zależności mapowe między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

- Aby ułatwić eksplorowanie mapy, zmień układ tak, aby odpowiadał rodzajom zadań, które chcesz wykonać.

     Na przykład, aby wizualizować warstwy w kodzie, wybierz układ drzewa. Zobacz [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Krótki opis: Mocne strony Map Kodowych
 Mapy kodu pomogą Ci:

- Dowiedz się więcej o organizacji i relacjach w istniejącym kodzie.

- Określ obszary, na które może mieć wpływ proponowana zmiana.

- Znajdź obszary złożoności, wzorce, warstwy lub inne obszary, które można poprawić, aby ułatwić jego konserwację, zmianę i ponowne użycie.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opisuje**|
|-|-|
|Diagram zależności|Logiczna architektura systemu. Użyj sprawdzania poprawności zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Aby ułatwić identyfikowanie istniejących zależności lub zamierzonych zależności, utwórz mapę kodu i zgrupuj powiązane elementy. Aby utworzyć diagram zależności, zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)|
|Diagram klas (oparty na kodzie)|Istniejące klasy w kodzie dla określonego projektu.<br /><br /> Aby wizualizować i modyfikować istniejącą klasę w kodzie, użyj Projektanta klas.<br /><br /> Zobacz [Jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definiowanie glosariusza typów: diagramy klas
 Diagramy klas definiują jednostki, terminy lub pojęcia, które uczestniczą w systemie i ich relacje ze sobą. Na przykład można użyć tych diagramów podczas tworzenia do opisania atrybutów i operacji dla każdej klasy, niezależnie od ich języka implementacji lub stylu.

 Aby pomóc Lucernie opisać i omówić jednostki, które uczestniczą w przypadku użycia płatności procesu, rysują następujący diagram klasy:

 ![Przetwarzanie jednostek płatności na diagramie klas](../modeling/media/uml_payentities.png)

 **Przetwarzanie encji płatności na diagramie klas**

 Ten diagram pokazuje, że klient może mieć wiele zamówień i różne sposoby płacenia za zamówienia. BankAccount i CreditCard dziedziczą po płatności.

 Podczas opracowywania Lucerna używa następującego diagramu klasy, aby opisać i omówić szczegóły każdej klasy:

 ![Szczegóły jednostki płatności procesowych na diagramie klas](../modeling/media/uml_payment.png)

 **Szczegóły płatności procesu na diagramie klasy**

#### <a name="drawing-a-class-diagram"></a>Rysowanie diagramu klas

Diagram klasy ma następujące główne cechy:

- Typy, takie jak klasy, interfejsy i wyliczenia:

  - *Klasa* jest definicją obiektów, które mają określone cechy strukturalne lub behawioralne.

  - *Interfejs* definiuje część zewnętrznie widoczne zachowanie obiektu.

  - *Wyliczenie* jest klasyfikatorem, który zawiera listę wartości literału.

- *Atrybuty* są wartościami określonego typu, które opisują każde *wystąpienie klasyfikatora*. Klasyfikator jest ogólną nazwą dla typów, składników, przypadków użycia, a nawet podmiotów.

- *Operacje* są metody lub funkcje, które mogą wykonywać wystąpienia klasyfikatora.

- *Skojarzenie* wskazuje pewnego rodzaju relacji między dwoma klasyfikatorami.

  - *Agregacja* jest skojarzeniem, które wskazuje współwłasność między klasyfikatorami.

  - *Kompozycja* jest skojarzeniem, które wskazuje relację całej części między klasyfikatorami.

    Aby wyświetlić agregacje lub kompozycje, ustaw właściwość **Agregacja** na skojarzeniu. **Udostępnione** pokazuje agregacje i **Composite** pokazuje kompozycje.

- *Zależność* wskazuje, że zmiana definicji jednego klasyfikatora może zmienić definicję innego klasyfikatora.

- *Uogólnienie* wskazuje, że określony klasyfikator dziedziczy część swojej definicji z klasyfikatora ogólnego. *Realizacja* wskazuje, że klasa implementuje operacje i atrybuty oferowane przez interfejs.

     Aby utworzyć te relacje, użyj narzędzia **Dziedziczenie.** Alternatywnie, realizacja może być reprezentowana jako *lizak*.

- *Pakiety* są grupami klasyfikatorów, skojarzeń, linii życia, składników i innych pakietów. *Relacje importu* wskazują, że jeden pakiet zawiera wszystkie definicje innego pakietu.

Jako punkt wyjścia do eksplorowania i omówienia istniejących klas, można użyć Projektanta klas do tworzenia diagramów klas z kodu.

- [Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Krótki opis: Mocne strony diagramów klasowych
 Diagramy klas ułatwią zdefiniowanie:

- Wspólny glosariusz terminów do użycia podczas omawiania potrzeb użytkowników i jednostek, które uczestniczą w systemie. Zobacz [Wymagania użytkownika modelu](../modeling/model-user-requirements.md).

- Typy, które są używane przez części systemu, takie jak składniki, niezależnie od ich implementacji. Zobacz [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md).

- Relacje, takie jak zależności, między typami. Na przykład można pokazać, że jeden typ może być skojarzony z wieloma wystąpieniami innego typu.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Diagram zależności|Zdefiniuj logiczną architekturę systemu, ponieważ odnosi się do klas.<br /><br /> Użyj sprawdzania poprawności zależności, aby upewnić się, że kod pozostaje zgodny z projektem.<br /><br /> Zobacz:<br /><br /> - [Tworzenie diagramów zależności na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md)<br />- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)<br />- [Sprawdzanie poprawności kodu za pomocą diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby zidentyfikować klasy, ich relacje i ich metody, należy utworzyć mapę kodu, która pokazuje te elementy.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Opis architektury logicznej: diagramy zależności
 Diagramy zależności opisują logiczną architekturę systemu, organizując artefakty w rozwiązaniu w abstrakcyjne grupy lub *warstwy*. Artefakty mogą być wiele rzeczy, takich jak przestrzenie nazw, projekty, klasy, metody i tak dalej. Warstwy reprezentują i opisują role lub zadania, które artefakty wykonują w systemie. Można również uwzględnić sprawdzanie poprawności warstwy w operacji kompilacji i zaewidencjonowania, aby upewnić się, że kod pozostaje zgodny z jego projektem.

 Aby zachować kod zgodne z projektem, Obiad teraz i Lucerna użyj następującego diagramu zależności, aby sprawdzić poprawność ich kodu w miarę jego ewolucji:

 ![Diagram zależności zintegrowanego systemu płatności](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram zależności dla obiad teraz zintegrowany z Lucerny**

 Warstwy na tym diagramie łącze do odpowiednich artefaktów rozwiązania obiad teraz i Lucerny. Na przykład warstwy biznesowej łączy się z DinnerNow.Business namespace i jego członków, które teraz obejmują PaymentApprover klasy. Warstwa dostępu do zasobów łączy się z obszarem nazw DinnerNow.Data. Strzałki lub *zależności*określają, że tylko warstwa Biznesowa może korzystać z funkcji w warstwie Dostęp do zasobów. Gdy zespoły aktualizują swój kod, sprawdzanie poprawności warstwy jest wykonywane regularnie, aby przechwytywać konflikty w miarę ich występowania i pomagać zespołom w ich szybkim rozwiązywaniu.

 Zespoły współpracują ze sobą, aby stopniowo integrować i testować oba systemy. Najpierw upewnij się, że PaymentApprover i reszta Obiad Teraz pracować ze sobą pomyślnie, zanim zajmą się PaymentProcessing.

 Poniższa mapa kodu pokazuje nowe połączenia między obiad teraz i PaymentApprover:

 ![Zaktualizowany wykres zależności ze zintegrowanym systemem](../modeling/media/depgraph_intsystem.png)

 **Mapa kodu ze zaktualizowanymi wywołaniami metod**

 Po potwierdzeniu, że system działa zgodnie z oczekiwaniami, Obiad teraz komentuje paymentprocessing kod. Raporty sprawdzania poprawności warstwy są czyste, a wynikowa mapa kodu pokazuje, że nie istnieje więcej zależności PaymentProcessing:

 ![Wykres zależności bez płatnościProcessing](../modeling/media/depgraph_nomore.png)

 **Mapa kodu bez płatnościProcessing**

#### <a name="drawing-a-dependency-diagram"></a>Rysowanie diagramu zależności

Diagram zależności ma następujące główne funkcje:

- *Warstwy* opisują logiczne grupy artefaktów.

- *Łącze* jest skojarzeniem między warstwą a artefaktem.

     Aby utworzyć warstwy z artefaktów, przeciągnij elementy z Eksploratora rozwiązań, map kodu, widoku klasy lub przeglądarki obiektów. Aby narysować nowe warstwy, a następnie połączyć je z artefaktami, użyj przybornika lub kliknij prawym przyciskiem myszy powierzchnię diagramu, aby utworzyć warstwy, a następnie przeciągnij elementy do tych warstw.

     Liczba na warstwie pokazuje liczbę artefaktów połączonych z warstwą. Te artefakty mogą być przestrzeniami nazw, projektami, klasami, metodami i tak dalej. Podczas interpretacji liczby artefaktów na warstwie należy pamiętać o następujących kwestiach:

  - Jeśli warstwa jest połączona z artefaktem zawierającym inne artefakty, ale warstwy nie łączy się bezpośrednio z innymi artefaktami, wówczas liczba uwzględnia tylko połączony artefakt. Jednak inne artefakty są uwzględniane w analizie podczas walidacji warstwy.

       Na przykład, jeżeli warstwa jest połączona z pojedynczą przestrzenią nazw, liczba połączonych artefaktów wynosi 1, nawet jeśli przestrzeń nazw zawiera klasy. Jeśli warstwa zawiera także łącza do każdej klasy w przestrzeni nazw, liczba będzie uwzględniać połączone klasy.

  - Jeśli warstwa zawiera inne warstwy, które są połączone z artefaktami, warstwa kontenerów jest także połączona z tymi artefaktami, mimo że liczba na warstwie kontenerów nie uwzględnia tych artefaktów.

    Aby wyświetlić artefakty połączone z warstwą, kliknij ją prawym przyciskiem myszy, a następnie kliknij polecenie **Wyświetl łącza,** aby otworzyć **Eksplorator warstw**.

- Zależność wskazuje, że jedna *warstwa* może korzystać z funkcji w innej warstwie, ale nie odwrotnie. *Zależność dwukierunkowa* wskazuje, że jedna warstwa może korzystać z funkcji w innej warstwie i na odwrót.

     Aby wyświetlić istniejące zależności na diagramie zależności, kliknij prawym przyciskiem myszy powierzchnię diagramu, a następnie kliknij polecenie **Generuj zależności**. Aby opisać zamierzone zależności, narysuj nowe.

Zobacz:

- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)

- [Diagramy zależności: Wskazówki](../modeling/layer-diagrams-guidelines.md)

- [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Krótki opis: Mocne strony diagramów zależności

Diagramy zależności pomagają:

- Opisz logiczną architekturę systemu zgodnie z funkcjonalnością jego artefaktów.

- Upewnij się, że kod w fazie rozwoju jest zgodny z określonym projektem.

#### <a name="relationship-to-other-diagrams"></a>Związek z innymi diagramami

|**Diagram**|**Opis**|
|-|-|
|Mapa kodu|Wizualizuj organizację i relacje w istniejącym kodzie.<br /><br /> Aby utworzyć warstwy, wygeneruj mapę kodu, a następnie pogrupuj elementy na mapie jako potencjalne warstwy. Przeciągnij grupy z mapy do diagramu zależności.<br /><br /> Zobacz:<br /><br /> - [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md)<br />- [Przeglądanie i zmienianie rozmieszczenia map kodu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategoria**|**Linki**|
|-|-|
|**Fora**|- [Narzędzia do modelowania & wizualizacji programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modelowanie SDK (NARZĘDZIA DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Używaj modeli w rozwoju Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)
