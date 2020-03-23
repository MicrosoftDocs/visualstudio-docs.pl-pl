---
title: Analizowanie użycia pamięci JavaScript w aplikacjach platformy uniwersalnej systemu Windows | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cfbc0dcecbf9b30afdfb268117e34c2fcfc0341e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189382"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>Analizowanie użycia pamięci JavaScript w aplikacjach platformy uniwersalnej systemu Windows
Analizator pamięci JavaScript jest dostępny w programie Visual Studio, aby ułatwić zrozumienie użycia pamięci i znajdowanie przecieków pamięci w aplikacjach platformy uniwersalnej systemu Windows utworzonych dla systemu Windows przy użyciu języka JavaScript. Obsługiwane aplikacje obejmują aplikacje dla uniwersalnych aplikacji systemu Windows.

 Analizator pamięci JavaScript może wykonać następujące czynności za Ciebie:

- Pomóż szybko znaleźć problemy z użyciem pamięci w aplikacji, podkreślając najbardziej odpowiednie dane.

     Te dane są dostępne w podsumowaniach migawek, które pokazują różnice między dwiema migawkami i zawierają łącza do bardziej szczegółowych widoków.

- Podaj widoki dominatorów, typów i katalogów głównych, aby ułatwić izolowanie problemów.

- Zmniejsz informacje o stercie javascript, które nie można podjąć.

     Obiekty, które nie są tworzone bezpośrednio w kodzie aplikacji, są automatycznie odfiltrowywane. Można również filtrować dane według nazwy obiektu.

## <a name="run-the-javascript-memory-analyzer"></a>Uruchamianie analizatora pamięci JavaScript
 Analizator pamięci można użyć, gdy masz działającą aplikację platformy uniwersalnej systemu w programie Visual Studio.

#### <a name="to-run-the-memory-analyzer"></a>Aby uruchomić analizator pamięci

1. Otwórz program Visual Studio.

2. Jeśli korzystasz z aplikacji z programu Visual Studio, na liście **Rozpocznij debugowanie** na pasku narzędzi **Standardowy** wybierz miejsce docelowe debugowania dla projektu: **komputer lokalny** lub **urządzenie**.

3. Na pasku menu wybierz pozycję **Debug** > **Performance Profiler**.

     Domyślnie bieżący projekt uruchamiania jest analizowany. Jeśli chcesz zmienić cel analizy, wybierz pozycję **Zmień miejsce docelowe**.

     ![Zmień cel analizy](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Dla celu analizy dostępne są następujące opcje:

    - **Projekt startowy**. Analizuje bieżący projekt startowy. Jeśli korzystasz z aplikacji na komputerze zdalnym, musisz wybrać tę opcję, która jest domyślna.

    - **Uruchamianie aplikacji**. Umożliwia wybranie aplikacji platformy uniwersalnej systemu Windows z listy uruchomionych aplikacji. Tej opcji nie można używać podczas uruchamiania aplikacji na komputerze zdalnym.

         Ta opcja służy do analizowania użycia pamięci aplikacji uruchomionych na komputerze, gdy nie masz dostępu do kodu źródłowego.

    - **Zainstalowana aplikacja**. Umożliwia wybranie zainstalowanej aplikacji platformy uniwersalnej systemu Windows, którą chcesz przeanalizować. Tej opcji nie można używać podczas uruchamiania aplikacji na komputerze zdalnym.

         Ta opcja służy do analizowania użycia pamięci aplikacji zainstalowanych na komputerze, gdy nie masz dostępu do kodu źródłowego. Ta opcja może być również przydatna, gdy chcesz tylko analizować użycie pamięci dowolnej aplikacji poza własnym programem tworzenia aplikacji.

4. W **obszarze Dostępne narzędzia**zaznacz pole wyboru Pamięć **JavaScript,** a następnie wybierz pozycję **Start**.

5. Po uruchomieniu analizatora pamięci okno Kontrola konta użytkownika może zażądać zgody na uruchomienie programu Visual Studio ETW Collector.exe. Wybierz **pozycję Tak**.

     Interakcja z aplikacją, aby przetestować odpowiednie scenariusze użycia pamięci i wyświetlić wykres pamięci, jak omówiono w poniższych sekcjach.

6. Przełącz się do programu Visual Studio, naciskając klawisz **Alt**+**Tab**.

7. Aby wyświetlić dane, które zbiera analizator pamięci, wybierz opcję **Zrób migawkę sterty**. Zobacz [Wyświetlanie podsumowania migawki](#view-a-snapshot-summary) w dalszej części tego tematu.

## <a name="check-memory-usage"></a>Sprawdzanie użycia pamięci
 Można spróbować zidentyfikować przecieki pamięci przy użyciu różnych widoków w analizatorze pamięci JavaScript. Jeśli podejrzewasz, że aplikacja przecieka pamięci, zobacz [Izolowanie przeciek pamięci](#isolate-a-memory-leak) dla sugerowanego przepływu pracy.

 Użyj następujących widoków, aby zidentyfikować przecieki pamięci w aplikacji:

- [Wyświetl podsumowanie użycia pamięci na żywo](#view-live-memory-usage-summary). Użyj wykresu użycia pamięci, aby wyszukać nagły wzrost użycia pamięci lub stale zwiększając użycie pamięci, które wynika z określonych akcji. Użyj widoku podsumowania użycia pamięci na żywo, aby zrobić migawki sterty. Migawki są wyświetlane jako kolekcja w obszarze wykres użycia pamięci.

    > [!TIP]
    > Podczas robienia migawki zostanie wyświetlony skok użycia pamięci. Użyj podsumowań migawki, aby uzyskać dokładniejsze wskazanie wzrostu.

- [Wyświetlanie podsumowania migawki](#view-a-snapshot-summary). Można wyświetlić informacje podsumowania migawki podczas lub po sesji profilowania pamięci. Użyj podsumowań migawki, aby utworzyć łącze do szczegółów migawki i widoków różnicowych migawek.

    > [!TIP]
    > Zazwyczaj widoki różnicy migawki zapewni najbardziej przydatne informacje o przecieki pamięci.

- [Wyświetl szczegóły migawki](#view-snapshot-details). Pokazuje szczegółowe dane użycia pamięci dla pojedynczej migawki.

- [Wyświetlanie różnicy migawki](#view-a-snapshot-diff). Pokazuje wartości różnicowe między migawkami. Widoki te pokazują różnice w rozmiarze obiektu i liczbie obiektów.

## <a name="isolate-a-memory-leak"></a>Wyizolowanie przecieku pamięci
 Te kroki zapewniają przepływ pracy, który może pomóc w skuteczniejszym użyciu analizatora pamięci JavaScript. Te kroki mogą być przydatne, jeśli podejrzewasz, że aplikacja ma przeciek pamięci. Aby zapoznać się z samouczkiem, który prowadzi użytkownika przez proces identyfikowania przecieku pamięci w działającej aplikacji, zobacz [Przewodnik: Znajdowanie przecieku pamięci (JavaScript)](javascript-memory.md).

1. Otwórz aplikację w programie Visual Studio.

2. Uruchom analizator pamięci JavaScript (zobacz wcześniejsze kroki).

3. Uruchom aplikację w scenariuszu, który chcesz przetestować. Na przykład scenariusz może obejmować dużą mutację DOM, gdy dana strona ładuje się lub gdy aplikacja zostanie uruchomiony.

4. Powtórz scenariusz 1-4 dodatkowe czasy.

   > [!TIP]
   > Powtarzając scenariusz testu kilka razy, można się upewnić, że praca inicjowania może być odfiltrowana z wyników.

5. Przełącz się do **Alt**+programu Visual Studio (naciśnij**klawisz Alt Tab**).

6. Zrób migawkę sterty linii bazowej, wybierając **pozycję Zrób migawkę sterty**.

    Na poniższej ilustracji przedstawiono przykład migawki linii bazowej.

    ![Migawka linii bazowej](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Aby uzyskać bardziej precyzyjną kontrolę nad czasem migawek, można użyć [polecenia Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data) w kodzie.

7. Przełącz się do aplikacji i powtórz testowany scenariusz (powtórz tylko raz).

8. Przełącz się do programu Visual Studio i zrób drugą migawkę.

9. Przełącz się do aplikacji i powtórz testowany scenariusz (powtórz tylko raz).

10. Przełącz się do programu Visual Studio i zrób trzecią migawkę.

     Na poniższej ilustracji przedstawiono przykład drugiej i trzeciej migawki.

     ![Druga i trzecia migawka](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Korzystając z linii bazowej, drugiej i trzeciej migawki w tym przepływie pracy, można odfiltrować zmiany, które nie są skojarzone z przeciekami pamięci łatwiej. Na przykład mogą wystąpić oczekiwane zmiany, takie jak aktualizowanie nagłówków i stopek na stronie, które wygenerują pewne zmiany w użyciu pamięci, ale mogą być niezwiązane z przeciekami pamięci.

11. Z trzeciej migawki wybierz łącze do jednego z widoków różnicowych:

    - Rozmiar sterty różnicowej (lewe łącze poniżej rozmiaru sterty). Tekst łącza pokazuje różnicę między rozmiarem sterty bieżącej migawki a rozmiarem sterty poprzedniej migawki.

    - Liczba obiektów różnicowych (prawe łącze pod liczbą obiektów). Tekst łącza zawiera dwie wartości (na przykład +1858 / -1765): Pierwsza wartość to liczba nowych obiektów dodanych od poprzedniej migawki, a druga wartość to liczba obiektów usuniętych od poprzedniej migawki.

      Te łącza otwierają widok szczegółów migawki różnicowej typów na stercie, posortowany według liczby zachowanych rozmiarów lub obiektów, w zależności od tego, które łącze zostało otwarte.

12. Wybierz jedną z następujących opcji **filtru zakresu,** aby zidentyfikować problemy z użyciem pamięci:

    - **Obiekty pozostały z #2 migawka**.

    - **Obiekty dodane między #2 migawką a #3**

    > [!TIP]
    > Użyj filtrowanego widoku obiektów pozostałych z poprzedniej migawki, aby zbadać przecieki pamięci. Na przykład jeśli liczba obiektów różnicowych jest +205 / -195, ten widok pokaże 10 obiektów pozostałych, a są one prawdopodobnie kandydatów do przecieków pamięci.

     Na poniższej ilustracji przedstawiono widok różnicowy obiektów pozostałych po #2 migawki.

     ![Widok różnicy migawki przedstawiający typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Na poprzedniej ilustracji widzimy, że dwa obiekty są pozostawione z poprzedniej migawki. Sprawdź, czy jest to oczekiwane zachowanie dla danej aplikacji. Jeśli nie, może to wskazywać na przeciek pamięci.

13. Aby zobaczyć, gdzie obiekty w widokach różnicowych są zakorzenione w obiekcie globalnym, co uniemożliwia ich gromadzenie śmieci, otwórz menu skrótów dla obiektu, a następnie wybierz pozycję **Pokaż w widoku korzeniowym**. Duża liczba obiektów może być przechowywana w pamięci, ponieważ są one odwoływane przez pojedynczy obiekt (lub kilka obiektów), które są zakorzenione w obiekcie globalnym.

14. Jeśli istnieje zbyt wiele obiektów w widoku obiektów pozostałych, spróbuj dodatkowo wyizolować okres, w którym występuje przeciek pamięci, a następnie ponownie wykonać trzy migawki. Aby dodatkowo wyizolować przeciek pamięci, należy użyć [skojarzyć kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data), Skojarz kod [źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data)i innymi danymi użycia pamięci dostępnymi w analizatorze pamięci.

## <a name="view-live-memory-usage-summary"></a>Wyświetlanie podsumowania użycia pamięci na żywo
 Widok podsumowania użycia pamięci na żywo zawiera wykres użycia pamięci dla uruchomionej aplikacji i kolekcję wszystkich kafelków podsumowania migawki. W tym widoku można wykonywać podstawowe zadania, takie jak wykonywanie migawek, analizowanie informacji podsumowujących i przechodzenie do innych widoków. Po zatrzymaniu zbierania danych wykres pamięci zniknie i zobaczysz tylko [widok podsumowania migawki.](#view-a-snapshot-summary)

 Wykres pamięci pokazuje podgląd na żywo pamięci procesu aplikacji, który obejmuje bajty prywatne, pamięć natywną i stertę JavaScript. Wykres pamięci jest przewijanym widokiem pamięci procesu. Oto jak to wygląda:

 ![Wykres pamięci analizatora pamięci JavaScript](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Jeśli do kodu aplikacji dodano znaczniki użytkownika (zobacz [Skojarzenie kodu źródłowego z danymi użycia pamięci),](#associate-source-code-with-memory-usage-data)na wykresie użycia pamięci pojawi się odwrócony trójkąt wskazujący, kiedy ta sekcja kodu zostanie osiągnięta.

 Część pamięci wyświetlanej na wykresie pamięci jest przydzielana przez środowisko wykonawcze JavaScript. Nie można kontrolować tego użycia pamięci w aplikacji. Użycie pamięci wyświetlane na wykresie zwiększa się podczas robienia pierwszej migawki, a następnie zwiększa minimalnie dla każdej dodatkowej migawki.

## <a name="view-a-snapshot-summary"></a>Wyświetlanie podsumowania migawki
 Aby zrobić migawkę bieżącego stanu użycia pamięci aplikacji, wybierz pozycję **Zrób migawkę sterty** z wykresu pamięci. Kafelek podsumowania migawki, który pojawia się zarówno w podsumowaniu użycia pamięci na żywo (gdy aplikacja jest uruchomiona), jak i w podsumowaniu migawki (po zatrzymaniu aplikacji), zawiera informacje o stercie JavaScript i łącza do bardziej szczegółowych informacji. Jeśli wziąć dwie lub więcej migawek, migawka zawiera dodatkowe informacje porównujące jego dane do poprzedniej migawki.

> [!NOTE]
> Analizator pamięci JavaScript wymusza wyrzucanie elementów bezużytecznych przed każdą migawką. Pomaga to zapewnić bardziej spójne wyniki wśród przebiegów.

 Oto przykład podsumowania migawki podczas robienia wielu migawek.

 ![Podsumowanie migawki](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Podsumowanie migawki obejmuje:

- Tytuł migawki i sygnatura czasowa.

- Liczba potencjalnych problemów (oznaczonej niebieską ikoną informacji). Ta liczba, jeśli jest obecny, identyfikuje potencjalne problemy z pamięcią, takie jak węzły, które nie są dołączone do dom. Liczba łączy do widoku Typy migawki, który jest sortowany według typu problemu, aby wyróżnić potencjalne problemy. Etykietka narzędzia zawiera opis problemu.

- Rozmiar sterty. Liczba ta zawiera elementy DOM i obiekty, które aparat środowiska wykonawczego JavaScript dodaje do sterty JavaScript. Rozmiar sterty łączy się z types widoku migawki.

- Rozmiar sterty różnicowej. Ta wartość pokazuje różnicę między rozmiar sterty bieżącej migawki i rozmiar sterty poprzedniej migawki. Po wartości następuje czerwona strzałka w górę, jeśli występuje zwiększenie pamięci lub zielona strzałka w dół, jeśli występuje zmniejszenie pamięci. Jeśli rozmiar sterty nie uległ zmianie między migawkami, zamiast liczby zostanie wyświetlony tekst **Brak zmiany.** W przypadku pierwszej migawki zostanie wyświetlony tekst **Linia bazowa**. Rozmiar sterty różnicowej łączy się z types widoku różnicy migawki.

- Liczba obiektów. Ta liczba pokazuje tylko obiekty utworzone w aplikacji i filtruje wbudowane obiekty utworzone przez środowisko wykonawcze JavaScript. Liczba obiektów łączy się z widokem Typy szczegółów migawki.

- Liczba obiektów różnicowych. Pokazuje dwie wartości: pierwsza wartość to liczba nowych obiektów dodanych od poprzedniej migawki; a drugą wartością jest liczba obiektów usuniętych od poprzedniej migawki. Na przykład ilustracja pokazuje, że dodano 1859 obiektów i 1733 obiekty zostały usunięte od #1 migawki. Po tych informacjach następuje czerwona strzałka w górę, jeśli całkowita liczba obiektów wzrosła lub zielona strzałka w dół, jeśli została zmniejszona. Jeśli liczba obiektów nie uległa zmianie, zamiast liczby zostanie wyświetlony tekst **Brak zmiany.** W przypadku pierwszej migawki zostanie wyświetlony tekst **Linia bazowa**. Liczba obiektów różnicowych łączy się z widokem Typy różnicy migawki.

- Zrzut ekranu na ekranie w momencie robienia migawki.

## <a name="view-snapshot-details"></a>Wyświetlanie szczegółów migawki
 Można wyświetlić szczegółowe informacje na temat użycia pamięci dla każdej migawki w widokach szczegółów migawki.

 W widoku podsumowania migawki wybierz łącze, aby wyświetlić szczegóły migawki. Na przykład łącze rozmiar sterty otwiera szczegóły migawki z widokem Typy otwarte domyślnie.

 Na tej ilustracji przedstawiono typy widoku w szczegółach migawki, z danymi użycia pamięci posortowane według rozmiaru zachowanego.

 ![Widok szczegółów migawki przedstawiający potencjalne problemy](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 W widoku szczegółów migawki można przejrzeć dane użycia pamięci według typu, katalogu głównego lub dominatora, wybierając opcję z paska narzędzi:

- **Typy**. Pokazuje liczbę wystąpień i całkowity rozmiar obiektów na stercie pogrupowanych według typu obiektu. Domyślnie są one sortowane według liczby wystąpień.

  > [!TIP]
  > Zazwyczaj widoki różnicowe typów na stercie obiektu są najbardziej przydatne widoki do identyfikacji przeciek pamięci; widoki te zapewniają **scope filtr,** aby ułatwić identyfikację pozostałych obiektów.

- **Korzenie**. Pokazuje hierarchiczny widok obiektów z obiektów głównych za pośrednictwem odniesień podrzędnych. Domyślnie węzły podrzędne są sortowane według kolumny o rozmiarze zachowanym, z największą u góry.

- **Dominatory**. Pokazuje listę obiektów na stercie, które mają wyłączne odwołania do innych obiektów. Dominatory są sortowane według zachowanych rozmiarów.

  > [!TIP]
  > Po usunięciu dominatora z pamięci, można odzyskać całą pamięć, która zachowuje obiekt. W przypadku kilku aplikacji widok Dominators może pomóc w wyjaśnieniu rozmiarów pamięci zachowanych, ponieważ można zbadać pełny łańcuch odwołań do obiektów.

  Wszystkie trzy widoki mają podobne typy wartości, w tym:

- **Identyfikatory .** Nazwa, która najlepiej identyfikuje obiekt. Na przykład dla elementów HTML szczegóły migawki pokaż wartość atrybutu identyfikator, jeśli jest używany.

- **Wpisz**. Typ obiektu (na przykład element łącza HTML lub element div).

- **Rozmiar**. Rozmiar obiektu, z wyłączeniem rozmiaru obiektów, do których istnieją odwołania.

- **Zachowany rozmiar**. Rozmiar obiektu plus rozmiar wszystkich obiektów podrzędnych, które nie mają innych chyłek. Ze względów praktycznych jest to ilość pamięci zachowanej przez obiekt, więc jeśli usuniesz obiekt, odzyskasz określoną ilość pamięci.

- **Policz**. Liczba wystąpień obiektów. Ta wartość jest wyświetlana tylko w widoku Typy.

## <a name="view-a-snapshot-diff"></a>Wyświetlanie różnicy migawki
 W analizatorze pamięci JavaScript można porównać migawkę z poprzednią migawką w widokach różnicowych migawki.

 W widoku podsumowania migawki można wyświetlić szczegóły migawki różnicowej, wybierając rozmiar sterty różnicowej lub łącza liczby obiektów różnicowych po wykonaniu dwóch lub więcej migawek.

 Można wyświetlać informacje różnicowe dotyczące typów, katalogów głównych i dominatorów. Różnice między migawką zawiera informacje, takie jak obiekty, które zostały dodane do sterty między dwoma migawek.

 Na tej ilustracji przedstawiono widok Typy w diff migawki.

 ![Widok różnicy migawki przedstawiający typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 W oknie różnicy migawki widoki Dominators, Typy i Korzenie widoki są takie same jak w [oknie Szczegóły migawki widoku.](#view-snapshot-details) Różnice między migawkami są wyświetlane te same informacje, co szczegóły migawki, z następującymi dodatkowymi wartościami:

- **Rozmiar diff**. Różnica między rozmiarem obiektu w bieżącej migawki i jego rozmiar w poprzedniej migawki, bez uwzględnienia rozmiaru żadnych obiektów, do których istnieje odwołanie.

- **Zachowany rozmiar różnicy**. Różnica między zachowanym rozmiarem obiektu w bieżącej migawce a jego zachowanym rozmiarem w poprzedniej migawce. Zachowany rozmiar zawiera rozmiar obiektu plus rozmiar wszystkich jego obiektów podrzędnych, które nie mają innych wiązek rzowych. Ze względów praktycznych zachowany rozmiar to ilość pamięci zatrzymanej przez obiekt, więc po usunięciu obiektu odzyskasz określoną ilość pamięci.

  Aby filtrować informacje różnicowe między migawkami, wybierz jeden z filtrów **zakresu** w górnej części widoków różnicowych.

- **Obiekty pozostały z\<migawka # numer>**. Ten filtr pokazuje różnice między obiektami dodanymi do sterty i usuniętymi ze sterty w porównaniu z migawką linii bazowej i poprzednią migawką. Na przykład jeśli podsumowanie migawki pokazuje +205 / -195 w liczbie obiektów, ten filtr pokaże dziesięć obiektów, które zostały dodane, ale nie usunięte.

  > [!TIP]
  > Aby wyświetlić najbardziej przydatne informacje w tym filtrze, wykonaj kroki opisane w [izolowaniu przecieku pamięci](#isolate-a-memory-leak).

- **Obiekty dodane między\<migawką #\<liczba> i # liczba>**. Ten filtr pokazuje wszystkie obiekty dodane do sterty z poprzedniej migawki.

- **Wszystkie obiekty w\<migawka # numer>**. To ustawienie filtru nie odfiltruje żadnych obiektów na stercie.

  Aby wyświetlić odwołania do obiektów, które nie pasują do bieżącego **filtru zakresu,** wybierz pozycję **Pokaż niepasujące odwołania** na liście ![ustawień rozwijanej&#45;w dół listy w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka. Jeśli to ustawienie zostanie włączone, niepasujące odniesienia będą wyświetlane z szarym tekstem.

> [!TIP]
> Zaleca się wykonanie kroków w [Izolowanie przeciek pamięci,](#isolate-a-memory-leak) a następnie użyć obiektów pozostałych za pomocą **filtru Scope,** aby ułatwić identyfikowanie obiektów, które przeciekają pamięci.

## <a name="view-objects-by-dominator"></a>Wyświetlanie obiektów według dominatora
 W widokach Typy i Dominatory można wybrać, czy obiekty mają być wyświetlane w ich dominatorach (jest to widok domyślny na karcie **Dominatory).** Gdy ten widok jest zaznaczony, tylko dominatory są wyświetlane w widoku najwyższego poziomu obiektów. (Obiekty, które są elementami podrzędnymi obiektów innych niż globalne, są ukryte w widoku najwyższego poziomu). W przypadku niektórych aplikacji może to wyjaśnić, które obiekty powodują przeciek pamięci, zmniejszając hałas w danych.

 Aby przełączyć widok obiektów według dominatora, wybierz przycisk **Złóż w obiektach za pomocą przycisku dominatora.** ![Składanie obiektów do dominatorów](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Aby uzyskać więcej informacji na temat dominatorów, zobacz [Wyświetlanie szczegółów migawki](#view-snapshot-details).

## <a name="filter-data-by-identifier"></a>Filtrowanie danych według identyfikatora
 W widokach Dominators i Types można odfiltrować dane, wyszukując określone identyfikatory. Aby wyszukać identyfikator, wpisz jego nazwę w polu tekstowym **filtru identyfikatora** w prawym górnym rogu. Po rozpoczęciu wpisywania identyfikatory, które nie zawierają wpisanych znaków, są odfiltrowywane.

 Każdy widok ma swój własny filtr, więc filtr nie jest zachowywany po przełączeniu do innego widoku.

## <a name="find-an-object-in-the-object-tree"></a>Znajdowanie obiektu w drzewie obiektów
 W widokach Typy i Dominators można zobaczyć relację `Global` określonego obiektu z obiektem. Obiekty zakorzenione `Global` w obiekcie nie będą zbierane od śmieci. Znany obiekt można łatwo znaleźć w widoku Korzenie bez przeszukiwania drzewa `Global` obiektów. Aby to zrobić, otwórz menu skrótów dla obiektu w widoku Dominators lub Type, a następnie wybierz polecenie **Pokaż w widoku korzeniowym**.

## <a name="view-shared-object-references"></a>Wyświetlanie odwołań do obiektów udostępnionych
 W widokach Typy i Dominators dolne okienko zawiera listę odwołań do obiektu, na których są wyświetlane odwołania udostępnione. Po wybraniu obiektu w górnym okienku na liście Odwołania do obiektu zostaną wyświetlone wszystkie obiekty wskazujące ten obiekt.

> [!NOTE]
> Odwołania cykliczne są wyświetlane z gwiazdką (*) i etykietką narzędzi informacyjnych i nie można ich rozwinąć. W przeciwnym razie uniemożliwiłyby one przechodzenie w górę drzewa odwołań i identyfikowanie obiektów, które zachowują pamięć.

 Jeśli chcesz uzyskać dodatkową pomoc w identyfikacji równoważnych obiektów, wybierz pozycję **Wyświetl identyfikatory obiektów** na liście ![ustawień Upuść&#45;w dół w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu górnego okienka. Ta opcja wyświetla identyfikatory obiektów obok nazw obiektów na liście **Identyfikatorów (identyfikatory** są wyświetlane we wszystkich widokach, a nie tylko na liście Odwołania do obiektów). Obiekty o tym samym identyfikatorze są odwołaniami udostępnionymi.

 Na poniższej ilustracji przedstawiono listę odwołań do obiektów dla wybranego elementu z wyświetlonymi identyfikatorami.

 ![Odwołania do obiektów z wyświetlonymi identyfikatorami](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Pokaż wbudowane obiekty
 Domyślnie widoki Dominators i Types pokazują tylko obiekty utworzone w aplikacji. Pomaga to odfiltrować niepotrzebne informacje i wyizolować problemy związane z aplikacjami. Jednak czasami może być przydatne do wyświetlania wszystkich obiektów, które środowisko wykonawcze JavaScript generuje dla aplikacji.

 Aby wyświetlić te obiekty, wybierz pozycję **Pokaż wbudowane** na liście ![ustawień upuść&#45;w dół listy w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka.

## <a name="save-diagnostic-session-files"></a>Zapisywanie plików sesji diagnostycznych
 Podsumowania migawki diagnostycznej i skojarzone z nimi widoki szczegółów są zapisywane jako . *diagsession* plików. **Eksplorator rozwiązań** wyświetla poprzednie sesje diagnostyczne w folderze Sesje diagnostyczne. W **Eksploratorze rozwiązań**można otwierać poprzednie sesje lub usuwać lub zmieniać nazwy plików.

## <a name="associate-source-code-with-memory-usage-data"></a>Kojarzenie kodu źródłowego z danymi użycia pamięci
 Aby ułatwić wyizolowanie sekcji kodu, która ma problem z pamięcią, należy użyć następujących metod:

- Poszukaj nazw klas i identyfikatorów elementów DOM w widokach szczegółów i różnic.

- Poszukaj wartości ciągów w szczegółach i widokach różnicowych, które mogą być skojarzone z kodem źródłowym.

- Polecenie [Znajdź obiekt w drzewie obiektów](#find-an-object-in-the-object-tree) służy do przejścia w górę drzewa obiektów. Może to pomóc w zidentyfikowaniu skojarzonego kodu źródłowego.

- Dodaj polecenia analizatora pamięci do kodu źródłowego.

  W kodzie źródłowym można użyć następujących poleceń:

- `console.takeHeapSnapshot`wykonuje migawkę sterty, która pojawia się w analizatorze pamięci JavaScript. To polecenie jest jednym z [poleceń konsoli JavaScript](../debugger/javascript-console-commands.md).

- `performance.mark`ustawia znacznik użytkownika (odwrócony trójkąt), który pojawia się na osi czasu wykresu pamięci w widoku podsumowania, gdy aplikacja jest uruchomiona. To polecenie przyjmuje jeden argument ciągu, który opisuje zdarzenie i pojawia się jako etykietka narzędzia na wykresie pamięci. Opis ten nie może przekraczać 100 znaków.

> [!TIP]
> Służy `console.takeHeapSnapshot` do przyspieszenia analizy podczas powtarzania scenariuszy użycia pamięci.

 Te polecenia zgłaszają wyjątek, jeśli dodasz je do aplikacji i uruchomisz aplikację poza analizatorem pamięci JavaScript. Można jednak sprawdzić, czy polecenia istnieją przed ich użyciem. (Polecenia nie istnieją na początku fazy uruchamiania sesji). Aby sprawdzić, czy `takeHeapSnapshot`można bezpiecznie zadzwonić , użyj tego kodu:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Aby sprawdzić, czy `performance.mark`można bezpiecznie zadzwonić , użyj tego kodu:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Oto wykres pamięci z kilkoma znacznikami użytkownika i etykietką narzędzia dla aktualnie `performance.mark` wybranego znacznika użytkownika, dla którego argument ciąg jest ustawiony na "wygenerowane dane":

 ![Używanie znacznika profilu](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>Wskazówki dotyczące identyfikowania problemów z pamięcią

- Postępuj zgodnie z przepływem pracy opisanym w [Izolować przeciek pamięci](#isolate-a-memory-leak) i użyj **obiektów pozostałych od\<migawka # numer>** filtr w widoku różnicowym, aby zidentyfikować prawdopodobnych kandydatów do przecieków pamięci.

- Użyj [znajdź obiektu w drzewie obiektów,](#find-an-object-in-the-object-tree) aby zobaczyć, gdzie obiekt jest odwoływany w hierarchii pamięci. Widok Korzenie pokazuje, jak obiekt jest zakorzeniona w obiekcie globalnym, co uniemożliwiłoby mu zbierane śmieci.

- Gdy przyczyna problemu z pamięcią jest trudna do zidentyfikowania, użyj różnych widoków (takich jak Dominators i Types), aby wyszukać podobieństwa, szczególnie w celu zidentyfikowania jednego obiektu (lub kilku obiektów), które mogą zawierać odwołania do wielu innych obiektów, które pojawiają się w widoku.

- Poszukaj obiektów, które są przechowywane w pamięci przypadkowo po użytkownik przeszedł do nowej strony, co jest częstą przyczyną problemów z pamięcią. Przykład:

  - Nieprawidłowe użycie [adresu URL. Funkcja CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) może spowodować ten problem.

  - Niektóre obiekty mogą `dispose` zapewnić metodę i zalecenia dotyczące użycia. Na przykład należy `dispose` wywołać na [WinJS.Binding.List,](/previous-versions/windows/apps/hh700774\(v\=win.10\)) jeśli `createFiltered` wywołasz metodę listy, a następnie przejdź od strony.

  - Może być konieczne usunięcie co najmniej jednego detektora zdarzeń. Aby uzyskać więcej informacji, zobacz [Wyświetlanie detektorów zdarzeń DOM](../debugger/quickstart-debug-html-and-css.md).

- Obejrzyj drugą część [tego filmu wideo](https://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Build 2013 na temat analizatora pamięci JavaScript.

- Przeczytaj tryb [Zarządzanie pamięcią w aplikacjach platformy uniwersalnej systemu Windows](https://msdn.microsoft.com/magazine/jj651575.aspx).

- Należy rozważyć tymczasowe modyfikowanie kodu, aby wyizolować problemy. Na przykład możesz chcieć:

  - Użyj poleceń dla analizatora `console.takeSnapshot` `performance.mark`pamięci i . (Zobacz [Skojarzenie kodu źródłowego z danymi użycia pamięci).](#associate-source-code-with-memory-usage-data)

    Za pomocą tych poleceń można wyizolować problemy, których nie można wyizolować, ręcznie robiąc migawkę sterty.

  - Utwórz obiekt testowy i śledź go w widokach analizatora pamięci JavaScript, takich jak widok Typy. Na przykład można dołączyć bardzo duży obiekt do innego obiektu, aby zobaczyć, czy określony obiekt lub element został zebranych śmieci.
