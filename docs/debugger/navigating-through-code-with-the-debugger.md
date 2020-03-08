---
title: Przechodzenie do kodu z debugerem | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409317"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Nawigowanie po kodzie za pomocą debugera programu Visual Studio

Debuger programu Visual Studio może pomóc w nawigowaniu po kodzie, aby sprawdzić stan aplikacji i wyświetlić jego przepływ wykonania. Skróty klawiaturowe, poleceń debugowania, punkty przerwania i inne funkcje umożliwia szybki dostęp do kodu, który chcesz zbadać. Znajomość poleceń nawigacji debugera i skróty umożliwia szybsze i łatwiejsze do znajdowania i rozwiązywania problemów z aplikacjami.  Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="get-into-break-mode"></a>Zapoznaj się z "trybem przerwania"

W *trybie przerwania*wykonywanie aplikacji jest zawieszone, gdy funkcje, zmienne i obiekty pozostają w pamięci. Gdy debuger jest w trybie przerwania, można nawigować po kodzie. Najczęstszym sposobem na szybkie rozpoczęcie pracy w trybie przerwania jest:

- Rozpocznij krokowe wykonywanie kodu, naciskając klawisz **F10** lub **F11**. Dzięki temu można szybko znaleźć punkt wejścia aplikacji, a następnie nacisnąć polecenia krok po kroku, aby poruszać się po kodzie.

- [Uruchom do określonej lokalizacji lub funkcji](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), na przykład przez [ustawienie punktu przerwania](using-breakpoints.md) i uruchomienie aplikacji.

   Na przykład w edytorze kodu w programie Visual Studio można użyć polecenia **Uruchom do kursora** , aby uruchomić aplikację, debuger dołączony i przejść do trybu przerwania, a następnie klawisza **F11** , aby nawigować po kodzie.

   ![Uruchom do kursora i przejdź do kodu](../debugger/media/navigate-code-code-stepping.gif "Uruchom do kursora i przejdź do kodu")

W trybie przerwania można użyć różnych poleceń do nawigowania po kodzie. W trybie przerwania można sprawdzić wartości zmiennych, aby wyszukać naruszenia lub błędy. W przypadku niektórych typów projektu może również wprowadzać zmiany do aplikacji w trybie przerwania.

Większość okien debugera, takich jak **moduły** i okna **czujki** , jest dostępna tylko wtedy, gdy debuger jest dołączony do aplikacji. Niektóre funkcje debugera, takie jak wyświetlanie wartości zmiennych w oknie zmiennych **lokalnych** lub ocenianie wyrażeń w oknie **czujki** , są dostępne tylko podczas wstrzymania debugera (czyli w trybie przerwania).

> [!NOTE]
> Jeśli połączysz się z kodem, który nie ma załadowanych plików źródłowych lub symboli ( *. pdb*), debuger wyświetli **pliki źródłowe** , które nie zostały znalezione lub **nie znaleziono symboli** , które mogą pomóc w znalezieniu i załadowaniu plików. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie można załadować symboli lub plików źródłowych, można nadal debugować instrukcje zestawu w oknie **demontażu** .

## <a name="step-through-code"></a>Przejść przez kod

Polecenia kroku debugera pomóc sprawdzić stan swojej aplikacji lub dowiedzieć się więcej o przepływ jego wykonania.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Wkrocz do wiersza kodu według wiersza

Aby zatrzymać każdą instrukcję podczas debugowania, użyj instrukcji **Debug** > **Step Into**lub naciśnij klawisz **F11**.

Debuger nie wchodzi przez instrukcje kodu, a nie fizyczne wiersze. Na przykład klauzula `if` może być zapisywana w jednym wierszu:

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Jednak gdy wchodzisz do tego wiersza debuger traktuje ten warunek jako jeden krok, a jego konsekwencję jako inny. W poprzednim przykładzie warunek jest prawdziwy.

W przypadku wywołania funkcji zagnieżdżonej **Przejdź** do kroków do najbardziej głęboko zagnieżdżonej funkcji. Na przykład jeśli używasz **kroku do** wywołania, takie jak `Func1(Func2())`, debuger przeprowadzi procedurę do `Func2`funkcji.

>[!TIP]
>Gdy wykonujesz każdy wiersz kodu, możesz umieścić wskaźnik myszy nad zmiennymi, aby zobaczyć ich wartości, lub użyć okien [lokalnych](autos-and-locals-windows.md) i [czujki](watch-and-quickwatch-windows.md) , aby obejrzeć zmiany wartości. Możesz również wizualnie śledzić [stos wywołań](how-to-use-the-call-stack-window.md) podczas przechodzenia do funkcji. (Aby uzyskać tylko Visual Studio Enterprise, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="BKMK_Step_over_Step_out"></a>Przechodzenie przez kod i pomijanie niektórych funkcji

Może nie interesują funkcji podczas debugowania lub znasz jego działania, takie jak kod dobrze przetestowanych biblioteki. Poniższe polecenia służą do pomijania kodu podczas wykonywania kodu. Nadal wykonywać funkcje, ale debuger pomija nad nimi.

|Polecenie klawiatury|Debugowanie polecenia menu|Opis|
|----------------------|------------------|-----------------|
|**F10**|**Przekrocz nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji, **krok powyżej** uruchamia kod, a następnie wstrzymuje wykonywanie w pierwszym wierszu kodu po wywołaniu wywołanej funkcji.|
|**Shift**+**F11**|**Wyjdź**|**Krok** Wyjdź kontynuuje uruchamianie kodu i wstrzymuje wykonywanie, gdy bieżąca funkcja zwraca wartość. Debuger pomija za pomocą bieżącej funkcji.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Uruchom do określonej lokalizacji lub funkcji

Użytkownik może chcieć uruchomić bezpośrednio do określonej lokalizacji lub funkcji, gdy wiesz, jaki dokładnie kod chcesz sprawdzić lub wiesz, gdzie chcesz rozpocząć debugowanie.

### <a name="run-to-a-breakpoint-in-code"></a>Uruchom do punktu przerwania w kodzie

Aby ustawić prosty punkt przerwania w kodzie, kliknij przycisk po lewej stronie margines obok wiersza kodu, na którym ma się zawiesić wykonanie. Można również zaznaczyć wiersz i nacisnąć klawisz **F9**, wybrać polecenie **Debuguj** > **Przełącz punkt przerwania**lub kliknąć prawym przyciskiem myszy i wybrać pozycję **punkt przerwania** > **Wstaw punkt przerwania**. Punkt przerwania pojawia się jako czerwona kropka na lewym marginesie obok wiersza kodu. Debuger zawiesza wykonywanie tylko w przypadku, przed wykonaniem wiersza.

![Ustawianie punktu przerwania](../debugger/media/dbg_basics_setbreakpoint.png "Ustawianie punktu przerwania")

Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Aby uzyskać szczegółowe informacje, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Uruchom do punktu przerwania funkcji

Można polecić debugerowi, aby uruchomić, dopóki nie osiągnie określoną funkcję. Można określić funkcję według nazwy lub możesz ją wybrać spośród stosu wywołań.

**Aby określić punkt przerwania funkcji według nazwy**

1. Wybierz > debugowania **nowy punkt** przerwania > **funkcji**

1. W oknie dialogowym **nowy punkt przerwania funkcji** wpisz nazwę funkcji i wybierz jej język.

   ![Nowe okno dialogowe punktu przerwania funkcji](../debugger/media/dbg_execution_newbreakpoint.png "Nowy punkt przerwania funkcji")

1. Kliknij przycisk **OK**.

Jeśli funkcja jest przeciążona lub w więcej niż jednej przestrzeni nazw, możesz wybrać odpowiedni element w oknie **punkty przerwania** .

![Przeciążone punkty przerwania funkcji](../debugger/media/dbg_execution_overloadedbreakpoints.png "Przeciążone punkty przerwania funkcji")

**Aby wybrać punkt przerwania funkcji ze stosu wywołań**

1. Podczas debugowania Otwórz okno **stos wywołań** , wybierając pozycję **debuguj** > **Windows** > **stos wywołań**.

1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję i wybierz polecenie **Uruchom do kursora**lub naciśnij klawisz **Ctrl**+**F10**.

Aby wizualnie śledzić stos wywołań, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Uruchom do lokalizacji kursora

Aby uruchomić do lokalizacji kursora, w kodzie źródłowym lub oknie **stosu wywołań** , zaznacz wiersz, który chcesz przerwać, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom do kursora**lub naciśnij klawisz **Ctrl**+**F10**. Wybranie opcji **Uruchom do kursora** przypomina ustawienie tymczasowego punktu przerwania.

### <a name="run-to-click"></a>Uruchom do kliknięcia

W debugerze można umieścić wskaźnik myszy nad instrukcją w kodzie źródłowym lub w oknie **demontażu** , a następnie wybrać ikonę **Uruchom wykonywanie do tutaj** zieloną strzałkę. Użycie polecenia **Uruchom do kliknięcia** eliminuje konieczność ustawienia tymczasowego punktu przerwania.

![Uruchom do kliknięcia](../debugger/media/dbg-run-to-click.png "Uruchom do kliknięcia")

> [!NOTE]
> **Uruchomienie do kliknięcia** jest dostępne w [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

### <a name="manually-break-into-code"></a>Ręcznie Wejdź do kodu

Aby przerwać w następnym dostępnym wierszu kodu w działającej aplikacji, wybierz kolejno opcje **debuguj** > **Przerwij wszystko**lub naciśnij **klawisze CTRL**+**Alt**+**Break**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Przesuń wskaźnik, aby zmienić przepływ wykonywania

Gdy debuger jest wstrzymany, żółta strzałka na marginesie kodu źródłowego lub okna **demontażu** oznacza lokalizację następnej instrukcji do wykonania. Można zmienić następnej instrukcji do wykonania, przesuwając ten grot strzałki. Możesz pominąć część kodu lub powrócić do poprzedniego wiersza. Przeniesienie wskaźnika jest przydatne w sytuacjach, takich jak pomijanie sekcji kodu, który zawiera znany błąd.

 ![Przenoszenie wskaźnika](../debugger/media/dbg_basics_example3.gif "Przenoszenie wskaźnika")

Aby zmienić następnej instrukcji do wykonania, debuger musi być w trybie przerwania. W oknie kod źródłowy lub **demontaż** przeciągnij żółtą grot strzałki w inny wiersz lub kliknij prawym przyciskiem myszy wiersz, który chcesz wykonać w następnej kolejności, i wybierz polecenie **Ustaw następną instrukcję**.

Licznik programu przechodzi bezpośrednio do nowej lokalizacji i instrukcje między wykonywania stare i nowe punkty nie są wykonywane. Jednak jeśli przeniesiesz punkt wykonania Wstecz, instrukcje interwencyjne nie są cofnąć.

>[!CAUTION]
>- Przenoszenie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji.
>- W języku Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.
>- W natywnym kodzie C++ zostały włączone, kontrole czasu wykonywania ustawienie następnej instrukcji może spowodować wyjątek zgłaszany, gdy wykonywanie osiągnie koniec metody.
>- Gdy funkcja Edytuj i Kontynuuj jest włączona, **Ustawianie następnej instrukcji** kończy się niepowodzeniem, jeśli wprowadzono zmiany, które edytują i kontynuują, nie można od razu ponownie mapować. Może to występować, na przykład, jeśli edytowano kod wewnątrz bloku catch. W takim przypadku komunikat o błędzie informujący o tym, że operacja nie jest obsługiwany.
>- W kodzie zarządzanym nie można przenieść następnej instrukcji, jeśli:
>   - Następna instrukcja znajduje się w innej metodzie niż bieżąca instrukcja.
>   - Debugowanie zostało uruchomione przez Just-In-Time debugowania.
>   - Odwijania stosu wywołań jest w toku.
>   - Został zgłoszony wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debuguj kod niebędący użytkownikiem

Domyślnie debuger próbuje debugować tylko kod aplikacji przez włączenie ustawienia o nazwie *tylko mój kod*. Aby uzyskać więcej informacji o tym, jak działa ta funkcja dla różnych typów projektów i języków oraz jak można je dostosować, zobacz [tylko mój kod](../debugger/just-my-code.md).

Aby wyświetlić kod framework, kod biblioteki innych firm lub wywołań systemowych podczas debugowania, można wyłączyć opcję tylko mój kod. W oknie **Narzędzia** (lub **Debuguj**) > **Opcje** > **debugowania**wyczyść pole wyboru **Włącz tylko mój kod** . Po wyłączeniu tylko mój kod niebędący kodem użytkownika jest wyświetlana w oknach debugera, a debuger może wkroczyć do kodu niepochodzącego od użytkownika.

> [!NOTE]
> Tylko mój kod nie jest obsługiwana dla projektów urządzenia.

### <a name="debug-system-code"></a>Możliwe jest debugowanie kodu systemu

Jeśli masz załadowane symbole debugowania dla kodu systemu Microsoft i wyłączyć opcję tylko mój kod, możesz wejść do wywołania systemowego tak samo jak inne wywołania.

Aby załadować symbole firmy Microsoft, zobacz [Konfigurowanie lokalizacji symboli i opcji ładowania](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Aby załadować symbole dla określonego składnika systemu:**

1. Podczas debugowania Otwórz okno **moduły** , wybierając pozycję **debuguj** > **moduły** > **systemu Windows** lub naciskając klawisz **Ctrl**+**Alt**+**U**.

1. W oknie **moduły** można określić, które moduły mają symbole załadowane w kolumnie **stan symbolu** . Kliknij prawym przyciskiem myszy moduł, dla którego chcesz załadować symbole, a następnie wybierz pozycję **Załaduj symbole**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Wkrocz do właściwości i operatorów w kodzie zarządzanym
 Debuger nie wchodzi we właściwości i operatory w kodzie zarządzanym domyślnie. W większości przypadków zapewnia to lepszy proces debugowania. Aby włączyć krokowe przechodzenie do właściwości lub operatorów, wybierz opcję **debuguj** > **Opcje**. Na stronie **Ogólne** **debugowania** > wyczyść pole wyboru **Przekrocz nad właściwościami i operatorami (tylko zarządzane)** .

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Techniki i narzędzia debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
