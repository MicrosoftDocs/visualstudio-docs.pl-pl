---
title: Używanie punktów przerwania | Dokumentacja firmy Microsoft
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
manager: ghogen
ms.openlocfilehash: d980fd2367545eb5c824bacc507d9ced9aa2d723
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765962"
---
# <a name="using-breakpoints"></a>Używanie punktów przerwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Można ustawić punktów przerwania, jeśli chcesz zatrzymać wykonywanie debugera, być może wyświetlić stan zmiennych kodu lub Spójrz na stos wywołań. Są one jednym z najważniejszych technik debugowania dostępnych w przyborniku dla deweloperów.
  
##  <a name="BKMK_Overview"></a> Ustawianie punktu przerwania funkcji w kodzie źródłowym  
 Możesz ustawić punktu przerwania funkcji w kodzie źródłowym, klikając w lewy margines w pliku kodu źródłowego lub umieszczając kursor w wierszu kodu i naciskając klawisz F9. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie, a w wierszu kodu jest także pokolorowane:  
  
 ![Ustaw punkt przerwania](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Po uruchomieniu tego kodu w debugerze, zatrzyma wykonywanie zawsze wtedy, gdy punkt przerwania zostaje trafiony przed wykonaniem kodu w danym wierszu. Wiersz kodu źródłowego jest kolor żółty:  
  
 ![Punkt przerwania wykonywania zatrzymana](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 W tym momencie wartość `testInt` nadal jest 1.  
  
 Można sprawdzić bieżący stan aplikacji, w tym wartości zmiennych i stosu wywołań. Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
 Możesz ustawić punkt przerwania w każdym wierszu kodu wykonywalnego. Na przykład w języku C# kodu powyżej można ustawić punkt przerwania w deklaracji zmiennej `for` pętli lub dowolny kod wewnątrz `for` pętli, ale nie można ustawić punkt przerwania na deklaracje przestrzeni nazw lub klasy lub podpis metody.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Ustawienie inne rodzaje punktów przerwania  
 Można również ustawić punkty przerwania w stosie wywołań, w oknie demontażu i, w kodzie natywnym języku C++, warunek danych lub adres pamięci.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Ustawianie punktu przerwania w oknie stosu wywołań  
 Możesz przerwać wykonywanie w instrukcji lub wierszu, który powraca wywołanie funkcji, aby ustawić punkt przerwania w **stos wywołań** okna. Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md). Debuger musi mieć przestał być wykonywany.  
  
1. Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania jest zatrzymana (na przykład w punkcie przerwania). Otwórz **stos wywołań** okna (**debugowanie / Windows / stos wywołań**, lub **CTRL + ALT + C**).  
  
2. Kliknij prawym przyciskiem myszy funkcji wywołującej, a następnie wybierz pozycję **punktu przerwania / Wstaw punkt przerwania**, lub po prostu użyj klawisza skrótu **F9**.  
  
3. Symbol punktu przerwania pojawia się na lewym marginesie stos wywołań, obok nazwy wywołania funkcji.  
  
   W **punktów przerwania** , punkt przerwania stosu wywołań zostanie wyświetlone jako adresu z lokalizacją pamięci, która odpowiada następnej instrukcji wykonywalnej w funkcji. Debuger przerywa wykonywanie w instrukcji.  
  
   Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ustawienie punktu przerwania w oknie demontaż  
 Aby ustawić punkt przerwania w instrukcji montażu, debuger musi być w trybie przerwania.  
  
1.  Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania jest zatrzymana (na przykład w punkcie przerwania). Otwórz **dezasemblacji** okna (**debugowanie / Windows / dezasemblacji**, lub **Ctrl + Alt + D**).  
  
2.  Kliknij na lewym marginesie w instrukcji, które chcesz przerwać lub ustawić kursor na instrukcji i naciśnij klawisz **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a> Ustawianie punktu przerwania danych (tylko w natywnym kodzie C++)  
 Punkty przerwania danych przerwać wykonywanie, gdy wartość, która jest przechowywana w zmiany adresu określonego pamięci. Jeśli wartości jest czytana, ale nie został zmieniony, wykonanie nie zostanie przerwane. Aby ustawić punkty przerwania danych, debuger musi być w trybie przerwania.  
  
1. Rozpocznij debugowanie aplikacji i zaczekaj, aż do osiągnięcia punktu przerwania. Na **debugowania** menu, wybierz **nowego punktu przerwania / punktu przerwania danych** (lub Otwórz **punktów przerwania** okna i wybierz polecenie **New / punktu przerwania danych**.  
  
2. W **adres** wpisz adres pamięci lub wyrażenie, które daje w wyniku adres pamięci. Na przykład wpisz `&avar` przerwanie, kiedy zawartość zmiennej `avar` zmiany.  
  
3. W **liczba bajtów** listy rozwijanej wybierz liczbę bajtów, które chcesz, aby debuger ma uważać. Na przykład w przypadku wybrania **4**, debuger będzie obserwował cztery bajty począwszy `&avar` i przerwie działanie, jeśli którykolwiek z tych bajtów zmienić wartość.  
  
   Należy pamiętać, że punkty przerwania danych zależy od stosowania adresów pamięci.  
  
- Adres zmiennej zmieni się między jedną sesją debugowania do następnego. Punkty przerwania danych są automatycznie wyłączane na koniec każdej sesji debugowania.  
  
- Jeśli punkt przerwania danych zostanie ustawiony na zmiennej lokalnej, pozostaje punkt przerwania, włączona, gdy funkcja skończy działanie, ale adres pamięci nie ma już zastosowania, a zachowanie punktu przerwania są nieprzewidywalne. Jeśli punkt przerwania danych zostanie ustawiony na zmiennej lokalnej, należy usunąć lub wyłącz punkt przerwania przed końcem działania funkcji.  
  
  Punkty przerwania danych nie działają w tych warunkach:  
  
- Proces, który nie jest debugowany, zapisuje w lokalizacji pamięci  
  
- Lokalizacja pamięci jest współużytkowana przez dwa lub więcej procesów  
  
- Lokalizacja pamięci jest aktualizowana w jądrze. Na przykład, jeśli pamięć jest przekazywana do Windows 32-bitowych `ReadFile` funkcji, pamięć zostanie zaktualizowana z trybu jądra i debuger nie przerywa działania podczas zapisu w pamięci.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Ustawienie punktu przerwania przy użyciu adresu pamięci (tylko w natywnym kodzie C++)  
 Aby ustawić punkt przerwania na metodę o nazwie na określonym wystąpieniu klasy umożliwia także adres obiektu.  Oto przykład:  
  
 Na przykład, biorąc pod uwagę obiekt typu `my_class` za pomocą adresu, można ustawić punktu przerwania funkcji w metodę o nazwie `my_method` wywoływane z tego wystąpienia.  
  
1.  Ustaw punkt przerwania gdzieś po konkretyzacji tego wystąpienia klasy.  
  
2.  Znajdź adres wystąpienia (przycisk ma `0xcccccccc`).  
  
3.  Kliknij przycisk **debugowanie / nowy punkt przerwania / funkcji punktu przerwania** (lub **ALT + F9, B**).  
  
4.  Dodaj następujący tekst, aby **nazwy funkcji** pola:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Zarządzanie punktów przerwania  
 Możesz użyć **punktów przerwania** okna (**debugowanie / Windows / punktów przerwania**, lub **CTRL + ALT + B**) aby wyświetlić wszystkie punkty przerwania ustawiono w rozwiązaniu:  
  
 ![Okno punktów przerwania](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 **Punktów przerwania** okno udostępnia centralne miejsce do zarządzania wszystkimi punktami przerwań, które mogą być szczególnie przydatne w dużym rozwiązaniem lub złożonych scenariuszy debugowania, w których punkty przerwania mają kluczowe znaczenie. Jeśli trzeba zapisać lub udostępnić stan i lokalizację zbioru punktów przerwania, możesz wyeksportować i zaimportować punktów przerwania tylko z **punktów przerwania** okna.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Zaawansowane punkty przerwania  
  
## <a name="breakpoint-conditions"></a>Warunki punktu przerwania  
 Można kontrolować, kiedy i gdzie jest wykonywany punkt przerwania, ustawiając warunków.  
  
1. Kliknij prawym przyciskiem myszy punkt przerwania lub Najedź kursorem punkt przerwania i wybierz ikonę ustawienia.  
  
2. W menu kontekstowym wybierz **warunki**. Spowoduje to otwarcie **ustawienia punktu przerwania** okna:  
  
   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   Kiedy zaznaczysz **warunki** polu okna rozwija do wyświetlania różnych typów warunków.  
  
   **Wyrażenie warunkowe:** po wybraniu wyrażenia warunkowego, można wybrać dwa warunki: **ma wartość true** i **po zmianie**. Wybierz **ma wartość true** Jeśli chcesz przerwać gdy wyrażenie jest spełniony, lub wybierz **po zmianie** Jeśli chcesz przerwać, gdy zmieniono wartość wyrażenia.  
  
   W poniższym przykładzie, możemy ustawić punkt przerwania, aby trafić tylko wtedy, gdy wartość `testInt` jest **4**:  
  
   ![Spełniony jest warunek punktu przerwania](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   W poniższym przykładzie, możemy ustawić punkt przerwania, aby trafić tylko wtedy, gdy wartość `testInt` zmiany:  
  
   ![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Zachowanie po zmienionego pola jest różne w różnych językach programowania. Jeśli wybierzesz **po zmianie** dla kodu natywnego, debuger nie uważa pierwszej oceny warunku za zmianę, więc punkt przerwania nie zostanie osiągnięty przy pierwszej ocenie. Jeśli wybierzesz **po zmianie** dla kodu zarządzanego, punkt przerwania zostanie osiągnięty przy pierwszej ocenie po **po zmianie** jest zaznaczone.  
  
   Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, zostanie wyświetlony komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania o prawidłowej składni, ale nieprawidłowej semantyce, pojawi się ostrzeżenie, gdy punkt przerwania zostaje trafiony po raz pierwszy. W każdym z tych przypadków debuger przerywa wykonywanie, gdy nieprawidłowy punkt przerwania zostaje trafiony. Punkt przerwania jest pomijany tylko wtedy, gdy warunek jest prawidłowy i daje w wyniku `false`.  
  
   Warunek może być dowolnym prawidłowym wyrażeniem rozpoznawanym przez debuger. Aby uzyskać więcej informacji dotyczących prawidłowych wyrażeń, zobacz [wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Za pomocą identyfikatorów obiektów w warunkach punkt przerwania (C# i F#)  
 Istnieją momenty, gdy zachodzi potrzeba przyjrzeć się zachowaniu określonego obiektu; na przykład można dowiedzieć się, dlaczego obiekt został wstawiony więcej niż jeden raz w kolekcji. W C# i F#, można tworzyć identyfikatory obiektów dla określonego wystąpienia [typy odwołań](http://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług i powiązane z obiektem.  Aby utworzyć identyfikator obiektu, wykonaj następujące czynności:  
  
1. Ustaw punkt przerwania w kodzie na pewien czas, po utworzeniu obiektu.  
  
2. Uruchamianie debugowania oraz po zatrzymaniu w punkcie przerwania wykonywania znaleźć punkt przerwania w **lokalne** okna, kliknij go prawym przyciskiem myszy, a następnie wybierz pozycję **wprowadzić identyfikator obiektu**.  
  
    Powinien zostać wyświetlony **$** oraz liczbą **lokalne** okna. Jest to identyfikator obiektu.  
  
3. Dodaj nowe warunkowego punktu przerwania w punkcie, że chcesz zbadać, na przykład jeśli obiekt jest do dodania do kolekcji.  
  
4. W polu Wyrażenie warunkowe, należy użyć Identyfikatora obiektu. Na przykład, jeśli występuje zmienna `item` odwołujące się do obiektu, który ma zostać dodany do kolekcji, możesz umieścić **elementu == $n**, gdzie **n** jest numer Identyfikatora obiektu.  
  
    Wykonywanie zostanie przerwane w momencie gdy ten obiekt ma być dodana do kolekcji.  
  
   Jeśli chcesz później usunąć identyfikator obiektu, należy kliknąć prawym przyciskiem myszy zmiennej w **lokalne** okna, a następnie wybierz pozycję **usunięcia obiektu o identyfikatorze**.  
  
   Należy pamiętać, że identyfikatory obiektów tworzenie słabe odwołania i uniemożliwia obiektu jako elementu bezużytecznego zbierane. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
## <a name="hit-count"></a>Liczba trafień  
 Jeśli podejrzewasz, że pętla w kodzie rozpoczyna się niewłaściwie po określonej liczbie iteracji, możesz ustawić punkt przerwania, aby zatrzymać wykonywanie po określonej liczby dotarć do skojarzonego wiersza kodu, zamiast być zmuszonym do kilkukrotnego naciśnij  **F5** do osiągnięcia poziomu iteracji.  
  
 W **ustawienia punktu przerwania** oknie, warunek na **liczba trafień**. Następnie możesz określić liczbę iteracji. W poniższym przykładzie możemy ustawić punkt przerwania, aby trafić w każdej iteracji innych:  
  
 ![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtr  
 Można ograniczyć punkt przerwania, aby wyzwalać tylko dla określonego urządzenia lub w określonych procesów i wątków.  
  
 W **ustawienie punktu przerwania**s oknie, warunek na **filtru**. Wprowadź co najmniej jedną z następujących wyrażeń.  
  
- MachineName = "name"  
  
- ProcessId = wartość  
  
- ProcessName = "name"  
  
- ThreadId = wartość  
  
- ThreadName = "name"  
  
  Wartości parametrów należy ująć w cudzysłów. Można połączyć klauzule za pomocą `&` (oraz) `||` (lub), `!` (nie) i nawiasy.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Akcje punktu przerwania i punkty śledzenia  
 Punkt śledzenia jest punktem przerwania, który drukuje wiadomość w oknie danych wyjściowych. Tracepoint może zachowywać się jak tymczasowa instrukcja śledzenia w języku programowania.  
  
 W **ustawienia punktu przerwania** okno wyboru **akcje** pole. Wybierz **Rejestruj komunikat w oknie danych wyjściowych** w **akcji** grupy. Można wydrukować ciąg ogólnych, takich jak **to test**. Aby uwzględnić wartość zmiennej lub wyrażenia, należy ją ująć w nawiasy klamrowe.  
  
 Aby przerwać wykonywanie po osiągnięciu punktu śledzenia, wyczyść **Kontynuuj wykonywanie** pole wyboru. Gdy **Kontynuuj wykonywanie** jest zaznaczone, wykonanie nie zostało zatrzymane. W obu przypadkach komunikat jest drukowany.  
  
 Można użyć następujących specjalnych słów kluczowych w **komunikat**.  
  
|||  
|-|-|  
|**$ADDRESS**|Bieżącej instrukcji|  
|**$CALLER**|Nazwa funkcji wywoływania|  
|**$CALLSTACK**|Stos wywołań|  
|**$FUNCTION**|Nazwa bieżącej funkcji|  
|**$PID**|Identyfikator procesu|  
|**$PNAME**|Nazwa procesu|  
|**$TID**|Identyfikator wątku|  
|**$TNAME**|Nazwa wątku|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Etykiety punktów przerwania  
 Etykiety punktów przerwania są używane tylko w **punktów przerwania** okna, aby sortować i filtrować listy punktów przerwania. Aby dodać etykietę do punktu przerwania, wybierz wiersz punktu przerwania, a następnie wybierz **etykiety** w menu kontekstowym.  
  
## <a name="export-and-import-breakpoints"></a>Eksport i Import punktów przerwania  
 Punkt przerwania można wyeksportować do pliku XML, klikając prawym przyciskiem myszy punkt przerwania i wybierając polecenie **wyeksportować**. Plik jest zapisywany w katalogu rozwiązania domyślnie. Aby zaimportować punktów przerwania, otwórz **punktów przerwania** okna (**CTRL + ALT + B**) i na pasku narzędzi kliknij strzałkę skierowaną w prawo (etykietka narzędzia jest **Importuj punkty przerwania z plikiem**) .  
  
## <a name="troubleshoot-breakpoints"></a>Rozwiązywanie problemów z punktów przerwania  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po usunięciu punktu przerwania, ale można kontynuować trafień je, gdy I ponownie Rozpocznij debugowanie  
 Jeśli usunięty punkt przerwania podczas debugowania, w niektórych przypadkach można napotkać punkt przerwania ponownie przy następnym uruchomieniu debugowania. Aby zatrzymać, naciśnięcie tego punktu przerwania, sprawdź, czy wszystkie wystąpienia punktu przerwania są usuwane z **punktów przerwania** okna.  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Debuger nie może zlokalizować poprawnej wersji pliku źródłowego dla punktu przerwania  
 Jeśli plik źródłowy został zmieniony i źródło nie jest już zgodny z kodu, który jest debugowany, debuger może zlokalizować pliku źródłowego, który odpowiada punktowi przerwania, nawet jeśli plik źródłowy istnieje.  
  
1.  Jeśli chcesz, aby wyświetlić kod źródłowy, który nie pasuje do wersji programu Visual Studio debugowania, wybierz polecenie **Debuguj / opcje i ustawienia**. Na **debugowanie/ogólne** strony, wyczyść **wymaga plików źródłowych, które dokładnie dopasować oryginalną wersję** opcji.  
  
2.  Możesz również powiązać punkt przerwania w pliku źródłowym. Zaznacz punkt przerwania i wybierz polecenie **warunki** w menu kontekstowym. Sprawdź **Zezwalaj kod źródłowy różnił się od oryginału** w **ustawienia punktu przerwania** okna.  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Punkty przerwania nie działają w bibliotece DLL  
 Nie można ustawić punktu przerwania w pliku źródłowym, gdy debuger nie załadował jeszcze informacje debugowania dla modułu gdzie znajduje się kod. Objawy mogą obejmować takie jak wiadomości **nie będzie można ustawić punktu przerwania**. Glif ostrzegawczy punktu przerwania pojawia się w lokalizacji punktu przerwania. Jednak te ostrzegawcze punkty przerwania stają się rzeczywistymi punktami przerwania podczas ładowania kodu. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)



