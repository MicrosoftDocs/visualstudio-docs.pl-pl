---
title: Debugowanie wielu procesów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d0986e1780cb9fea061132b5985972cf9635c8b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752692"
---
# <a name="debug-multiple-processes"></a>Debugowanie wielu procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oto jak rozpocząć debugowanie procesów, przełączać się między procesami, podzielić i kontynuować wykonywanie, kroku w źródle, zatrzymać debugowanie i kończenie lub odłączanie od procesów.  
  
##  <a name="BKMK_Contents"></a> Zawartość  
 [Skonfiguruj zachowanie wykonania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Znajdowanie symboli i źródłowych plików (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie uruchamia proces w debugerze](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Przełączanie procesów, przerywanie i kontynuowanie wykonywania, krokowe źródła](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zatrzymywanie debugowania, kończenie lub odłączanie od procesów](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Skonfiguruj zachowanie wykonania wielu procesów  
 Domyślnie gdy działa wiele procesów w debugerze, istotne, przechodzenia i zatrzymywania poleceń debugera zazwyczaj dotyczą wszystkich procesów. Na przykład gdy jeden proces jest zawieszony w punkcie przerwania, wykonanie wszystkich innych procesów jest również zawieszone. Można zmienić to zachowanie domyślne, aby uzyskać większą kontrolę nad obiektami docelowymi poleceń wykonywania.  
  
1. Na **debugowania** menu, wybierz **opcje i ustawienia**.  
  
2. Na **debugowanie**, **ogólne** strony, wyczyść **Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** pole wyboru.  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Znajdowanie symboli i źródłowych plików (.pdb)  
 Aby nawigować po kodzie źródłowym procesu, debuger musi mieć dostęp do plików źródłowych i plików symboli procesu. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Jeśli nie masz dostępu plików dla procesu, można nawigować przy użyciu okna dezasemblacja. Zobacz [jak: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie uruchamia proces w debugerze  
  
-   [Uruchamianie debugowania wielu procesów w rozwiązaniu Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Zmień projekt startup](#BKMK_Change_the_startup_project) • [uruchamianie określonego projektu w rozwiązaniu](#BKMK_Start_a_specific_project_in_a_solution) • [uruchamianie wiele projektów w rozwiązanie](#BKMK_Start_multiple_projects_in_a_solution) • [Dołącz do procesu](#BKMK_Attach_to_a_process) • [automatycznie uruchamia proces w debugerze](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Debuger nie dołącza automatycznie do procesu podrzędnego uruchomionego przez proces debugowania, nawet jeśli projekt podrzędny znajduje się w tym samym rozwiązaniu. Aby debugować proces podrzędny:  
> 
> - Dołącz do procesu podrzędnego, po jego uruchomieniu.  
> 
>   —lub—  
>   -   Skonfiguruj Windows, aby automatycznie rozpocząć proces podrzędny w nowym wystąpieniu debugera.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Uruchamianie debugowania wielu procesów w rozwiązaniu Visual Studio  
 Jeśli masz więcej niż jednego projektu w rozwiązaniu Visual Studio, która może działać niezależnie (projekty uruchamiane w osobnych procesach), można wybrać, które projekty uruchamia debuger.  
  
 ![Zmiana typu uruchamiania dla projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Zmień projekt startowy  
 Aby zmienić projekt startowy dla rozwiązania, zaznacz projekt w Eksploratorze rozwiązań, a następnie wybierz **Ustaw jako projekt startowy** z menu kontekstowego.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Uruchamianie określonego projektu w rozwiązaniu  
 Aby uruchomić projekt rozwiązania bez zmieniania domyślnego projektu startowego, zaznacz projekt w Eksploratorze rozwiązań, a następnie wybierz **debugowania** z menu kontekstowego. Możesz wybrać **Uruchom nowe wystąpienie** lub **Wkrocz do nowego wystąpienia**.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie uruchamia proces w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Uruchamianie wiele projektów w rozwiązaniu  
  
1. Wybierz rozwiązanie w Eksploratorze rozwiązań, a następnie wybierz **właściwości** w menu kontekstowym.  
  
2. Wybierz **wspólne właściwości**, **projekt startowy** na **właściwości** okno dialogowe.  
  
3. Dla każdego projektu, który chcesz zmienić, wybierz **Start**, **Uruchom bez debugowania**, lub **Brak**.  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie uruchamia proces w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Dołącz do procesu  
 Debuger może również *dołączyć* do programów uruchomionych w procesach poza programem Visual Studio, w tym programy, które są uruchomione na urządzeniu zdalnym. Po dołączeniu do programu, można użyć poleceń debugera, sprawdzić stan programu i tak dalej. Możliwość kontroli programu może być ograniczona w zależności od tego, czy program został skompilowany według informacji o debugowaniu i czy masz dostęp do kodu źródłowego programu, oraz czy kompilator JIT środowiska uruchomieniowego języka wspólnego śledzi informacje debugowania.  
  
 Zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) Aby uzyskać więcej informacji.  
  
 **Dołącz do procesu, który jest uruchomiony na komputerze lokalnym**  
  
 Wybierz **debugowania**, **dołączyć do procesu**. Na **dołączyć do procesu** okna dialogowego Wybierz proces na **dostępne procesy** , a następnie wybierz **Dołącz**.  
  
 ![Dołącz do procesu, okno dialogowe](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatycznie uruchom proces w debugerze  
 Czasami może być konieczne zdebugowanie kodu startowego dla programu, który jest uruchamiany przez inny proces. Przykładami są usługi i akcje instalacji niestandardowej. W tych scenariuszach można mieć uruchomionego debugera i automatycznie dołączyć podczas uruchamiania aplikacji.  
  
1. Uruchom Edytor rejestru (**regedit.exe**).  
  
2. Przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** folderu.  
  
3. Wybierz folder aplikacji, które mają być uruchamiane w debugerze.  
  
    Jeśli nazwa aplikacji nie jest wymieniony jako folder podrzędny, wybierz opcję **Image File Execution Options** , a następnie wybierz **New**, **klucza** w menu kontekstowym. Wybierz nowy klucz, wybierz pozycję **Zmień nazwę** menu skrótów, a następnie wprowadź nazwę aplikacji.  
  
4. W menu kontekstowym folderu aplikacji, wybierz **New**, **wartość ciągu**.  
  
5. Zmień nazwę nowej wartości z **nową wartość** do `debugger`.  
  
6. W menu kontekstowym wejścia debugera wybierz **Modyfikuj**.  
  
7. W oknie dialogowym Edytowanie ciągu, wpisz `vsjitdebugger.exe` w **dane wartości** pole.  
  
    ![Ciąg, okno dialogowe Edytowanie](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Debuger automatycznego uruchamiania wpis w regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Przełączanie procesów, przerywanie i kontynuowanie wykonywania, krokowe źródła  
  
-   [Przełączanie się między procesami](#BKMK_Switch_between_processes) • [przerwania i kroku i Kontynuuj](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Przełączać się między procesami  
 Podczas debugowania, ale tylko jeden proces jest aktywny w debugerze w danym momencie, można dołączyć wiele procesów. Można ustawić aktywny lub *bieżącego* proces w pasku narzędzi debugowania lokalizacji lub **procesy** okna. Aby przełączyć się między procesami, oba procesy muszą być w trybie przerwania.  
  
 **Aby ustawić bieżący proces**  
  
- Na pasku narzędzi debugowania lokalizacji, wybierz **procesu** do wyświetlania **procesu** pola listy. Wybierz proces, który chcesz wyznaczyć jako proces bieżący.  
  
   ![Przełączanie się między procesami](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Jeśli **Lokalizacja debugowania** narzędzi nie jest widoczny, wybierz polecenie **narzędzia**, **Dostosuj**. Na **pasków narzędzi** kartę, wybrać **Lokalizacja debugowania**.  
  
- Otwórz **procesy** okna (skrót **Ctrl + Alt + Z**), Znajdź proces, który chcesz ustawić jako bieżący proces i kliknij ją dwukrotnie.  
  
   ![Okno procesów](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Bieżący proces jest oznaczony żółtą strzałką.  
  
  Przełączenie do projektu konfiguruje ją bieżącego procesu do celów debugowania. Każde okna debugera, które można wyświetlić wyświetli stan dla bieżącego procesu, a wszystkie polecenia dotyczą tylko bieżącego procesu.  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [przełączanie procesów, przerywanie i kontynuowanie wykonywania, krokowe źródła](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> BREAK, step and Kontynuuj  
  
> [!NOTE]
>  Domyślnie przerwa, kontynuować i poleceń debugera krok wpływają na wszystkie procesy, które są debugowane. Aby zmienić to zachowanie, zobacz [skonfiguruj zachowanie wykonania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Polecenie**|**Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu**<br /><br /> Zaznaczone (domyślne)|**Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu**<br /><br /> Wyczyszczone|  
|**Debugowanie** menu:<br /><br /> -   **Przerwij wszystko**|Wszystkie procesy zostaną przerwane.|Wszystkie procesy zostaną przerwane.|  
|**Debugowanie** menu:<br /><br /> -   **Kontynuuj**|Wszystkie procesy są wznawiane.|Wszystkie wstrzymane procesy wznawiają działanie.|  
|**Debugowanie** menu:<br /><br /> -   **Wkrocz**<br />-   **Przekrocz nad**<br />-   **Wyjdź**|Wszystkie procesy trwają postępem aktualnego procesu.<br /><br /> Następnie wszystkie procesy zostaną przerwane.|Kroki bieżącego procesu.<br /><br /> Wstrzymane procesy wznawiają działanie.<br /><br /> Działające procesy kontynuują działanie.|  
|**Debugowanie** menu:<br /><br /> -   **Wkrocz do bieżącego procesu**<br />-   **Przekrocz bieżący proces**<br />-   **Wyjdź z bieżącego procesu**|Brak|Kroki bieżącego procesu.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
|Okno źródłowe<br /><br /> -   **Punkt przerwania**|Wszystkie procesy zostaną przerwane.|Tylko proces okna źródła przerywa.|  
|Menu kontekstowe okna źródłowego:<br /><br /> -   **Uruchom do kursora**<br /><br /> Okno źródłowe musi znajdować się w bieżącym procesie.|Wszystkie procesy działają, podczas gdy procesu okna źródła działa do kursora, a następnie przerywa.<br /><br /> Następnie inne procesy zostaną przerwane.|Proces okna źródłowego działa do kursora.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Przerwij proces**|Brak|Wybrany proces przerywa działanie.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Kontynuuj proces**|Brak|Wybrany proces wznawia działanie.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [przełączanie procesów, przerywanie i kontynuowanie wykonywania, krokowe źródła](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Zatrzymywanie debugowania, kończenie lub odłączanie od procesów  
  
- [Zatrzymaj, kończenia i odłączania poleceń](#BKMK_Stop__terminate__and_detach_commands)  
  
  Domyślnie po wybraniu **debugowania**, **Zatrzymaj debugowanie** gdy wiele procesów jest otwartych w debugerze, debuger kończy pracę lub odłącza się od wszystkich procesów, w zależności od tego, jak proces został otwarty w Debuger:  
  
- Jeśli bieżący proces został uruchomiony w debugerze, ten proces zostanie zakończony.  
  
- Jeśli Debuger jest dołączony do bieżącego procesu, debuger odłączy się od procesu i pozostawia proces uruchomiony.  
  
  Na przykład jeśli uruchomisz debugowanie procesu z rozwiązania programu Visual Studio, dołączysz do innego procesu, który jest już uruchomiony, a następnie wybierz **Zatrzymaj debugowanie**, sesja debugowania kończy proces, który został uruchomiony w programie Visual Studio znaków jest zakończony, gdy proces, który zostanie dołączony zostanie pozostawiony jako uruchomiony. Można użyć poniższych procedur, aby kontrolować sposób zatrzymywania debugowania.  
  
> [!NOTE]
>  **Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** opcja wpływa na zatrzymywanie debugowania ani Kończenie i odłączanie od procesów.  
  
 **Aby zmienić oddziaływanie zatrzymania debugowania poszczególnych procesów**  
  
-   Otwórz **procesy** okna (skrót **Ctrl + Alt + Z**). Wybierz proces, a następnie zaznacz lub wyczyść **Odłącz po zatrzymaniu debugowania** pole wyboru.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Zatrzymaj, kończenia i odłączania poleceń  
  
|||  
|-|-|  
|**Polecenie**|**Opis**|  
|**Debugowanie** menu:<br /><br /> -   **Zatrzymaj debugowanie**|Jeśli zachowanie nie zostało zmienione przez **procesy** okna **Odłącz po zatrzymaniu debugowania** opcji:<br /><br /> 1.  Procesy uruchomione przez debugera zostają zakończone.<br />2.  Dołączone procesy są odłączone od debugera.|  
|**Debugowanie** menu:<br /><br /> -   **Zakończ wszystkie**|Wszystkie procesy są kończone.|  
|**Debugowanie** menu:<br /><br /> -   **Odłącz wszystko**|Debuger odłączy się od wszystkich procesów.|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Odłącz proces**|Debuger odłączy się od wybranych procesów.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Zakończenie procesu**|Wybrany proces zostanie zakończony.<br /><br /> Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|  
|**Procesy** menu kontekstowe okna:<br /><br /> -   **Odłącz po zatrzymaniu debugowania**|Przełącza **debugowania**, **Zatrzymaj debugowanie** dla wybranego procesu:<br /><br /> -Sprawdzono: Debuger odłączy się od procesu.<br />-Wyczyszczone: Ten proces zostanie zakończony.|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zatrzymywanie debugowania, kończenie lub odłączanie od procesów](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Nawigowanie po kodzie za pomocą debugera za](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
