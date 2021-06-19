---
title: Nawigowanie po kodzie za pomocą | Microsoft Docs
description: 'Dowiedz się, jak używać Visual Studio do rozwiązywania problemów z kodem. Tematy obejmują: przechodzenie w tryb przerwania, wykonywanie krokowe kodu i uruchamianie do obiektu docelowego.'
ms.custom: SEO-VS-2020
ms.date: 11/12/2018
ms.topic: how-to
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9c0424b07ba7a24f109e967d464856781e5dbb2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385243"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Nawigowanie po kodzie za pomocą Visual Studio debugowania

Debuger Visual Studio może ułatwić nawigowanie po kodzie w celu sprawdzenia stanu aplikacji i pokazania jej przepływu wykonywania. Możesz użyć skrótów klawiaturowych, poleceń debugowania, punktów przerwania i innych funkcji, aby szybko uzyskać dostęp do kodu, który chcesz zbadać. Znajomość poleceń nawigacji debugera i skrótów ułatwia znajdowanie i rozwiązywanie problemów z aplikacją.

> [!NOTE]
> Jeśli po raz pierwszy próbujesz debugować kod, przed przeczytaniem tego artykułu [](../debugger/write-better-code-with-visual-studio.md) warto przeczytać artykuł Debugowanie dla bezwzględnych początkujących oraz Techniki i narzędzia debugowania. [](../debugger/debugging-absolute-beginners.md)

## <a name="get-into-break-mode"></a>Uzyskiwanie "trybu przerwania"

W *trybie przerwania* wykonywanie aplikacji jest wstrzymane, a funkcje, zmienne i obiekty pozostają w pamięci. Gdy debuger będzie w trybie przerwania, możesz nawigować po kodzie. Najbardziej typowe sposoby szybkiego dojechanie do trybu przerwania to:

- Rozpocznij wykonywanie kodu krokowego, naciskając **klawisz F10** **lub F11.** Dzięki temu można szybko znaleźć punkt wejścia aplikacji, a następnie kontynuować naciskanie poleceń kroku w celu nawigowania po kodzie.

- [Uruchom do określonej lokalizacji lub funkcji](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), na przykład [ustawiając punkt przerwania](using-breakpoints.md) i uruchamiając aplikację.

   Na przykład w edytorze kodu w programie Visual Studio  możesz użyć polecenia Uruchom do kursora, aby uruchomić aplikację, dołączyć debuger i przejść w tryb przerwania, a następnie użyć klawisza **F11** do nawigowania po kodzie.

   ![Uruchom w celu kursora i wejd do kodu](../debugger/media/navigate-code-code-stepping.gif "Uruchamianie kursora i krok do kodu")

W trybie przerwania można używać różnych poleceń do nawigowania po kodzie. W trybie przerwania można sprawdzać wartości zmiennych, aby szukać naruszeń lub usterek. W przypadku niektórych typów projektów można również wprowadzić zmiany w aplikacji w trybie przerwania.

Większość okien debugera, takich jak **okna Moduły** i **Czujka,** jest dostępna tylko wtedy, gdy debuger jest dołączony do aplikacji. Niektóre funkcje debugera, takie jak  wyświetlanie wartości zmiennych w oknie Zmiennych lokalnych lub ocenianie wyrażeń w oknie Wyrażenie czujki, są dostępne tylko wtedy, gdy debuger jest wstrzymany (czyli w trybie przerwania). 

> [!NOTE]
> W przypadku włamania się do kodu, który nie ma załadowanych plików źródłowych lub symboli  *(.pdb),* debuger wyświetla stronę Nie znaleziono plików źródłowych lub Nie znaleziono symboli, która może pomóc w odnalezieniu i załadowaniu plików.  Zobacz [Temat Specify symbol (.pdb) and source files (Określanie plików symboli (.pdb) i plików źródłowych).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Jeśli nie można załadować symbolu lub plików źródłowych, nadal można debugować instrukcje zestawu w oknie **Dekompełowanie.**

## <a name="step-through-code"></a>Krok po kroku w kodzie

Polecenia kroku debugera ułatwiają sprawdzanie stanu aplikacji lub dowiedz się więcej o jej przepływie wykonywania.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Krok po wierszu kodu

Aby zatrzymać każdą instrukcje podczas debugowania, użyj **polecenia**  >  **Debuguj krok do** lub naciśnij klawisz **F11.**

Debuger przechodzi przez instrukcje kodu, a nie linie fizyczne. Na przykład `if` klauzula może być zapisywana w jednym wierszu:

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

Jednak gdy wchodzisz do tego wiersza, debuger traktuje warunek jako jeden krok, a konsekwencje jako inny. W poprzednim przykładzie warunek ma wartość true.

W wywołaniu funkcji zagnieżdżonych **kroki** do najbardziej głęboko zagnieżdżonych funkcji. Jeśli na przykład użyjemy funkcji **Step Into** w wywołaniu, na przykład `Func1(Func2())` , debuger wchodzi do funkcji `Func2` .

>[!TIP]
>Podczas wykonywania każdego wiersza kodu możesz zatrzymać wskaźnik myszy na zmiennych, aby [](watch-and-quickwatch-windows.md) wyświetlić ich wartości, lub użyć okien Zmiennych lokalnych i Czujka, aby obserwować zmiany wartości. [](autos-and-locals-windows.md) Możesz również wizualnie śledzić stos [wywołań podczas](how-to-use-the-call-stack-window.md) przechodzenia do funkcji. (Aby uzyskać Visual Studio Enterprise, zobacz [Map methods on the call stack while debugging (Metody mapowania na stosie wywołań podczas debugowania).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Przechodzenie przez kod i pomijanie niektórych funkcji

Funkcja podczas debugowania może nie być dla Ciebie lub wiesz, że działa, jak dobrze przetestowany kod biblioteki. Aby pominąć kod podczas krokowego wykonywanie kodu, można użyć następujących poleceń. Funkcje są nadal wykonywane, ale debuger pomija je.

|Polecenie klawiatury|Polecenie menu Debugowanie|Opis|
|----------------------|------------------|-----------------|
|**F10**|**Krok po kroku**|Jeśli bieżący wiersz zawiera wywołanie funkcji, funkcja **Step Over** uruchamia kod, a następnie wstrzymuje wykonywanie w pierwszym wierszu kodu po zwracaniu przez wywołaną funkcję.|
|**Shift (Przesunięcie)** + **F11**|**Wyetapuj**|**Funkcja Step Out** kontynuuje uruchamianie kodu i wstrzymuje wykonywanie po powrocie bieżącej funkcji. Debuger pomija bieżącą funkcję.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchamianie do określonej lokalizacji lub funkcji

Możesz wolisz uruchamiać skrypty bezpośrednio w określonej lokalizacji lub funkcji, gdy dokładnie wiesz, jaki kod chcesz sprawdzić, lub wiesz, gdzie chcesz rozpocząć debugowanie.

### <a name="run-to-a-breakpoint-in-code"></a>Uruchamianie w punkcie przerwania w kodzie

Aby ustawić prosty punkt przerwania w kodzie, kliknij lewy margines obok wiersza kodu, w którym chcesz wstrzymać wykonywanie. Możesz również zaznaczyć wiersz i nacisnąć klawisz **F9,** wybrać **pozycję**  >  **Debuguj Przełącz** punkt przerwania lub kliknąć prawym przyciskiem myszy i wybrać pozycję **Wstaw**  >  **punkt przerwania.** Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie obok wiersza kodu. Debuger wstrzymuje wykonywanie tuż przed wykonaniem wiersza.

![Ustawianie punktu przerwania](../debugger/media/dbg_basics_setbreakpoint.png "Ustawianie punktu przerwania")

Punkty przerwania w Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Aby uzyskać szczegółowe informacje, [zobacz Using breakpoints (Używanie punktów przerwania).](../debugger/using-breakpoints.md)

### <a name="run-to-a-function-breakpoint"></a>Uruchamianie w punkcie przerwania funkcji

Możesz poinformować debuger, aby działał do momentu osiągnięcia określonej funkcji. Możesz określić funkcję według nazwy lub wybrać ją ze stosu wywołań.

**Aby określić punkt przerwania funkcji według nazwy**

1. Wybieranie **opcji**  >  **Debuguj nowy punkt przerwania** funkcji punktu  >  **przerwania**

1. W **oknie dialogowym Nowy** punkt przerwania funkcji wpisz nazwę funkcji i wybierz jej język.

   ![Okno dialogowe Nowego punktu przerwania funkcji](../debugger/media/dbg_execution_newbreakpoint.png "Nowy punkt przerwania funkcji")

1. Wybierz przycisk **OK**.

Jeśli funkcja jest przeciążona lub znajduje się w więcej niż jednej przestrzeni nazw, możesz wybrać tę, która ma być w oknie **Punkty przerwania.**

![Punkty przerwania przeciążonych funkcji](../debugger/media/dbg_execution_overloadedbreakpoints.png "Przeciążone punkty przerwania funkcji")

**Aby wybrać punkt przerwania funkcji ze stosu wywołań**

1. Podczas debugowania otwórz okno **Stos wywołań,** wybierając pozycję **Debuguj**  >  **stos**  >  **wywołań systemu** Windows .

1. W **oknie Stos wywołań** kliknij prawym przyciskiem myszy funkcję i wybierz polecenie Uruchom do **kursora** lub naciśnij **klawisz Ctrl** + **F10.**

Aby wizualnie śledzić stos wywołań, zobacz [Metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Uruchamianie w lokalizacji kursora

Aby uruchomić polecenie w lokalizacji kursora, w kodzie źródłowym lub w oknie Stos wywołań wybierz wiersz, w którym chcesz przerwać, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom** do kursora lub naciśnij **klawisz Ctrl**  + **F10.** Wybranie **pozycji Uruchom do kursora** przypomina ustawienie tymczasowego punktu przerwania.

### <a name="run-to-click"></a>Uruchom do kliknięcia

Po wstrzymaniu w debugerze można zatrzymać wskaźnik myszy na instrukcji w  kodzie źródłowym lub w oknie Dezasembletowanie, a następnie wybrać ikonę Zielonej strzałki Uruchom wykonywanie do tego miejscu.  Użycie **funkcji Uruchom do kliknięcia** eliminuje konieczność ustawienia tymczasowego punktu przerwania.

![Uruchom do kliknięcia](../debugger/media/dbg-run-to-click.png "Uruchom do kliknięcia")

> [!NOTE]
> **Polecenie Uruchom do kliknięcia** jest dostępne począwszy od wersji [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

### <a name="manually-break-into-code"></a>Ręczne włamanie do kodu

Aby przerwać następny dostępny wiersz kodu w uruchomionej aplikacji, wybierz pozycję   >  **Debuguj** przerwij wszystko lub naciśnij **klawisze Ctrl** + **Alt** + **Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Przenoszenie wskaźnika w celu zmiany przepływu wykonywania

Gdy debuger jest **wstrzymany,** żółta strzałka na marginesie kodu źródłowego lub w oknie Dezasembera oznacza lokalizację następnej instrukcji do wykonania. Możesz zmienić następną instrukcje do wykonania, przesuwając tę strzałkę. Możesz pominąć część kodu lub wrócić do poprzedniego wiersza. Przesuwanie wskaźnika jest przydatne w sytuacjach takich jak pominięcie sekcji kodu zawierającej znaną usterkę.

 ![Przenoszenie wskaźnika](../debugger/media/dbg_basics_example3.gif "Przenoszenie wskaźnika")

Aby zmienić następną instrukcje do wykonania, debuger musi być w trybie przerwania. W oknie  kodu źródłowego lub dezasembrację przeciągnij żółtą strzałkę do innego wiersza lub kliknij prawym przyciskiem myszy wiersz, który chcesz wykonać, a następnie wybierz pozycję **Ustaw następną instrukcje**.

Licznik programu przechodzi bezpośrednio do nowej lokalizacji, a instrukcje między starymi i nowymi punktami wykonywania nie są wykonywane. Jeśli jednak przeniesiesz punkt wykonywania do tyłu, instrukcje interwencji nie są cofane.

>[!CAUTION]
>- Przeniesienie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek czasu działania. Jeśli spróbujesz przeniesienie następnej instrukcji do innego zakresu, debuger otworzy okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji.
>- W Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.
>- W natywnym języku C++, jeśli włączono sprawdzanie w czasie wykonywania, ustawienie następnej instrukcji może spowodować wyjątek, gdy wykonanie osiągnie koniec metody.
>- Gdy funkcja Edytuj i  kontynuuj jest włączona, ustawienie następnej instrukcji kończy się niepowodzeniem, jeśli w edycjach nie można natychmiast ponownie mapować opcji Edytuj i kontynuuj. Taka możliwość może wystąpić na przykład w przypadku edytowania kodu wewnątrz bloku catch. W takim przypadku zostanie wyświetlony komunikat o błędzie informujący, że operacja nie jest obsługiwana.
>- W kodzie zarządzanym nie można przenieść następnej instrukcji, jeśli:
>   - Następna instrukcja znajduje się w innej metodzie niż bieżąca instrukcja.
>   - Debugowanie zostało rozpoczęte przez debugowanie just in time.
>   - Trwa odwijanie stosu wywołań.
>   - Zgłaszany jest wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debugowanie kodu bez użytkownika

Domyślnie debuger próbuje debugować tylko kod aplikacji, włączając ustawienie o *nazwie Tylko mój kod*. Aby uzyskać więcej informacji o tym, jak ta funkcja działa dla różnych typów projektów i języków oraz jak można ją dostosować, zobacz [Tylko mój kod](../debugger/just-my-code.md).

Aby przyjrzeć się kodowi struktury, kodowi biblioteki innej firmy lub wywołaniom systemowym podczas debugowania, możesz wyłączyć Tylko mój kod. W **oknie** **Narzędzia**(lub Debugowanie ) > **debugowania** opcji wyczyść pole wyboru Włącz Tylko mój kod  >  debugowania.  Gdy Tylko mój kod jest wyłączona, w oknach debugera jest wyświetlany kod niebędący użytkownikiem, a debuger może przejść do kodu bez użytkownika.

> [!NOTE]
> Tylko mój kod nie jest obsługiwana w projektach urządzeń.

### <a name="debug-system-code"></a>Debugowanie kodu systemowego

Jeśli załadowano symbole debugowania dla kodu systemowego firmy Microsoft i wyłączono Tylko mój kod, możesz przejść do wywołania systemowego tak samo jak w przypadku każdego innego wywołania.

Aby załadować symbole firmy Microsoft, [zobacz Configure symbol locations and loading options](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)(Konfigurowanie lokalizacji symboli i opcji ładowania).

**Aby załadować symbole dla określonego składnika systemu:**

1. Podczas debugowania otwórz okno  Moduły, wybierając pozycję **Debuguj** moduły  >  **systemu Windows**  >  lub naciskając **klawisze Ctrl** + **Alt** + **U.**

1. W **oknie** Moduły możesz określić, które moduły mają symbole załadowane w **kolumnie Stan** symboli. Kliknij prawym przyciskiem myszy moduł, dla którego chcesz załadować symbole, a następnie wybierz **pozycję Załaduj symbole**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Krok do właściwości i operatorów w kodzie zarządzanym
 Debuger domyślnie przejmuje kroki nad właściwościami i operatorami w kodzie zarządzanym. W większości przypadków zapewnia to lepsze środowisko debugowania. Aby włączyć przechodzenie do właściwości lub operatorów, wybierz **pozycję Opcje**  >  **debugowania.** Na stronie **Ogólne** debugowanie wyczyść pole wyboru Przek osuń  >   właściwości **i operatory (tylko** zarządzane).

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
