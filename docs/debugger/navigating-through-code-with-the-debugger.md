---
title: Nawigowanie po kodzie za pomocą debugera | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302120"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Poruszanie się po kodzie za pomocą debugera programu Visual Studio

Debuger programu Visual Studio może pomóc w nawigowania po kodzie, aby sprawdzić stan aplikacji i pokazać jej przepływ wykonywania. Można użyć skrótów klawiaturowych, poleceń debugowania, punktów przerwania i innych funkcji, aby szybko przejść do kodu, który chcesz sprawdzić. Znajomość poleceń nawigacyjnych debugera i skrótów sprawia, że szybsze i łatwiejsze znajdowanie i rozwiązywanie problemów z aplikacją.  Jeśli jest to pierwszy raz, który próbowałeś debugować kod, można przeczytać [debugowanie dla początkujących absolutnych](../debugger/debugging-absolute-beginners.md) i [debugowanie technik i narzędzi](../debugger/write-better-code-with-visual-studio.md) przed przejściem przez ten artykuł.

## <a name="get-into-break-mode"></a>Dostać się do "trybu przerwania"

W *trybie przerwania*wykonywanie aplikacji jest zawieszone, podczas gdy funkcje, zmienne i obiekty pozostają w pamięci. Gdy debuger jest w trybie przerwania, można poruszać się po kodzie. Najczęstszymi sposobami szybkiego wejścia w tryb przerwania jest:

- Rozpocznij krok po kroku kodu, naciskając **klawisze F10** lub **F11**. Dzięki temu można szybko znaleźć punkt wejścia aplikacji, a następnie można kontynuować naciśnięcie poleceń kroku, aby przejść do kodu.

- [Uruchom do określonej lokalizacji lub funkcji](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), na przykład, [ustawiając punkt przerwania](using-breakpoints.md) i uruchamianie aplikacji.

   Na przykład z edytora kodu w programie Visual Studio, można użyć **Uruchom do kursora** polecenia, aby uruchomić aplikację, debuger dołączone i przejść do trybu przerwania, a następnie **F11,** aby przejść do kodu.

   ![Uruchamianie do kursora i krok do kodu](../debugger/media/navigate-code-code-stepping.gif "Uruchamianie do kursora i krok do kodu")

Po przejściu w tryb przerwania można użyć różnych poleceń, aby poruszać się po kodzie. W trybie przerwania można sprawdzić wartości zmiennych w celu wyszukania naruszeń lub błędów. W przypadku niektórych typów projektów można również wprowadzać zmiany w aplikacji w trybie przerwania.

Większość okien debugera, takich jak **moduły** i **okna czujki,** są dostępne tylko wtedy, gdy debuger jest dołączony do aplikacji. Niektóre funkcje debugera, takie jak wyświetlanie wartości zmiennych w oknie **Zmienne lokalne** lub oceny wyrażeń w oknie **Czujka,** są dostępne tylko wtedy, gdy debuger jest wstrzymany (czyli w trybie przerwania).

> [!NOTE]
> Jeśli podzielisz się na kod, który nie ma załadowanych plików źródłowych lub symboli (*pdb),* debuger wyświetli stronę **Nieodnaleziono plików źródłowych** lub **Symbole nieodnalezione,** które mogą pomóc w znalezieniu i załadowaniu plików. Zobacz [Określanie symbolu (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie można załadować plików symbolu lub źródła, nadal można debugować instrukcje złożenia w oknie **Demontaż.**

## <a name="step-through-code"></a>Krok po kroku przez kod

Polecenia kroku debugera ułatwiają sprawdzanie stanu aplikacji lub dowiedz się więcej o przepływie jego wykonywania.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Krok po wierszu kodu wiersz po wierszu

Aby zatrzymać każdą instrukcję podczas debugowania, użyj przycisku > **Debugowania Step Into**lub naciśnij **klawisz F11**. **Debug**

Debuger kroki za pomocą instrukcji kodu, a nie wierszy fizycznych. Na przykład `if` klauzula może być napisana w jednym wierszu:

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

Jednak po wejściu do tego wiersza debuger traktuje warunek jako jeden krok, a konsekwencja jako inny. W poprzednim przykładzie warunek jest spełniony.

W wywołaniu funkcji zagnieżdżonej **krok do** najbardziej głęboko zagnieżdżonej funkcji. Na przykład, jeśli używasz **Step** `Func1(Func2())`Into na wywołanie jak `Func2`, debuger kroki do funkcji .

>[!TIP]
>Podczas wykonywania każdego wiersza kodu można najechać kursorem na zmienne, aby wyświetlić ich wartości, lub użyć okien [Locals](autos-and-locals-windows.md) i [Watch,](watch-and-quickwatch-windows.md) aby obserwować zmianę wartości. Można również wizualnie śledzić [stos wywołań](how-to-use-the-call-stack-window.md) podczas przechodzenia do funkcji. (Tylko w programie Visual Studio Enterprise zobacz [Mapowanie metod na stosie wywołań podczas debugowania).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Krok po kodzie i pominąć niektóre funkcje

Możesz nie dbać o funkcję podczas debugowania lub wiesz, że działa, podobnie jak dobrze przetestowany kod biblioteki. Za pomocą następujących poleceń można pominąć kod podczas przechodzenia do kodu. Funkcje nadal wykonywane, ale debuger pomija nad nimi.

|Polecenie Klawiatura|Polecenie menu debugowania|Opis|
|----------------------|------------------|-----------------|
|**F10**|**Krok nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji, **Step Over** uruchamia kod, a następnie zawiesza wykonanie w pierwszym wierszu kodu po zwraca wywołaną funkcję.|
|**Zmiana**+**F11**|**Wyjdź**|**Step Out** kontynuuje uruchamianie kodu i zawiesza wykonywanie, gdy zwraca bieżącą funkcję. Debuger przeskakuje przez bieżącą funkcję.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Uruchamianie do określonej lokalizacji lub funkcji

Może wolisz uruchomić bezpośrednio do określonej lokalizacji lub funkcji, gdy wiesz dokładnie, jaki kod chcesz sprawdzić lub wiesz, gdzie chcesz rozpocząć debugowanie.

### <a name="run-to-a-breakpoint-in-code"></a>Uruchamianie do punktu przerwania w kodzie

Aby ustawić prosty punkt przerwania w kodzie, kliknij skrajnie lewy margines obok wiersza kodu, w którym chcesz zawiesić wykonanie. Można również zaznaczyć linię i nacisnąć **klawisz F9**, wybrać **opcję Debug** > **Toggle Breakpoint**lub kliknąć prawym przyciskiem myszy i wybrać polecenie **Breakpoint** > **Insert Breakpoint**. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie obok wiersza kodu. Debuger zawiesza wykonanie tuż przed wykonaniem wiersza.

![Ustawianie punktu przerwania](../debugger/media/dbg_basics_setbreakpoint.png "Ustawianie punktu przerwania")

Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Aby uzyskać szczegółowe informacje, zobacz [Korzystanie z punktów przerwania](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Uruchamianie do punktu przerwania funkcji

Debugera można powiedzieć, aby działał, dopóki nie osiągnie określonej funkcji. Można określić funkcję według nazwy lub wybrać ją ze stosu wywołań.

**Aby określić punkt przerwania funkcji według nazwy**

1. Wybierz **pozycję Debuguj** > nowy punkt**przerwania** > funkcji punktu**przerwania**

1. W oknie dialogowym **Nowy punkt przerwania funkcji** wpisz nazwę funkcji i wybierz jej język.

   ![Okno dialogowe Nowy punkt przerwania funkcji](../debugger/media/dbg_execution_newbreakpoint.png "Nowy punkt przerwania funkcji")

1. Kliknij przycisk **OK**.

Jeśli funkcja jest przeciążona lub w więcej niż jednej przestrzeni nazw, można wybrać tę, którą chcesz w oknie **Punkty przerwania.**

![Przeciążone punkty przerwania funkcji](../debugger/media/dbg_execution_overloadedbreakpoints.png "Przeciążone punkty przerwania funkcji")

**Aby wybrać punkt przerwania funkcji ze stosu wywołań**

1. Podczas debugowania otwórz okno **Stos wywołań,** wybierając pozycję **Debugowanie** > **stosu wywołań****systemu Windows** > .

1. W oknie **Stos wywołań** kliknij prawym przyciskiem myszy funkcję i wybierz polecenie **Uruchom kursor**lub naciśnij klawisz **Ctrl**+**F10**.

Aby wizualnie śledzić stos wywołań, zobacz [Mapowanie metod na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Uruchamianie w lokalizacji kursora

Aby uruchomić do lokalizacji kursora, w kodzie źródłowym lub w oknie **Stos wywołań** zaznacz linię, którą chcesz przerwać, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom kursor**lub naciśnij klawisz **Ctrl**+**F10**. Wybranie **opcji Uruchom kursor** jest jak ustawienie tymczasowego punktu przerwania.

### <a name="run-to-click"></a>Uruchom do kliknięcia

Wstrzymane w debugerze można najechać kursorem na instrukcję w kodzie źródłowym lub w oknie **Demontaż** i wybrać ikonę **Uruchom wykonanie w tym miejscu** zieloną strzałką. Za pomocą **Uruchom, aby kliknąć** eliminuje konieczność ustawiania tymczasowego punktu przerwania.

![Uruchom do kliknięcia](../debugger/media/dbg-run-to-click.png "Uruchom do kliknięcia")

> [!NOTE]
> **Uruchom do kliknięcia** [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]jest dostępny od .

### <a name="manually-break-into-code"></a>Ręcznie włamyć się do kodu

Aby przerwać następny dostępny wiersz kodu w uruchomionej aplikacji, wybierz opcję **Debuguj** > **przerwij wszystko**lub naciśnij klawisz **Ctrl**+**Alt**+**Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Przenoszenie wskaźnika w celu zmiany przepływu wykonania

Gdy debuger jest wstrzymany, żółty grot strzałki na marginesie kodu źródłowego lub okna **demontażu** oznacza lokalizację następnej instrukcji do wykonania. Następną instrukcję można zmienić, przesuwając tę strzałkę. Można pominąć część kodu lub powrócić do poprzedniego wiersza. Przenoszenie wskaźnika jest przydatne w sytuacjach, takich jak pomijanie sekcji kodu, która zawiera znany błąd.

 ![Przenoszenie wskaźnika](../debugger/media/dbg_basics_example3.gif "Przenoszenie wskaźnika")

Aby zmienić następną instrukcję do wykonania, debuger musi być w trybie przerwania. W oknie kod źródłowy lub **Demontaż** przeciągnij żółty grot strzałki do innej linii lub kliknij prawym przyciskiem myszy linię, którą chcesz wykonać dalej, a następnie wybierz pozycję **Ustaw następną instrukcję**.

Licznik programu przeskakuje bezpośrednio do nowej lokalizacji, a instrukcje między starymi i nowymi punktami wykonywania nie są wykonywane. Jednak jeśli przeniesiesz punkt wykonywania do tyłu, instrukcje interwencji nie są cofnięte.

>[!CAUTION]
>- Przeniesienie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek w czasie wykonywania. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otworzy okno dialogowe z ostrzeżeniem i daje szansę na anulowanie operacji.
>- W języku Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.
>- W natywnych C++, jeśli masz włączone sprawdzanie czasu wykonywania, ustawienie następnej instrukcji może spowodować wyjątek, który ma zostać zgłoszony, gdy wykonanie osiągnie koniec metody.
>- Gdy opcja Edycja i Kontynuuj jest włączona, **ustaw następną instrukcję,** jeśli wprowadzone zostały zmiany, których edycja i kontynuuj nie mogą natychmiast ponownie mapować. Może to nastąpić, na przykład, jeśli edytowano kod wewnątrz bloku catch. W takim przypadku komunikat o błędzie informuje, że operacja nie jest obsługiwana.
>- W kodzie zarządzanym nie można przenieść następnej instrukcji, jeśli:
>   - Następna instrukcja jest w innej metodzie niż bieżąca instrukcja.
>   - Debugowanie zostało uruchomione przez debugowanie just-in-time.
>   - Odwijanie stosu wywołań jest w toku.
>   - A System.StackOverflowException lub System.Threading.Threading.ThreadAbortException wyjątek został zgłoszony.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Debugowanie kodu niebędącego użytkownikiem

Domyślnie debuger próbuje debugować tylko kod aplikacji, włączając ustawienie o nazwie *Tylko mój kod*. Aby uzyskać więcej informacji o tym, jak ta funkcja działa dla różnych typów projektów i języków oraz jak można ją dostosować, zobacz [Tylko mój kod](../debugger/just-my-code.md).

Aby przyjrzeć się kodowi framework, kodowi biblioteki innych firm lub wywołaniom systemowym podczas debugowania, można wyłączyć tylko mój kod. W **obszarze Narzędzia** (lub **Debugowanie)**>**debugowanie** **opcji** > wyczyść pole wyboru **Włącz tylko mój kod.** Gdy tylko mój kod jest wyłączona, kod niebędący użytkownikiem pojawia się w oknach debugera, a debuger może wkroczyć do kodu niebędącego użytkownikiem.

> [!NOTE]
> Tylko mój kod nie jest obsługiwany dla projektów urządzeń.

### <a name="debug-system-code"></a>Kod systemu debugowania

Jeśli załadowano symbole debugowania dla kodu systemu firmy Microsoft i wyłączono tylko mój kod, możesz wejść do wywołania systemowego, tak jak każde inne wywołanie.

Aby załadować symbole firmy Microsoft, zobacz [Konfigurowanie lokalizacji symboli i opcji ładowania](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Aby załadować symbole dla określonego komponentu systemu:**

1. Podczas debugowania otwórz okno **Moduły,** wybierając pozycję **Debugowanie** > **modułów****systemu Windows** > lub naciskając klawisz **Ctrl**+**Alt**+**U**.

1. W oknie **Moduły** można sprawdzić, które moduły mają symbole ładowane w kolumnie **Stan symbolu.** Kliknij prawym przyciskiem myszy moduł, dla którego chcesz załadować symbole, a następnie wybierz polecenie **Załaduj symbole**.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Krok do właściwości i operatorów w kodzie zarządzanym
 Debuger kroki nad właściwości i operatorów w kodzie zarządzanym domyślnie. W większości przypadków zapewnia to lepsze środowisko debugowania. Aby włączyć przechodzenie do właściwości lub operatorów, wybierz opcję**Opcje** **debugowania** > . Na stronie **Debugowanie** > **ogólne** wyczyść pole wyboru Krok **nad właściwościami i operatorami (tylko zarządzane).**

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
