---
title: Używanie punktów przerwania w debugerze | Microsoft Docs
description: Dowiedz się więcej o punktach przerwania, jednej z najważniejszych technik debugowania. Ten artykuł obejmuje akcje punktu przerwania, punkty śledzenia, warunki i wiele innych.
ms.custom: SEO-VS-2020
ms.date: 06/30/2020
ms.topic: how-to
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0865c71d2893203ca3af925da1d76946d882c4c4
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798586"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Używanie punktów przerwania w Visual Studio debugowania

Punkty przerwania to jedna z najważniejszych technik debugowania w przyborniku dewelopera. Punkty przerwania ustawia się wszędzie tam, gdzie chcesz wstrzymać wykonywanie debugera. Na przykład możesz zobaczyć stan zmiennych kodu lub sprawdzić stos wywołań w określonym punkcie przerwania.  Jeśli próbujesz rozwiązać ostrzeżenie lub problem podczas korzystania z punktów przerwania, zobacz Rozwiązywanie problemów z punktami przerwania w [Visual Studio debugerze](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Jeśli znasz zadanie lub problem, który próbujesz rozwiązać, ale musisz wiedzieć, jakiego rodzaju punktu przerwania użyć, zobacz Często zadawane pytania — znajdowanie funkcji [debugowania](../debugger/find-your-debugging-task.yml#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Ustawianie punktów przerwania w kodzie źródłowym

Punkt przerwania można ustawić w dowolnym wierszu kodu wykonywalnego. Na przykład w poniższym kodzie języka C# można ustawić punkt przerwania w wierszu kodu za pomocą przypisania zmiennej ( ), pętli lub dowolnego kodu `int testInt = 1` `for` wewnątrz `for` pętli. Nie można ustawić punktu przerwania dla sygnatur metod, deklaracji dla przestrzeni nazw lub klasy ani deklaracji zmiennych, jeśli nie ma przypisania ani metody getter/setter.

Aby ustawić punkt przerwania w kodzie źródłowym, kliknij lewy margines obok wiersza kodu. Możesz również wybrać wiersz i nacisnąć klawisz **F9,** wybrać **pozycję Debuguj** Przełącz punkt przerwania lub kliknąć prawym przyciskiem myszy i wybrać  >  pozycję **Wstaw**  >  **punkt** przerwania. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie.

W przypadku większości języków, w tym języka C#, punkty przerwania i bieżące wiersze wykonywania są automatycznie wyróżniane. W przypadku kodu W języku C++ można włączyć wyróżnianie punktów przerwania i bieżących wierszy, wybierając pozycję Narzędzia **(lub** Debugowanie **)**> **Opcje** debugowania Wyróżnij cały wiersz źródłowy dla punktów przerwania i bieżącej instrukcji  >    >   **(tylko C++).**

![Ustawianie punktu przerwania](../debugger/media/basicbreakpoint.png "Podstawowy punkt przerwania")

Podczas debugowania wykonywanie jest wstrzymywane w punkcie przerwania przed wykonaniem kodu w tym wierszu. Symbol punktu przerwania pokazuje żółtą strzałkę.

W punkcie przerwania w poniższym przykładzie wartość nadal `testInt` wynosi 1. Dlatego wartość nie zmieniła się od momentu zainicjowania zmiennej (ustawionej na wartość 1), ponieważ instrukcja w kolorze żółtym nie została jeszcze wykonana.

![Zatrzymano wykonywanie punktu przerwania](../debugger/media/breakpointexecution.png "Wykonywanie punktu przerwania")

Gdy debuger zatrzyma się w punkcie przerwania, możesz przyjrzeć się [](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) bieżącemu stanowi aplikacji, w tym wartościom zmiennych i [stosowi wywołań](../debugger/how-to-use-the-call-stack-window.md).

Oto kilka ogólnych instrukcji dotyczących pracy z punktami przerwania.

- Punkt przerwania jest przełącznikiem. Możesz go kliknąć, nacisnąć **klawisz F9** lub użyć **punktu** przerwania przełącznika debugowania, aby go usunąć lub  >   ponownie włączyć.

- Aby wyłączyć punkt przerwania bez usuwania go, umieść na nim wskaźnik myszy lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Wyłącz punkt przerwania.** Wyłączone punkty przerwania są wyświetlane jako puste kropki na lewym marginesie lub **w oknie Punkty przerwania.** Aby ponownie włączyć punkt przerwania, umieść na nim wskaźnik myszy lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Włącz punkt przerwania.**

- Ustaw warunki i akcje, dodaj i edytuj etykiety lub wyeksportuj punkt przerwania, klikając go prawym przyciskiem myszy i wybierając odpowiednie polecenie lub umieszczając na nim wskaźnik myszy i wybierając **ikonę** Ustawienia.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akcje punktu przerwania i punkty śledzenia

Punkt *śledzenia* to punkt przerwania, który drukuje komunikat w **oknie Dane** wyjściowe. Punkt śledzenia może działać jak tymczasowa instrukcja śledzenia w języku programowania i nie wstrzymuje wykonywania kodu. Punkt śledzenia można utworzyć, ustawiając specjalną akcję w **oknie Ustawienia punktu** przerwania. Aby uzyskać szczegółowe instrukcje, [zobacz Używanie punktów śledzenia w Visual Studio debugowania.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Warunki punktu przerwania

Możesz kontrolować, kiedy i gdzie jest wykonywany punkt przerwania, ustawiając warunki. Warunek może być dowolnym prawidłowym wyrażeniem rozpoznawczym przez debuger. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń, zobacz [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).

**Aby ustawić warunek punktu przerwania:**

1. Kliknij prawym przyciskiem myszy symbol punktu przerwania i wybierz pozycję **Warunki** (lub naciśnij **klawisze Alt**  +  **F9,** **C**). Możesz też zatrzymać wskaźnik myszy na symbolu punktu przerwania, wybrać **ikonę Ustawienia,** a następnie wybrać pozycję **Warunki** w **oknie Ustawienia punktu przerwania.**

   Możesz również ustawić warunki w oknie **Punkty** przerwania, klikając prawym przyciskiem myszy punkt przerwania i wybierając pozycję **Ustawienia,** a następnie wybierając **pozycję Warunki.**

   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Na liście rozwijanej wybierz pozycję **Wyrażenie warunkowe,** **Liczba trafień** lub **Filtruj** i odpowiednio ustaw wartość.

3. Wybierz **pozycję Zamknij** lub naciśnij klawisz **Ctrl** + **Enter,** aby zamknąć **okno Ustawienia punktu przerwania.** Lub w oknie **Punkty przerwania** wybierz przycisk **OK,** aby zamknąć okno dialogowe.

Punkty przerwania z ustawionymi warunkami są wyświetlane z symbolem w kodzie źródłowym i **+** **oknach punktów przerwania.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Tworzenie wyrażenia warunkowego

Po wybraniu opcji **Wyrażenie warunkowe** możesz wybrać jeden z dwóch warunków: **Ma wartość true** lub Gdy **zmieniono wartość**. Wybierz **opcję Ma wartość true,** aby  przerwać, gdy wyrażenie jest spełnione, lub wartość Po zmianie, aby przerwać, gdy wartość wyrażenia została zmieniona.

W poniższym przykładzie punkt przerwania jest trafiony tylko wtedy, gdy wartość `testInt` to **4:**

![Warunek punktu przerwania ma wartość true](../debugger/media/breakpointconditionistrue.png "Punkt przerwania ma wartość true")

W poniższym przykładzie punkt przerwania jest trafiony tylko wtedy, gdy wartość zmienia `testInt` się:

![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "Punkt przerwania po zmianie")

Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania z prawidłową składnią, ale nieprawidłową semantyką, przy pierwszym trafieniu punktu przerwania zostanie wyświetlony komunikat ostrzegawczy. W obu przypadkach debuger przerywa działania, gdy trafia do nieprawidłowego punktu przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy warunek jest prawidłowy i ma wartość `false` .

>[!NOTE]
> W przypadku **pola** Po zmianie debuger nie uznaje pierwszej oceny warunku za zmianę, więc nie trafia do punktu przerwania przy pierwszej ocenie.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Używanie identyfikatorów obiektów w wyrażeniach warunkowych (tylko C# i F#)

 Istnieją sytuacje, w których chcesz obserwować zachowanie określonego obiektu. Na przykład możesz dowiedzieć się, dlaczego obiekt został wstawiony do kolekcji więcej niż raz. W językach C# i F# można tworzyć identyfikatory obiektów dla określonych wystąpień typów od referencyjnych [i](/dotnet/csharp/language-reference/keywords/reference-types)używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzony z obiektem .

**Aby utworzyć identyfikator obiektu:**

1. Ustaw punkt przerwania w kodzie w pewnym miejscu po utworzeniu obiektu.

2. Rozpocznij debugowanie i po wstrzymaniu wykonywania w punkcie przerwania wybierz pozycję **Debuguj** lokalne systemy Windows (lub naciśnij klawisze  >    >   **Ctrl** Alt V, L ), aby otworzyć  +    +   **okno Locals (Lokalne).** 

   Znajdź określone wystąpienie obiektu w oknie **Ustawienia lokalne,** kliknij je prawym przyciskiem myszy, a następnie wybierz **pozycję Make Object ID (Określ identyfikator obiektu).**

   W oknie **$** **Locals (Lokalne)** powinien zostać wyświetlony znak plus a number. Jest to identyfikator obiektu.

3. Dodaj nowy punkt przerwania w punkcie, który chcesz zbadać. na przykład gdy obiekt ma zostać dodany do kolekcji. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **Warunki.**

4. Użyj identyfikatora obiektu w polu **Wyrażenie warunkowe.** Jeśli na przykład zmienna jest obiektem, który ma zostać dodany do kolekcji, wybierz pozycję Jest true i wpisz `item` **element == $ \<n>**, gdzie to numer identyfikatora  \<n> obiektu.

   Wykonanie spowoduje przerwę w punkcie, gdy ten obiekt ma zostać dodany do kolekcji.

   Aby usunąć identyfikator obiektu, kliknij prawym przyciskiem myszy zmienną w oknie **Zmienne** lokalne i wybierz **polecenie Usuń identyfikator obiektu**.

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania i nie uniemożliwiają odśmiecania pamięci obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

### <a name="set-a-hit-count-condition"></a>Ustawianie warunku liczby trafień

Jeśli podejrzewasz, że pętla w kodzie zaczyna nieprawidłowo zachowywać się po określonej liczbie iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonywanie po tej liczbie trafień, zamiast wielokrotnie naciskać **klawisz F5** w celu osiągnięcia tej iteracji.

W **obszarze** Warunki w **oknie Ustawienia punktu** przerwania wybierz pozycję **Liczba** trafień, a następnie określ liczbę iteracji. W poniższym przykładzie punkt przerwania jest ustawiony na trafienie w każdej innej iteracji:

![Liczba trafień punktów przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Ustawianie warunku filtru

Można ograniczyć punkt przerwania do działania tylko na określonych urządzeniach lub w określonych procesach i wątkach.

W **obszarze** Warunki w **oknie Ustawienia punktu** przerwania wybierz pozycję **Filtruj,** a następnie wprowadź co najmniej jedno z następujących wyrażeń:

- MachineName = "name"
- ProcessId = wartość
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Ujmij wartości ciągu w cudzysłów podwójny. Klauzule można łączyć przy `&` użyciu (AND), `||` (OR), `!` (NOT) i nawiasów.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Ustawianie punktów przerwania funkcji

Wykonywanie można przerwać, gdy wywoływana jest funkcja. Jest to przydatne na przykład wtedy, gdy znasz nazwę funkcji, ale nie jej lokalizację. Jest to również przydatne, jeśli masz funkcje o tej samej nazwie i chcesz je wszystkie przerwać (na przykład przeciążone funkcje lub funkcje w różnych projektach).

**Aby ustawić punkt przerwania funkcji:**

1. Wybierz **pozycję**  >  **Debuguj nowy punkt** przerwania funkcji  >  **punktu** przerwania lub naciśnij klawisze **Ctrl**  +  **K,** **B**.

   Możesz również wybrać pozycję **Nowy**  >  **punkt przerwania funkcji** w **oknie Punkty przerwania.**

1. W **oknie dialogowym Nowy punkt** przerwania funkcji wprowadź nazwę funkcji w **polu Nazwa** funkcji.

   Aby zawęzić specyfikację funkcji:

   - Użyj w pełni kwalifikowanej nazwy funkcji.

     Przykład:  `Namespace1.ClassX.MethodA()`

   - Dodaj typy parametrów przeciążonych funkcji.

     Przykład:  `MethodA(int, string)`

   - Użyj symbolu "!", aby określić moduł.

     Przykład: `App1.dll!MethodA`

   - Użyj operatora kontekstu w natywnym języku C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Przykład: `{MethodA, , App1.dll}+2`

1. Z **listy rozwijanej** Język wybierz język funkcji.

1. Wybierz przycisk **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Ustawianie punktu przerwania funkcji przy użyciu adresu pamięci (tylko natywny język C++)
 Za pomocą adresu obiektu można ustawić punkt przerwania funkcji w metodzie wywoływanej przez określone wystąpienie klasy.  Na przykład, mając adresowalny obiekt typu , można ustawić punkt przerwania funkcji dla `my_class` `my_method` metody, która wywołuje to wystąpienie.

1. Ustaw punkt przerwania gdzieś po wystąpieniu klasy.

2. Znajdź adres wystąpienia (na przykład `0xcccccccc` ).

3. Wybierz **pozycję**  >  **Debuguj nowy punkt** przerwania funkcji  >  **punktu** przerwania lub naciśnij klawisze **Ctrl**  +  **K,** **B**.

4. Dodaj następujący kod do **pola Nazwa funkcji** i wybierz pozycję Język **C++.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Ustawianie punktów przerwania danych (program .NET Core 3.0 lub wyższy)

Punkty przerwania danych przerwać wykonywanie po zmianie właściwości określonego obiektu.

**Aby ustawić punkt przerwania danych**

1. W projekcie .NET Core rozpocznij debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania.

2. W **oknie Automatyczne** elementy  , **Obejrzyj** lub Ustawienia lokalne  kliknij prawym przyciskiem myszy właściwość i wybierz polecenie Przerwij, gdy wartość zmieni się w menu kontekstowym.

    ![Zarządzany punkt przerwania danych](../debugger/media/managed-data-breakpoint.png "Zarządzany punkt przerwania danych")

Punkty przerwania danych na platformie .NET Core nie będą działać w przypadku:

- Właściwości, których nie można rozwinąć w etykietce narzędzia, ustawieniach lokalnych, automatycznych lub okno wyrażeń kontrolnych
- Zmienne statyczne
- Klasy z atrybutem DebuggerTypeProxy
- Pola wewnątrz struktur

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Ustawianie punktów przerwania danych (tylko natywny język C++)

 Punkty przerwania danych przerwiją wykonywanie, gdy wartość przechowywana pod określonym adresem pamięci się zmieni. Jeśli wartość jest odczytywana, ale nie zostanie zmieniona, wykonanie nie spowoduje przerwania.

**Aby ustawić punkt przerwania danych:**

1. W projekcie języka C++ rozpocznij debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania. W menu **Debug (Debugowanie)** wybierz pozycję New **Breakpoint**  >  **Data Breakpoint (Nowy** punkt przerwania danych przerwania).

    Możesz również wybrać pozycję **Nowy** punkt przerwania danych w oknie Punkty przerwania lub kliknąć prawym przyciskiem myszy element w oknie Automatyczne, Czujka lub Ustawienia lokalne i wybrać polecenie Przerwij, gdy wartość zmieni się w  >   menu kontekstowym.     

2. W polu **Adres** wpisz adres pamięci lub wyrażenie, które oblicza jako adres pamięci. Na przykład wpisz , `&avar` aby przerwać, gdy zawartość zmiennej zmieni `avar` się.

3. Na liście **rozwijanej Liczba bajtów** wybierz liczbę bajtów, które ma obserwować debuger. Jeśli na przykład wybierzesz **wartość 4,** debuger będzie obserwować cztery bajty zaczynające się od i przerwać, jeśli którykolwiek z tych bajtów `&avar` zmieni wartość.

Punkty przerwania danych nie działają w następujących warunkach:
- Proces, który nie jest debugowany, zapisuje w lokalizacji pamięci.
- Lokalizacja pamięci jest współdzielona między co najmniej dwoma procesami.
- Lokalizacja pamięci jest aktualizowana w jądrze. Jeśli na przykład pamięć zostanie przekazana do 32-bitowej funkcji systemu Windows, pamięć zostanie zaktualizowana z trybu jądra, więc debuger nie przerwie działania `ReadFile` aktualizacji.
- Gdzie wyrażenie wyrażenia chłoniaka jest większe niż 4 bajty na sprzęcie 32-bitowym i 8 bajtów na sprzęcie 64-bitowym. Jest to ograniczenie architektury x86.

> [!NOTE]
> - Punkty przerwania danych zależą od określonych adresów pamięci. Adres zmiennej zmienia się z jednej sesji debugowania na następną, więc punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.
>
> - Jeśli ustawisz punkt przerwania danych dla zmiennej lokalnej, punkt przerwania pozostanie włączony po zakończeniu działania funkcji, ale adres pamięci nie będzie już miał zastosowania, więc zachowanie punktu przerwania będzie nieprzewidywalne. Jeśli ustawisz punkt przerwania danych dla zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem działania funkcji.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Zarządzanie punktami przerwania w oknie Punkty przerwania

 Okno Punkty przerwania **umożliwia** wyświetlanie wszystkich punktów przerwania w rozwiązaniu i zarządzanie nimi. Ta scentralizowana lokalizacja jest szczególnie przydatna w dużych rozwiązaniach lub w złożonych scenariuszach debugowania, w których punkty przerwania mają krytyczne znaczenie.

W **oknie Punkty przerwania** można wyszukiwać, sortować, filtrować, włączać/wyłączać lub usuwać punkty przerwania. Można również ustawić warunki i akcje lub dodać nową funkcję lub punkt przerwania danych.

Aby otworzyć okno **Punkty przerwania,** wybierz pozycję **Debuguj** punkty przerwania systemu  >  **Windows**  >  lub naciśnij **klawisze Ctrl** + **Alt** + **B**.

![Okno punktów przerwania](../debugger/media/breakpointswindow.png "Okno punktów przerwania")

Aby wybrać kolumny do wyświetlenia w oknie **Punkty przerwania,** wybierz pozycję **Pokaż kolumny**. Wybierz nagłówek kolumny, aby posortować listę punktów przerwania według tej kolumny.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etykiety punktów przerwania
Za pomocą etykiet można sortować i filtrować listę punktów przerwania w **oknie Punkty przerwania.**

1. Aby dodać etykietę do punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub oknie **Punkty** przerwania, a następnie wybierz pozycję **Edytuj etykiety**. Dodaj nową etykietę lub wybierz istniejącą, a następnie wybierz przycisk **OK.**
2. Posortuj listę punktów przerwania w oknie **Punkty** przerwania, wybierając nagłówki **Etykiety,** **Warunki** lub inne kolumny. Możesz wybrać kolumny do wyświetlenia, wybierając pozycję **Pokaż kolumny** na pasku narzędzi.

### <a name="export-and-import-breakpoints"></a>Eksportowanie i importowanie punktów przerwania
 Aby zapisać lub udostępnić stan i lokalizację punktów przerwania, możesz je wyeksportować lub zaimportować.

- Aby wyeksportować pojedynczy punkt przerwania do pliku XML, kliknij prawym  przyciskiem myszy punkt przerwania  w oknie kodu źródłowego lub punktów przerwania, a następnie wybierz pozycję Eksportuj lub **Eksportuj wybraną pozycję**. Wybierz lokalizację eksportu, a następnie wybierz pozycję **Zapisz.** Domyślna lokalizacja to folder rozwiązania.
- Aby wyeksportować kilka punktów  przerwania, w oknie Punkty przerwania zaznacz pola obok punktów przerwania lub wprowadź kryteria wyszukiwania w **polu** Wyszukaj. Wybierz **ikonę Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami** wyszukiwania i zapisz plik.
- Aby wyeksportować wszystkie punkty przerwania, usuń zaznaczenie wszystkich pól i **pozostaw pole** Wyszukaj puste. Wybierz **ikonę Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami** wyszukiwania i zapisz plik.
- Aby zaimportować punkty przerwania, w oknie  Punkty przerwania wybierz ikonę Importuj punkty przerwania z pliku, przejdź do lokalizacji pliku XML i wybierz pozycję **Otwórz**. 

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Ustawianie punktów przerwania z okien debugera

Punkty przerwania można również ustawiać w oknach debugera **stosu wywołań** i dezbucji. 

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Ustawianie punktu przerwania w oknie stosu wywołań

 Aby przerwać działanie instrukcji lub wiersza, do których wraca funkcja wywołująca, możesz ustawić punkt przerwania w **oknie stosu** wywołań.

**Aby ustawić punkt przerwania w oknie stosu wywołań:**

1. Aby otworzyć okno **stos wywołań,** musisz być wstrzymany podczas debugowania. Wybierz **pozycję**  >  **Debuguj stos** wywołań systemu Windows lub naciśnij klawisze  >   **Ctrl** + **Alt** + **C.**

2. W **oknie Stos wywołań** kliknij prawym przyciskiem myszy funkcję wywołującą i wybierz polecenie **Wstaw** punkt przerwania punktu przerwania  >  lub naciśnij **klawisz F9**.

   Symbol punktu przerwania jest wyświetlany obok nazwy wywołania funkcji na lewym marginesie stosu wywołań.

Punkt przerwania stosu wywołań  jest wyświetlany w oknie Punkty przerwania jako adres z lokalizacją pamięci odpowiadającą następnej instrukcji wykonywalnego w funkcji.

Debuger przerywa instrukcje .

Aby uzyskać więcej informacji na temat stosu wywołań, [zobacz Jak używać okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz Map methods on the call stack while debugging (Metody mapowania [na stosie wywołań podczas debugowania).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ustawianie punktu przerwania w oknie Dezmisja

1. Aby otworzyć okno **dezasembletu,** musisz zostać wstrzymany podczas debugowania. Wybierz **pozycję**  >  **Debuguj**  >  **dekompełtę** systemu Windows lub naciśnij **klawisze Ctrl** + **Alt** + **D**.

2. W **oknie** Dekompełtowanie kliknij lewy margines instrukcji, którą chcesz przerwać. Możesz również go zaznaczyć i nacisnąć **klawisz F9** lub kliknąć prawym przyciskiem myszy i wybrać pozycję **Wstaw** punkt przerwania  >  **punktu przerwania.**

## <a name="see-also"></a>Zobacz też

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Pisanie lepszego kodu w języku C# przy użyciu Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Rozwiązywanie problemów z punktami przerwania w Visual Studio debugowania](../debugger/troubleshooting-breakpoints.md)
