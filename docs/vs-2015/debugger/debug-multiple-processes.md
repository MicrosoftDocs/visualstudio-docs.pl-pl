---
title: Debugowanie wielu procesów | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302554"
---
# <a name="debug-multiple-processes"></a>Debugowanie wielu procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oto jak rozpocząć procesy debugowania, przełączać się między procesami, przerywać i kontynuować wykonywanie, krok po źródle, zatrzymać debugowanie i zakończyć lub odłączyć od procesów.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Zawartość  
 [Konfigurowanie zachowania wykonywania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Znajdowanie plików źródłowych i symboli (pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Uruchamianie wielu procesów w rozwiązaniu VS, dołączanie do procesu, automatyczne uruchamianie procesu w debugerze](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Przełączanie procesów, przerywanie i kontynuowanie wykonywania, przechodzenie przez źródło](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zatrzymywać debugowanie, kończyć lub odłączać się od procesów](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Konfigurowanie zachowania wykonywania wielu procesów  
 Domyślnie, gdy wiele procesów są uruchomione w debugerze, podział, stepping i zatrzymanie debugera polecenia zwykle wpływają na wszystkie procesy. Na przykład, gdy jeden proces jest zawieszony w punkcie przerwania, wykonywanie wszystkich innych procesów jest również zawieszone. Można zmienić to domyślne zachowanie, aby uzyskać większą kontrolę nad celami poleceń wykonywania.  
  
1. W menu **Debugowanie** wybierz polecenie **Opcje i ustawienia**.  
  
2. Na **debugowaniu**, **Ogólne** strony, wyczyść **pole wyboru Przerwij wszystkie procesy, gdy jeden proces dzieli.**  
  
   ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Znajdowanie plików źródłowych i symboli (pdb)  
 Aby poruszać się po kodzie źródłowym procesu, debuger potrzebuje dostępu do plików źródłowych i plików symboli procesu. Zobacz [Określanie symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Jeśli nie możesz uzyskać dostępu do plików dla procesu, możesz nawigować za pomocą okna Disassemby. Zobacz [jak: Użyj okna demontażu](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Uruchamianie wielu procesów w rozwiązaniu VS, dołączanie do procesu, automatyczne uruchamianie procesu w debugerze  
  
- [Rozpocznij debugowanie wielu procesów w rozwiązaniu programu Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Zmień projekt startowy](#BKMK_Change_the_startup_project) • [Rozpocznij określony projekt w rozwiązaniu](#BKMK_Start_a_specific_project_in_a_solution) • [Rozpocznij wiele projektów w rozwiązaniu](#BKMK_Start_multiple_projects_in_a_solution) • [Dołącz do procesu](#BKMK_Attach_to_a_process) • Automatycznie [rozpocznij proces w debugerze](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Debuger nie automatycznie dołączyć do procesu podrzędnego, który jest uruchamiany przez debugowany proces, nawet jeśli projekt podrzędny jest w tym samym rozwiązaniu. Aby debugować proces podrzędny:  
> 
> - Dołącz do procesu podrzędnego po jego uruchomieniu.  
> 
>   — lub —  
>   - Skonfiguruj system Windows, aby automatycznie uruchamiał proces podrzędny w nowym wystąpieniu debugera.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Uruchamianie debugowania wielu procesów w rozwiązaniu programu Visual Studio  
 Jeśli masz więcej niż jeden projekt w rozwiązaniu programu Visual Studio, który można uruchomić niezależnie (projekty, które są uruchamiane w oddzielnych procesach), można wybrać projekty uruchamia debuger.  
  
 ![Zmienianie typu uruchamiania projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Zmienianie projektu startowego  
 Aby zmienić projekt uruchamiania rozwiązania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu kontekstowego.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Rozpoczynanie określonego projektu w rozwiązaniu  
 Aby uruchomić projekt dla rozwiązania bez zmiany domyślnego projektu uruchamiania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz **debugowanie** z menu kontekstowego. Następnie można wybrać **pozycję Rozpocznij nowe wystąpienie** lub **Krok do nowego wystąpienia**.  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Uruchamianie wielu procesów w programie VS, dołączanie do procesu, automatyczne uruchamianie procesu w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Uruchamianie wielu projektów w rozwiązaniu  
  
1. Wybierz rozwiązanie w Eksploratorze rozwiązań, a następnie wybierz polecenie **Właściwości** w menu kontekstowym.  
  
2. Wybierz **pozycję Wspólne właściwości**, Projekt **uruchamiania** w oknie dialogowym **Właściwości.**  
  
3. Dla każdego projektu, który chcesz zmienić, wybierz opcję **Start**, **Start bez debugowania**lub **Brak**.  
  
   ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Uruchamianie wielu procesów w programie VS, dołączanie do procesu, automatyczne uruchamianie procesu w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Dołączanie do procesu  
 Debuger można również *dołączyć* do programów, które są uruchomione w procesach poza programem Visual Studio, w tym programów, które są uruchomione na urządzeniu zdalnym. Po dołączeniu do programu można użyć poleceń wykonywania debugera, sprawdzić stan programu i tak dalej. Możliwość sprawdzenia programu może być ograniczona, w zależności od tego, czy program został zbudowany z informacji debugowania i czy masz dostęp do kodu źródłowego programu i czy wspólny język runtime kompilator JIT jest śledzenie informacji debugowania.  
  
 Aby uzyskać więcej informacji, zobacz [Dołączanie do uruchomionych procesów.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 **Dołączanie do procesu uruchomionego na komputerze lokalnym**  
  
 Wybierz **debugowanie**, **Dołącz do procesu**. W oknie dialogowym **Dołączanie do procesu** wybierz proces z listy **Dostępne procesy,** a następnie wybierz pozycję **Dołącz**.  
  
 ![Okno dialogowe Dołączanie do procesu](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automatyczne uruchamianie procesu w debugerze  
 Czasami może być konieczne debugowanie kodu startowego dla programu, który jest uruchamiany przez inny proces. Przykłady obejmują usługi i akcje konfiguracji niestandardowej. W tych scenariuszach można uruchomić debuger i automatycznie dołączyć po uruchomieniu aplikacji.  
  
1. Uruchom Edytor rejestru (**regedit.exe**).  
  
2. Przejdź do folderu **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** folder.  
  
3. Wybierz folder aplikacji, który chcesz uruchomić w debugerze.  
  
    Jeśli nazwa aplikacji nie jest wymieniona jako folder podrzędny, wybierz pozycję **Opcje wykonywania plików obrazu,** a następnie w menu kontekstowym wybierz pozycję **Nowy** **klawisz** . Wybierz nowy klawisz, wybierz polecenie **Zmień nazwę** w menu skrótów, a następnie wprowadź nazwę aplikacji.  
  
4. W menu kontekstowym folderu aplikacji wybierz polecenie **Nowa**, **Wartość ciągu**.  
  
5. Zmień nazwę nowej wartości z Nowa `debugger` **wartość** na .  
  
6. W menu kontekstowym wpisu debugera wybierz polecenie **Modyfikuj**.  
  
7. W oknie dialogowym Edytowanie ciągu wpisz `vsjitdebugger.exe` pole Dane **wartości.**  
  
    ![Okno dialogowe Edytowanie ciągu](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Automatyczny wpis startowy debugera w pliku regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Przełączanie procesów, przerywanie i kontynuowanie wykonywania, przechodzenie przez źródło  
  
- [Przełączanie między procesami](#BKMK_Switch_between_processes) • [Przerywanie, krok i kontynuowanie poleceń](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>Przełączanie między procesami  
 Można dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w debugerze w danym momencie. Aktywny lub *bieżący* proces można ustawić na pasku narzędzi Lokalizacja debugowania lub w oknie **Procesy.** Aby przełączać się między procesami, oba procesy muszą być w trybie przerwania.  
  
 **Aby ustawić bieżący proces**  
  
- Na pasku narzędzi Lokalizacja debugowania wybierz pozycję **Proces,** aby wyświetlić pole listy **Proces.** Wybierz proces, który chcesz wyznaczyć jako bieżący proces.  
  
   ![Przełączanie między procesami](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Jeśli pasek narzędzi **Lokalizacja debugowania** nie jest widoczny, wybierz polecenie **Narzędzia**, **Dostosuj**. Na karcie **Paski narzędzi** wybierz pozycję **Lokalizacja debugowania**.  
  
- Otwórz okno **Procesy** (skrót **Ctrl+Alt+Z**), znajdź proces, który chcesz ustawić jako bieżący proces, i kliknij go dwukrotnie.  
  
   ![Okno Procesy](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Bieżący proces jest oznaczony żółtą strzałką.  
  
  Przełączanie do projektu ustawia go bieżący proces do celów debugowania. Każde okno debugera, które można wyświetlić pokaże stan dla bieżącego procesu, a wszystkie polecenia krokowe mają wpływ tylko na bieżący proces.  
  
  ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Przełączanie procesów, przerwy i kontynuować wykonywanie, krok przez źródło](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Przerywanie, krok i kontynuowanie poleceń  
  
> [!NOTE]
> Domyślnie polecenia podziału, kontynuuj i debugera kroku wpływają na wszystkie procesy, które są debugowane. Aby zmienić to zachowanie, zobacz [Konfigurowanie zachowania wykonywania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Polecenie**|**Przerywanie wszystkich procesów, gdy jeden proces się zepsuje**<br /><br /> Więdna (domyślnie)|**Przerywanie wszystkich procesów, gdy jeden proces się zepsuje**<br /><br /> Wyczyszczone|  
|Menu **debugowania:**<br /><br /> -   **Przerwij wszystko**|Wszystkie procesy pękają.|Wszystkie procesy pękają.|  
|Menu **debugowania:**<br /><br /> -   **Kontynuować**|Wszystkie procesy wznawiają się.|Wszystkie zawieszone procesy zostaną wznowione.|  
|Menu **debugowania:**<br /><br /> -   **Wejdź do**<br />-   **Krok nad**<br />-   **Wyjdź**|Wszystkie procesy są uruchamiane podczas bieżących kroków procesu.<br /><br /> Następnie wszystkie procesy pękają.|Bieżące etapy procesu.<br /><br /> Zawieszone procesy wznowić.<br /><br /> Procesy uruchomione są kontynuowane.|  
|Menu **debugowania:**<br /><br /> -   **Krok do bieżącego procesu**<br />-   **Krok nad bieżącym procesem**<br />-   **Wyjdź z bieżącego procesu**|Nie dotyczy|Bieżące etapy procesu.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
|Okno źródło<br /><br /> -   **Punkt przerwania**|Wszystkie procesy pękają.|Tylko podziały procesu okna źródła.|  
|Menu kontekstowe okna źródła:<br /><br /> -   **Uruchamianie do kursora**<br /><br /> Okno źródłowe musi być w bieżącym procesie.|Wszystkie procesy są uruchamiane, gdy proces okna źródłowego jest uruchamiany do kursora, a następnie przerywa.<br /><br /> Następnie wszystkie inne procesy pękają.|Proces okna źródłowego jest uruchamiany do kursora.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
|Menu kontekstowe okna **procesów:**<br /><br /> -   **Proces przerwania**|Nie dotyczy|Wybrane przerwy procesu.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
|Menu kontekstowe okna **procesów:**<br /><br /> -   **Kontynuuj proces**|Nie dotyczy|Wznawia się wybrany proces.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Przełączanie procesów, przerwy i kontynuować wykonywanie, krok przez źródło](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Zatrzymywać debugowanie, kończyć lub odłączać się od procesów  
  
- [Polecenia zatrzymania, zakończenia i odłączyć](#BKMK_Stop__terminate__and_detach_commands)  
  
  Domyślnie po wybraniu **opcji Debugowanie**, **Zatrzymaj debugowanie,** gdy w debugerze otwartych jest wiele procesów, debuger kończy lub odłącza się od wszystkich procesów w zależności od sposobu otwarcia procesu w debugerze:  
  
- Jeśli bieżący proces został uruchomiony w debugerze, ten proces zostanie zakończony.  
  
- Jeśli debuger został dołączony do bieżącego procesu, debuger odłącza się od procesu i pozostawia proces uruchomiony.  
  
  Na przykład po rozpoczęciu debugowania procesu z rozwiązania programu Visual Studio, dołącz do innego procesu, który jest już uruchomiony, a następnie wybierz pozycję **Zatrzymaj debugowanie**, sesja debugowania kończy się, proces, który został uruchomiony w programie Visual Studio zostanie zakończony, podczas gdy dołączony proces pozostaje uruchomiony. Poniższe procedury umożliwiają kontrolowanie sposobu, w jaki można zatrzymać debugowanie.  
  
> [!NOTE]
> **Przerwać wszystkie procesy, gdy jeden proces przerwy** opcja nie wpływa na zatrzymanie debugowania lub zakończenia i odłączania od procesów.  
  
 **Aby zmienić wpływ debugowania stop na pojedynczy proces**  
  
- Otwórz okno **Procesy** (skrót **Ctrl+Alt+Z**). Zaznacz proces, a następnie zaznacz lub wyczyść pole wyboru **Odłącz po zatrzymaniu debugowania.**  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Polecenia zatrzymania, zakończenia i odłączyć  
  
|||  
|-|-|  
|**Polecenie**|**Opis**|  
|Menu **debugowania:**<br /><br /> -   **Zatrzymaj debugowanie**|Chyba że zachowanie jest zmieniane przez **procesy** okna **Odłączyć podczas debugowania zatrzymuje** opcję:<br /><br /> 1. Procesy uruchamiane przez debuger są kończone.<br />2. Dołączone procesy są odłączane od debugera.|  
|Menu **debugowania:**<br /><br /> -   **Zakończ wszystkie**|Wszystkie procesy są zakończone.|  
|Menu **debugowania:**<br /><br /> -   **Odłącz wszystko**|Debuger odłącza się od wszystkich procesów.|  
|Menu kontekstowe okna **procesów:**<br /><br /> -   **Proces odłączyć**|Debuger odłącza się od wybranego procesu.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
|Menu kontekstowe okna **procesów:**<br /><br /> -   **Zakończenie procesu**|Wybrany proces zostanie zakończony.<br /><br /> Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|  
|Menu kontekstowe okna **procesów:**<br /><br /> -   **Odłączanie po zatrzymaniu debugowania**|Przełącza zachowanie **debugowania**, **Zatrzymaj debugowanie** dla wybranego procesu:<br /><br /> - Zaznaczone: debuger odłącza się od procesu.<br />- Wyczyszczone: Proces został zakończony.|  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zatrzymaj debugowanie, zakończ lub odłącz procesy](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Powrót do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zawartość](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Określ symbol (pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Poruszanie się po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Debugowanie just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
