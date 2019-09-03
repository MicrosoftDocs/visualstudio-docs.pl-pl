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
ms.openlocfilehash: e07e2612e01453115cf4cd6120d92bfd5b0168bd
ms.sourcegitcommit: fe212f8960d7882a1b0fdae9e22f008996aacf3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222652"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Nawigowanie po kodzie za pomocą debugera programu Visual Studio

Debuger programu Visual Studio może pomóc w nawigowaniu po kodzie, aby sprawdzić stan aplikacji i wyświetlić jego przepływ wykonania. Skróty klawiaturowe, poleceń debugowania, punkty przerwania i inne funkcje umożliwia szybki dostęp do kodu, który chcesz zbadać. Znajomość poleceń nawigacji debugera i skróty umożliwia szybsze i łatwiejsze do znajdowania i rozwiązywania problemów z aplikacjami.  Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla](../debugger/debugging-absolute-beginners.md) bezwzględnych [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="basic-debugging"></a>Debugowanie podstawowe

Aby uruchomić aplikację w debugerze, naciśnij klawisz **F5**, wybierz opcję **debugowania** > **Rozpocznij debugowanie**, lub wybierz zieloną strzałkę na pasku narzędzi programu Visual Studio.

 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")

Podczas debugowania, wyróżnij żółty pokazuje wiersza kodu, które spowodują wykonanie następnego.

 ![DBG&#95;podstawy&#95;Przerwij&#95;tryb](../debugger/media/dbg_basics_break_mode.png "trybie przerwania")

Najbardziej debugera, takie jak **modułów** i **Obejrzyj** systemu windows, są dostępne tylko w przypadku, gdy debuger jest uruchomiona. Niektóre funkcje debugera, takie jak wyświetlanie wartości zmiennych w **lokalne** okna lub oceny wyrażenia w **Obejrzyj** okna, są dostępne tylko w przypadku, gdy debuger jest wstrzymana w punkcie przerwania, nazywany również *trybu przerwania*.

W trybie przerwania wykonanie aplikacji jest wstrzymana podczas funkcje, zmienne i obiekty pozostają w pamięci. Można sprawdzić pozycje elementów i Stany, aby szukać naruszeń lub błędów. W przypadku niektórych typów projektu może również wprowadzać zmiany do aplikacji w trybie przerwania. Film przedstawiający tych funkcji, zobacz [wprowadzenie do debugera](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Jeśli przerwiesz w kodzie, który nie ma źródłowych lub symboli ( *.pdb*) pliki ładowane, debuger wyświetla **nie znaleziono źródła plików** lub **nie można odnaleźć symboli** strona, która pomoże Ci Znajdź i Załaduj pliki. Zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie można załadować plików symboli lub źródłowych, nadal możesz debugować instrukcje montażu w **dezasemblacji** okna.

Zawsze masz nie można rozpocząć debugowania, uruchamiając aplikację na początku. Można również nacisnąć klawisz **F11** do [kodu krok po kroku](#BKMK_Step_into__over__or_out_of_the_code), naciśnij klawisz **F10** do [Przekrocz nad kodem](#BKMK_Step_over_Step_out), lub [uruchomić do określonej lokalizacji lub Funkcja](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).

## <a name="step-through-code"></a>Przejść przez kod

Polecenia kroku debugera pomóc sprawdzić stan swojej aplikacji lub dowiedzieć się więcej o przepływ jego wykonania.

Jeśli musisz odnaleźć punktu wejścia w swojej aplikacji, skorzystaj z **F10** lub **F11**.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Wejdź do kodu wiersz po wierszu

Aby zatrzymać, w każdym wierszu kodu lub instrukcji podczas debugowania, użyj **debugowania** > **Step Into**, lub naciśnij **F11**.

Debuger nie wchodzi przez instrukcje kodu, a nie fizyczne wiersze. Na przykład `if` klauzuli mogą być zapisywane w jednym wierszu:

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

W wywołaniu funkcji zagnieżdżonej **Step Into** wchodzi do najgłębiej zagnieżdżonej funkcji. Na przykład, jeśli używasz **Step Into** przy wywołaniu, takich jak `Func1(Func2())`, debuger wchodzi do funkcji `Func2`.

>[!TIP]
>Podczas wykonywania wszystkich wierszy kodu, możesz umieścić kursor zmienne, aby zobaczyć ich wartości lub użyć [lokalne](autos-and-locals-windows.md) i [Obejrzyj](watch-and-quickwatch-windows.md) systemu windows, aby obejrzeć wartości zmiany. Można również wizualnie śledzić stos wywołań, wchodząc krok do funkcji. Zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="BKMK_Step_over_Step_out"></a> Przejść przez kod i pominąć niektóre funkcje

Może nie interesują funkcji podczas debugowania lub znasz jego działania, takie jak kod dobrze przetestowanych biblioteki. Można użyć następujących poleceń, aby przejść przez kod. Nadal wykonywać funkcje, ale debuger pomija nad nimi.

|Polecenie klawiatury|Debugowanie polecenia menu|Opis|
|----------------------|------------------|-----------------|
|**F10**|**Przekrocz nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji **Step Over** uruchamia kod, a następnie zawiesza wykonywanie w pierwszym wierszu kodu po powrocie wywołanej funkcji.|
|**SHIFT**+**F11**|**Wyjdź**|**Step Out** kontynuuje wykonywanie kodu, a następnie zawiesza wykonywanie, gdy zwraca bieżącą funkcję. Debuger pomija za pomocą bieżącej funkcji.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchamianie do określonej lokalizacji lub funkcji

Użytkownik może chcieć uruchomić bezpośrednio do określonej lokalizacji lub funkcji, gdy wiesz, jaki dokładnie kod chcesz sprawdzić lub wiesz, gdzie chcesz rozpocząć debugowanie.

### <a name="run-to-a-breakpoint-in-code"></a>Uruchom do punktu przerwania w kodzie

Aby ustawić prosty punkt przerwania w kodzie, kliknij przycisk po lewej stronie margines obok wiersza kodu, na którym ma się zawiesić wykonanie. Możesz również wybrać wiersza i naciśnij klawisz **F9**, wybierz opcję **debugowania** > **Przełącz punkt przerwania**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **punktuprzerwania**  >  **Wstaw punkt przerwania**. Punkt przerwania pojawia się jako czerwona kropka na lewym marginesie obok wiersza kodu. Debuger zawiesza wykonywanie tylko w przypadku, przed wykonaniem wiersza.

![Ustaw punkt przerwania](../debugger/media/dbg_basics_setbreakpoint.png "Ustaw punkt przerwania")

Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Aby uzyskać więcej informacji, zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Uruchom do punktu przerwania funkcji

Można polecić debugerowi, aby uruchomić, dopóki nie osiągnie określoną funkcję. Można określić funkcję według nazwy lub możesz ją wybrać spośród stosu wywołań.

**Do określenia punktu przerwania funkcji według nazwy**

1. Wybierz **debugowania** > **nowego punktu przerwania** > **funkcji punktu przerwania**

1. W **nowy punkt przerwania funkcji** okno dialogowe, wpisz nazwę funkcji, a następnie wybierz jego język.

   ![Okno dialogowe Nowy punkt przerwania funkcji](../debugger/media/dbg_execution_newbreakpoint.png "nowy punkt przerwania funkcji")

1. Wybierz **OK**.

Jeśli funkcja jest przeciążona lub w więcej niż jednej przestrzeni nazw, możesz wybrać odpowiedni w **punktów przerwania** okna.

![Punkty przerwania funkcji przeciążonych](../debugger/media/dbg_execution_overloadedbreakpoints.png "przeciążone punkty przerwania funkcji")

**Aby wybrać punktu przerwania funkcji ze stosu wywołań**

1. Podczas debugowania, należy otworzyć **stos wywołań** okna, wybierając **debugowania** > **Windows** > **stos wywołań**.

1. W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcję i wybierz **Uruchom do kursora**, lub naciśnij **Ctrl**+**F10**.

Aby wizualnie śledzić stos wywołań, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Uruchom do lokalizacji kursora

Aby uruchomić do lokalizacji kursora, w kodzie źródłowym lub **stos wywołań** okna, zaznacz wiersz, aby przerwać, kliknij prawym przyciskiem myszy i wybierz **Uruchom do kursora**, lub naciśnij **Ctrl** + **F10**. Wybieranie **Uruchom do kursora** przypomina ustawienie tymczasowy punkt przerwania.

### <a name="run-to-click"></a>Uruchom do kliknięcia

Gdy wstrzymaniu w debugerze, możesz umieścić kursor instrukcji w kodzie źródłowym lub **dezasemblacji** okna, a następnie wybierz **uruchom wykonywanie do tego miejsca** zielona strzałka. Za pomocą **uruchamianie do kliknięcia** eliminuje potrzebę ustawienia tymczasowy punkt przerwania.

![Uruchamianie do kliknięcia](../debugger/media/dbg-run-to-click.png "uruchamianie do kliknięcia")

> [!NOTE]
> **Polecenie Uruchom do kliknięcia** jest dostępne od [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]początku.

### <a name="manually-break-into-code"></a>Ręcznie Wejdź do kodu

Włamanie się następnego dostępnego wiersza kodu w uruchomionej aplikacji, wybierz **debugowania** > **Przerwij wszystkie**, lub naciśnij **Ctrl**+**Alt**  + **Przerwij**.

## <a name="BKMK_Set_the_next_statement_to_execute"></a> Przenieść wskaźnik, aby zmienić przepływ wykonania

Gdy debuger jest wstrzymany, żółty grot strzałki na marginesie kodu źródłowego lub **dezasemblacji** okno oznacza lokalizację następnej instrukcji do wykonania. Można zmienić następnej instrukcji do wykonania, przesuwając ten grot strzałki. Możesz pominąć część kodu lub powrócić do poprzedniego wiersza. Przeniesienie wskaźnika jest przydatne w sytuacjach, takich jak pomijanie sekcji kodu, który zawiera znany błąd.

 ![Przesuń wskaźnik](../debugger/media/dbg_basics_example3.gif "przesuwania wskaźnika")

Aby zmienić następnej instrukcji do wykonania, debuger musi być w trybie przerwania. W kodzie źródłowym lub **dezasemblacji** okna, przeciągnij żółty grot strzałki do innego wiersza lub kliknij prawym przyciskiem myszy wiersz, którego chcesz wykonać w następnej kolejności, a następnie wybierz pozycję **Ustaw następną instrukcję**.

Licznik programu przechodzi bezpośrednio do nowej lokalizacji i instrukcje między wykonywania stare i nowe punkty nie są wykonywane. Jednak jeśli przeniesiesz punkt wykonania Wstecz, instrukcje interwencyjne nie są cofnąć.

>[!CAUTION]
>- Przenoszenie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji.
>- W języku Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.
>- W natywnym kodzie C++ zostały włączone, kontrole czasu wykonywania ustawienie następnej instrukcji może spowodować wyjątek zgłaszany, gdy wykonywanie osiągnie koniec metody.
>- Gdy Edytuj i Kontynuuj jest włączona, **Ustaw następną instrukcję** kończy się niepowodzeniem, jeśli zostały wprowadzone zmiany, których Edytuj i Kontynuuj nie może od razu ponownie zamapować. Może to występować, na przykład, jeśli edytowano kod wewnątrz bloku catch. W takim przypadku komunikat o błędzie informujący o tym, że operacja nie jest obsługiwany.
>- W kodzie zarządzanym nie można przenieść następnej instrukcji, jeśli:
>   - Następna instrukcja znajduje się w innej metodzie niż bieżąca instrukcja.
>   - Debugowanie zostało uruchomione przez Just-In-Time debugowania.
>   - Odwijania stosu wywołań jest w toku.
>   - Został zgłoszony wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Możliwe jest debugowanie kodu niepochodzącego od użytkownika

Domyślnie debuger podejmie próbę debugowania tylko kodu aplikacji, należy włączyć ustawienie o nazwie *tylko mój kod*. Aby uzyskać więcej informacji o różnych typach projektów i języków, jak działa ta funkcja i jak można go dostosować, zobacz [tylko mój kod](../debugger/just-my-code.md).

Aby wyświetlić kod framework, kod biblioteki innych firm lub wywołań systemowych podczas debugowania, można wyłączyć opcję tylko mój kod. W **narzędzia** (lub **debugowania**) > **opcje** > **debugowanie**, wyczyść **Włącz tylko mój kod** pole wyboru. Po wyłączeniu tylko mój kod niebędący kodem użytkownika jest wyświetlana w oknach debugera, a debuger może wkroczyć do kodu niepochodzącego od użytkownika.

> [!NOTE]
> Tylko mój kod nie jest obsługiwana dla projektów urządzenia.

### <a name="debug-system-code"></a>Możliwe jest debugowanie kodu systemu

Jeśli masz załadowane symbole debugowania dla kodu systemu Microsoft i wyłączyć opcję tylko mój kod, możesz wejść do wywołania systemowego tak samo jak inne wywołania.

Aby załadować symbole firmy Microsoft, zobacz [skonfigurować lokalizacje symboli i ładowania opcji](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Aby załadować symbole dla określonego składnika systemu:**

1. Podczas debugowania, otwórz **modułów** okna, wybierając **debugowania** > **Windows** > **modułów**, lub naciskając **Ctrl**+**Alt**+**U**.

1. W **modułów** okna, można sprawdzić, co moduły mają załadowane w symbole **stan symboli** kolumny. Kliknij prawym przyciskiem myszy moduł, który chcesz załadować symbole, a następnie wybierz pozycję **załadować symbole**.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Wejdź do właściwości i operatory w kodzie zarządzanym
 Debuger nie wchodzi we właściwości i operatory w kodzie zarządzanym domyślnie. W większości przypadków zapewnia to lepszy proces debugowania. Aby włączyć przechodzenie krok po kroku do właściwości lub operatorów, wybierz opcję **debugowania** > **opcje**. Na **debugowanie** > **ogólne** strony, wyczyść **Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)** pole wyboru.

## <a name="see-also"></a>Zobacz także
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Techniki i narzędzia debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md)
