---
title: Korzystanie z punktów przerwania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: cadaf069bb53c9d212e6de5ebd6ea2cf9efe7bb1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302470"
---
# <a name="using-breakpoints"></a>Używanie punktów przerwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Można ustawić punkty przerwania, gdy chcesz zatrzymać wykonywanie debugera, być może, aby zobaczyć stan zmiennych kodu lub spojrzeć na stos wywołań. Są one jedną z najważniejszych technik debugowania w przyborniku dewelopera.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Ustawianie punktu przerwania funkcji w kodzie źródłowym  
 Punkt przerwania funkcji w kodzie źródłowym można ustawić, klikając lewy margines pliku kodu źródłowego lub umieszczając kursor w wierszu kodu i naciskając klawisz F9. Punkt przerwania jest wyświetlany jako czerwona kropka na lewym marginesie, a wiersz kodu jest również kolorowy:  
  
 ![Ustawianie punktu przerwania](../debugger/media/basicbreakpoint.png "PodstawowyPunkt podziału")  
  
 Po uruchomieniu tego kodu w debugerze, wykonanie zatrzymuje się za każdym razem, gdy punkt przerwania zostanie trafiony, przed wykonaniem kodu w tym wierszu. Linia kodu źródłowego jest w kolorze żółtym:  
  
 ![Przerwano wykonywanie punktu przerwania](../debugger/media/breakpointexecution.png "BreakpointWykonańcja")  
  
 W tym momencie `testInt` wartość jest nadal 1.  
  
 Można spojrzeć na bieżący stan aplikacji, w tym wartości zmiennych i stos wywołań. Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [Jak: Użyj okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
 Punkt przerwania można ustawić w dowolnym wierszu kodu wykonywalnego. Na przykład w kodzie C# powyżej można ustawić punkt przerwania na deklaracji zmiennej, `for` pętli lub dowolnego kodu wewnątrz `for` pętli, ale nie można ustawić punkt przerwania w obszarze nazw lub deklaracji klasy lub podpis metody.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Ustawianie innych rodzajów punktów przerwania  
 Można również ustawić punkty przerwania w stosie wywołań, w oknie demontażu i, w natywnym kodzie C++, w warunku danych lub adres pamięci.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Ustawianie punktu przerwania w oknie stos wywołań  
 Można przerwać wykonywanie w instrukcji lub wierszu, do którego powraca funkcja wywołująca, ustawiając punkt przerwania w oknie **Stos wywołań.** Aby uzyskać więcej informacji na temat stosu wywołań, zobacz [Jak: Użyj okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md). Debuger musi przestać wykonywać.  
  
1. Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania zostanie zatrzymane (na przykład w punkcie przerwania). Otwórz okno **Stos wywołań** **(Debug / Windows / Call Stack**lub **CTRL + ALT + C**).  
  
2. Kliknij prawym przyciskiem myszy funkcję wywołującą, a następnie wybierz **pozycję Breakpoint / Insert Breakpoint**lub po prostu użyj klawisza skrótu **F9**.  
  
3. Symbol punktu przerwania pojawia się na lewym marginesie stosu wywołań, obok nazwy wywołania funkcji.  
  
   W oknie **Punkty przerwania** stosu wywołań jest wyświetlany jako adres z lokalizacją pamięci odpowiadającą następnej instrukcji wykonywalnej w funkcji. Debuger przerywa wykonywanie w instrukcji.  
  
   Aby wizualnie śledzić punkty przerwania podczas wykonywania kodu, zobacz [Mapowanie metod na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ustawianie punktu przerwania w oknie demontażu  
 Aby ustawić punkt przerwania w instrukcji zestawu, debuger musi być w trybie przerwania.  
  
1. Rozpocznij debugowanie aplikacji, a wykonanie oczekiwania zostanie zatrzymane (na przykład w punkcie przerwania). Otwórz okno **Demontaż** **(Debug / Windows / Demontaż**lub **Ctrl + Alt + D**).  
  
2. Kliknij lewy margines na instrukcję, którą chcesz złamać, lub ustaw kursor na instrukcji i naciśnij **klawisz F9**.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Ustawianie punktu przerwania danych (tylko natywny język C++)  
 Punkty przerwania danych przerwania wykonywania, gdy wartość, która jest przechowywana w określonym adresie pamięci zmienia. Jeśli wartość jest odczytywana, ale nie zmieniona, wykonanie nie zostanie przerwane. Aby ustawić punkty przerwania danych, debuger musi być w trybie przerwania.  
  
1. Rozpocznij debugowanie aplikacji i poczekaj, aż zostanie osiągnięty punkt przerwania. W menu **Debugowanie** wybierz polecenie **Nowy punkt przerwania / punkt przerwania danych** (lub otwórz okno Punkty **przerwania** i wybierz pozycję **Nowy / Punkt przerwania danych**.  
  
2. W polu **Adres** wpisz adres pamięci lub wyrażenie, które ocenia adres pamięci. Na przykład `&avar` wpisz, aby przerwać, `avar` gdy zawartość zmiennej zmienia.  
  
3. W menu rozwijanym **Liczba bajtów** wybierz liczbę bajtów, które mają być obserwowane przez debugera. Na przykład, jeśli wybierzesz **4**, debuger będzie `&avar` oglądać cztery bajty, począwszy od i przerwy, jeśli którykolwiek z tych bajtów zmienić wartość.  
  
   Należy pamiętać, że punkty przerwania danych zależą od możliwości zastosowania określonych adresów pamięci.  
  
- Adres zmiennej zmienia się z jednej sesji debugowania do następnej. Punkty przerwania danych są automatycznie wyłączane na końcu każdej sesji debugowania.  
  
- Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, punkt przerwania pozostaje włączony po zakończeniu funkcji, ale adres pamięci nie ma już zastosowania, a zachowanie punktu przerwania jest nieprzewidywalne. Jeśli ustawisz punkt przerwania danych na zmiennej lokalnej, należy usunąć lub wyłączyć punkt przerwania przed zakończeniem funkcji.  
  
  Punkty przerwania danych nie działają w następujących warunkach:  
  
- Proces, który nie jest debugowany zapisuje w lokalizacji pamięci  
  
- Lokalizacja pamięci jest współużytkowana przez dwa lub więcej procesów  
  
- Lokalizacja pamięci zostanie zaktualizowana w jądrze. Na przykład jeśli pamięć jest przekazywana do `ReadFile` 32-bitowej funkcji systemu Windows, pamięć zostanie zaktualizowana z trybu jądra, a debuger nie zostanie przerwany podczas zapisu pamięci.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Ustawianie punktu przerwania z adresem pamięci (tylko natywny język C++)  
 Można również użyć adresu obiektu, aby ustawić punkt przerwania dla metody wywoływanej w określonym wystąpieniu klasy.  Oto przykład:  
  
 Na przykład biorąc pod `my_class` uwagę obiekt typu z adresem, można ustawić `my_method` punkt przerwania funkcji dla metody o nazwie wywoływanej z tego wystąpienia.  
  
1. Ustaw punkt przerwania gdzieś po wystąpieniu wystąpienia tego wystąpienia wystąpienia tej klasy.  
  
2. Znajdź adres instancji (powiemy, że jest). `0xcccccccc`  
  
3. Kliknij **przycisk Debug / Nowy punkt przerwania / Punkt przerwania funkcji** (lub ALT + **F9, B**).  
  
4. Dodaj następujący tekst do pola **Nazwa funkcji:**  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Zarządzanie punktami przerwania  
 Można użyć okna **Punkty przerwania** **(Debug / Windows / Breakpoints**lub **CTRL + ALT + B**), aby wyświetlić wszystkie punkty przerwania ustawione w rozwiązaniu:  
  
 ![Okno punktów przerwania](../debugger/media/breakpointswindow.png "Punkty przerwaniaWindow")  
  
 **Okno Punkty przerwania** zapewnia centralne miejsce do zarządzania wszystkimi punktami przerwania, co może być szczególnie przydatne w dużym rozwiązaniu lub złożonym scenariuszu debugowania, w którym punkty przerwania są krytyczne. Jeśli chcesz zapisać lub udostępnić stan i lokalizację zestawu punktów przerwania, można eksportować i importować punkty przerwania tylko z okna **Punkty przerwania.**  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Zaawansowane punkty przerwania  
  
## <a name="breakpoint-conditions"></a>Warunki punktu przerwania  
 Można kontrolować, kiedy i gdzie punkt przerwania jest wykonywany przez ustawienie warunków.  
  
1. Kliknij prawym przyciskiem myszy punkt przerwania lub umieść wskaźnik myszy na punkcie przerwania i wybierz ikonę ustawień.  
  
2. W menu kontekstowym wybierz pozycję **Warunki**. Spowoduje to otwarcie okna **Ustawienia punktu przerwania:**  
  
   ![Ustawienia punktu przerwania](../debugger/media/breakpointsettings.png "Rozłamywanie")  
  
   Po zaznaczeniu **pola Warunki** okno rozwija się, aby wyświetlić różne rodzaje warunków.  
  
   **Wyrażenie warunkowe:** Po wybraniu wyrażenia warunkowego można wybrać dwa warunki: **Jest true** i **Po zmianie**. Wybierz **opcję Jest prawdziwa,** jeśli chcesz przerwać, gdy wyrażenie jest spełnione, lub wybierz **po zmianie,** jeśli chcesz przerwać, gdy wartość wyrażenia została zmieniona.  
  
   W poniższym przykładzie ustawiamy punkt przerwania, `testInt` aby trafić tylko wtedy, gdy wartość wynosi **4:**  
  
   ![Warunek punktu przerwania jest spełniony](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   W poniższym przykładzie ustawiamy punkt przerwania, `testInt` aby trafić tylko wtedy, gdy wartość zmian:  
  
   ![Punkt przerwania po zmianie](../debugger/media/breakpointwhenchanged.png "Punkt przerwaniaWhenZanged")  
  
   Zachowanie pola When changed różni się w przypadku różnych języków programowania. Jeśli wybierzesz **Po zmianie** dla kodu macierzystego, debuger nie bierze pod uwagę pierwszej oceny warunku jako zmiany, więc punkt przerwania nie zostanie trafiony w pierwszej oceny. Jeśli wybierzesz **Po zmianie** dla kodu zarządzanego, on punkt przerwania zostanie trafiony w pierwszej ocenie po **wybraniu po zmianie.**  
  
   Jeśli ustawisz warunek punktu przerwania z nieprawidłową składnią, pojawi się komunikat ostrzegawczy. Jeśli określisz warunek punktu przerwania z prawidłową składnią, ale nieprawidłową semantyką, komunikat ostrzegawczy pojawi się przy pierwszym trafieniu punktu przerwania. W obu przypadkach debuger przerywa wykonanie po trafieniu nieprawidłowego punktu przerwania. Punkt przerwania jest pomijany tylko wtedy, gdy `false`warunek jest prawidłowy i ocenia .  
  
   Warunkiem może być dowolne prawidłowe wyrażenie rozpoznawane przez debuger. Aby uzyskać więcej informacji na temat prawidłowych wyrażeń, zobacz [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Używanie identyfikatorów obiektów w warunkach punktu przerwania (C# i F#)  
 Istnieją chwile, kiedy chcesz obserwować zachowanie określonego obiektu; na przykład można dowiedzieć się, dlaczego obiekt został wstawiony więcej niż jeden raz do kolekcji. W językach C# i F#można utworzyć identyfikatory obiektów dla określonych wystąpień [typów odwołań](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) i używać ich w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania wspólnego środowiska wykonawczego języka (CLR) i skojarzony z obiektem.  Aby utworzyć identyfikator obiektu, wykonaj następujące czynności:  
  
1. Ustaw punkt przerwania w kodzie jakiś czas po utworzeniu obiektu.  
  
2. Rozpocznij debugowanie, a gdy wykonanie zatrzyma się w punkcie przerwania, znajdź punkt przerwania w oknie **Zmiennych,** kliknij go prawym przyciskiem myszy i wybierz polecenie **Make Object ID**.  
  
    W oknie **$** **Locals** powinien zostać wyświetlony numer plus. Jest to identyfikator obiektu.  
  
3. Dodaj nowy warunkowy punkt przerwania w punkcie, który chcesz zbadać, na przykład, gdy obiekt ma zostać dodany do kolekcji.  
  
4. Użyj identyfikatora obiektu w polu Wyrażenie warunkowe. Na przykład, jeśli istnieje `item` zmienna odnosząca się do obiektu, który ma zostać dodany do kolekcji, należy umieścić **element == $n**, gdzie **n** jest numerem identyfikatora obiektu.  
  
    Wykonanie zostanie przerwane w momencie, gdy ten obiekt ma zostać dodany do kolekcji.  
  
   Jeśli później chcesz usunąć identyfikator obiektu, możesz kliknąć zmienną prawym przyciskiem myszy w oknie **Zmienne lokalne** i wybrać polecenie **Usuń identyfikator obiektu**.  
  
   Należy zauważyć, że identyfikatory obiektów utworzyć słabe odwołania i nie uniemożliwiają obiektu są zbierane śmieci. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
## <a name="hit-count"></a>Liczba trafień  
 Jeśli podejrzewasz, że pętla w kodzie zaczyna się niewłaściwie po określonej liczby iteracji, można ustawić punkt przerwania, aby zatrzymać wykonanie po określonej liczbie trafień do skojarzonego wiersza kodu, a nie jest zmuszony do wielokrotnego naciskania **klawisza F5,** aby osiągnąć poziom iteracji.  
  
 W oknie **Ustawienia punktu przerwania** ustaw warunek na **Liczba trafień**. Następnie można określić liczbę iteracji. W poniższym przykładzie ustawimy punkt przerwania, aby trafić na każdej innej iteracji:  
  
 ![Liczba trafień punktu przerwania](../debugger/media/breakpointhitcount.png "Policz y breakpointhitcount")  
  
## <a name="filter"></a>Filtr  
 Punkt przerwania można ograniczyć do uruchamiania tylko na określonych urządzeniach lub w określonych procesach i wątkach.  
  
 W oknie **Ustawienia punktu przerwania**ustaw warunek na **Filtr .** Wprowadź jedno lub więcej z następujących wyrażeń.  
  
- Nazwa maszyny = "nazwa"  
  
- ProcessId = wartość  
  
- Nazwa procesu = "nazwa"  
  
- Identyfikator wątku = wartość  
  
- Nazwa wątku = "nazwa"  
  
  Wartości ciągów należy ująć w cudzysłowy. Można łączyć klauzule przy użyciu `&` (AND), `||` (OR), `!` (NIE) i nawiasach.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Akcje punktu przerwania i punkty śledzenia  
 Punkt śledzenia jest punktem przerwania, który drukuje komunikat do okna Dane wyjściowe. Punkt śledzenia może działać jak tymczasowa instrukcja śledzenia w języku programowania.  
  
 W oknie **Ustawienia punktu przerwania** zaznacz pole wyboru **Akcje.** Wybierz pozycję **Zaloguj wiadomość do okna Dane wyjściowe** w grupie **Akcja.** Można wydrukować ciąg ogólny, na przykład **jest to test**. Aby uwzględnić wartość zmiennej lub wyrażenia, ująć ją w nawiasy klamrowe.  
  
 Aby przerwać wykonywanie po trafieniu punktu śledzenia, wyczyść pole wyboru **Kontynuuj wykonywanie.** Po **zaznaczeniu kontynuuj wykonywanie** wykonywanie, wykonanie nie jest zatrzymywał. W obu przypadkach wiadomość jest drukowana.  
  
 W **wiadomości**można użyć następujących specjalnych słów kluczowych.  
  
|||  
|-|-|  
|**$ADDRESS**|Aktualna instrukcja|  
|**$CALLER**|Nazwa funkcji wywołującej|  
|**$CALLSTACK**|Stos wywołań|  
|**$FUNCTION**|Bieżąca nazwa funkcji|  
|**$PID**|Identyfikator procesu|  
|**$PNAME**|Nazwa procesu|  
|**$TID**|Identyfikator wątku|  
|**$TNAME**|Nazwa wątku|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Etykiety punktów przerwania  
 Etykiety punktów przerwania są używane tylko w oknie **Punkty przerwania** do sortowania i filtrowania listy punktów przerwania. Aby dodać etykietę do punktu przerwania, wybierz wiersz punktu przerwania, a następnie w menu kontekstowym wybierz polecenie **Etykieta.**  
  
## <a name="export-and-import-breakpoints"></a>Eksportowanie i importowanie punktów przerwania  
 Punkt przerwania można wyeksportować do pliku XML, klikając prawym przyciskiem myszy punkt przerwania i wybierając pozycję **Eksportuj**. Plik jest domyślnie zapisywany w katalogu rozwiązania. Aby zaimportować punkty przerwania, otwórz okno **Punkty przerwania** **(CTRL + ALT + B**) i na pasku narzędzi kliknij strzałkę wskazującą prawym przyciskiem myszy (etykietka narzędzia to **Importuj punkty przerwania z pliku**).  
  
## <a name="troubleshoot-breakpoints"></a>Rozwiązywanie problemów z punktami przerwania  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Usunąłem punkt przerwania, ale nadal go uderzam, gdy ponownie zacznę debugować  
 Jeśli usunięto punkt przerwania podczas debugowania, w niektórych przypadkach można ponownie trafić punkt przerwania przy następnym uruchomieniu debugowania. Aby zatrzymać trafienie tego punktu przerwania, upewnij się, że wszystkie wystąpienia punktu przerwania są usuwane z okna **Punkty przerwania.**  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Debuger nie może zlokalizować poprawnej wersji pliku źródłowego dla punktu przerwania  
 Jeśli plik źródłowy został zmieniony, a źródło nie pasuje już do kodu, który debugujesz, debuger może zlokalizować plik źródłowy odpowiadający punktowi przerwania, nawet jeśli istnieje plik źródłowy.  
  
1. Jeśli chcesz, aby program Visual Studio wyświetlał kod źródłowy niezgodny z wersją debugowania, wybierz opcję **Debugowanie / Opcje i ustawienia**. Na **debugowanie/ogólne** strony, wyczyść **Wymagaj plików źródłowych, które dokładnie pasują do oryginalnej wersji** opcji.  
  
2. Punkt przerwania można również powiązać z plikiem źródłowym. Wybierz punkt przerwania i wybierz pozycję **Warunki** w menu kontekstowym. Zaznacz **pole wyboru Zezwalaj, aby kod źródłowy różnił się od oryginału** w oknie **Ustawienia punktu przerwania.**  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Punkty przerwania nie działają w biblioteki DLL  
 Nie można ustawić punktu przerwania w pliku źródłowym, gdy debuger nie załadował informacji debugowania dla modułu, w którym znajduje się kod. Objawy mogą obejmować **komunikaty,** takie jak punkt przerwania nie zostanie ustawiony . Glif punktu przerwania ostrzeżenia pojawia się w miejscu punktu przerwania. Jednak te punkty przerwania ostrzeżenie stają się rzeczywiste punkty przerwania po załadowaniu kodu. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określanie symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
