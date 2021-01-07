---
title: Nawigowanie po kodzie za pomocą debugera | Microsoft Docs
description: 'Dowiedz się, jak rozwiązywać problemy z kodem za pomocą debugera programu Visual Studio. Tematy obejmują: poruszanie się w tryb przerwania, krokowe przechodzenie przez kod i uruchamianie do obiektu docelowego.'
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffe163ab567de98161f185ba2f3d2522c505095
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975215"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Nawigowanie po kodzie za pomocą debugera programu Visual Studio

Debuger programu Visual Studio może pomóc w nawigowaniu po kodzie, aby sprawdzić stan aplikacji i pokazać swój przepływ wykonania. Za pomocą skrótów klawiaturowych, poleceń debugowania, punktów przerwania i innych funkcji można szybko uzyskać dostęp do kodu, który ma zostać sprawdzony. Znajomość poleceń nawigacyjnych debugera i skrótów ułatwia szybkie i łatwiejsze znajdowanie i rozwiązywanie problemów z aplikacjami.

> [!NOTE]
> Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="get-into-break-mode"></a>Zapoznaj się z "trybem przerwania"

W *trybie przerwania* wykonywanie aplikacji jest zawieszone, gdy funkcje, zmienne i obiekty pozostają w pamięci. Gdy debuger jest w trybie przerwania, można nawigować po kodzie. Najczęstszym sposobem na szybkie rozpoczęcie pracy w trybie przerwania jest:

- Rozpocznij krokowe wykonywanie kodu, naciskając klawisz **F10** lub **F11**. Dzięki temu można szybko znaleźć punkt wejścia aplikacji, a następnie nacisnąć polecenia krok po kroku, aby poruszać się po kodzie.

- [Uruchom do określonej lokalizacji lub funkcji](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), na przykład przez [ustawienie punktu przerwania](using-breakpoints.md) i uruchomienie aplikacji.

   Na przykład w edytorze kodu w programie Visual Studio można użyć polecenia **Uruchom do kursora** , aby uruchomić aplikację, debuger dołączony i przejść do trybu przerwania, a następnie klawisza **F11** , aby nawigować po kodzie.

   ![Uruchom do kursora i przejdź do kodu](../debugger/media/navigate-code-code-stepping.gif "Uruchom do kursora i przejdź do kodu")

W trybie przerwania można użyć różnych poleceń do nawigowania po kodzie. W trybie przerwania można sprawdzić wartości zmiennych, aby wyszukać naruszenia lub błędy. W przypadku niektórych typów projektów można także wprowadzić zmiany w aplikacji w trybie przerwania.

Większość okien debugera, takich jak **moduły** i okna **czujki** , jest dostępna tylko wtedy, gdy debuger jest dołączony do aplikacji. Niektóre funkcje debugera, takie jak wyświetlanie wartości zmiennych w oknie zmiennych **lokalnych** lub ocenianie wyrażeń w oknie **czujki** , są dostępne tylko podczas wstrzymania debugera (czyli w trybie przerwania).

> [!NOTE]
> Jeśli połączysz się z kodem, który nie ma załadowanych plików źródłowych lub symboli (*. pdb*), debuger wyświetli **pliki źródłowe** , które nie zostały znalezione lub **nie znaleziono symboli** , które mogą pomóc w znalezieniu i załadowaniu plików. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie można załadować symboli lub plików źródłowych, można nadal debugować instrukcje zestawu w oknie **demontażu** .

## <a name="step-through-code"></a>Przejdź do kodu

Polecenia kroku debugera ułatwiają sprawdzenie stanu aplikacji lub Dowiedz się więcej na temat jego przepływu wykonania.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Wkrocz do wiersza kodu według wiersza

Aby zatrzymać każdą instrukcję podczas debugowania, użyj kroku **Debuguj**  >  **do** lub naciśnij klawisz **F11**.

Kroki debugera za pomocą instrukcji kodu, a nie linii fizycznych. Na przykład `if` klauzula może być zapisywana w jednym wierszu:

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

Jednak po przekroczeniu tego wiersza debuger traktuje warunek jako jeden krok, a także sekwencję inną. W poprzednim przykładzie warunek ma wartość true.

W przypadku wywołania funkcji zagnieżdżonej **Przejdź** do kroków do najbardziej głęboko zagnieżdżonej funkcji. Na przykład jeśli używasz **kroku do** wywołania `Func1(Func2())` , jak, debuger przeprowadzi do funkcji `Func2` .

>[!TIP]
>Gdy wykonujesz każdy wiersz kodu, możesz umieścić wskaźnik myszy nad zmiennymi, aby zobaczyć ich wartości, lub użyć okien [lokalnych](autos-and-locals-windows.md) i [czujki](watch-and-quickwatch-windows.md) , aby obejrzeć zmiany wartości. Możesz również wizualnie śledzić [stos wywołań](how-to-use-the-call-stack-window.md) podczas przechodzenia do funkcji. (Aby uzyskać tylko Visual Studio Enterprise, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Przechodzenie przez kod i pomijanie niektórych funkcji

Podczas debugowania nie można zadbać o to, czy wiadomo, że działa, jak również kod biblioteki, który został przetestowany. Poniższe polecenia służą do pomijania kodu podczas wykonywania kodu. Funkcje są nadal wykonywane, ale debuger pominie je.

|Polecenie klawiatury|Polecenie menu Debuguj|Opis|
|----------------------|------------------|-----------------|
|**F10**|**Przekrocz nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji, **krok powyżej** uruchamia kod, a następnie wstrzymuje wykonywanie w pierwszym wierszu kodu po wywołaniu wywołanej funkcji.|
|**SHIFT** + Klawisz **F11**|**Wyjdź**|**Krok** Wyjdź kontynuuje uruchamianie kodu i wstrzymuje wykonywanie, gdy bieżąca funkcja zwraca wartość. Debuger pomija bieżącą funkcję.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchom do określonej lokalizacji lub funkcji

Być może wolisz pracować bezpośrednio z określoną lokalizacją lub funkcją, gdy dokładnie wiesz, jaki kod chcesz sprawdzić, lub wiesz, gdzie chcesz rozpocząć debugowanie.

### <a name="run-to-a-breakpoint-in-code"></a>Uruchom do punktu przerwania w kodzie

Aby ustawić prosty punkt przerwania w kodzie, kliknij skrajnie lewy margines obok wiersza kodu, w którym chcesz wstrzymać wykonywanie. Można również zaznaczyć wiersz i nacisnąć klawisz **F9**, wybrać pozycję **Debuguj**  >  **Przełącz punkt przerwania** lub kliknąć prawym przyciskiem myszy i wybrać **punkt** przerwania  >  **Wstaw punkt przerwania**. Punkt przerwania jest wyświetlany jako czerwona kropka w lewym marginesie obok wiersza kodu. Debuger zawiesza wykonywanie tuż przed wykonaniem wiersza.

![Ustawianie punktu przerwania](../debugger/media/dbg_basics_setbreakpoint.png "Ustawianie punktu przerwania")

Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Aby uzyskać szczegółowe informacje, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Uruchom do punktu przerwania funkcji

Możesz powiedzieć, że debuger zostanie uruchomiony do momentu, aż osiągnie określoną funkcję. Można określić funkcję według nazwy lub wybrać ją ze stosu wywołań.

**Aby określić punkt przerwania funkcji według nazwy**

1. Wybierz pozycję **Debuguj**  >  **Nowy** punkt  >  **przerwania funkcji**

1. W oknie dialogowym **nowy punkt przerwania funkcji** wpisz nazwę funkcji i wybierz jej język.

   ![Nowe okno dialogowe punktu przerwania funkcji](../debugger/media/dbg_execution_newbreakpoint.png "Nowy punkt przerwania funkcji")

1. Wybierz przycisk **OK**.

Jeśli funkcja jest przeciążona lub w więcej niż jednej przestrzeni nazw, możesz wybrać odpowiedni element w oknie **punkty przerwania** .

![Przeciążone punkty przerwania funkcji](../debugger/media/dbg_execution_overloadedbreakpoints.png "Przeciążone punkty przerwania funkcji")

**Aby wybrać punkt przerwania funkcji ze stosu wywołań**

1. Podczas debugowania Otwórz okno **stos wywołań** , wybierając pozycję **Debuguj**  >    >  **stos wywołań** systemu Windows.

1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję i wybierz polecenie **Uruchom do kursora** lub naciśnij klawisz **Ctrl** + **F10**.

Aby wizualnie śledzić stos wywołań, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Uruchom do lokalizacji kursora

Aby uruchomić do lokalizacji kursora, w kodzie źródłowym lub oknie **stosu wywołań** , zaznacz wiersz, który chcesz przerwać, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom do kursora** lub naciśnij klawisz **Ctrl** + **F10**. Wybranie opcji **Uruchom do kursora** przypomina ustawienie tymczasowego punktu przerwania.

### <a name="run-to-click"></a>Uruchom do kliknięcia

W debugerze można umieścić wskaźnik myszy nad instrukcją w kodzie źródłowym lub w oknie **demontażu** , a następnie wybrać ikonę **Uruchom wykonywanie do tutaj** zieloną strzałkę. Użycie polecenia **Uruchom do kliknięcia** eliminuje konieczność ustawienia tymczasowego punktu przerwania.

![Uruchom do kliknięcia](../debugger/media/dbg-run-to-click.png "Uruchom do kliknięcia")

> [!NOTE]
> **Polecenie Uruchom do kliknięcia** jest dostępne od początku [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

### <a name="manually-break-into-code"></a>Ręczne przebicie na kod

Aby przerwać w następnym dostępnym wierszu kodu w działającej aplikacji, wybierz kolejno opcje **Debuguj**  >  **Przerwij wszystkie** lub naciśnij **klawisze CTRL** + **Alt** + **Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Przesuń wskaźnik, aby zmienić przepływ wykonywania

Gdy debuger jest wstrzymany, żółta strzałka na marginesie kodu źródłowego lub okna **demontażu** oznacza lokalizację następnej instrukcji do wykonania. Możesz zmienić następną instrukcję, aby wykonać, przenosząc tę grot strzałki. Możesz pominąć część kodu lub powrócić do poprzedniego wiersza. Przesuwanie wskaźnika jest przydatne w przypadku sytuacji, takich jak pomijanie sekcji kodu zawierającej znaną usterkę.

 ![Przenoszenie wskaźnika](../debugger/media/dbg_basics_example3.gif "Przenoszenie wskaźnika")

Aby zmienić następną instrukcję do wykonania, debuger musi być w trybie przerwania. W oknie kod źródłowy lub **demontaż** przeciągnij żółtą grot strzałki w inny wiersz lub kliknij prawym przyciskiem myszy wiersz, który chcesz wykonać w następnej kolejności, i wybierz polecenie **Ustaw następną instrukcję**.

Licznik programu przechodzi bezpośrednio do nowej lokalizacji, a instrukcje między starym i nowym punktem wykonywania nie są wykonywane. Jeśli jednak przeniesiesz punkt wykonania wstecz, instrukcje dotyczące interwencji nie zostaną cofnięte.

>[!CAUTION]
>- Przeniesienie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, co powoduje błąd lub wyjątek czasu wykonywania. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji.
>- W Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.
>- W natywnym języku C++, jeśli włączono sprawdzanie w czasie wykonywania, ustawienie następnej instrukcji może spowodować wystąpienie wyjątku, gdy wykonanie osiągnie koniec metody.
>- Gdy funkcja Edytuj i Kontynuuj jest włączona, **Ustawianie następnej instrukcji** kończy się niepowodzeniem, jeśli wprowadzono zmiany, które edytują i kontynuują, nie można od razu ponownie mapować. Może się to zdarzyć na przykład w przypadku edytowania kodu wewnątrz bloku catch. W takim przypadku zostanie wyświetlony komunikat o błędzie informujący o tym, że operacja nie jest obsługiwana.
>- W kodzie zarządzanym nie można przenieść następnej instrukcji, jeśli:
>   - Następna instrukcja znajduje się w innej metodzie niż bieżąca.
>   - Debugowanie zostało rozpoczęte przez debugowanie just in Time.
>   - Odwinięcie stosu wywołań jest w toku.
>   - Zgłoszono wyjątek System. StackOverflowException lub system. Threading. ThreadAbortException.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debuguj kod niebędący użytkownikiem

Domyślnie debuger próbuje debugować tylko kod aplikacji przez włączenie ustawienia o nazwie *tylko mój kod*. Aby uzyskać więcej informacji o tym, jak działa ta funkcja dla różnych typów projektów i języków oraz jak można je dostosować, zobacz [tylko mój kod](../debugger/just-my-code.md).

Aby wyszukać kod struktury, kod biblioteki innej firmy lub wywołania systemowe podczas debugowania, można wyłączyć Tylko mój kod. W oknie **Narzędzia** (lub **Debuguj**) >  >  **debugowanie** opcji Wyczyść pole wyboru **Włącz tylko mój kod** . Gdy Tylko mój kod jest wyłączona, kod niebędący użytkownikiem zostanie wyświetlony w oknach debugera, a debuger może przejść do kodu niezwiązanego z użytkownikiem.

> [!NOTE]
> Tylko mój kod nie jest obsługiwana w przypadku projektów urządzeń.

### <a name="debug-system-code"></a>Debuguj kod systemu

Jeśli załadowałeś symbole debugowania dla kodu systemowego firmy Microsoft i wyłączono Tylko mój kod, możesz przejść do wywołania systemowego tak samo jak w przypadku każdego innego wywołania.

Aby załadować symbole firmy Microsoft, zobacz [Konfigurowanie lokalizacji symboli i opcji ładowania](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Aby załadować symbole dla określonego składnika systemu:**

1. Podczas debugowania Otwórz okno **moduły** , wybierając pozycję **Debuguj**  >  **moduły systemu Windows**  >  lub naciśnij **klawisze CTRL** + **Alt** + **U**.

1. W oknie **moduły** można określić, które moduły mają symbole załadowane w kolumnie **stan symbolu** . Kliknij prawym przyciskiem myszy moduł, dla którego chcesz załadować symbole, a następnie wybierz pozycję **Załaduj symbole**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Wkrocz do właściwości i operatorów w kodzie zarządzanym
 Debuger domyślnie krokowo przekracza właściwości i operatory w kodzie zarządzanym. W większości przypadków zapewnia to lepsze środowisko debugowania. Aby włączyć krokowe przechodzenie do właściwości lub operatorów , wybierz  >  **Opcje** debugowania. Na stronie   >  **Ogólne** debugowanie wyczyść pole wyboru **Przekrocz nad właściwościami i operatorami (tylko zarządzane)** .

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
