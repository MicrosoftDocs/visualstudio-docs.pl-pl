---
title: Używanie punktów przerwania w debugerze | Microsoft Docs
description: Poznaj punkty przerwania, jedną z najważniejszych technik debugowania. Artykuł obejmuje akcje punktów przerwania, punkty śledzenia, warunki i wiele innych.
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
ms.openlocfilehash: cdc0231b7c42dbdb4aca86040347ec5bfd57607d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940673"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Używanie punktów przerwania w debugerze programu Visual Studio

Punkty przerwania są jedną z najważniejszych technik debugowania w przyborniku dewelopera. Punkty przerwania są ustawiane wszędzie tam, gdzie chcesz wstrzymać wykonywanie debugera. Na przykład możesz chcieć zobaczyć stan zmiennych kodu lub sprawdzić stos wywołań w określonym punkcie przerwania.  Jeśli próbujesz rozwiązać ostrzeżenie lub problem podczas korzystania z punktów przerwania, zobacz [Rozwiązywanie problemów z punktami przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Jeśli znasz zadanie lub problem, który próbujesz rozwiązać, ale musisz wiedzieć, jakiego rodzaju punkt przerwania ma być używany, zobacz [często zadawane pytania i Znajdź funkcję debugowania](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Ustaw punkty przerwania w kodzie źródłowym

Punkt przerwania można ustawić na dowolnym wierszu kodu wykonywalnego. Na przykład w poniższym kodzie C# można ustawić punkt przerwania w wierszu kodu z przypisaniem zmiennej ( `int testInt = 1` ), `for` pętlą lub dowolnym kodem wewnątrz `for` pętli. Nie można ustawić punktu przerwania w sygnaturach metod, deklaracjach dla przestrzeni nazw lub klasy lub deklaracji zmiennych, jeśli nie ma przypisania ani metody pobierającej/ustawiającej.

Aby ustawić punkt przerwania w kodzie źródłowym, kliknij w lewym górnym rogu obok wiersza kodu. Można również zaznaczyć wiersz i nacisnąć klawisz **F9**, wybrać pozycję **Debuguj**  >  **Przełącz punkt przerwania** lub kliknąć prawym przyciskiem myszy i wybrać **punkt** przerwania  >  **Wstaw punkt przerwania**. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie.

W przypadku większości języków, w tym C#, punkt przerwania i bieżące wiersze wykonania są automatycznie wyróżniane. W przypadku kodu C++ można włączyć wyróżnianie punktów przerwania i bieżących wierszy, wybierając pozycję **Narzędzia** (lub **Debuguj**) > **Opcje**  >  **debugowanie**  >   **Wyróżnij wszystkie wiersze źródłowe dla punktów przerwania i bieżącej instrukcji (tylko C++)**.

![Ustawianie punktu przerwania](../debugger/media/basicbreakpoint.png "Podstawowy punkt przerwania")

Podczas debugowania, wykonywanie jest wstrzymywane w punkcie przerwania, przed wykonaniem kodu w tym wierszu. Symbol punktu przerwania pokazuje żółtą strzałkę.

W punkcie przerwania w poniższym przykładzie wartość jest równa `testInt` 1. Tak więc wartość nie zmieniła się od momentu zainicjowania zmiennej (wartość 1), ponieważ instrukcja w żółtym nie została jeszcze wykonana.

![Zatrzymano wykonywanie punktu przerwania](../debugger/media/breakpointexecution.png "Wykonywanie punktu przerwania")

Gdy debuger zatrzyma się w punkcie przerwania, można sprawdzić bieżący stan aplikacji, w tym [wartości zmiennych](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) i [stos wywołań](../debugger/how-to-use-the-call-stack-window.md).

Poniżej przedstawiono kilka ogólnych instrukcji dotyczących pracy z punktami przerwania.

- Punkt przerwania jest przełącznikiem. Możesz kliknąć go, nacisnąć klawisz **F9** lub użyć polecenia **Debuguj**  >  **Przełącz punkt przerwania** , aby usunąć lub ponownie wstawić.

- Aby wyłączyć punkt przerwania bez usuwania, umieść kursor nad lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Wyłącz punkt przerwania**. Wyłączone punkty przerwania są wyświetlane jako puste kropki na lewym marginesie lub w oknie **punkty przerwania** . Aby ponownie włączyć punkt przerwania, umieść kursor nad lub kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **Włącz punkt przerwania**.

- Ustaw warunki i akcje, Dodaj i edytuj etykiety lub wyeksportuj punkt przerwania, klikając go prawym przyciskiem myszy i wybierając odpowiednie polecenie lub umieszczając je na nim, a następnie wybierając ikonę **Ustawienia** .

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akcje punktu przerwania i punkty śledzenia

*Punkt śledzenia* jest punktem przerwania, który drukuje komunikat do okna **danych wyjściowych** . Punkt śledzenia może działać jak tymczasowa instrukcja śledzenia w języku programowania i nie wstrzymuje wykonywania kodu. Tworzysz punkt śledzenia przez ustawienie specjalnej akcji w oknie **Ustawienia punktu przerwania** . Aby uzyskać szczegółowe instrukcje, zobacz [Korzystanie z punkty śledzenia w debugerze programu Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Warunki punktu przerwania

Można kontrolować, kiedy i gdzie wykonywany jest punkt przerwania, ustawiając warunki. Warunek może być dowolnym prawidłowym wyrażeniem rozpoznawanym przez debuger. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń, zobacz [wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).

**Aby ustawić warunek punktu przerwania:**

1. Kliknij prawym przyciskiem myszy symbol punktu przerwania i wybierz pozycję **warunki** (lub naciśnij klawisz **Alt**  +  **F9**, **C**). Lub umieść wskaźnik myszy nad symbolem punktu przerwania, wybierz ikonę **Ustawienia** , a następnie wybierz pozycję **warunki** w oknie **Ustawienia punktu przerwania** .

   Możesz również ustawić warunki w oknie **punkty przerwania** , klikając prawym przyciskiem myszy punkt przerwania i wybierając pozycję **Ustawienia**, a następnie wybierając pozycję **warunki**.

   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Na liście rozwijanej wybierz pozycję **wyrażenie warunkowe**, **liczba trafień** lub **Filtr**, a następnie ustaw odpowiednią wartość.

3. Wybierz przycisk **Zamknij** lub naciśnij klawisz **Ctrl** + **,** aby zamknąć okno **Ustawienia punktu przerwania** . Lub z okna **punkty przerwania** wybierz **przycisk OK** , aby zamknąć okno dialogowe.

Punkty przerwania z zestawem warunków są wyświetlane z **+** symbolem w oknach kod źródłowy i **punkty przerwania** .

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Tworzenie wyrażenia warunkowego

W przypadku wybrania **wyrażenia warunkowego** można wybrać dwa warunki: **wartość true** lub w **przypadku zmiany**. Wybierz **wartość true** , aby przerwać, gdy wyrażenie jest spełnione, lub **gdy zmiana** zostanie przerwana, gdy wartość wyrażenia została zmieniona.

W poniższym przykładzie punkt przerwania jest trafień tylko wtedy, gdy wartość `testInt` wynosi **4**:

![Warunek punktu przerwania ma wartość true](../debugger/media/breakpointconditionistrue.png "Punkt przerwania ma wartość true")

W poniższym przykładzie punkt przerwania jest trafień tylko wtedy, gdy zmienia się wartość `testInt` :

![Punkt przerwania w przypadku zmiany](../debugger/media/breakpointwhenchanged.png "Punkt przerwania w przypadku zmiany")

Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania z prawidłową składnią, ale z nieprawidłową semantyką, pojawi się komunikat ostrzegawczy przy pierwszym trafieniu punktu przerwania. W obu przypadkach debuger przerywa, gdy trafi na nieprawidłowy punkt przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy warunek jest prawidłowy i ma wartość `false` .

>[!NOTE]
> W przypadku **zmiany** pola debuger nie uwzględnia pierwszej oceny warunku do zmiany, dlatego nie trafi punkt przerwania przy pierwszej ocenie.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Używanie identyfikatorów obiektów w wyrażeniach warunkowych (tylko w językach C# i F #)

 Istnieją przypadki, w których chcesz obserwować zachowanie określonego obiektu. Na przykład możesz chcieć dowiedzieć się, dlaczego obiekt został wstawiony do kolekcji więcej niż raz. W językach C# i F # można tworzyć identyfikatory obiektów dla określonych wystąpień [typów referencyjnych](/dotnet/csharp/language-reference/keywords/reference-types)i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzone z obiektem.

**Aby utworzyć identyfikator obiektu:**

1. Ustaw punkt przerwania w kodzie trochę miejsca po utworzeniu obiektu.

2. Rozpocznij debugowanie i kiedy wykonywanie jest wstrzymywane w punkcie przerwania, wybierz pozycję **Debuguj**  >    >  **Ustawienia lokalne** systemu Windows (lub naciśnij **klawisze CTRL**  +  **Alt**  +  **V**, **L**), aby otworzyć okno zmienne **lokalne** .

   Znajdź wystąpienie określonego obiektu w oknie **zmiennych lokalnych** , kliknij je prawym przyciskiem myszy, a następnie wybierz pozycję **Utwórz identyfikator obiektu**.

   Powinna zostać wyświetlona **$** Plus cyfra w oknie **zmiennych lokalnych** . To jest identyfikator obiektu.

3. Dodaj nowy punkt przerwania w punkcie, który chcesz zbadać; na przykład gdy obiekt ma zostać dodany do kolekcji. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **warunki**.

4. Użyj identyfikatora obiektu w polu **wyrażenia warunkowego** . Na przykład jeśli zmienna `item` jest obiektem, który ma zostać dodany do kolekcji, wybierz opcję **ma wartość true** i wpisz **element = = \<n> $**, gdzie \<n> jest numerem identyfikatora obiektu.

   Wykonanie zostanie przerwane w momencie, gdy ten obiekt zostanie dodany do kolekcji.

   Aby usunąć identyfikator obiektu, kliknij prawym przyciskiem myszy zmienną w oknie zmiennych **lokalnych** i wybierz pozycję **Usuń identyfikator obiektu**.

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania i nie uniemożliwiają odzyskiwania obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

### <a name="set-a-hit-count-condition"></a>Ustaw warunek liczby trafień

Jeśli podejrzewasz, że pętla w kodzie zaczyna się błędna po określonej liczbie iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonywanie po tej liczbie trafień, a nie trzeba wielokrotnie nacisnąć klawisz **F5** w celu osiągnięcia tej iteracji.

W obszarze **warunki** w oknie **Ustawienia punktu przerwania** wybierz pozycję **liczba trafień**, a następnie określ liczbę iteracji. W poniższym przykładzie punkt przerwania jest ustawiony na wartość trafij przy każdej innej iteracji:

![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Ustaw warunek filtru

Punkt przerwania można ograniczyć do uruchamiania tylko na określonych urządzeniach lub w określonych procesach i wątkach.

W obszarze **warunki** w oknie **Ustawienia punktu przerwania** wybierz opcję **Filtr**, a następnie wprowadź co najmniej jeden z następujących wyrażeń:

- MachineName = "name"
- ProcessId = wartość
- ProcessName = "name"
- ThreadId = wartość
- ThreadName = "name"

Ujmij wartości ciągu w podwójne cudzysłowy. Można łączyć klauzule przy użyciu `&` (i), `||` (lub), `!` (nie) i nawiasów.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Ustaw punkty przerwania funkcji

Możesz przerwać wykonywanie, gdy wywoływana jest funkcja. Jest to przydatne, na przykład w przypadku znajomości nazwy funkcji, ale nie jej lokalizacji. Jest ona również przydatna, jeśli masz funkcje o tej samej nazwie i chcesz przerwać ich wszystkie (na przykład przeciążone funkcje lub funkcje w różnych projektach).

**Aby ustawić punkt przerwania funkcji:**

1. Wybierz kolejno opcje **Debuguj** nowy punkt przerwania  >    >  **funkcji** lub naciśnij **klawisze CTRL**  +  **K**, **B**.

   Możesz również wybrać pozycję **Nowy**  >  **punkt przerwania funkcji** w oknie **punkty przerwania** .

1. W oknie dialogowym **nowy punkt przerwania funkcji** wprowadź nazwę funkcji w polu **nazwa funkcji** .

   Aby zawęzić specyfikację funkcji:

   - Użyj w pełni kwalifikowanej nazwy funkcji.

     Przyklad  `Namespace1.ClassX.MethodA()`

   - Dodaj typy parametrów przeciążonej funkcji.

     Przyklad  `MethodA(int, string)`

   - Użyj symbolu "!", aby określić moduł.

     Przykład: `App1.dll!MethodA`

   - Użyj operatora kontekstu w natywnym języku C++.

     `{function, , [module]} [+<line offset from start of method>]`

     Przykład: `{MethodA, , App1.dll}+2`

1. Z listy rozwijanej **Język** wybierz język funkcji.

1. Wybierz przycisk **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Ustawianie punktu przerwania funkcji przy użyciu adresu pamięci (tylko natywne C++)
 Możesz użyć adresu obiektu, aby ustawić punkt przerwania funkcji dla metody wywoływanej przez określone wystąpienie klasy.  Na przykład, przy użyciu obiektu możliwego do adresowania typu `my_class` , można ustawić punkt przerwania funkcji dla `my_method` metody wywołującej.

1. Ustaw punkt przerwania w dowolnym miejscu po utworzeniu wystąpienia klasy.

2. Znajdź adres wystąpienia (na przykład `0xcccccccc` ).

3. Wybierz kolejno opcje **Debuguj** nowy punkt przerwania  >    >  **funkcji** lub naciśnij **klawisze CTRL**  +  **K**, **B**.

4. Dodaj następujący kod do pola **nazwa funkcji** i wybierz język **C++** .

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Ustaw punkty przerwania danych (.NET Core 3,0 lub nowszy)

Punkty przerwania danych przerywają wykonywanie w przypadku zmiany właściwości określonego obiektu.

**Aby ustawić punkt przerwania danych**

1. W projekcie .NET Core, Rozpocznij debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania.

2. W oknie **Autokorekty**, **czujka** lub **lokalne** kliknij prawym przyciskiem myszy właściwość i wybierz pozycję **Przerwij, gdy wartość zostanie zmieniona** w menu kontekstowym.

    ![Zarządzany punkt przerwania danych](../debugger/media/managed-data-breakpoint.png "Zarządzany punkt przerwania danych")

Punkty przerwania danych w programie .NET Core nie będą działały dla:

- Właściwości, które nie są rozwijane w etykietce narzędzia, elementy lokalne, autouzupełniania ani okno wyrażeń kontrolnych
- Zmienne statyczne
- Klasy z atrybutem DebuggerTypeProxy
- Pola wewnątrz struktur

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Ustaw punkty przerwania danych (tylko natywne C++)

 Punkty przerwania danych przerywają wykonywanie, gdy wartość przechowywana w określonym adresie pamięci ulegnie zmianie. Jeśli wartość jest odczytywana, ale nie została zmieniona, wykonywanie nie jest przerywane.

**Aby ustawić punkt przerwania danych:**

1. W projekcie w języku C++ Rozpocznij debugowanie i poczekaj, aż zostanie osiągnięty punkt przerwania. W menu **Debuguj** wybierz pozycję **Nowy** punkt  >  **przerwania danych** punktu przerwania.

    Możesz również wybrać pozycję **Nowy**  >  **punkt przerwania danych** w oknie **punkty przerwania** lub kliknąć prawym przyciskiem myszy element w oknie **autostarty**, **czujka** lub **lokalne** i wybrać polecenie **Przerwij, gdy wartość zostanie zmieniona** w menu kontekstowym.

2. W polu **adres** wpisz adres pamięci lub wyrażenie, którego wynikiem jest adres pamięci. Na przykład wpisz, `&avar` Aby przerwać, gdy zmieni się zawartość zmiennej `avar` .

3. Z listy rozwijanej **liczba bajtów** wybierz liczbę bajtów, które ma oglądać debuger. Na przykład po wybraniu opcji **4** debuger będzie oglądać cztery bajty, zaczynając od `&avar` i Break, jeśli którykolwiek z tych bajtów zmieni wartość.

Punkty przerwania danych nie działają w następujących warunkach:
- Proces, który nie jest debugowany zapis w lokalizacji pamięci.
- Lokalizacja pamięci jest współdzielona przez dwa lub więcej procesów.
- Lokalizacja pamięci jest aktualizowana w jądrze. Na przykład jeśli pamięć jest przenoszona do 32-bitowej funkcji systemu Windows `ReadFile` , pamięć zostanie zaktualizowana z trybu jądra, więc debuger nie będzie przerywał działania aktualizacji.
- Gdzie wyrażenie czujki jest większe niż 4 bajty na 32-bitowym sprzęcie i 8 bajtów na urządzeniu 64-bitowym. Jest to ograniczenie architektury x86.

> [!NOTE]
> - Punkty przerwania danych są zależne od określonych adresów pamięci. Adres zmiennej zmienia się z jednej sesji debugowania na następną, więc punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.
>
> - Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, punkt przerwania zostanie włączony, gdy funkcja zostanie zakończona, ale adres pamięci nie będzie już stosowany, więc zachowanie punktu przerwania jest nieprzewidywalne. Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem działania funkcji.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Zarządzanie punktami przerwania w oknie punkty przerwania

 Możesz użyć okna **punkty przerwania** , aby zobaczyć wszystkie punkty przerwania w rozwiązaniu i zarządzać nimi. Ta scentralizowana lokalizacja jest szczególnie przydatna w dużych rozwiązaniach lub złożonych scenariuszach debugowania, w których punkty przerwania są krytyczne.

W oknie **punkty przerwania** można wyszukiwać, sortować, filtrować, włączać/wyłączać lub usuwać punkty przerwania. Możesz również ustawić warunki i akcje lub dodać nową funkcję lub punkt przerwania danych.

Aby otworzyć okno **punkty przerwania** , wybierz pozycję **Debuguj**  >    >  **punkty przerwania** systemu Windows lub naciśnij **klawisze CTRL** + **Alt** + **B**.

![Okno punktów przerwania](../debugger/media/breakpointswindow.png "Okno punktów przerwania")

Aby wybrać kolumny, które mają być wyświetlane w oknie **punkty przerwania** , wybierz pozycję **Pokaż kolumny**. Wybierz nagłówek kolumny, aby posortować listę punktów przerwania według tej kolumny.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etykiety punktów przerwania
Za pomocą etykiet można sortować i filtrować listę punktów przerwania w oknie **punkty przerwania** .

1. Aby dodać etykietę do punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub w oknie **punkty przerwania** , a następnie wybierz polecenie **Edytuj etykiety**. Dodaj nową etykietę lub wybierz istniejącą, a następnie wybierz przycisk **OK**.
2. Posortuj listę punktów przerwania w oknie **punkty przerwania** , wybierając **etykiety**, **warunki** lub inne nagłówki kolumn. Możesz wybrać kolumny do wyświetlenia, wybierając pozycję **Pokaż kolumny** na pasku narzędzi.

### <a name="export-and-import-breakpoints"></a>Eksportuj i Importuj punkty przerwania
 Aby zapisać lub udostępnić stan i lokalizację punktów przerwania, można je wyeksportować lub zaimportować.

- Aby wyeksportować pojedynczy punkt przerwania do pliku XML, kliknij prawym przyciskiem myszy punkt przerwania w oknie kod źródłowy lub **punkty przerwania** , a następnie wybierz opcję **Eksportuj** lub **Eksportuj zaznaczone**. Wybierz lokalizację eksportu, a następnie wybierz pozycję **Zapisz**. Domyślną lokalizacją jest folder rozwiązanie.
- Aby wyeksportować kilka punktów przerwania, w oknie **punkty przerwania** zaznacz pola obok punktów przerwania lub wprowadź kryteria wyszukiwania w polu **wyszukiwania** . Zaznacz ikonę **Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami wyszukiwania** i Zapisz plik.
- Aby wyeksportować wszystkie punkty przerwania, usuń zaznaczenie wszystkich pól i pozostaw puste pole **wyszukiwania** . Zaznacz ikonę **Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami wyszukiwania** i Zapisz plik.
- Aby zaimportować punkty przerwania, w oknie **punkty przerwania** wybierz pozycję **Importuj punkty przerwania z ikony pliku** , przejdź do lokalizacji pliku XML, a następnie wybierz pozycję **Otwórz**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Ustawianie punktów przerwania z okien debugera

Możesz również ustawić punkty przerwania w oknach **stosu wywołań** i **demontażu** .

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Ustawianie punktu przerwania w oknie stosu wywołań

 Aby przerwać w instrukcji lub wierszu, do którego funkcja wywołująca wraca do, można ustawić punkt przerwania w oknie **stosu wywołań** .

**Aby ustawić punkt przerwania w oknie stosu wywołań:**

1. Aby otworzyć okno **stosu wywołań** , należy wstrzymać podczas debugowania. Wybierz pozycję **Debuguj**  >    >  **stos wywołań** systemu Windows lub naciśnij **klawisze CTRL** + **+** + **C**.

2. W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję wywołującą i wybierz **punkt przerwania**  >  **Wstaw punkt przerwania** lub naciśnij klawisz **F9**.

   Symbol punktu przerwania pojawia się obok nazwy wywołania funkcji na lewym marginesie stosu wywołań.

Punkt przerwania stosu wywołań jest wyświetlany w oknie **punkty przerwania** jako adres, z lokalizacją w pamięci, która odpowiada następnej instrukcji wykonywalnej w funkcji.

Debuger przerwie się w instrukcji.

Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ustawianie punktu przerwania w oknie demontażu

1. Aby otworzyć okno **demontaż** , należy wstrzymać podczas debugowania. Wybierz pozycję **Debuguj**  >    >  **demontaż** systemu Windows lub naciśnij **klawisze CTRL** + **Alt** + **D**.

2. W oknie **demontażu** kliknij na lewym marginesie instrukcji, która ma zostać przerwana. Można go również zaznaczyć i nacisnąć klawisz **F9** lub kliknąć prawym przyciskiem myszy i wybrać **punkt przerwania**  >  **Wstaw punkt przerwania**.

## <a name="see-also"></a>Zobacz też

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Pisanie lepszego kodu w języku C# za pomocą programu Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
- [Rozwiązywanie problemów z punktami przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md)
