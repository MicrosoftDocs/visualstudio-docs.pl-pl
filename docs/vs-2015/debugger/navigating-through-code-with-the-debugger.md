---
title: Nawigowanie po kodzie za pomocą debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "64836311"
---
# <a name="navigating-through-code-with-the-debugger"></a>Nawigowanie po kodzie za pomocą debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapoznaj się z poleceniami i skrótami umożliwiającymi nawigowanie po kodzie w debugerze i szybsze i łatwiejsze znajdowanie i rozwiązywanie problemów w aplikacji. Podczas nawigowania po kodzie w debugerze można [sprawdzić stan aplikacji](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) lub dowiedzieć się więcej o jej przepływie wykonania.  
  
## <a name="start-debugging"></a>Rozpocznij debugowanie  
 Często rozpoczynasz sesję debugowania przy użyciu klawisza **F5** (**Debuguj** / **Rozpocznij debugowanie**). To polecenie uruchamia aplikację z dołączonym debugerem.  
  
 Zielona strzałka uruchamia również debuger (analogicznie jak **F5**).  
  
 ![&#95;Podstawowe informacje&#95;Rozpocznij&#95;debugowanie](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Oto kilka innych sposobów uruchamiania aplikacji z dołączonym debugerem: **F11** ([Wkrocz do kodu](#BKMK_Step_into__over__or_out_of_the_code)), **F10** (Przekrocz[kod](#BKMK_Step_over_Step_out)) lub za pomocą polecenia **Uruchom do kursora**.  Zapoznaj się z innymi sekcjami w tym temacie, aby uzyskać informacje na temat tych opcji.  
  
 Podczas debugowania żółty wiersz pokazuje kod, który zostanie wykonany dalej.  
  
 ![Tryb&#95;podziału&#95;&#95;podstawy DBG](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Podczas debugowania można przełączać się między poleceniami, takimi jak **F5**, **F11** i korzystać z innych funkcji opisanych w tym temacie (na przykład punktów przerwania), aby szybko uzyskać dostęp do kodu, który chcesz zobaczyć.  
  
 Większość funkcji debugera, takich jak przeglądanie wartości zmiennych w oknie zmiennych lokalnych lub ocenianie wyrażeń w okno wyrażeń kontrolnych, jest dostępna tylko podczas wstrzymania debugera (nazywanego również *trybem przerwania*). Gdy debuger zostanie wstrzymany, stan aplikacji jest zawieszony, gdy funkcje, zmienne i obiekty pozostają w pamięci. W trybie przerwania można sprawdzić pozycje i Stany elementów, aby wyszukać naruszenia lub błędy. W przypadku niektórych typów projektu może również wprowadzać zmiany do aplikacji w trybie przerwania.  
  
## <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Wkrocz do kodu, wiersz po wierszu  
 Aby zatrzymać każdy wiersz kodu (poszczególne instrukcje) podczas debugowania, użyj skrótu klawiaturowego **F11** (lub **Debuguj** / **Wkrocz do** menu).  
  
> [!TIP]
> Gdy wykonujesz każdy wiersz kodu, możesz umieścić wskaźnik myszy nad zmiennymi, aby zobaczyć ich wartości, lub użyć okien [lokalnych](../debugger/autos-and-locals-windows.md) i kontrolki [, aby](../debugger/autos-and-locals-windows.md) obejrzeć ich wartości.  
  
 Poniżej przedstawiono niektóre szczegółowe informacje o zachowaniu **kroku w**programie:  
  
- W wywołaniu funkcji zagnieżdżonej **Step Into** wchodzi do najgłębiej zagnieżdżonej funkcji. Jeśli używasz **kroku do** wywołania, takie jak `Func1(Func2())`, debuger przeprowadzi procedurę do `Func2`funkcji.  
  
- Debuger w rzeczywistości prowadzi przez instrukcje Code zamiast wierszy fizycznych. Na przykład klauzula `if` może być zapisywana w jednym wierszu:  
  
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
  
   Po przekroczeniu tego wiersza debuger traktuje warunek jako jeden krok, a w dalszej kolejności (w tym przykładzie warunek ma wartość true).  
  
  Aby wizualnie śledzić stos wywołań podczas przechodzenia do funkcji, zobacz [Mapowanie metod na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="BKMK_Step_over_Step_out"></a>Przechodzenie przez kod, funkcje pomijania  
 Gdy uruchamiasz kod w debugerze, często będziesz mieć świadomość, że nie musisz zobaczyć, co się dzieje w konkretnym działaniu (nie musisz Cię zadbać o to, lub wiesz, że działa, jak dobrze przetestowano kod biblioteki). Użyj tych poleceń, aby przeskoczyć przez kod (funkcje są nadal wykonywane, oczywiście ale debuger pomija je).  
  
|Polecenie klawiatury|Polecenie menu|Opis|  
|----------------------|------------------|-----------------|  
|**F10**|**Przekrocz nad**|Jeśli bieżący wiersz zawiera wywołanie funkcji, **krok powyżej** uruchamia kod, a następnie wstrzymuje wykonywanie w pierwszym wierszu kodu po wywołaniu wywołanej funkcji.|  
|**Shift+F11**|**Wyjdź**|**Krok** Wyjdź kontynuuje uruchamianie kodu i wstrzymuje wykonywanie, gdy bieżąca funkcja zwróci wartość (debuger pomija bieżącą funkcję).|  
  
> [!TIP]
> Jeśli musisz odnaleźć punktu wejścia w swojej aplikacji, skorzystaj z **F10** lub **F11**. Te polecenia są często przydatne podczas sprawdzania stanu aplikacji lub prób dowiedzieć się więcej o przepływie wykonania.  
  
## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Uruchamianie do określonej lokalizacji lub funkcji  
 Często preferowaną metodą debugowania kodu są te metody, które są przydatne, gdy dokładnie wiesz, jaki kod chcesz sprawdzić, lub co najmniej wiesz, gdzie chcesz rozpocząć debugowanie.  
  
- **Ustawianie punktów przerwania w kodzie**  
  
     Aby ustawić prosty punkt przerwania w kodzie, Otwórz plik źródłowy w edytorze programu Visual Studio. Ustaw kursor w wierszu kodu, w którym chcesz wstrzymać wykonywanie, a następnie kliknij prawym przyciskiem myszy w oknie kodu, aby wyświetlić menu kontekstowe, a następnie wybierz pozycję **punkt przerwania/Wstaw punkt przerwania** (lub naciśnij klawisz **F9**). Debuger zawiesza wykonywanie bezpośrednio przed wykonaniem wiersza.  
  
     ![Ustawianie punktu przerwania](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Punkty przerwania w programie Visual Studio zapewniają bogaty zestaw dodatkowych funkcji, takich jak warunkowe punkty przerwania i punkty śledzenia. Zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
- **Uruchom do lokalizacji kursora**  
  
     Aby uruchomić do lokalizacji kursora, umieść kursor w wierszu kodu wykonywalnego w oknie źródłowym. W menu kontekstowym edytora (kliknij prawym przyciskiem myszy w edytorze) wybierz polecenie **Uruchom do kursora**. Jest to podobne do ustawiania tymczasowego punktu przerwania.  
  
- **Ręczne przebicie na kod**  
  
     Aby przerwać w następnym dostępnym wierszu kodu w wykonywanej aplikacji, wybierz **Debuguj**, **Przerwij wszystkie** (klawiatura: **CTRL + ALT + BREAK**).  
  
     W przypadku przerwania kodu bez odpowiednich plików źródłowych lub symboli (. pdb) debuger wyświetla **pliki źródłowe, które nie zostały odnalezione** lub **nie znaleziono symboli** , które mogą pomóc w znalezieniu odpowiednich plików. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Jeśli nie możesz uzyskać dostępu do plików pomocniczych, nadal możesz debugować instrukcje zestawu w oknie demontażu.  
  
- **Uruchom do funkcji na stosie wywołań**  
  
     W oknie **stos wywołań** (dostępne podczas debugowania) zaznacz funkcję, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom do kursora**. Aby wizualnie śledzić stos wywołań, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Uruchom do funkcji określonej przez nazwę**  
  
     Możesz powiedzieć debugerowi, aby uruchomić aplikację do momentu, aż osiągnie określoną funkcję. Można określić funkcję według nazwy lub wybrać ją ze stosu wywołań.  
  
     Aby określić funkcję według nazwy, wybierz **Debuguj**, **nowy punkt przerwania**, **Przerwij w funkcji**, a następnie wprowadź nazwę funkcji i inne informacje identyfikujące.  
  
     ![Nowy punkt przerwania — okno dialogowe](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Jeśli funkcja jest przeciążona lub znajduje się w wielu przestrzeniach nazw, możesz wybrać odpowiednie funkcje w oknie dialogowym **Wybierz punkty przerwania** .  
  
     ![Okno dialogowe Wybieranie punktów przerwania](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="BKMK_Set_the_next_statement_to_execute"></a> Przenieść wskaźnik, aby zmienić przepływ wykonania  
 Gdy debuger jest wstrzymany, można przenieść wskaźnik instrukcji, aby ustawić następną instrukcję kodu do wykonania. Żółta strzałka na marginesie okna źródłowego lub demontażowego oznacza lokalizację następnej instrukcji do wykonania. Przenosząc tę grot strzałki, możesz pominąć część kodu lub wrócić do wcześniej wykonanej linii. Można jej użyć w takich sytuacjach, jak pomijanie sekcji kodu zawierającej znaną usterkę.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Aby ustawić następną instrukcję do wykonania, należy użyć jednej z następujących procedur:  
  
- W oknie źródła przeciągnij żółtą grot strzałki do lokalizacji, w której chcesz ustawić następną instrukcję w tym samym pliku źródłowym  
  
- W oknie źródła Ustaw kursor w wierszu, który chcesz wykonać w następnej kolejności, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw następną instrukcję**.  
  
- W oknie demontażu Ustaw kursor instrukcji zestawu, który chcesz wykonać w następnej kolejności, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw następną instrukcję**.  
  
> [!CAUTION]
> Ustawienie następnej instrukcji powoduje, że licznik programu przechodzi bezpośrednio do nowej lokalizacji. Użyj tego polecenia z zachowaniem ostrożności:  
> 
> - Instrukcje między starym i nowym punktem wykonywania nie są wykonywane.  
>   - Po przeniesieniu punktu wykonywania do tyłu instrukcje dotyczące interwencji nie są cofane.  
>   - Przenoszenie następnej instrukcji do innej funkcji lub zakresu zwykle powoduje uszkodzenie stosu wywołań, powodując błąd lub wyjątek. Jeśli spróbujesz przenieść następną instrukcję do innego zakresu, debuger otwiera okno dialogowe z ostrzeżeniem i daje możliwość anulowania operacji. W języku Visual Basic nie można przenieść następnej instrukcji do innego zakresu lub funkcji.  
>   - W natywnym kodzie C++ zostały włączone, kontrole czasu wykonywania ustawienie następnej instrukcji może spowodować wyjątek zgłaszany, gdy wykonywanie osiągnie koniec metody.  
>   - Gdy Edytuj i Kontynuuj jest włączona, **Ustaw następną instrukcję** kończy się niepowodzeniem, jeśli zostały wprowadzone zmiany, których Edytuj i Kontynuuj nie może od razu ponownie zamapować. Może to występować, na przykład, jeśli edytowano kod wewnątrz bloku catch. W takim przypadku zostanie wyświetlony komunikat o błędzie informujący o tym, że operacja nie jest obsługiwana.  
> 
> [!NOTE]
> W kodzie zarządzanym nie można przenieść następnej instrukcji w następujących warunkach:  
> 
> - Następna instrukcja znajduje się w innej metodzie niż bieżąca instrukcja.  
>   - Debugowanie zostało uruchomione przy użyciu debugowania just in Time.  
>   - Trwa wykonywanie operacji unwind stosu wywołań.  
>   - Został zgłoszony wyjątek System.StackOverflowException lub System.Threading.ThreadAbortException.  
  
 Nie można ustawić następnej instrukcji, gdy aplikacja jest aktywnie uruchomiona. Aby ustawić następną instrukcję, debuger musi być w trybie przerwania.  
  
## <a name="step-into-non-user-code"></a>Wkrocz do kodu niezwiązanego z użytkownikiem  
 Domyślnie debuger próbuje wyświetlić tylko kod aplikacji podczas debugowania, który jest określany przez ustawienie debugera o nazwie *tylko mój kod*. (Zobacz [tylko mój kod](../debugger/just-my-code.md) , aby zobaczyć, jak to działa dla różnych typów projektów i języków oraz jak można dostosować zachowanie.) Jednak czasami podczas debugowania można chcieć sprawdzić kod struktury, kod biblioteki innej firmy lub wywołania systemu operacyjnego (wywołania systemowe).  
  
 Tylko mój kod można wyłączyć, przechodząc do opcji **Narzędzia** **Opcje** /  / **debugowanie** i usunąć zaznaczenie pola wyboru **Włącz tylko mój kod** .  
  
 Po wyłączeniu Tylko mój kod debuger może przejść do kodu niezwiązanego z użytkownikiem, a kod niebędący użytkownikiem pojawia się w oknach debugera.  
  
> [!NOTE]
> Tylko mój kod nie jest obsługiwana dla projektów urządzenia.  
  
 **Wkrocz do wywołań systemowych**  
  
 Jeśli załadowałeś symbole debugowania dla kodu systemowego i Tylko mój kod nie jest włączona, możesz przejść do wywołania systemowego tak samo jak w przypadku każdego innego wywołania.  
  
 Aby uzyskać dostęp do plików symboli firmy Microsoft, zobacz [Używanie serwerów symboli do znajdowania plików symboli, które nie znajdują się na komputerze lokalnym](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) , w temacie [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
 Aby załadować symbole dla określonego składnika systemu podczas debugowania:  
  
1. Otwórz okno moduły (klawiatura: **Ctrl + Alt + U**).  
  
2. Wybierz moduł, dla którego chcesz załadować symbole.  
  
     Możesz sprawdzić, które moduły mają załadowane symbole, patrząc na kolumnę **stan symbolu** .  
  
3. Wybierz pozycję **Załaduj symbole** z menu kontekstowego.  
  
## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Wejdź do właściwości i operatory w kodzie zarządzanym  
 Debuger nie wchodzi we właściwości i operatory w kodzie zarządzanym domyślnie. W większości przypadków zapewnia to lepszy proces debugowania. Aby włączyć przechodzenie krok po kroku do właściwości lub operatorów, wybierz opcję **debugowania** / **opcje**. Na stronie **Ogólne** **debugowania** / wyczyść pole wyboru **Przekrocz nad właściwościami i operatorami (tylko zarządzane)**
