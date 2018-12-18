---
title: Używanie punktów przerwania w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/15/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16bcb4bb12e852a8fa268998d0605b2ffc7471e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068451"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Używanie punktów przerwania w debugerze programu Visual Studio
Punkty przerwania są jednym z najważniejszych technik debugowania dostępnych w przyborniku dla deweloperów. Ustaw punkty przerwania, wszędzie tam, gdzie chcesz wstrzymać wykonanie w debugerze. Na przykład można wyświetlić stan zmiennych kodu lub Spójrz na stos wywołań w niektórych punkcie przerwania. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [debugowania dla początkujących](../debugger/debugging-absolute-beginners.md) przed przejściem w tym artykule.
  
##  <a name="BKMK_Overview"></a> Ustawianie punktów przerwania w kodzie źródłowym  
 Możesz ustawić punkt przerwania w każdym wierszu kodu wykonywalnego. Na przykład w poniższym kodzie C#, można ustawić punkt przerwania w deklaracji zmiennej `for` pętli lub dowolny kod wewnątrz `for` pętli. Nie można ustawić punktu przerwania, deklaracje przestrzeni nazw lub klasy lub podpis metody.  

 Aby ustawić punkt przerwania w kodzie źródłowym, kliknij na marginesie po lewej stronie obok wiersza kodu. Możesz również wybrać wiersza i naciśnij klawisz **F9**, wybierz opcję **debugowania** > **Przełącz punkt przerwania**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **punktuprzerwania**  >  **Wstaw punkt przerwania**. Punkt przerwania pojawia się jako czerwona kropka na lewym marginesie.  

W C# automatycznie wyróżniony kod, punkt przerwania i bieżącej linii wykonywania. Dla kodu C++, można włączyć wyróżnianie punktu przerwania i bieżącej linii, wybierając **narzędzia** (lub **debugowania**) > **opcje**  >   **Debugowanie** >  **Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji (tylko C++)**. 
  
 ![Ustaw punkt przerwania](../debugger/media/basicbreakpoint.png "podstawowego punktu przerwania")  
  
 Podczas debugowania, wykonywanie jest wstrzymane w punkcie przerwania, przed wykonaniem kodu w danym wierszu. Symbol punktu przerwania pokazuje żółta strzałka. 

 W punkcie przerwania w poniższym przykładzie wartość `testInt` nadal jest 1.  
  
 ![Punkt przerwania wykonywania zatrzymana](../debugger/media/breakpointexecution.png "punktu przerwania wykonywania")  
  
 Po zatrzymaniu debugera w punkcie przerwania, można sprawdzić bieżący stan aplikacji, w tym wartości zmiennych i stosu wywołań. Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  

- Punkt przerwania jest przełącznikiem. Można kliknąć go, naciśnij **F9**, lub użyj **debugowania** > **Przełącz punkt przerwania** usunąć lub ponownie.
  
- Aby wyłączyć punkt przerwania, bez usuwania go, umieść kursor nad lub kliknij ją prawym przyciskiem myszy i wybierz **Wyłącz punkt przerwania**. Wyłączone punkty przerwania są wyświetlane jako puste kropki na lewym marginesie lub **punktów przerwania** okna. Aby ponownie włączyć punkt przerwania, Najedź kursorem lub kliknij ją prawym przyciskiem myszy i wybierz **Włącz punkt przerwania**. 
  
- Ustaw warunki i akcje, dodawanie i edytowanie etykiet lub wyeksportuj punkt przerwania, kliknij go prawym przyciskiem myszy i wybierając odpowiednie polecenie lub przenosząc kursor myszy nad nim i wybierając **ustawienia** ikony.

##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Ustawianie punktów przerwania w debugerze systemu windows 

Można również ustawić punkty przerwania z **stos wywołań** i **dezasemblacji** debugera systemu windows.  
  
### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Ustaw punkt przerwania w oknie stosu wywołań  

 Aby przerwać w instrukcji lub wierszu, który powraca wywołanie funkcji, można ustawić punkt przerwania w **stos wywołań** okna. 
  
**Aby ustawić punkt przerwania w oknie wywołania stosu:**

1. Aby otworzyć **stos wywołań** oknie zostanie wstrzymana podczas debugowania. Wybierz **debugowania** > **Windows** > **stos wywołań**, lub naciśnij **Ctrl** + **Alt**+**C**.  
   
2. W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcji wywołującej i wybierz **punktu przerwania** > **Wstaw punkt przerwania**, lub naciśnij **F9**.  
   
   Symbol punktu przerwania pojawia się obok nazwy wywołania funkcji na lewym marginesie na stosie wywołań.
   
Punkt przerwania stosu wywołań jest wyświetlany w **punktów przerwania** okno jako adres, z lokalizacji w pamięci, która odpowiada następnej instrukcji wykonywalnej w funkcji. 

Debuger przerywa w instrukcji.  

Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md). 

Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 
  
### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ustaw punkt przerwania w oknie demontaż  
   
1. Aby otworzyć **dezasemblacji** oknie zostanie wstrzymana podczas debugowania. Wybierz **debugowania** > **Windows** > **dezasemblacji**, lub naciśnij **Alt** + **8**.  
   
2. W **dezasemblacji** kliknij na lewym marginesie instrukcji, aby przerwać. Możesz również wybrać go i naciśnij klawisz **F9**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **punktu przerwania** > **Wstaw punkt przerwania**. 

##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Ustawianie punktów przerwania z — funkcja  

  Aby przerwać wykonywanie, gdy funkcja jest wywoływana. 

**Aby ustawić punktu przerwania funkcji:**
  
1. Wybierz **debugowania** > **nowego punktu przerwania** > **przerwania funkcji**, lub naciśnij **Alt** + **F9** > **Ctrl**+**B**. 
   
   Możesz również wybrać **New** > **przerwania funkcji** w **punktów przerwania** okna.
   
1. W **nowy punkt przerwania funkcji** okno dialogowe, wprowadź nazwę funkcji w **nazwy funkcji** pole. 

   Aby zawęzić specyfikację funkcji:
   
   - Użyj w pełni kwalifikowana nazwa funkcji. 
     
     Przykład:  `Namespace1.ClassX.MethodA()`
     
   - Dodaj typy parametrów przeciążonej funkcji. 
     
     Przykład:  `MethodA(int, string)`
     
   - Użyj '!' symbolu, aby określić moduł.
     
     Przykład: `App1.dll!MethodA`
     
   - Użyj operatora kontekstu w natywnym kodzie C++.
     
     `{function, , [module]} [+<line offset from start of method>]`
     
     Przykład: `{MethodA, , App1.dll}+2`
   
1. W **języka** listy rozwijanej wybierz język funkcji.
   
1. Wybierz **OK**.
  
### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Ustaw punkt przerwania funkcji przy użyciu adresu pamięci (tylko w natywnym kodzie C++)  
 Adres obiektu umożliwia ustawianie punktu przerwania funkcji metody wywoływane przez konkretnego wystąpienia klasy.  Na przykład, biorąc pod uwagę adresowalnych obiektu typu `my_class`, można ustawić punktu przerwania funkcji w `my_method` wystąpienie wywołania metody. 
  
1.  Ustaw punkt przerwania gdzieś po tworzone jest wystąpienie klasy.  
    
2.  Znajdź adres obiektu (na przykład `0xcccccccc`). 
    
3.  Wybierz **debugowania** > **nowego punktu przerwania** > **przerwania funkcji**, lub naciśnij **Alt** + **F9** > **Ctrl**+**B**.  
    
4.  Dodaj następujące polecenie, aby **nazwy funkcji** i zaznacz **C++** języka.  
    
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Ustaw punkty przerwania danych (tylko w natywnym kodzie C++) 
 
 Punkty przerwania danych przerwać wykonywanie, gdy wartość przechowywaną w zmiany adresu określonego pamięci. Jeśli wartości jest czytana, ale nie został zmieniony, wykonanie nie zostanie przerwane.  
  
**Aby ustawić punkt przerwania danych:**

1.  W projekcie w języku C++ rozpocząć debugowanie i zaczekaj, aż do osiągnięcia punktu przerwania. Na **debugowania** menu, wybierz **nowego punktu przerwania** > **punkt przerwania danych** 

    Możesz również wybrać **New** > **punkt przerwania danych** w **punktów przerwania** okna.
  
2.  W **adres** wpisz adres pamięci lub wyrażenie, które daje w wyniku adres pamięci. Na przykład wpisz `&avar` przerwanie, kiedy zawartość zmiennej `avar` zmiany.  
  
3.  W **liczba bajtów** listy rozwijanej wybierz liczbę bajtów, które chcesz, aby debuger ma uważać. Na przykład w przypadku wybrania **4**, debuger będzie obserwował cztery bajty począwszy `&avar` i przerwie działanie, jeśli którykolwiek z tych bajtów zmienić wartość.  

Punkty przerwania danych nie działają w następujących warunkach:  
-   Proces, który nie jest debugowany, zapisuje w lokalizacji pamięci.  
-   Lokalizacja pamięci jest współużytkowana przez dwa lub więcej procesów.  
-   Lokalizacja pamięci jest aktualizowana w jądrze. Na przykład, jeśli pamięć jest przekazywana do Windows 32-bitowych `ReadFile` funkcji, pamięć zostanie zaktualizowana z trybu jądra, debuger nie spowodują przerwania działania aktualizacji.  

>[!NOTE]
>- Punkty przerwania danych są zależne od adresów pamięci. Adres zmiennej zmiany między jedną sesją debugowania do następnego, dzięki czemu punkty przerwania danych są automatycznie wyłączane na koniec każdej sesji debugowania.  
>  
>- Jeśli punkt przerwania danych zostanie ustawiony na zmiennej lokalnej, punkt przerwania pozostaje włączony nawet gdy funkcja skończy działanie, ale adres pamięci nie ma już zastosowania, więc zachowanie punktu przerwania są nieprzewidywalne. Jeśli punkt przerwania danych zostanie ustawiony na zmiennej lokalnej, należy usunąć lub wyłącz punkt przerwania przed końcem działania funkcji.  

##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Zarządzanie punktami przerwania w oknie punktów przerwania 

 Możesz użyć **punktów przerwania** okna, aby zobaczyć i wszystkie punkty przerwania w rozwiązaniu do zarządzania. Scentralizowane jest szczególnie przydatne w rozwiązaniach dużych lub złożonych scenariuszy debugowania, w których punkty przerwania mają kluczowe znaczenie. 

W **punktów przerwania** oknie można wyszukiwania, sortowania, filtrowania, Włącz/Wyłącz lub Usuń punkty przerwania. Można również ustawić warunki i akcje lub dodać nowej funkcji lub punkt przerwania danych.
  
Aby otworzyć **punktów przerwania** wybierz **debugowania** > **Windows** > **punktów przerwania**, lub naciśnij  **ALT**+**F9** lub **Ctrl**+**Alt**+**B**.
  
![Okno punktów przerwania](../debugger/media/breakpointswindow.png "okno punktów przerwania")  
  
Aby wybrać kolumny do wyświetlenia w **punktów przerwania** wybierz **Pokaż kolumny**. Wybierz nagłówek kolumny w celu listę punktów przerwania można sortować według tej kolumny. 

###  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etykiety punktów przerwania  
Etykiety można użyć do sortowania i filtrowania listy punktów przerwania w **punktów przerwania** okna. 

1. Aby dodać etykietę do punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub **punktów przerwania** okna, a następnie wybierz pozycję **Edytuj etykiety**. Dodaj nową etykietę lub wybierz istniejącą grupę, a następnie wybierz **OK**.
2. Listę można sortować punkt przerwania w **punktów przerwania** okna, wybierając **etykiety**, **warunki**, lub innych nagłówków kolumn. Można wybrać kolumny, aby wyświetlić, wybierając **Pokaż kolumny** na pasku narzędzi. 
  
### <a name="export-and-import-breakpoints"></a>Eksportowanie i importowanie punktów przerwania  
 Aby zapisać lub udostępnić stan i lokalizacja punktów przerwania, można eksportować lub importować je. 

- Aby wyeksportować pojedynczy punkt przerwania w pliku XML, kliknij prawym przyciskiem myszy punkt przerwania w kodzie źródłowym lub **punktów przerwania** okna, a następnie wybierz **wyeksportować** lub **Eksportuj zaznaczone**. Wybierz lokalizację eksportu, a następnie wybierz **Zapisz**. Domyślna lokalizacja to folder rozwiązania. 
- Aby wyeksportować kilka punktów przerwania, w **punktów przerwania** okna, zaznacz pola wyboru obok punktów przerwania lub wprowadź kryteria wyszukiwania we **wyszukiwania** pola. Wybierz **Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami wyszukiwania** ikonę, a następnie zapisz plik. 
- Aby wyeksportować wszystkie punkty przerwania, usuń zaznaczenie wszystkich pól i pozostawić **wyszukiwania** pole puste. Wybierz **Eksportuj wszystkie punkty przerwania zgodne z bieżącymi kryteriami wyszukiwania** ikonę, a następnie zapisz plik.  
- Można zaimportować punktów przerwania, w **punktów przerwania** wybierz **Importuj punkty przerwania z plikiem** ikony, przejdź do lokalizacji pliku XML, a następnie wybierz pozycję **Otwórz**. 

##  <a name="breakpoint-conditions"></a>Warunki punktu przerwania  
 Można kontrolować, kiedy i gdzie jest wykonywany punkt przerwania, ustawiając warunków. Warunek może być dowolne prawidłowe wyrażenie, które rozpoznaje debugera. Aby uzyskać więcej informacji dotyczących prawidłowych wyrażeń, zobacz [wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).  

**Aby ustawić warunek punktu przerwania:**

1. Kliknij prawym przyciskiem myszy symbol punktu przerwania i wybierz **warunki**. Lub ustaw kursor myszy symbol punktu przerwania, wybierz opcję **ustawienia** ikonę, a następnie wybierz **warunki** w **ustawienia punktu przerwania** okna.  

   Można również ustawić warunki, w **punktów przerwania** okna, kliknij prawym przyciskiem myszy punkt przerwania i wybierając **ustawienia**, a następnie wybierając **warunki**. 
  
   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
2. Z listy rozwijanej wybierz **wyrażenia warunkowego**, **liczba trafień**, lub **filtru**i odpowiednio ustawić wartości. 
  
3. Wybierz **Zamknij** lub naciśnij **Ctrl**+**Enter** zamknąć **ustawienia punktu przerwania** okna. Lub z **punktów przerwania** wybierz **OK** aby zamknąć okno dialogowe. 

Punkty przerwania z zestawem warunków są wyświetlane razem ze **+** symbol w kodzie źródłowym i **punktów przerwania** systemu windows. 

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Wyrażenie warunkowe

Po wybraniu **wyrażenia warunkowego**, możesz wybrać dwa warunki: **ma wartość true** lub **po zmianie**. Wybierz **ma wartość true** na przerwanie, gdy wyrażenie jest spełniony, lub **po zmianie** na przerwanie, gdy zmieniono wartość wyrażenia.  
  
 W poniższym przykładzie zostaje trafiony punkt przerwania tylko wtedy, gdy wartość `testInt` jest **4**:  
  
 ![Spełniony jest warunek punktu przerwania](../debugger/media/breakpointconditionistrue.png "punkt przerwania jest wartość true")  
  
 W poniższym przykładzie zostaje trafiony punkt przerwania tylko wtedy, gdy wartość `testInt` zmiany:  
  
 ![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "punktu przerwania po zmianie")  
  
 Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania o prawidłowej składni, ale nieprawidłowej semantyce, pojawi się ostrzeżenie, gdy punkt przerwania zostaje trafiony po raz pierwszy. W każdym z tych przypadków debuger przerywa przypadku trafienia nieprawidłowy punkt przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy warunek jest prawidłowy i daje w wyniku `false`.  
  
 >[!NOTE]
 >Zachowanie **po zmianie** pola różni się w różnych językach programowania. 
 >- Dla kodu natywnego debuger nie uważa pierwszej oceny warunku za zmianę, więc nie trafiony punkt przerwania w pierwszej oceny. 
 >- Dla kodu zarządzanego, debuger uderza w punkt przerwania w pierwszej ocenie po **po zmianie** jest zaznaczone.  
  
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Za pomocą identyfikatorów obiektów w wyrażeniach warunkowych (C# i F# tylko)  
 Istnieją terminy, gdy zachodzi potrzeba przyjrzeć się zachowaniu określonego obiektu. Na przykład można dowiedzieć się, dlaczego obiekt został wstawiony do kolekcji więcej niż jeden raz. W C# i F#, można tworzyć identyfikatory obiektów dla określonego wystąpienia [typy odwołań](/dotnet/csharp/language-reference/keywords/reference-types)i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług i powiązane z obiektem.  

**Aby utworzyć identyfikator obiektu:** 
  
1. Ustaw punkt przerwania w kodzie niektóre miejsca po utworzeniu obiektu.  
   
2. Rozpocznij debugowanie, a po wstrzymuje wykonywanie w punkcie przerwania, wybierz **debugowania** > **Windows** > **lokalne** lub **Alt** + **4** otworzyć **lokalne** okna.
   
   Znajdź punkt przerwania w **lokalne** okna, kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **wprowadzić identyfikator obiektu**.  
   
   Powinien zostać wyświetlony **$** oraz liczbą **lokalne** okna. Jest to identyfikator obiektu.  
   
3. Dodaj nowy punkt przerwania w punkcie, który chcesz zbadać; na przykład, gdy obiekt jest do dodania do kolekcji. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz **warunki**.  
   
4. Użyj Identyfikatora obiektu w **wyrażenia warunkowego** pola. Na przykład jeśli zmienna `item` jest obiektem, który ma zostać dodany do kolekcji, wybierz opcję **ma wartość true** i typ **elementu == $\<n >**, gdzie \<n > jest numer Identyfikatora obiektu .  
   
   Wykonywanie zostanie przerwane w momencie gdy ten obiekt ma być dodana do kolekcji.  
   
   Aby usunąć identyfikator obiektu, kliknij prawym przyciskiem myszy zmiennej w **lokalne** okna, a następnie wybierz pozycję **usunięcia obiektu o identyfikatorze**.  

>[!NOTE]
>Identyfikatory obiektów Utwórz słabe odwołania i uniemożliwia obiektu jako elementu bezużytecznego zbierane. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
### <a name="hit-count"></a>Liczba trafień  
 Jeśli podejrzewasz, że pętla w kodzie rozpoczyna się niewłaściwie po określonej liczbie iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonywanie po tę liczbę trafień, zamiast wielokrotnie naciskać **F5** do osiągnięcia tej iteracji.  
  
 W obszarze **warunki** w **ustawienia punktu przerwania** wybierz **liczba trafień**, a następnie określ liczbę iteracji. W poniższym przykładzie ustawiono punkt przerwania, aby trafić w każdej iteracji inne:  
  
 ![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
### <a name="filter"></a>Filtr  
Można ograniczyć punkt przerwania, aby wyzwalać tylko dla określonego urządzenia lub w określonych procesów i wątków.  
  
W obszarze **warunki** w **ustawienia punktu przerwania** wybierz **filtru**, a następnie wprowadź co najmniej jedną z następujących wyrażeń:  
  
-   MachineName = "name"  
-   ProcessId = wartość  
-   ProcessName = "name"  
-   ThreadId = wartość  
-   ThreadName = "name"  

Wartości parametrów należy ująć w cudzysłów. Można połączyć klauzule za pomocą `&` (oraz) `||` (lub), `!` (nie) i nawiasy.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akcje punktu przerwania i punkty śledzenia  
 A *śledzenia* jest punktem przerwania, który drukuje wiadomość do **dane wyjściowe** okna. Tracepoint może zachowywać się jak tymczasowa instrukcja śledzenia w języku programowania.  
  
**Aby ustawić punkt śledzenia:**

1. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz **akcje**. Lub w **ustawienia punktu przerwania** oknie, umieść kursor nad punkt przerwania, wybierz **ustawienia** ikonę, a następnie wybierz **akcje**.  
   
1. Wprowadź wiadomość w **Rejestruj komunikat w oknie danych wyjściowych** pola. Wiadomość może zawierać ciągi zwykłego tekstu, wartości zmiennych lub wyrażenie ujęte w nawiasy klamrowe i specyfikatorów formatu ([C#](../debugger/format-specifiers-in-csharp.md) i [C++](../debugger/format-specifiers-in-cpp.md)) dla wartości.
   
   Umożliwia także następujące słowa kluczowe w komunikacie:  
   
   - **$ADDRESS** — bieżący rozkaz  
   - **$CALLER** -nazwy funkcji wywoływania  
   - **$CALLSTACK** — stos wywołań 
   - **$FUNCTION** — nazwa bieżącej funkcji  
   - **$PID** — identyfikator procesu  
   - **$PNAME** — nazwa procesu  
   - **$TID** — identyfikator wątku  
   - **$TNAME** — Nazwa wątku  
   - **$TICK** -liczba znaczników (z Windows `GetTickCount`)  
   
1. Aby wydrukować komunikat **dane wyjściowe** okna bez przerywania wybierz **Kontynuuj wykonywanie** pole wyboru. Aby wydrukować komunikat i przerwania wykonywania na punkt śledzenia, wyczyść pole wyboru. 

Punkty śledzenia są wyświetlane jako czerwone diamenty na lewym marginesie kodu źródłowego i **punktów przerwania** systemu windows. 
  
## <a name="see-also"></a>Zobacz także  
 [Co to jest debugowanie?](../debugger/what-is-debugging.md)  
 [Tworzenie lepszych C# kodu za pomocą programu Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md)  
 [Rozwiązywanie problemów z punktów przerwania w debugerze programu Visual Studio](../debugger/troubleshooting-breakpoints.md)  
