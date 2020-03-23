---
title: Używanie punktów przerwania w debugerze | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302036"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Używanie punktów przerwania w debugerze programu Visual Studio

Punkty przerwania są jedną z najważniejszych technik debugowania w przyborniku dewelopera. Można ustawić punkty przerwania wszędzie tam, gdzie chcesz wstrzymać wykonywanie debugera. Na przykład można wyświetlić stan zmiennych kodu lub spojrzeć na stos wywołań w określonym punkcie przerwania.  Jeśli próbujesz rozwiązać ostrzeżenie lub problem podczas korzystania z punktów przerwania, zobacz [Rozwiązywanie problemów z punktami przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Jeśli znasz zadanie lub problem, który próbujesz rozwiązać, ale musisz wiedzieć, jakiego rodzaju punktu przerwania użyć, zobacz [Znajdowanie zadania debugowania](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Ustawianie punktów przerwania w kodzie źródłowym

Punkt przerwania można ustawić w dowolnym wierszu kodu wykonywalnego. Na przykład w poniższym kodzie Języka C# można ustawić punkt `for` przerwania na deklaracji `for` zmiennej, pętli lub dowolnego kodu wewnątrz pętli. Nie można ustawić punktu przerwania w obszarze nazw lub deklaracji klas lub na podpis metody.

Aby ustawić punkt przerwania w kodzie źródłowym, kliknij margines po lewej stronie obok wiersza kodu. Można również zaznaczyć linię i nacisnąć **klawisz F9**, wybrać **opcję Debug** > **Toggle Breakpoint**lub kliknąć prawym przyciskiem myszy i wybrać polecenie **Breakpoint** > **Insert breakpoint**. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie.

Dla większości języków, w tym C#, punkt przerwania i bieżące wiersze wykonywania są automatycznie podświetlone. W przypadku kodu Języka C++ można włączyć wyróżnianie punktu przerwania i bieżących wierszy, wybierając **polecenie Narzędzia** (lub **Debugowanie)**> **Opcje** > **Debugowania** >  **Wyróżnij cały wiersz źródłowy dla punktów przerwania i bieżącej instrukcji (tylko C++).**

![Ustawianie punktu przerwania](../debugger/media/basicbreakpoint.png "Podstawowy punkt przerwania")

Podczas debugowania, wykonanie wstrzymuje się w punkcie przerwania, przed kod w tym wierszu jest wykonywany. Symbol punktu przerwania pokazuje żółtą strzałkę.

W punkcie przerwania w poniższym `testInt` przykładzie wartość jest nadal 1. Tak więc wartość nie zmieniła się od czasu zainicjowania zmiennej (ustawionej na wartość 1), ponieważ instrukcja w kolorze żółtym nie została jeszcze wykonana.

![Przerwano wykonywanie punktu przerwania](../debugger/media/breakpointexecution.png "Wykonanie punktu przerwania")

Gdy debuger zatrzymuje się w punkcie przerwania, można spojrzeć na bieżący stan aplikacji, w tym [wartości zmiennych](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) i [stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

Oto kilka ogólnych instrukcji dotyczących pracy z punktami przerwania.

- Punkt przerwania jest przełącznikiem. Można go kliknąć, nacisnąć klawisz **F9**lub użyć **funkcji Debug** > **Toggle Breakpoint,** aby go usunąć lub ponownie wstawić.

- Aby wyłączyć punkt przerwania bez jego usuwania, umieść go na nim lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Wyłącz punkt przerwania**. Wyłączone punkty przerwania są wyświetlane jako puste kropki na lewym marginesie lub w oknie **Punkty przerwania.** Aby ponownie włączyć punkt przerwania, umieść go kursorem myszy na nim lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Włącz punkt przerwania**.

- Ustaw warunki i akcje, dodaj i edytuj etykiety lub eksportuj punkt przerwania, klikając je prawym przyciskiem myszy, zaznaczając odpowiednie polecenie lub najeżdżając na nie kursorem i wybierając ikonę **Ustawienia.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akcje punktu przerwania i punkty śledzenia

*Punkt śledzenia* jest punktem przerwania, który drukuje komunikat do okna **Dane wyjściowe.** Punkt śledzenia może działać jak tymczasowa instrukcja śledzenia w języku programowania i nie wstrzymuje wykonywania kodu. Punkt śledzenia można utworzyć, ustawiając specjalną akcję w oknie **Ustawienia punktu przerwania.** Aby uzyskać szczegółowe instrukcje, zobacz [Używanie punktów śledzenia w debugerze programu Visual Studio.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Warunki punktu przerwania

Można kontrolować, kiedy i gdzie punkt przerwania jest wykonywany przez ustawienie warunków. Warunkiem może być dowolne prawidłowe wyrażenie rozpoznawane przez debuger. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń, zobacz [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).

**Aby ustawić warunek punktu przerwania:**

1. Kliknij prawym przyciskiem myszy symbol punktu przerwania i wybierz pozycję **Warunki**. Możesz też najechać kursorem na symbol punktu przerwania, zaznacz ikonę **Ustawienia,** a następnie wybierz pozycję **Warunki** w oknie **Ustawienia punktu przerwania.**

   Warunki można również ustawić w oknie **Punkty przerwania,** klikając prawym przyciskiem myszy punkt przerwania i wybierając **pozycję Ustawienia,** a następnie wybierając pozycję **Warunki**.

   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "Rozłamywanie")

2. Z listy rozwijanej wybierz opcję **Wyrażenie warunkowe**, **Liczba trafień**lub **Filtr**i odpowiednio ustaw wartość.

3. Wybierz **pozycję Zamknij** lub naciśnij klawisz **Ctrl**+**Enter,** aby zamknąć okno **Ustawienia punktu przerwania.** Lub z okna **Punkty przerwania** wybierz przycisk **OK,** aby zamknąć okno dialogowe.

Punkty przerwania z ustawionymi **+** warunkami są wyświetlane z symbolem w kodzie źródłowym i **oknach punktów przerwania.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Tworzenie wyrażenia warunkowego

Po **wybraniu opcji Wyrażenie warunkowe**można wybrać jeden z dwóch warunków: **Jest true** lub **Po zmianie**. Wybierz **opcję Jest true** do przerwania, gdy wyrażenie jest spełnione, lub Po **zmianie** na przerwanie, gdy wartość wyrażenia została zmieniona.

W poniższym przykładzie punkt przerwania jest `testInt` trafiony tylko wtedy, gdy wartość wynosi **4:**

![Warunek punktu przerwania jest spełniony](../debugger/media/breakpointconditionistrue.png "Punkt przerwania jest true")

W poniższym przykładzie punkt przerwania jest `testInt` trafiony tylko wtedy, gdy wartość zmian:

![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "Punkt przerwania po zmianie")

Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, pojawi się komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania z prawidłową składnią, ale nieprawidłową semantyką, komunikat ostrzegawczy pojawi się przy pierwszym trafieniu punktu przerwania. W obu przypadkach debuger przerwy, gdy trafi nieprawidłowy punkt przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy `false`warunek jest prawidłowy i ocenia .

>[!NOTE]
>Zachowanie pola **When changed** różni się w przypadku różnych języków programowania.
>- Dla kodu macierzystego debuger nie bierze pod uwagę pierwszej oceny warunku do zmiany, więc nie trafić punkt przerwania w pierwszej oceny.
>- Dla kodu zarządzanego debuger uderza punkt przerwania w pierwszej ocenie po **wybraniu po wybraniu zmiany.**

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Używanie identyfikatorów obiektów w wyrażeniach warunkowych (tylko w językach C# i F#)

 Istnieją chwile, kiedy chcesz obserwować zachowanie określonego obiektu. Na przykład można dowiedzieć się, dlaczego obiekt został wstawiony do kolekcji więcej niż jeden raz. W językach C# i F#można tworzyć identyfikatory obiektów dla określonych wystąpień [typów odwołań](/dotnet/csharp/language-reference/keywords/reference-types)i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania wspólnego środowiska wykonawczego języka (CLR) i skojarzony z obiektem.

**Aby utworzyć identyfikator obiektu:**

1. Ustaw punkt przerwania w kodzie w pewnym miejscu po utworzeniu obiektu.

2. Rozpocznij debugowanie, a gdy wykonanie wstrzymuje się w punkcie przerwania, wybierz **debugowanie** > **lokalnych okien** > **lokalnych** lub **Alt**+**4,** aby otworzyć okno **zmiennych lokalnych.**

   Znajdź wystąpienie określonego obiektu w oknie **Zmiennoukalistan,** kliknij je prawym przyciskiem myszy i wybierz polecenie **Make Object ID**.

   W oknie **$** **Locals** powinien zostać wyświetlony numer plus. Jest to identyfikator obiektu.

3. Dodaj nowy punkt przerwania w punkcie, który chcesz zbadać; na przykład, gdy obiekt ma zostać dodany do kolekcji. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **Warunki**.

4. Użyj identyfikatora obiektu w polu **Wyrażenie warunkowe.** Na przykład, jeśli `item` zmienna jest obiektem, który ma zostać dodany do kolekcji, wybierz **opcję Jest true** i element typu **== $\<n>**, gdzie \<n> jest numerem identyfikatora obiektu.

   Wykonanie zostanie przerwane w momencie, gdy ten obiekt ma zostać dodany do kolekcji.

   Aby usunąć identyfikator obiektu, kliknij ją prawym przyciskiem myszy w oknie **Zmienne lokalne** i wybierz polecenie **Usuń identyfikator obiektu**.

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania i nie uniemożliwiają śmietnika obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

### <a name="set-a-hit-count-condition"></a>Ustawianie warunku liczby trafień

Jeśli podejrzewasz, że pętla w kodzie zaczyna się niewłaściwie po określonej liczby iteracji, można ustawić punkt przerwania, aby zatrzymać wykonanie po tej liczbie trafień, zamiast wielokrotnie naciskać **klawisz F5,** aby osiągnąć tę iterację.

W **obszarze Warunki** w oknie Ustawienia punktu **przerwania** wybierz pozycję **Liczba trafień**, a następnie określ liczbę iteracji. W poniższym przykładzie punkt przerwania jest ustawiony na trafienie w każdej innej iteracji:

![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "Policz y breakpointhitcount")

### <a name="set-a-filter-condition"></a>Ustawianie warunku filtru

Punkt przerwania można ograniczyć do uruchamiania tylko na określonych urządzeniach lub w określonych procesach i wątkach.

W **obszarze Warunki** w oknie Ustawienia punktu **przerwania** wybierz pozycję **Filtr**, a następnie wprowadź jedno lub więcej z następujących wyrażeń:

- Nazwa maszyny = "nazwa"
- ProcessId = wartość
- Nazwa procesu = "nazwa"
- Identyfikator wątku = wartość
- Nazwa wątku = "nazwa"

Wartości ciągów należy ująć w cudzysłowy. Można łączyć klauzule przy użyciu `&` (AND), `||` (OR), `!` (NIE) i nawiasach.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Ustawianie punktów przerwania funkcji

Można przerwać wykonywanie, gdy wywoływana jest funkcja. Jest to przydatne, na przykład, gdy znasz nazwę funkcji, ale nie jej lokalizację. Jest to również przydatne, jeśli masz funkcje o tej samej nazwie i chcesz podzielić na nich wszystkie (takie jak przeciążone funkcje lub funkcje w różnych projektach).

**Aby ustawić punkt przerwania funkcji:**

1. Wybierz **opcję Debugowanie** > nowego**punktu przerwania****funkcji** > lub naciśnij **klawisz Alt**+**F9** > **Ctrl**+**B**.

   W oknie **Punkty przerwania** można również **wybrać** > nowy**punkt przerwania funkcji.**

1. W oknie dialogowym **Nowy punkt przerwania funkcji** wprowadź nazwę funkcji w polu Nazwa **funkcji.**

   Aby zawęzić specyfikację funkcji:

   - Użyj w pełni kwalifikowanej nazwy funkcji.

     Przykład:`Namespace1.ClassX.MethodA()`

   - Dodaj typy parametrów przeciążonej funkcji.

     Przykład:`MethodA(int, string)`

   - Użyj symbolu '!', aby określić moduł.

     Przykład: `App1.dll!MethodA`

   - Użyj operatora kontekstu w natywnym języku C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Przykład: `{MethodA, , App1.dll}+2`

1. W **menu rozwijanym Język** wybierz język funkcji.

1. Kliknij przycisk **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Ustawianie punktu przerwania funkcji przy użyciu adresu pamięci (tylko natywny język C++)
 Adres obiektu służy do ustawiania punktu przerwania funkcji w metodzie wywoływanej przez określone wystąpienie klasy.  Na przykład biorąc pod uwagę `my_class`adresowalny obiekt typu, można `my_method` ustawić punkt przerwania funkcji w metodzie, którą wywołuje wystąpienie.

1. Set a breakpoint somewhere after the instance of the class is instantiated.

2. Znajdź adres wystąpienia (na przykład `0xcccccccc`).

3. Wybierz **opcję Debugowanie** > nowego**punktu przerwania****funkcji** > lub naciśnij **klawisz Alt**+**F9** > **Ctrl**+**B**.

4. Dodaj następujące elementy do pola **Nazwa funkcji** i wybierz język **C++.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Ustawianie punktów przerwania danych (.NET Core 3.0 lub nowszych)

Punkty przerwania danych przerwania wykonywania, gdy zmienia się właściwość określonego obiektu.

**Aby ustawić punkt przerwania danych**

1. W projekcie .NET Core uruchom debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania.

2. W oknie **Autos**, **Watch**lub **Locals** kliknij prawym przyciskiem myszy właściwość i wybierz polecenie **Przerwij, gdy wartość zmieni się** w menu kontekstowym.

    ![Zarządzany punkt przerwania danych](../debugger/media/managed-data-breakpoint.png "Zarządzany punkt przerwania danych")

Punkty przerwania danych w programie .NET Core nie będą działać w przypadku:

- Właściwości, które nie można rozwinąć w oknie Etykietka narzędzia, Zmienne lokalne, Auto lub Czujka
- Zmienne statyczne
- Klasy z atrybutem DebuggerTypeProxy
- Pola wewnątrz struktur

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Ustawianie punktów przerwania danych (tylko natywny język C++)

 Punkty przerwania danych przerwania wykonywania, gdy wartość przechowywana w określonym adresie pamięci zmienia. Jeśli wartość jest odczytywana, ale nie zmieniona, wykonanie nie zostanie przerwane.

**Aby ustawić punkt przerwania danych:**

1. W projekcie C++ rozpocznij debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania. W menu **Debugowanie** wybierz polecenie Nowy**punkt przerwania danych** punktu **przerwania** > 

    Można również wybrać **nowy** > **punkt przerwania danych** w oknie Punkty **przerwania** lub kliknąć prawym przyciskiem myszy element w oknie **Autos**, **Watch**lub **Locals** i wybrać opcję **Przerwij, gdy wartość zmieni się** w menu kontekstowym.

2. W polu **Adres** wpisz adres pamięci lub wyrażenie, które ocenia adres pamięci. Na przykład `&avar` wpisz, aby przerwać, `avar` gdy zawartość zmiennej zmienia.

3. W menu rozwijanym **Liczba bajtów** wybierz liczbę bajtów, które mają być obserwowane przez debugera. Na przykład, jeśli wybierzesz **4**, debuger będzie `&avar` oglądać cztery bajty, począwszy od i przerwy, jeśli którykolwiek z tych bajtów zmienić wartość.

Punkty przerwania danych nie działają w następujących warunkach:
- Proces, który nie jest debugowany zapisuje do lokalizacji pamięci.
- Lokalizacja pamięci jest współużytkowana przez co najmniej dwa procesy.
- Lokalizacja pamięci zostanie zaktualizowana w jądrze. Na przykład jeśli pamięć jest przekazywana do `ReadFile` 32-bitowej funkcji systemu Windows, pamięć zostanie zaktualizowana z trybu jądra, więc debuger nie zostanie przerwany w aktualizacji.
- Gdzie wyrażenie zegarka jest większe niż 4 bajty na sprzęcie 32-bitowym i 8 bajtów na sprzęcie 64-bitowym. Jest to ograniczenie architektury x86.

> [!NOTE]
> - Punkty przerwania danych zależą od określonych adresów pamięci. Adres zmiennej zmienia się z jednej sesji debugowania do następnej, więc punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.
>
> - Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, punkt przerwania pozostaje włączony po zakończeniu funkcji, ale adres pamięci nie ma już zastosowania, więc zachowanie punktu przerwania jest nieprzewidywalne. Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem funkcji.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Zarządzanie punktami przerwania w oknie Punkty przerwania

 Za pomocą okna **Punkty przerwania** można wyświetlić i zarządzać wszystkimi punktami przerwania w rozwiązaniu. Ta scentralizowana lokalizacja jest szczególnie przydatna w dużym rozwiązaniu lub w przypadku złożonych scenariuszy debugowania, w których punkty przerwania są krytyczne.

W oknie **Punkty przerwania** można wyszukiwać, sortować, filtrować, włączać/wyłączać lub usuwać punkty przerwania. Można również ustawić warunki i akcje lub dodać nową funkcję lub punkt przerwania danych.

Aby otworzyć okno **Punkty przerwania,** wybierz opcję **Debugowanie** > **punktów przerwania****systemu Windows** > lub naciśnij **klawisze Alt**+**F9** lub **Ctrl**+**Alt**+**B**.

![Okno punktów przerwania](../debugger/media/breakpointswindow.png "Okno punktów przerwania")

Aby zaznaczyć kolumny do wyświetlenia w oknie **Punkty przerwania,** wybierz pozycję **Pokaż kolumny**. Wybierz nagłówek kolumny, aby posortować listę punktów przerwania według tej kolumny.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Etykiety punktów przerwania
Za pomocą etykiet można sortować i filtrować listę punktów przerwania w oknie **Punkty przerwania.**

1. Aby dodać etykietę do punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub w oknie **Punkty przerwania,** a następnie wybierz polecenie **Edytuj etykiety**. Dodaj nową etykietę lub wybierz istniejącą, a następnie wybierz przycisk **OK**.
2. Sortuj listę punktów przerwania w oknie **Punkty przerwania,** zaznaczając **nagłówki Etykiety,** **Warunki**lub inne nagłówki kolumn. Kolumny do wyświetlenia można wybrać, zaznaczając **pozycję Pokaż kolumny** na pasku narzędzi.

### <a name="export-and-import-breakpoints"></a>Eksportowanie i importowanie punktów przerwania
 Aby zapisać lub udostępnić stan i lokalizację punktów przerwania, można je wyeksportować lub zaimportować.

- Aby wyeksportować pojedynczy punkt przerwania do pliku XML, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub oknie **Punkty przerwania,** a następnie wybierz polecenie **Eksportuj** lub **Eksportuj zaznaczone**. Wybierz lokalizację eksportu, a następnie wybierz pozycję **Zapisz**. Domyślną lokalizacją jest folder rozwiązania.
- Aby wyeksportować kilka punktów przerwania, w oknie **Punkty przerwania** zaznacz pola obok punktów przerwania lub wprowadź kryteria wyszukiwania w polu **Wyszukiwanie.** Wybierz ikonę **Eksportuj wszystkie punkty przerwania pasujące do bieżących kryteriów wyszukiwania** i zapisz plik.
- Aby wyeksportować wszystkie punkty przerwania, usuń zaznaczenie wszystkich pól i pozostaw pole **Wyszukaj** puste. Wybierz ikonę **Eksportuj wszystkie punkty przerwania pasujące do bieżących kryteriów wyszukiwania** i zapisz plik.
- Aby zaimportować punkty przerwania, w oknie **Punkty przerwania** wybierz **ikonę Importuj punkty przerwania z ikony pliku,** przejdź do lokalizacji pliku XML i wybierz pozycję **Otwórz**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Ustawianie punktów przerwania z okien debugera

Można również ustawić punkty przerwania z **rozmieszczeń wywołań** i **debugera demontażu** okna.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Ustawianie punktu przerwania w oknie Stos wywołań

 Aby przerwać na instrukcji lub wierszu, który zwraca funkcję wywołującą, można ustawić punkt przerwania w oknie **Stos wywołań.**

**Aby ustawić punkt przerwania w oknie Stos wywołań:**

1. Aby otworzyć okno **Stos wywołań,** należy wstrzymać podczas debugowania. Wybierz **opcję Debugowanie** > **stosu wywołań****systemu Windows** > lub naciśnij **klawisze Ctrl**+**Alt**+**C**.

2. W oknie **Stos wywołań** kliknij prawym przyciskiem myszy funkcję wywołującą i wybierz polecenie **Wstaw** > **punkt przerwania**lub naciśnij klawisz **F9**.

   Symbol punktu przerwania pojawia się obok nazwy wywołania funkcji na lewym marginesie stosu wywołań.

Punkt przerwania stosu wywołań pojawia się w oknie **Punkty przerwania** jako adres, z lokalizacją pamięci, która odpowiada następnej instrukcji wykonywalnej w funkcji.

Debuger przerwy na instrukcji.

Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [Jak: Użyj okna Stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [Mapowanie metod na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ustawianie punktu przerwania w oknie Demontaż

1. Aby otworzyć okno **demontażu,** należy wstrzymać podczas debugowania. Wybierz **opcję Debugowanie** > **demontażu****systemu Windows** > lub naciśnij klawisz **Alt**+**8**.

2. W oknie **Demontaż** kliknij lewy margines instrukcji, którą chcesz przerwać. Można go również zaznaczyć i nacisnąć klawisz **F9**lub kliknąć prawym przyciskiem myszy i wybrać polecenie **Wstaw** > **punkt przerwania**.

## <a name="see-also"></a>Zobacz też

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Napisz lepszy kod języka C# za pomocą programu Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Rozwiązywanie problemów z punktami przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md)
