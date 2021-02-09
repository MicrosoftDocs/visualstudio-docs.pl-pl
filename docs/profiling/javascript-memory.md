---
title: Analizowanie użycia pamięci JavaScript w aplikacjach platformy UWP | Microsoft Docs
description: Dowiedz się, w jaki sposób jest dostępny Analizator pamięci języka JavaScript, który ułatwia zrozumienie użycia pamięci i znalezienie przecieków pamięci w aplikacjach platformy UWP utworzonych dla systemu Windows przy użyciu języka JavaScript.
ms.custom: ''
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f6fb446890c1485b6af249fd593cc9065bdba5aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918115"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>Analizowanie użycia pamięci JavaScript w aplikacjach platformy UWP
Analizator pamięci języka JavaScript jest dostępny w programie Visual Studio, aby ułatwić zrozumienie użycia pamięci i znalezienie przecieków pamięci w aplikacjach platformy UWP utworzonych dla systemu Windows przy użyciu języka JavaScript. Obsługiwane aplikacje obejmują aplikacje dla uniwersalnych aplikacji systemu Windows.

 Analizator pamięci JavaScript może wykonać następujące czynności:

- Pomożesz szybko znaleźć problemy dotyczące użycia pamięci w aplikacji, podkreślając najbardziej odpowiednie dane.

     Te dane są wyświetlane w podsumowaniu migawek, które pokazują różnice między dwiema migawkami i oferują linki do bardziej szczegółowych widoków.

- Podaj widoki dla elementów, typów i katalogów głównych, aby ułatwić wyizolowanie problemów.

- Zmniejsz informacje niewymagające podejmowania akcji w danych sterty JavaScript.

     Obiekty, które nie są tworzone bezpośrednio w kodzie aplikacji, są automatycznie odfiltrowane. Można również filtrować dane według nazwy obiektu.

## <a name="run-the-javascript-memory-analyzer"></a>Uruchamianie analizatora pamięci JavaScript
 Możesz użyć analizatora pamięci, gdy w programie Visual Studio jest otwarta działająca aplikacja platformy UWP.

#### <a name="to-run-the-memory-analyzer"></a>Aby uruchomić Analizator pamięci

1. Otwórz program Visual Studio.

2. Jeśli używasz aplikacji z programu Visual Studio, na liście **Rozpocznij debugowanie** na pasku narzędzi **Standardowy** wybierz element docelowy debugowania dla projektu: **komputer lokalny** lub **urządzenie**.

3. Na pasku menu wybierz kolejno opcje **Debuguj program**  >  **Profiler wydajności**.

     Domyślnie jest analizowany bieżący projekt startowy. Jeśli chcesz zmienić cel analizy, wybierz pozycję **Zmień cel**.

     ![Cel analizy zmian](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Dla celu analizy dostępne są następujące opcje:

    - **Projekt startowy**. Analizuje bieżący projekt startowy. Jeśli aplikacja jest uruchamiana na komputerze zdalnym, należy wybrać tę opcję, która jest domyślna.

    - **Uruchomiona aplikacja**. Umożliwia wybranie aplikacji platformy UWP z listy uruchomionych aplikacji. Nie można użyć tej opcji, jeśli aplikacja jest uruchamiana na komputerze zdalnym.

         Użyj tej opcji, aby analizować użycie pamięci przez aplikacje uruchomione na komputerze, gdy nie masz dostępu do kodu źródłowego.

    - **Zainstalowana aplikacja**. Pozwala wybrać zainstalowaną aplikację platformy UWP, którą chcesz analizować. Nie można użyć tej opcji, jeśli aplikacja jest uruchamiana na komputerze zdalnym.

         Użyj tej opcji, aby analizować użycie pamięci przez aplikacje zainstalowane na komputerze, gdy nie masz dostępu do kodu źródłowego. Ta opcja może być również przydatna, gdy chcesz tylko analizować użycie pamięci przez dowolną aplikację poza własnym programowaniem aplikacji.

4. Z **dostępnych narzędzi**, zaznacz pole wyboru **pamięć JavaScript** , a następnie wybierz **Uruchom**.

5. Po uruchomieniu analizatora pamięci okno Kontrola konta użytkownika może zażądać uprawnień do uruchamiania Collector.exe funkcji ETW programu Visual Studio. Wybierz opcję **tak**.

     Korzystając z aplikacji, przetestuj odpowiednie scenariusze użycia pamięci i Wyświetl wykres pamięci, zgodnie z opisem w poniższych sekcjach.

6. Przejdź do programu Visual Studio, naciskając klawisz **Alt** + **Tab**.

7. Aby wyświetlić dane, które zbiera Analizator pamięci, wybierz polecenie **Utwórz migawkę sterty**. Zobacz sekcję [Wyświetlanie podsumowania migawek](#view-a-snapshot-summary) w dalszej części tego tematu.

## <a name="check-memory-usage"></a>Sprawdź użycie pamięci
 Można spróbować identyfikować przecieki pamięci przy użyciu różnych widoków w analizatorze pamięci JavaScript. Jeśli podejrzewasz, że w aplikacji występuje przeciek pamięci, zobacz [izolowanie przecieku pamięci](#isolate-a-memory-leak) dla sugerowanego przepływu pracy.

 Poniższe widoki służą do identyfikowania przecieków pamięci w aplikacji:

- [Wyświetl podsumowanie użycia pamięci na żywo](#view-live-memory-usage-summary). Użyj grafu użycie pamięci, aby wyszukać nagłe zwiększenie użycia pamięci lub ciągle zwiększając użycie pamięci, które wynikają z określonych działań. Użyj widoku Podsumowanie użycia pamięci na żywo, aby wykonać migawki sterty. Migawki są wyświetlane jako kolekcja w grafie użycia pamięci.

    > [!TIP]
    > Podczas tworzenia migawki zostanie wyświetlone ograniczenie użycia pamięci. Użyj podsumowań migawek, aby uzyskać dokładniejsze wskazanie wzrostu.

- [Wyświetl podsumowanie migawki](#view-a-snapshot-summary). Informacje podsumowujące migawek można wyświetlić podczas sesji profilowania pamięci lub po niej. Użyj podsumowań migawek, aby utworzyć łącze do szczegółów migawek i widoków różnic migawek.

    > [!TIP]
    > Zazwyczaj widoki różnic migawek zawierają najbardziej przydatne informacje dotyczące przecieków pamięci.

- [Wyświetl szczegóły migawki](#view-snapshot-details). Pokazuje szczegółowe dane dotyczące użycia pamięci dla pojedynczej migawki.

- [Wyświetl porównanie migawek](#view-a-snapshot-diff). Pokazuje różnice między migawkami. Te widoki pokazują różnice w rozmiarze obiektów i licznikach obiektów.

## <a name="isolate-a-memory-leak"></a>Izolowanie przecieku pamięci
 Te kroki zapewniają przepływ pracy, który może pomóc w wydajniejszym użyciu analizatora pamięci języka JavaScript. Te kroki mogą być przydatne, jeśli podejrzewasz, że aplikacja ma przeciek pamięci. Aby zapoznać się z samouczkiem, który przeprowadzi Cię przez proces identyfikowania przecieku pamięci w działającej aplikacji, zobacz [Przewodnik: Znajdowanie przecieku pamięci (JavaScript)](javascript-memory.md).

1. Otwórz aplikację w programie Visual Studio.

2. Uruchom Analizator pamięci JavaScript (zobacz wcześniejsze kroki).

3. Uruchom aplikację za pomocą scenariusza, który chcesz przetestować. Na przykład scenariusz może dotyczyć dużego mutacji modelu DOM, gdy załaduje się określoną stronę lub gdy aplikacja zostanie uruchomiona.

4. Powtórz scenariusz 1-4 dodatkowych razy.

   > [!TIP]
   > Powtarzając scenariusz testu kilka razy, możesz pomóc upewnić się, że inicjacja może zostać odfiltrowana z wyników.

5. Przejdź do programu Visual Studio (naciśnij klawisz **Alt** + **Tab**).

6. Utwórz migawkę sterty linii bazowej, wybierając pozycję **Wykonaj migawkę sterty**.

    Na poniższej ilustracji przedstawiono przykład migawki linii bazowej.

    ![Migawka linii bazowej](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Aby uzyskać dokładniejszą kontrolę nad chronometrażem migawek, można użyć polecenia [Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data) w kodzie.

7. Przejdź do aplikacji i powtórz testowany scenariusz (tylko jeden raz).

8. Przejdź do programu Visual Studio i wykonaj drugą migawkę.

9. Przejdź do aplikacji i powtórz testowany scenariusz (tylko jeden raz).

10. Przejdź do programu Visual Studio i wykonaj trzecią migawkę.

     Na poniższej ilustracji przedstawiono przykładowy drugi i trzecią migawkę.

     ![Druga i trzecia migawka](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Tworząc linię bazową, drugą i trzecią migawkę w tym przepływie pracy, możesz odfiltrować zmiany, które nie są jeszcze w stanie kojarzyć z przeciekami pamięci. Na przykład mogą wystąpić takie zmiany, jak aktualizowanie nagłówków i stopek na stronie, które spowodują wygenerowanie pewnych zmian w pamięci, ale mogą być niezwiązane z przeciekami pamięci.

11. Z trzeciej migawki wybierz łącze do jednego z widoków różnicowych:

    - Różnicowy rozmiar sterty (łącze z lewej strony poniżej rozmiaru sterty). Tekst linku pokazuje różnicę między rozmiarem sterty bieżącej migawki a rozmiarem sterty poprzedniej migawki.

    - Liczba obiektów różnicowych (prawy link poniżej liczby obiektów). Tekst linku przedstawia dwie wartości (na przykład + 1858/-1765): pierwsza wartość to liczba nowych obiektów dodanych od poprzedniej migawki, a druga wartość to liczba obiektów usuniętych od poprzedniej migawki.

      Te linki otwierają widok szczegółów migawek różnicowych typów na stercie, posortowane według rozmiaru zachowanego lub liczby obiektów, w zależności od tego, który Link został otwarty.

12. Wybierz jedną z następujących opcji filtrowania **zakresu** , aby pomóc identyfikować problemy dotyczące użycia pamięci:

    - **Obiekty pozostałe z migawki #2**.

    - **Obiekty dodane między migawką #2 i #3**

    > [!TIP]
    > Użyj filtrowanego widoku obiektów pozostawionych z poprzedniej migawki w celu zbadania przecieków pamięci. Na przykład, jeśli liczba obiektów różnicowych to + 205/-195, ten widok pokaże 10 obiektów po lewej stronie i prawdopodobnie są to sugestie dotyczące przecieków pamięci.

     Na poniższej ilustracji przedstawiono widok różnicowy obiektów, które pozostały do użycia w migawce #2.

     ![Widok porównania migawek pokazujący typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Na powyższej ilustracji widać, że dwa obiekty są pozostawiane z poprzedniej migawki. Sprawdź, czy jest to oczekiwane zachowanie dla konkretnej aplikacji. W przeciwnym razie może wskazywać przeciek pamięci.

13. Aby zobaczyć, gdzie obiekty w widokach diff są osadzone w obiekcie globalnym, co uniemożliwia ich odrzucanie elementów bezużytecznych, otwórz menu skrótów dla obiektu, a następnie wybierz **Pokaż w widoku elementów głównych**. Duża liczba obiektów może być przechowywana w pamięci, ponieważ odwołują się do nich pojedynczy obiekt (lub kilka obiektów), które są osadzone w obiekcie globalnym.

14. Jeśli w widoku obiektów pozostawiono zbyt wiele obiektów, spróbuj jeszcze bardziej odizolować okres, w którym występuje przeciek pamięci, a następnie ponownie wykonaj trzy migawki. Aby dodatkowo wyizolować przeciek pamięci, użyj [Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data), [Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data)i inne dane użycia pamięci dostępne w analizatorze pamięci.

## <a name="view-live-memory-usage-summary"></a>Wyświetl podsumowanie użycia pamięci na żywo
 Widok Podsumowanie użycia pamięci na żywo zawiera wykres użycia pamięci dla uruchomionej aplikacji i kolekcję wszystkich kafelków podsumowania migawek. W tym widoku można wykonywać podstawowe zadania, takie jak tworzenie migawek, analizowanie informacji podsumowujących i nawigowanie w innych widokach. Po zatrzymaniu zbierania danych Wykres pamięci zostanie wysunięty i zobaczysz tylko widok [podsumowania migawek](#view-a-snapshot-summary) .

 Wykres pamięci pokazuje dynamiczny widok pamięci procesu aplikacji, w tym bajty prywatne, pamięć natywną i stertę JavaScript. Wykres pamięci jest przewijanym widokiem pamięci procesu. Oto jak wygląda:

 ![Wykres pamięci analizatora pamięci JavaScript](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Jeśli dodano znaczniki użytkownika do kodu aplikacji (zobacz [Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data)), odwrócony trójkąt pojawia się na wykresie użycia pamięci, aby wskazać, kiedy ta sekcja kodu została osiągnięta.

 Część pamięci wyświetlanej w grafie pamięci jest alokowana przez środowisko uruchomieniowe JavaScript. Nie możesz kontrolować tego użycia pamięci w aplikacji. Użycie pamięci pokazanej na grafie zwiększa się podczas pierwszej migawki, a następnie zwiększa się minimalnie dla każdej kolejnej migawki.

## <a name="view-a-snapshot-summary"></a>Wyświetl podsumowanie migawek
 Aby wykonać migawkę bieżącego stanu użycia pamięci aplikacji, wybierz polecenie **Utwórz migawkę sterty** z grafu pamięci. Kafelek podsumowania migawek, który pojawia się zarówno w podsumowaniu użycia pamięci na żywo (podczas gdy aplikacja jest uruchomiona), jak i podsumowanie migawki (gdy aplikacja jest zatrzymana), zawiera informacje na temat sterty JavaScript oraz linki do bardziej szczegółowych informacji. Jeśli zajmiesz co najmniej dwie migawki, migawka zawiera dodatkowe informacje porównujące jego dane z poprzednią migawką.

> [!NOTE]
> Analizator pamięci JavaScript wymusza wyrzucanie elementów bezużytecznych przed każdą migawką. Zapewnia to bardziej spójne wyniki między przebiegami.

 Oto przykład podsumowania migawki podczas wykonywania wielu migawek.

 ![Podsumowanie migawek](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Podsumowanie migawek obejmuje następujące:

- Tytuł migawki i sygnatura czasowa.

- Liczba potencjalnych problemów (oznaczona przez niebieską ikonę informacji). Ta liczba (jeśli istnieje) identyfikuje potencjalne problemy z pamięcią, takie jak węzły, które nie są dołączone do modelu DOM. Liczba łączy do widoku typów migawki, która jest posortowana według typu problemu w celu wyróżnienia potencjalnych problemów. Etykietka narzędzia zawiera opis problemu.

- Rozmiar sterty. Ta liczba obejmuje elementy DOM i obiekty, które aparat środowiska uruchomieniowego JavaScript dodaje do sterty JavaScript. Rozmiar sterty łączy się z widokiem typów migawki.

- Różnicowa rozmiar sterty. Ta wartość pokazuje różnicę między rozmiarem sterty bieżącej migawki a rozmiarem sterty poprzedniej migawki. Po wykonaniu tej wartości następuje czerwona strzałka w górę w przypadku zwiększenia ilości pamięci lub zielonej strzałki w dół w przypadku zmniejszenia ilości pamięci. Jeśli rozmiar sterty nie został zmieniony między migawkami, zobaczysz tekst **bez zmian** zamiast liczby. Dla pierwszej migawki zobaczysz **linię bazową** tekstu. Rozmiar sterty różnicowej łączy się z widokiem typów porównania migawek.

- Liczba obiektów. Ta liczba przedstawia tylko obiekty utworzone w aplikacji i filtruje wbudowane obiekty utworzone przez środowisko uruchomieniowe JavaScript. Liczba obiektów łączy się z widokiem typów w szczegółach migawki.

- Liczba obiektów różnicowych. Pokazuje dwie wartości: pierwsza wartość to liczba nowych obiektów dodanych od poprzedniej migawki; Druga wartość to liczba obiektów usuniętych od poprzedniej migawki. Na przykład ilustracja pokazuje, że dodano 1 859 obiektów i 1 733 obiektów zostało usuniętych od #1 migawek. Do tych informacji następuje czerwona strzałka w górę, jeśli całkowita liczba obiektów została zwiększona lub zielona strzałka w dół w przypadku jej zmniejszenia. Jeśli licznik obiektów nie został zmieniony, zobaczysz tekst **bez zmian** zamiast liczby. Dla pierwszej migawki zobaczysz **linię bazową** tekstu. Liczba obiektów różnicowych łączy się z widokiem typów porównania migawek.

- Zrzut ekranu przedstawiający ekran w czasie trwania migawki.

## <a name="view-snapshot-details"></a>Wyświetl szczegóły migawki
 Możesz wyświetlić szczegółowe informacje o wykorzystaniu pamięci dla każdej migawki w widokach szczegółów migawek.

 W widoku podsumowania migawek wybierz łącze, aby wyświetlić szczegóły migawki. Na przykład link rozmiaru sterty otwiera szczegóły migawki z widokiem typy otwarte domyślnie.

 Na tej ilustracji przedstawiono widok typów w szczegółach migawki z danymi użycia pamięci posortowanymi według rozmiaru zachowanego.

 ![Widok szczegółów migawek przedstawiający potencjalne problemy](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 W widoku Szczegóły migawki można przeglądać dane użycia pamięci według typu, głównego lub Dominatora, wybierając opcję z paska narzędzi:

- **Typy**. Pokazuje liczbę wystąpień i łączny rozmiar obiektów w stercie pogrupowane według typu obiektu. Domyślnie są one sortowane według liczby wystąpień.

  > [!TIP]
  > Zazwyczaj widoki różnic typów na stercie obiektów są najbardziej przydatnymi widokami służącymi do identyfikowania przecieku pamięci. te widoki zapewniają filtr **zakresu** , który pomaga identyfikować pozostałe obiekty.

- Elementy **Główne**. Pokazuje hierarchiczny widok obiektów z obiektów głównych za pośrednictwem odwołań podrzędnych. Domyślnie węzły podrzędne są sortowane według kolumny o zachowanym rozmiarze i największej w górnej części.

- **Dominuje**. Pokazuje listę obiektów na stercie, które mają wyłączne odwołania do innych obiektów. Rozmiary są sortowane według rozmiaru zachowanego.

  > [!TIP]
  > Po usunięciu Dominatora z pamięci Odzyskaj całą pamięć, która jest zachowywana przez obiekt. W przypadku kilku aplikacji widok, który może pomóc w wyjaśnieniu zachowywanych rozmiarów pamięci, ponieważ można zbadać kompletny łańcuch odwołań do obiektów.

  Wszystkie trzy widoki pokazują podobne typy wartości, w tym:

- **Identyfikatory**. Nazwa, która najlepiej identyfikuje obiekt. Na przykład dla elementów HTML szczegóły migawki pokazują wartość atrybutu ID, jeśli jest używana.

- **Typ**. Typ obiektu (na przykład element linku HTML lub element DIV).

- **Rozmiar**. Rozmiar obiektu, bez uwzględniania rozmiaru wszystkich obiektów, do których istnieją odwołania.

- **Zachowany rozmiar**. Rozmiar obiektu plus rozmiar wszystkich obiektów podrzędnych, które nie mają innych elementów nadrzędnych. W praktyce jest to ilość pamięci zajmowanej przez obiekt, więc po usunięciu obiektu Odbierz określoną ilość pamięci.

- **Liczba**. Liczba wystąpień obiektu. Ta wartość jest wyświetlana tylko w widoku typy.

## <a name="view-a-snapshot-diff"></a>Wyświetlanie różnic migawek
 W analizatorze pamięci JavaScript można porównać migawkę z poprzednią migawką w widokach różnic migawek.

 W widoku podsumowania migawek można wyświetlić szczegóły migawki różnicowej, wybierając linki różnicowe rozmiaru sterty lub liczby obiektów różnicowych po wykonaniu dwóch lub większej liczby migawek.

 Można wyświetlić informacje różnicowe o typach, katalogach głównych i obiektach. Różnica migawek zawiera informacje, takie jak obiekty, które zostały dodane do sterty między dwiema migawkami.

 Na tej ilustracji przedstawiono widok typów w ramach porównania migawek.

 ![Widok porównania migawek pokazujący typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 W oknie porównania migawek, obiekty, typy i widoki główne są takie same jak w oknie [szczegóły migawki widoku](#view-snapshot-details) . Różnica migawek zawiera te same informacje, co szczegóły migawki, z następującymi dodatkowymi wartościami:

- **Różnica w rozmiarze** Różnica między rozmiarem obiektu w bieżącej migawce i jego rozmiarem w poprzedniej migawce, bez uwzględnienia rozmiaru wszystkich obiektów, do których istnieją odwołania.

- **Różnica rozmiarów zachowanych**. Różnica między zachowanym rozmiarem obiektu w bieżącej migawce i jego rozmiarem zachowanym w poprzedniej migawce. Zachowany rozmiar obejmuje rozmiar obiektu oraz rozmiar wszystkich jego obiektów podrzędnych, które nie mają innych elementów nadrzędnych. W praktyce zachowywany rozmiar to ilość pamięci przechowywanej przez obiekt, więc w przypadku usunięcia obiektu Odbierz określoną ilość pamięci.

  Aby filtrować informacje różnicowe między migawkami, wybierz jeden z filtrów **zakresu** w górnej części widoków różnicowych.

- **Obiekty pozostałe z migawki nr \<number>**. Ten filtr pokazuje różnicę między obiektami dodanymi do sterty i usuniętymi z sterty w porównaniu z migawką bazową i poprzednią migawką. Na przykład, jeśli podsumowanie migawki pokazuje + 205/-195 w liczniku obiektów, ten filtr wyświetli dziesięć obiektów, które zostały dodane, ale nie zostały usunięte.

  > [!TIP]
  > Aby wyświetlić najbardziej przydatne informacje w tym filtrze, wykonaj kroki opisane w sekcji [izolowanie przecieku pamięci](#isolate-a-memory-leak).

- **Obiekty dodane między migawką # \<number> i \<number> #**. Ten filtr pokazuje wszystkie obiekty dodane do sterty z poprzedniej migawki.

- **Wszystkie obiekty w migawce # \<number>**. To ustawienie filtru nie odfiltruje żadnych obiektów na stercie.

  Aby wyświetlić odwołania do obiektów, które nie pasują do bieżącego filtru **zakresu** , wybierz pozycję **Pokaż niepasujące odwołania** na liście ustawienia listy ![rozwijanej&#45;Zmniejsz listę w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka. Jeśli włączysz to ustawienie, niezgodne odwołania są wyświetlane z szarym tekstem.

> [!TIP]
> Zalecamy wykonanie kroków [izolowania przecieku pamięci](#isolate-a-memory-leak) , a następnie użycie filtru obiektów pozostawionych nad **zakresem** , aby ułatwić identyfikację obiektów, które są przyczyną przecieku pamięci.

## <a name="view-objects-by-dominator"></a>Wyświetl obiekty według Dominatora
 W widokach typy i ustawienia, można wybrać, czy obiekty mają być wyświetlane w ich selektorach (jest to domyślny widok na karcie **zdominowane** ). Po wybraniu tego widoku w widoku najwyższego poziomu są wyświetlane tylko elementy, które są widoczne. (Obiekty, które są elementami podrzędnymi obiektów nieglobalnych, są ukryte w widoku najwyższego poziomu). W przypadku niektórych aplikacji można wyjaśnić, które obiekty powodują przeciek pamięci przez zmniejszenie szumu w danych.

 Aby przełączać widok obiektów według Dominatora, kliknij przycisk **zgięcie w obiektach według Dominatora** . ![Składanie obiektów w ich obiektach](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Aby uzyskać więcej informacji na temat, zobacz [Wyświetlanie szczegółów migawek](#view-snapshot-details).

## <a name="filter-data-by-identifier"></a>Filtruj dane według identyfikatora
 W widokach i typach, można odfiltrować dane przez wyszukiwanie określonych identyfikatorów. Aby wyszukać identyfikator, po prostu wpisz jego nazwę w polu tekstowym **Filtr identyfikatora** w prawym górnym rogu. Po rozpoczęciu wpisywania identyfikatory, które nie zawierają wpisanych znaków, są odfiltrowane.

 Każdy widok ma własny filtr, dlatego filtr nie jest zachowywany po przełączeniu do innego widoku.

## <a name="find-an-object-in-the-object-tree"></a>Znajdowanie obiektu w drzewie obiektów
 W widokach typy i dominuje można zobaczyć relację określonego obiektu do `Global` obiektu. Obiekty z odblokowanym dostępem do `Global` obiektu nie będą zbierane jako elementy bezużyteczne. Możesz łatwo znaleźć znany obiekt w widoku katalogów głównych bez przeszukiwania `Global` drzewa obiektów. Aby to zrobić, otwórz menu skrótów dla obiektu w obszarze obiekty lub widok typu, a następnie wybierz **Pokaż w widoku elementów głównych**.

## <a name="view-shared-object-references"></a>Wyświetl odwołania do obiektów udostępnionych
 W widokach typy i dominuj dolny panel zawiera listę odwołań do obiektów, która wyświetla odwołania udostępnione. Po wybraniu obiektu w górnym okienku Lista odwołania do obiektów wyświetla wszystkie obiekty, które wskazują na ten obiekt.

> [!NOTE]
> Odwołania cykliczne są wyświetlane przy użyciu gwiazdki (*) i informacyjnej etykietki narzędzia i nie mogą być rozwinięte. W przeciwnym razie uniemożliwi to poszukiwanie drzewa odwołań i identyfikowanie obiektów, które zachowują pamięć.

 Jeśli potrzebujesz dodatkowej pomocy w identyfikacji obiektów równoważnych, wybierz pozycję **Wyświetl identyfikatory obiektów** na liście Ustawienia listy ![rozwijanej&#45;Zmniejsz listę w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu górnego okienka. Ta opcja powoduje wyświetlenie identyfikatorów obiektów obok nazw obiektów na liście **identyfikatorów** (identyfikatory są wyświetlane we wszystkich widokach, a nie tylko na liście odwołania do obiektów). Obiekty mające ten sam identyfikator to odwołania udostępnione.

 Na poniższej ilustracji przedstawiono listę odwołań do obiektów dla wybranego elementu z wyświetlonymi identyfikatorami.

 ![Odwołania do obiektów z wyświetlanymi identyfikatorami](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Pokaż obiekty wbudowane
 Domyślnie w widokach ustawienia i typy są wyświetlane tylko obiekty utworzone w aplikacji. Pozwala to na odfiltrowanie niepotrzebnych informacji i odizolowanie problemów związanych z aplikacjami. Jednak czasami warto wyświetlić wszystkie obiekty generowane przez środowisko uruchomieniowe języka JavaScript dla aplikacji.

 Aby wyświetlić te obiekty, wybierz pozycję **Pokaż wbudowane** na liście Ustawienia listy ![rozwijanej&#45;Zmniejsz listę w analizatorze pamięci](../profiling/media/js_mem_settings.png "JS_Mem_Settings") w prawym górnym rogu okienka.

## <a name="save-diagnostic-session-files"></a>Zapisz pliki sesji diagnostycznej
 Podsumowania migawek diagnostycznych i skojarzonych z nimi widoków szczegółów są zapisywane jako. pliki *diagsession* . **Eksplorator rozwiązań** wyświetla poprzednie sesje diagnostyczne w folderze sesji diagnostycznych. W **Eksplorator rozwiązań** można otworzyć poprzednie sesje lub usunąć lub zmienić nazwy plików.

## <a name="associate-source-code-with-memory-usage-data"></a>Skojarz kod źródłowy z danymi użycia pamięci
 Aby ułatwić odizolowanie sekcji kodu zawierającej problem z pamięcią, należy użyć następujących metod:

- Poszukaj nazw klas i identyfikatorów dla elementów DOM w widokach szczegółów i różnicowych.

- Wyszukaj wartości ciągu w widokach szczegóły i różnice, które mogą być skojarzone z kodem źródłowym.

- Użyj polecenia [Znajdź obiekt w drzewie obiektów](#find-an-object-in-the-object-tree) , aby wyświetlić drzewo obiektów. Może to ułatwić zidentyfikowanie skojarzonego kodu źródłowego.

- Dodawanie poleceń analizatora pamięci do kodu źródłowego.

  W kodzie źródłowym można używać następujących poleceń:

- `console.takeHeapSnapshot` wykonuje migawkę sterty, która pojawia się w analizatorze pamięci JavaScript. To polecenie jest jednym z [poleceń konsoli JavaScript](../debugger/javascript-console-commands.md).

- `performance.mark` Ustawia znacznik użytkownika (odwrócony trójkąt), który pojawia się na osi czasu grafu pamięci w widoku Podsumowanie, gdy aplikacja jest uruchomiona. To polecenie przyjmuje jeden argument ciągu, który opisuje zdarzenie i pojawia się jako etykietka narzędzia w grafie pamięci. Ten opis nie może zawierać więcej niż 100 znaków.

> [!TIP]
> Służy `console.takeHeapSnapshot` do przyspieszenia analizy w przypadku powtarzających się scenariuszy użycia pamięci.

 Te polecenia zgłaszają wyjątek, jeśli dodasz je do aplikacji i uruchomisz aplikację poza analizatorem pamięci języka JavaScript. Można jednak sprawdzić, czy polecenia istnieją przed ich użyciem. (Polecenia nie istnieją wcześniej w fazie uruchamiania sesji). Aby sprawdzić, czy można bezpiecznie wywołać `takeHeapSnapshot` , użyj tego kodu:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Aby sprawdzić, czy można bezpiecznie wywołać `performance.mark` , użyj tego kodu:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Oto wykres pamięci z kilkoma znakami użytkownika i etykietki narzędzia dla aktualnie wybranego znacznika użytkownika, dla którego `performance.mark` argument ciągu jest ustawiony na "dane wygenerowane":

 ![Używanie znacznika profilu](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>Porady dotyczące identyfikowania problemów z pamięcią

- Postępuj zgodnie z przepływem pracy opisanym w artykule [izolowanie przecieku pamięci](#isolate-a-memory-leak) i Użyj **obiektów \<number> z lewej strony z migawki #** Filter w widoku diff, aby zidentyfikować podejrzane sugestie dotyczące przecieków pamięci.

- Użyj [Znajdź obiekt w drzewie obiektów,](#find-an-object-in-the-object-tree) aby zobaczyć, gdzie istnieje odwołanie do obiektu w hierarchii pamięci. Widok katalogów głównych pokazuje, jak obiekt jest odblokowany w obiekcie globalnym, co uniemożliwi jego odtworzenie elementów bezużytecznych.

- Gdy trudno jest zidentyfikować przyczynę problemu z pamięcią, Użyj różnych widoków (takich jak obiekty i typy), aby wyszukać commonalities, szczególnie w celu ułatwienia zidentyfikowania jednego obiektu (lub kilku obiektów), które mogą zawierać odwołania do wielu innych obiektów, które są wyświetlane w widoku.

- Poszukaj obiektów, które są przechowywane w pamięci przypadkowo po przejściu do nowej strony, która jest często przyczyną problemów z pamięcią. Na przykład:

  - Nieprawidłowe użycie [adresu URL. Funkcja CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) może być przyczyną tego problemu.

  - Niektóre obiekty mogą zawierać `dispose` metodę i zalecenia do użycia. Na przykład, należy wywołać `dispose` na [WinJS. Binding. list](/previous-versions/windows/apps/hh700774\(v\=win.10\)) , jeśli wywołasz `createFiltered` metodę listy, a następnie opuścisz stronę.

  - Może być konieczne usunięcie co najmniej jednego detektora zdarzeń. Aby uzyskać więcej informacji, zobacz [Wyświetlanie odbiorników zdarzeń dom](../debugger/quickstart-debug-html-and-css.md).

- Obejrzyj tę ostatnią część [tego filmu wideo](https://channel9.msdn.com/Events/Build/2013/3-316) z konferencji Build 2013 dotyczącej analizatora pamięci JavaScript.

- Odczytuj [Zarządzanie pamięcią w aplikacjach platformy UWP](/archive/msdn-magazine/2012/windows-8-special-issue/javascript-managing-memory-in-windows-store-apps).

- Należy rozważyć tymczasowe zmodyfikowanie kodu w celu odizolowania problemów. Na przykład możesz chcieć:

  - Użyj poleceń analizatora pamięci `console.takeSnapshot` i `performance.mark` . (Zobacz [Skojarz kod źródłowy z danymi użycia pamięci](#associate-source-code-with-memory-usage-data)).

    Za pomocą tych poleceń można wyizolować problemy, których nie można izolować przez ręczne przetworzenie migawki sterty.

  - Utwórz obiekt testowy i śledź go w widokach analizatora pamięci języka JavaScript, takich jak widok typów. Na przykład można dołączyć bardzo duży obiekt do innego obiektu, aby sprawdzić, czy określony obiekt lub element został pobrany jako bezużyteczny.