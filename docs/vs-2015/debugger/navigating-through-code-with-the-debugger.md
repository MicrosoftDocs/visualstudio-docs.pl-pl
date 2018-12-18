---
title: Nawigowanie po kodzie za pomocą debugera za | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43155bbd4236ea34d67058443e8814f7ccf00b1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750576"
---
# <a name="navigating-through-code-with-the-debugger"></a>Nawigowanie po kodzie za pomocą debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapoznaj się z poleceń i skrótów, przechodzenie do kodu w debugerze i który ułatwi przyspiesza i ułatwia znajdowanie i rozwiązywanie problemów w aplikacji. Gdy przejdziesz kodu w debugerze, możesz [sprawdzić stan aplikacji](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) lub Dowiedz się więcej o przepływ jego wykonania.  
  
## <a name="start-debugging"></a>Rozpocznij debugowanie  
 Często uruchamiania sesji debugowania przy użyciu **F5** (**debugowania** / **Rozpocznij debugowanie**). To polecenie uruchamia aplikację w debugerze.  
  
 Zielona strzałka rozpoczyna się debugera (taka sama jak **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Obejmują kilka innych sposobów, możesz uruchomić aplikację w debugerze **F11** ([kodu krok po kroku](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([Przekrocz nad kodem](#BKMK_Step_over_Step_out)), lub za pomocą **Uruchom do kursora**.  Zobacz inne sekcje w tym temacie, aby uzyskać informacje o tych opcji zrobić.  
  
 Podczas debugowania, żółta linia zawiera kod, który będzie wykonać w następnej kolejności.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Podczas debugowania, można przełączać się między poleceń, takich jak **F5**, **F11** i korzystanie z innych funkcji opisanych w tym temacie, (na przykład punktów przerwania), aby szybko uzyskać dostęp do kodu, aby przyjrzeć się.  
  
 Większość funkcji debugera, takie jak wyświetlanie wartości zmiennych w okienku zmiennych lokalnych lub oceny wyrażenia w oknie czujki, są dostępne tylko wtedy, gdy debuger jest wstrzymana (nazywane również *trybu przerwania*). Gdy debuger jest wstrzymany, swój stan aplikacji jest wstrzymana podczas funkcje, zmienne i obiekty pozostają w pamięci. W trybie break można sprawdzić pozycje elementów i Stany, aby szukać naruszeń lub błędów. W przypadku niektórych typów projektu może również wprowadzać zmiany do aplikacji w trybie przerwania.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Wykonywanie kodu, wiersz po wierszu  
 Aby zatrzymać w każdym wierszu kodu (każda instrukcja) podczas debugowania, użyj **F11** skróty klawiaturowe (lub **debugowania** / **Step Into** menu).  
  
> [!TIP]
>  Podczas wykonywania wszystkich wierszy kodu, możesz umieścić kursor zmienne, aby zobaczyć ich wartości lub użyć [lokalne](../debugger/autos-and-locals-windows.md) i [Obejrzyj](../debugger/autos-and-locals-windows.md) systemu windows, aby obejrzeć ich wartości, Zmień.  
  
 Poniżej przedstawiono niektóre szczegóły na temat zachowania **Step Into**:  
  
- W wywołaniu funkcji zagnieżdżonej **Step Into** wchodzi do najgłębiej zagnieżdżonej funkcji. Jeśli używasz **Step Into** przy wywołaniu, takich jak `Func1(Func2())`, debuger wchodzi do funkcji `Func2`.  
  
- Debuger faktycznie przechodzi przez instrukcje kodu, a nie fizyczne wiersze. Na przykład `if` klauzuli mogą być zapisywane w jednym wierszu:  
  
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
  
   Gdy wchodzisz do tego wiersza debuger traktuje ten warunek jako jeden krok, a jego konsekwencję jako inny (w tym przykładzie, warunek jest spełniony).  
  
  Aby wizualnie śledzić stos wywołań, wchodząc krok do funkcji, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Przejść przez kod, pomijanie funkcji  
 Podczas uruchamiania kodu w debugerze, często będą okazuje się, że nie jest wymagane zobaczyć, co dzieje się w określonej funkcji (nie dba o go lub ją znasz dzieła, takie jak kod dobrze przetestowanych biblioteki). Używać tych poleceń, aby przejść przez kod (funkcje nadal wykonywane, oczywiście, ale debuger pomija nad nimi).  
  
|Polecenie klawiatury|Polecenia menu|Opis|  
|----------------------|------------------|-----------------|  
|**F10**|**Przekrocz nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji **Step Over** uruchamia kod, a następnie zawiesza wykonywanie w pierwszym wierszu kodu po powrocie wywołanej funkcji.|  
|**Shift+F11**|**Wyjdź**|**Step Out** kontynuuje wykonywanie kodu, a następnie zawiesza wykonywanie, gdy bieżąca funkcja zwróci wartość (pomija debugera za pomocą bieżącej funkcji).|  
  
> [!TIP]
>  Jeśli musisz odnaleźć punktu wejścia w swojej aplikacji, skorzystaj z **F10** lub **F11**. Te polecenia są często pomocne podczas sprawdzania stanu usługi aplikacji i podjęcie próby dowiedzieć się więcej na temat jego przepływ wykonania.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchamianie do określonej lokalizacji lub funkcji  
 Często preferowaną metodą debugowania kodu, te metody są przydatne, gdy wiesz, jaki dokładnie kod chcesz sprawdzić lub co najmniej wiesz, gdzie chcesz rozpocząć debugowanie.  
  
-   **Ustawianie punktów przerwania w kodzie**  
  
     Aby ustawić prosty punkt przerwania w kodzie, otwórz plik źródłowy w edytorze programu Visual Studio. Ustaw kursor w wierszu kodu, w którym chcesz zawiesić wykonanie, a następnie kliknij prawym przyciskiem myszy w oknie kodu, aby wyświetlić menu kontekstowe i wybrać **punktu przerwania / Wstaw punkt przerwania** (lub naciśnij **F9**). Debuger zawiesza wykonywanie po prawej stronie, przed wykonaniem wiersza.  
  
     ![Ustaw punkt przerwania](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
-   **Uruchom do lokalizacji kursora**  
  
     Aby uruchomić do lokalizacji kursora, umieść kursor w wierszu pliku wykonywalnego kodu w oknie źródła. W menu kontekstowym edytora (kliknij prawym przyciskiem myszy w edytorze), wybierz **Uruchom do kursora**. Jest to np. ustawienie tymczasowy punkt przerwania.  
  
-   **Ręcznie Wejdź do kodu**  
  
     Aby przerwać następnego dostępnego wiersza kodu w wykonywanej aplikacji, wybierz opcję **debugowania**, **Przerwij wszystkie** (klawiatura: **Ctrl + Alt + Break**).  
  
     Jeśli użytkownik przerwiesz podczas wykonywania kodu bez odpowiadającego jej źródła lub symboli (.pdb) plików), debuger wyświetla **nie znaleziono źródła plików** lub **nie można odnaleźć symboli** strona, która pomoże Ci znaleźć odpowiednią pliki. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie masz dostępu do plików pomocniczych, nadal możesz debugować instrukcje montażu w oknie demontażu.  
  
-   **Uruchom do funkcji na stosie wywołań**  
  
     W **stos wywołań** okna (dostępne podczas debugowania), wybierz funkcję, kliknij prawym przyciskiem myszy i wybierz **Uruchom do kursora**. Aby wizualnie śledzić stos wywołań, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Uruchom do funkcji określonej przez nazwę**  
  
     Można polecić debugerowi, aby uruchomić aplikację, aż do osiągnięcia określonej funkcji. Można określić funkcję według nazwy lub możesz ją wybrać spośród stosu wywołań.  
  
     Aby określić funkcję według nazwy, wybierz opcję **debugowania**, **nowego punktu przerwania**, **Przerwij w funkcji**, wprowadź nazwę funkcji i inne informacje identyfikacyjne.  
  
     ![Nowy punkt przerwania, okno dialogowe](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Jeśli funkcja jest przeciążona lub jest w wielu przestrzeniach nazw, możesz wybrać funkcje, które mają wejść w **wybierz punkty przerwania** okno dialogowe.  
  
     ![Wybierz punkty przerwania, okno dialogowe](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Przenieść wskaźnik, aby zmienić przepływ wykonania  
 Gdy debuger jest wstrzymany, można przenieść wskaźnik instrukcji w celu ustawienia następnej instrukcji kodu do wykonania. Żółty grot strzałki na marginesie źródła lub okna dezasemblacji oznacza lokalizację następnej instrukcji do wykonania. Przesuwając ten grot strzałki, można pominąć część kodu lub powrócić do wiersza wcześniej wykonywanego. Możesz użyć tego w sytuacjach, takich jak pomijanie sekcji kodu, który zawiera znany błąd.  
  
 ![Przykład2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Aby ustawić następną instrukcję do wykonania, użyj jednej z poniższych procedur:  
  
-   W oknie źródła przeciągnij żółty grot do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym  
  
-   W oknie źródła, ustaw kursor na wierszu, który chcesz wykonać w następnej kolejności, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw następną instrukcję**.  
  
-   W oknie demontażu Ustaw kursor na instrukcji montażu, którą chcesz wykonać w następnej kolejności, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw następną instrukcję**.  
  
> [!CAUTION]
>  Ustawienie następnej instrukcji powoduje, że licznik programu przechodzi bezpośrednio do nowej lokalizacji. Użyj tego polecenia ostrożnie:  
> 
> - Instrukcje między stary i nowymi punktami wykonania nie są wykonywane.  
>   -   Jeśli przeniesiesz punkt wykonania Wstecz, instrukcje interwencyjne nie zostaną cofnięte.  
>   -   Przenoszenie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji. W języku Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.  
>   -   W natywnym kodzie C++ zostały włączone, kontrole czasu wykonywania ustawienie następnej instrukcji może spowodować wyjątek zgłaszany, gdy wykonywanie osiągnie koniec metody.  
>   -   Gdy Edytuj i Kontynuuj jest włączona, **Ustaw następną instrukcję** kończy się niepowodzeniem, jeśli zostały wprowadzone zmiany, których Edytuj i Kontynuuj nie może od razu ponownie zamapować. Może to występować, na przykład, jeśli edytowano kod wewnątrz bloku catch. W takim przypadku zobaczysz komunikat o błędzie informujący o tym, że ta operacja nie jest obsługiwane.  
> 
> [!NOTE]
>  W kodzie zarządzanym nie można przenieść następnej instrukcji w następujących warunkach:  
> 
> - Następna instrukcja znajduje się w innej metodzie niż bieżąca instrukcja.  
>   -   Debugowanie zostało uruchomione przy użyciu Just-In-Time debugowania.  
>   -   Odwijanie stosu wywołań jest w toku.  
>   -   Został zgłoszony wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.  
  
 Nie można ustawić następnej instrukcji, gdy aplikacja jest aktywnie uruchomiona. Aby ustawić następną instrukcję, debuger musi być w trybie przerwania.  
  
## <a name="step-into-non-user-code"></a>Wejdź do kodu innych użytkowników  
 Domyślnie debuger podejmie próbę pokazują tylko kodu aplikacji podczas debugowania, który jest określony przez debuger nosi nazwę *tylko mój kod*. (Zobacz [tylko mój kod](../debugger/just-my-code.md) aby zobaczyć, jak to działa na różnych typach projektów i języków i jak możesz dostosować zachowanie.) Jednak czasami, podczas debugowania, możesz chcieć Przyjrzyj się kodu struktury, kod biblioteki innych firm lub wywołań do systemu operacyjnego (wywołań systemowych).  
  
 Można wyłączyć opcję tylko mój kod, przechodząc do **narzędzia** / **opcje** / **debugowanie** i wyczyść **Włącz tylko mój kod** pole wyboru.  
  
 Po wyłączeniu tylko mój kod debuger można wkroczyć do kodu niepochodzącego od użytkownika, a kod niezwiązany z użytkownikiem, który pojawia się w oknach debugera.  
  
> [!NOTE]
>  Tylko mój kod nie jest obsługiwana dla projektów urządzenia.  
  
 **Wejdź do wywołań systemowych**  
  
 Jeśli zostały załadowane symbole debugowania dla kodu systemowego i nie włączono opcję tylko mój kod, możesz wejść do wywołania systemowego tak samo jak inne wywołania.  
  
 Aby uzyskać dostęp do plików symboli firmy Microsoft, zobacz [Użyj serwerów symboli, aby znaleźć pliki symboli nie na komputerze lokalnym](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) w [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tematu.  
  
 Aby załadować symbole dla określonego składnika systemu podczas debugowania:  
  
1.  Otwórz okno modułów (klawiatura: **Ctrl + Alt + U**).  
  
2.  Wybierz moduł, który chcesz załadować symbole.  
  
     Można stwierdzić, które moduły mają załadowane symbole, patrząc **stan symboli** kolumny.  
  
3.  Wybierz **załadować symbole** w menu kontekstowym.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Wejdź do właściwości i operatory w kodzie zarządzanym  
 Debuger nie wchodzi we właściwości i operatory w kodzie zarządzanym domyślnie. W większości przypadków zapewnia to lepszy proces debugowania. Aby włączyć przechodzenie krok po kroku do właściwości lub operatorów, wybierz opcję **debugowania** / **opcje**. Na **debugowanie** / **ogólne** strony, wyczyść **Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)** pola wyboru





