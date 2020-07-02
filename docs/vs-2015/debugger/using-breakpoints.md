---
title: Używanie punktów przerwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bbe2ecf89f94cc75ff9036285ae9acbf9cf3b657
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534501"
---
# <a name="using-breakpoints"></a>Używanie punktów przerwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Możesz ustawić punkty przerwania, gdy chcesz zatrzymać wykonywanie debugera, być może widzisz stan zmiennych kodu lub obejrzyj stos wywołań. Są one jedną z najważniejszych technik debugowania w przyborniku dewelopera.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Ustawianie punktu przerwania funkcji w kodzie źródłowym  
 Aby ustawić punkt przerwania funkcji w kodzie źródłowym, kliknij na lewym marginesie pliku kodu źródłowego lub przez umieszczenie kursora w wierszu kodu i naciśnięcie klawisza F9. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie, a wiersz kodu jest również kolorowy:  
  
 ![Ustawianie punktu przerwania](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Po uruchomieniu tego kodu w debugerze wykonywanie jest przerywane za każdym razem, gdy punkt przerwania zostanie osiągnięty, przed wykonaniem kodu w tym wierszu. Linia kodu źródłowego jest kolorem żółtym:  
  
 ![Zatrzymano wykonywanie punktu przerwania](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 W tym momencie wartość jest równa `testInt` 1.  
  
 Możesz sprawdzić bieżący stan aplikacji, w tym wartości zmiennych i stos wywołań. Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
 Punkt przerwania można ustawić na dowolnym wierszu kodu wykonywalnego. Na przykład w powyższym kodzie C# można ustawić punkt przerwania dla deklaracji zmiennej, `for` pętlę lub dowolny kod wewnątrz `for` pętli, ale nie można ustawić punktu przerwania w przypadku deklaracji przestrzeni nazw lub klasy ani sygnatury metody.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Ustawianie innych rodzajów punktów przerwania  
 Możesz również ustawić punkty przerwania w stosie wywołań, w oknie demontażu, a w kodzie natywnym C++, w warunku danych lub w adresie pamięci.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Ustawianie punktu przerwania w oknie stosu wywołań  
 Możesz przerwać wykonywanie w instrukcji lub wierszu, z którym wraca funkcja wywołująca, przez ustawienie punktu przerwania w oknie **stosu wywołań** . Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md). Debuger musi zatrzymać wykonywanie.  
  
1. Rozpocznij debugowanie aplikacji i zaczekaj na zatrzymanie wykonywania (na przykład w punkcie przerwania). Otwórz okno **stos wywołań** (**Debugowanie/Windows/stos wywołań**lub **Ctrl + Alt + C**).  
  
2. Kliknij prawym przyciskiem myszy funkcję wywołującą, a następnie wybierz pozycję **punkt przerwania/Wstaw punkt przerwania**lub po prostu Użyj klawisza skrótu **F9**.  
  
3. Symbol punktu przerwania pojawia się na lewym marginesie stosu wywołań obok nazwy wywołania funkcji.  
  
   W oknie **punkty przerwania** stos wywołań jest wyświetlany jako adres z lokalizacją w pamięci, która odpowiada następnej instrukcji wykonywalnej w funkcji. Debuger przerywa wykonywanie w instrukcji.  
  
   Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ustawianie punktu przerwania w oknie demontażu  
 Aby ustawić punkt przerwania w instrukcji zestawu, debuger musi być w trybie przerwania.  
  
1. Rozpocznij debugowanie aplikacji i zaczekaj na zatrzymanie wykonywania (na przykład w punkcie przerwania). Otwórz okno **demontaż** (**Debuguj/Windows/demontażu**lub **Ctrl + Alt + D**).  
  
2. Kliknij na lewym marginesie instrukcji, która ma zostać przerwana, lub ustaw kursor na instrukcji i naciśnij klawisz **F9**.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Ustawianie punktu przerwania danych (tylko natywne C++)  
 Punkty przerwania danych przerywają wykonywanie w przypadku zmiany wartości przechowywanej w określonym adresie pamięci. Jeśli wartość jest odczytywana, ale nie została zmieniona, wykonywanie nie jest przerywane. Aby ustawić punkty przerwania danych, debuger musi być w trybie przerwania.  
  
1. Rozpocznij debugowanie aplikacji i poczekaj, aż zostanie osiągnięty punkt przerwania. W menu **Debuguj** wybierz pozycję **nowy punkt przerwania/punkt przerwania danych** (lub Otwórz okno **punkty przerwania** i wybierz pozycję **nowy/punkt przerwania danych**).  
  
2. W polu **adres** wpisz adres pamięci lub wyrażenie, które daje w wyniku adres pamięci. Na przykład wpisz, `&avar` Aby przerwać, gdy zmieni się zawartość zmiennej `avar` .  
  
3. Z listy rozwijanej **liczba bajtów** wybierz liczbę bajtów, które ma oglądać debuger. Na przykład po wybraniu opcji **4**debuger będzie oglądać cztery bajty, zaczynając od `&avar` i Break, jeśli którykolwiek z tych bajtów zmieni wartość.  
  
   Należy pamiętać, że punkty przerwania danych zależą od możliwości zastosowania określonych adresów pamięci.  
  
- Adres zmiennej zmienia się z jednej sesji debugowania na następną. Punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.  
  
- Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, punkt przerwania zostanie włączony, gdy funkcja zostanie zakończona, ale adres pamięci nie będzie już stosowany, a zachowanie punktu przerwania jest nieprzewidywalne. Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem działania funkcji.  
  
  Punkty przerwania danych nie działają w następujących warunkach:  
  
- Proces, który nie jest debugowany zapis w lokalizacji pamięci  
  
- Lokalizacja pamięci jest współdzielona przez dwa lub więcej procesów  
  
- Lokalizacja pamięci jest aktualizowana w jądrze. Na przykład jeśli pamięć jest przenoszona do 32-bitowej funkcji systemu Windows `ReadFile` , pamięć zostanie zaktualizowana z trybu jądra, a debuger nie przerwie podczas zapisu w pamięci.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Ustawianie punktu przerwania z adresem pamięci (tylko natywne C++)  
 Możesz również użyć adresu obiektu, aby ustawić punkt przerwania dla metody wywoływanej w konkretnym wystąpieniu klasy.  Przykład:  
  
 Na przykład, mając obiekt typu `my_class` z adresem, można ustawić punkt przerwania funkcji dla metody o nazwie `my_method` wywoływanej z tego wystąpienia.  
  
1. Ustaw punkt przerwania w dowolnym miejscu po utworzeniu wystąpienia klasy.  
  
2. Znajdź adres wystąpienia (to znaczy `0xcccccccc` ).  
  
3. Kliknij pozycję **Debuguj/nowy punkt przerwania/punkt przerwania funkcji** (lub **ALT + F9, B**).  
  
4. Dodaj następujący tekst do pola **nazwa funkcji** :  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Zarządzanie punktami przerwania  
 Możesz użyć okna **punkty przerwania** (**debugowanie/okna/punkty przerwania**lub **Ctrl + Alt + B**), aby zobaczyć wszystkie punkty przerwania ustawione w rozwiązaniu:  
  
 ![Okno punktów przerwania](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 Okno **punkty przerwania** udostępnia centralne miejsce do zarządzania wszystkimi punktami przerwania, które mogą być szczególnie przydatne w przypadku dużych rozwiązań lub złożonych scenariuszy debugowania, w których punkty przerwania są krytyczne. Jeśli zachodzi potrzeba zapisania lub udostępnienia stanu i lokalizacji zestawu punktów przerwania, można eksportować i importować punkty przerwania tylko z okna **punkty przerwania** .  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Zaawansowane punkty przerwania  
  
## <a name="breakpoint-conditions"></a>Warunki punktu przerwania  
 Można kontrolować, kiedy i gdzie wykonywany jest punkt przerwania, ustawiając warunki.  
  
1. Kliknij prawym przyciskiem myszy punkt przerwania lub umieść kursor nad punktem przerwania, a następnie wybierz ikonę Ustawienia.  
  
2. W menu kontekstowym wybierz pozycję **warunki**. Spowoduje to otwarcie okna **Ustawienia punktu przerwania** :  
  
   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   Po zaznaczeniu pola **warunki** okno zostanie rozwinięte, aby pokazać różne rodzaje warunków.  
  
   **Wyrażenie warunkowe:** Po wybraniu wyrażenia warunkowego można wybrać dwa warunki: **wartość true** i **po zmianie**. Wybierz **wartość PRAWDA** , jeśli chcesz przerwać, gdy wyrażenie jest spełnione, lub wybierz, **Kiedy zmiana** ma zostać przerwana, gdy wartość wyrażenia zostanie zmieniona.  
  
   W poniższym przykładzie ustawimy punkt przerwania, tylko wtedy, gdy wartość `testInt` wynosi **4**:  
  
   ![Warunek punktu przerwania ma wartość true](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   W poniższym przykładzie ustawimy punkt przerwania tak, aby był trafiony tylko w przypadku `testInt` zmiany wartości:  
  
   ![Punkt przerwania w przypadku zmiany](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Zachowanie w przypadku zmiany pola jest różne dla różnych języków programowania. Jeśli wybierzesz **zmianę** dla kodu natywnego, debuger nie uwzględnia pierwszej oceny warunku do zmiany, więc punkt przerwania nie zostanie osiągnięty przy pierwszej ocenie. Jeśli wybierzesz **zmianę** dla kodu zarządzanego, punkt przerwania zostanie osiągnięty podczas pierwszej oceny po wybraniu opcji **zmieniono** .  
  
   Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania z prawidłową składnią, ale z nieprawidłową semantyką, pojawi się komunikat ostrzegawczy przy pierwszym trafieniu punktu przerwania. W obu przypadkach debuger przerywa wykonywanie, gdy zostanie trafiony nieprawidłowy punkt przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy warunek jest prawidłowy i ma wartość `false` .  
  
   Warunek może być dowolnym prawidłowym wyrażeniem rozpoznawanym przez debuger. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń, zobacz [wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Korzystanie z identyfikatorów obiektów w warunkach punktu przerwania (C# i F #)  
 Istnieją przypadki, w których chcesz obserwować zachowanie określonego obiektu; na przykład możesz chcieć dowiedzieć się, dlaczego obiekt został wstawiony do kolekcji więcej niż raz. W językach C# i F # można tworzyć identyfikatory obiektów dla określonych wystąpień [typów referencyjnych](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzone z obiektem.  Aby utworzyć identyfikator obiektu, wykonaj następujące czynności:  
  
1. Ustaw punkt przerwania w kodzie jakiś czas po utworzeniu obiektu.  
  
2. Rozpocznij debugowanie i po zatrzymaniu wykonywania w punkcie przerwania Znajdź punkt przerwania w oknie **zmiennych lokalnych** , kliknij go prawym przyciskiem myszy, a następnie wybierz polecenie **Utwórz identyfikator obiektu**.  
  
    Powinna zostać wyświetlona **$** Plus cyfra w oknie **zmiennych lokalnych** . To jest identyfikator obiektu.  
  
3. Dodaj nowy warunkowy punkt przerwania w punkcie, który chcesz zbadać, na przykład gdy obiekt ma zostać dodany do kolekcji.  
  
4. Użyj identyfikatora obiektu w polu wyrażenia warunkowego. Na przykład, jeśli istnieje zmienna `item` odwołująca się do obiektu, który ma zostać dodany do kolekcji, należy umieścić **element = = $n**, gdzie **n** jest numerem identyfikatora obiektu.  
  
    Wykonanie zostanie przerwane w momencie, gdy ten obiekt zostanie dodany do kolekcji.  
  
   Jeśli chcesz później usunąć identyfikator obiektu, możesz kliknąć prawym przyciskiem myszy zmienną w oknie **zmiennych lokalnych** i wybrać pozycję **Usuń identyfikator obiektu**.  
  
   Należy zauważyć, że identyfikatory obiektów tworzą słabe odwołania i nie uniemożliwiają odzyskiwania obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
## <a name="hit-count"></a>Liczba trafień  
 Jeśli podejrzewasz, że pętla w kodzie zaczyna się błędna po określonej liczbie iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonywanie po podanej liczbie trafień do skojarzonego wiersza kodu, zamiast wymuszać wielokrotne naciśnięcie klawisza **F5** w celu osiągnięcia poziomu iteracji.  
  
 W oknie **Ustawienia punktu przerwania** Ustaw warunek na **liczbę trafień**. Następnie można określić liczbę iteracji. W poniższym przykładzie ustawimy punkt przerwania w przypadku każdej innej iteracji:  
  
 ![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtr  
 Punkt przerwania można ograniczyć do uruchamiania tylko na określonych urządzeniach lub w określonych procesach i wątkach.  
  
 W oknie **Ustawienia punktu przerwania**Ustaw warunek do **filtrowania**. Wprowadź co najmniej jedno z następujących wyrażeń.  
  
- MachineName = "name"  
  
- ProcessId = wartość  
  
- ProcessName = "name"  
  
- ThreadId = wartość  
  
- ThreadName = "name"  
  
  Ujmij wartości ciągu w podwójne cudzysłowy. Można łączyć klauzule przy użyciu `&` (i), `||` (lub), `!` (nie) i nawiasów.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akcje punktu przerwania i punkty śledzenia  
 Punkt śledzenia jest punktem przerwania, który drukuje komunikat do okna danych wyjściowych. Punkt śledzenia może działać jak tymczasowa instrukcja śledzenia w języku programowania.  
  
 W oknie **Ustawienia punktu przerwania** zaznacz pole **Akcje** . Wybierz pozycję **Rejestruj komunikat w oknie danych wyjściowych** w grupie **akcji** . Można wydrukować ciąg ogólny, na przykład **ten test**. Aby uwzględnić wartość zmiennej lub wyrażenia, należy ująć ją w nawiasy klamrowe.  
  
 Aby przerwać wykonywanie po trafieniu punkt śledzenia, usuń zaznaczenie pola wyboru **Kontynuuj wykonywanie** . Gdy jest zaznaczone pole wyboru **Kontynuuj wykonywanie** , wykonywanie nie jest zatrzymywane. W obu przypadkach komunikat jest drukowany.  
  
 W **komunikacie**można używać następujących specjalnych słów kluczowych.  
  
|Słowo kluczowe|Opis|  
|-|-|  
|**$ADDRESS**|Bieżąca instrukcja|  
|**$CALLER**|Nazwa funkcji wywołującej|  
|**$CALLSTACK**|Stos wywołań|  
|**$FUNCTION**|Nazwa bieżącej funkcji|  
|**$PID**|Identyfikator procesu|  
|**$PNAME**|Nazwa procesu|  
|**$TID**|Identyfikator wątku|  
|**$TNAME**|Nazwa wątku|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Etykiety punktów przerwania  
 Etykiety punktów przerwania są używane tylko w oknie **punkty przerwania** do sortowania i filtrowania listy punktów przerwania. Aby dodać etykietę do punktu przerwania, wybierz wiersz punktu przerwania, a następnie wybierz pozycję **etykieta** w menu kontekstowym.  
  
## <a name="export-and-import-breakpoints"></a>Eksportuj i Importuj punkty przerwania  
 Punkt przerwania można wyeksportować do pliku XML, klikając prawym przyciskiem myszy punkt przerwania i wybierając pozycję **Eksportuj**. Plik jest domyślnie zapisywany w katalogu rozwiązania. Aby zaimportować punkty przerwania, Otwórz okno **punkty przerwania** (**Ctrl + Alt + B**) i na pasku narzędzi kliknij strzałkę wskazującą w prawo (etykietka narzędzia powoduje **Importowanie punktów przerwania z pliku**).  
  
## <a name="troubleshoot-breakpoints"></a>Rozwiązywanie problemów z punktami przerwania  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po usunięciu punktu przerwania nadal go klikam, gdy Rozpocznij debugowanie ponownie  
 Jeśli punkt przerwania został usunięty podczas debugowania, w niektórych przypadkach można ponownie uruchomić punkt przerwania przy następnym rozpoczęciu debugowania. Aby przerwać ten punkt przerwania, upewnij się, że wszystkie wystąpienia punktu przerwania są usuwane z okna **punkty przerwania** .  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Debuger nie może znaleźć poprawnej wersji pliku źródłowego dla punktu przerwania  
 Jeśli plik źródłowy został zmieniony, a źródło nie pasuje już do kodu, który jest debugowany, debuger może zlokalizować plik źródłowy, który odnosi się do punktu przerwania, nawet jeśli plik źródłowy istnieje.  
  
1. Jeśli chcesz, aby program Visual Studio wyświetlał kod źródłowy, który jest niezgodny z debugowaną wersją, wybierz polecenie **Debuguj/opcje i ustawienia**. Na stronie **debugowanie/ogólne** wyczyść pole wyboru **Wymagaj plików źródłowych, które dokładnie pasują do oryginalnej wersji** .  
  
2. Można również powiązać punkt przerwania z plikiem źródłowym. Wybierz punkt przerwania i wybierz pozycję **warunki** w menu kontekstowym. Zaznacz pole wyboru **Zezwalaj, aby kod źródłowy różnił się od oryginału** w oknie **Ustawienia punktu przerwania** .  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Punkty przerwania nie działają w bibliotece DLL  
 Nie można ustawić punktu przerwania w pliku źródłowym, gdy debuger nie załadował informacji debugowania dla modułu, w którym znajduje się kod. Objawy mogą zawierać komunikaty, takie jak **punkt przerwania nie zostanie ustawiony**. Symbol punktu przerwania ostrzeżenia pojawia się w lokalizacji punktu przerwania. Jednak te ostrzeżenia są wyświetlane jako rzeczywiste punkty przerwania podczas ładowania kodu. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
