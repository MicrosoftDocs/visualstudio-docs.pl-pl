---
title: Debugowanie wielu procesów | Microsoft Docs
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
ms.openlocfilehash: 97d98522e011023cb3a021a69c9a82e8bb34cef3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533279"
---
# <a name="debug-multiple-processes"></a>Debugowanie wielu procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oto jak rozpocząć debugowanie procesów, przełączać się między procesami, przerywać i kontynuować wykonywanie, przechodzić przez źródło, zatrzymywać debugowanie i kończyć lub odłączać od procesów.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Contents  
 [Skonfiguruj zachowanie wykonywania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Znajdowanie plików źródłowych i symboli (. pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie Rozpocznij proces w debugerze](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Przełączanie procesów, przerywanie i kontynuowanie wykonywania, krok po kroku](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Zatrzymaj debugowanie, Przerwij lub odłącz od procesów](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Skonfiguruj zachowanie wykonywania wielu procesów  
 Domyślnie, gdy w debugerze są uruchomione wiele procesów, polecenia dzielące, krokowe i zatrzymujące debugera zwykle wpływają na wszystkie procesy. Na przykład po wstrzymaniu jednego procesu w punkcie przerwania wykonywanie wszystkich innych procesów jest również zawieszone. To zachowanie domyślne można zmienić, aby uzyskać większą kontrolę nad obiektami docelowymi poleceń wykonania.  
  
1. W menu **debugowanie** wybierz **Opcje i ustawienia**.  
  
2. Na stronie **debugowanie**, **Ogólne** wyczyść pole wyboru **Przerwij wszystkie procesy w przypadku wystąpienia jednego procesu** .  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Znajdowanie plików źródłowych i symboli (. pdb)  
 Aby nawigować po kodzie źródłowym procesu, debuger musi mieć dostęp do plików źródłowych i plików symboli procesu. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Jeśli nie możesz uzyskać dostępu do plików dla procesu, możesz nawigować przy użyciu okna dezasemblacja. Zobacz [jak: korzystanie z okna demontażu](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Uruchom wiele procesów w rozwiązaniu programu VS, Dołącz do procesu, automatycznie Rozpocznij proces w debugerze  
  
- [Rozpocznij debugowanie wielu procesów w rozwiązaniu programu Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Zmień projekt startowy](#BKMK_Change_the_startup_project) • [Rozpocznij konkretny projekt w rozwiązaniu](#BKMK_Start_a_specific_project_in_a_solution) • [Rozpocznij wiele projektów w rozwiązaniu](#BKMK_Start_multiple_projects_in_a_solution) • [dołączanie do procesu](#BKMK_Attach_to_a_process) • [Automatyczne uruchamianie procesu w debugerze](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Debuger nie dołącza automatycznie do procesu podrzędnego, który jest uruchamiany przez debugowany proces, nawet jeśli projekt podrzędny znajduje się w tym samym rozwiązaniu. Aby debugować proces podrzędny:  
> 
> - Dołącz do procesu podrzędnego po jego uruchomieniu.  
> 
>   -lub-  
>   - Skonfiguruj system Windows w taki sposób, aby automatycznie uruchomił proces podrzędny w nowym wystąpieniu debugera.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Rozpocznij debugowanie wielu procesów w rozwiązaniu programu Visual Studio  
 Jeśli masz więcej niż jeden projekt w rozwiązaniu programu Visual Studio, który można uruchamiać niezależnie (projekty działające w oddzielnych procesach), możesz wybrać, które projekty zaczynają się debugerem.  
  
 ![Zmiana typu uruchomienia dla projektu](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a> Zmień projekt startowy  
 Aby zmienić projekt startowy dla rozwiązania, wybierz projekt w Eksplorator rozwiązań a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu kontekstowego.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a> Uruchamianie określonego projektu w rozwiązaniu  
 Aby rozpocząć projekt rozwiązania bez zmiany domyślnego projektu startowego, wybierz projekt w Eksplorator rozwiązań a następnie wybierz **Debuguj** z menu kontekstowego. Następnie możesz wybrać **Uruchom nowe wystąpienie** lub **Wkrocz do nowego wystąpienia**.  
  
 ![Wróć do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [wiele procesów w rozwiązaniu programu vs, Dołącz do procesu, automatycznie Rozpocznij proces w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a> Uruchamianie wielu projektów w rozwiązaniu  
  
1. Wybierz rozwiązanie w Eksplorator rozwiązań a następnie wybierz **Właściwości** z menu kontekstowego.  
  
2. W oknie dialogowym **Właściwości** wybierz pozycję **wspólne właściwości**, **projekt startowy** .  
  
3. Dla każdego projektu, który chcesz zmienić, wybierz opcję **Uruchom**, **Uruchom bez debugowania**lub **Brak**.  
  
   ![Wróć do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [wiele procesów w rozwiązaniu programu vs, Dołącz do procesu, automatycznie Rozpocznij proces w debugerze](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Dołącz do procesu  
 Debuger może również *dołączyć* do programów uruchomionych w procesach poza programem Visual Studio, w tym programów uruchomionych na urządzeniu zdalnym. Po dołączeniu do programu można użyć poleceń wykonywania debugera, sprawdzić stan programu i tak dalej. Możliwość kontroli programu może być ograniczona, w zależności od tego, czy program został skompilowany z informacjami o debugowaniu i czy masz dostęp do kodu źródłowego programu, oraz czy kompilator JIT środowiska uruchomieniowego języka wspólnego nie śledzi informacji debugowania.  
  
 Aby uzyskać więcej informacji [, zobacz Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 **Dołącz do procesu, który jest uruchomiony na komputerze lokalnym**  
  
 Wybierz **Debuguj**, **Dołącz do procesu**. W oknie dialogowym **Dołącz do procesu** wybierz proces z listy **dostępne procesy** , a następnie wybierz **Dołącz**.  
  
 ![Okno dialogowe Dołączanie do procesu](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Automatycznie uruchamiaj proces w debugerze  
 Czasami może być konieczne Debugowanie kodu początkowego dla programu uruchamianego przez inny proces. Przykłady obejmują usługi i akcje instalacji niestandardowej. W tych scenariuszach można uruchamiać debuger i automatycznie dołączać się podczas uruchamiania aplikacji.  
  
1. Uruchom Edytor rejestru (**regedit.exe**).  
  
2. Przejdź do folderu **HKEY_LOCAL_MACHINE \Software\microsoft\windows NT\CurrentVersion\Image Opcje wykonania pliku** .  
  
3. Wybierz folder aplikacji, którą chcesz uruchomić w debugerze.  
  
    Jeśli nazwa aplikacji nie jest wymieniona jako folder podrzędny, wybierz pozycję **Opcje wykonywania pliku obrazu** , a następnie wybierz polecenie **Nowy**, **klucz** z menu kontekstowego. Wybierz nowy klucz, wybierz polecenie **Zmień nazwę** w menu skrótów, a następnie wprowadź nazwę aplikacji.  
  
4. W menu kontekstowym folderu aplikacji wybierz pozycję **Nowy**, **wartość ciągu**.  
  
5. Zmień nazwę nowej wartości z **Nowa wartość** na `debugger` .  
  
6. W menu kontekstowym wpisu debugera wybierz polecenie **Modyfikuj**.  
  
7. W oknie dialogowym Edytowanie ciągu wpisz `vsjitdebugger.exe` w polu **dane wartości** .  
  
    ![Okno dialogowe Edytowanie ciągu](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Wpis początkowy debugera automatycznego w regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Przełączanie procesów, przerywanie i kontynuowanie wykonywania, krok po kroku  
  
- [Przełączanie między procesami](#BKMK_Switch_between_processes) • [poleceniami Break, Step i Continue](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Przełączanie między procesami  
 Podczas debugowania można dołączyć do wielu procesów, ale tylko jeden proces jest aktywny w debugerze w danym momencie. Można ustawić aktywny lub *bieżący* proces na pasku narzędzi lokalizacji debugowania lub w oknie **procesy** . Aby przełączać się między procesami, oba procesy muszą być w trybie przerwania.  
  
 **Aby ustawić bieżący proces**  
  
- Na pasku narzędzi Lokalizacja debugowania wybierz pozycję **proces** , aby wyświetlić pole listy **proces** . Wybierz proces, który chcesz wyznaczyć jako bieżący proces.  
  
   ![Przełączanie między procesami](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Jeśli pasek narzędzi **Lokalizacja debugowania** nie jest widoczny, wybierz pozycję **Narzędzia**, a następnie pozycję **Dostosuj**. Na karcie **paski narzędzi** wybierz pozycję **Debugowanie lokalizacji**.  
  
- Otwórz okno **procesy** (skrót **Ctrl + Alt + Z**), Znajdź proces, który chcesz ustawić jako bieżący proces, a następnie kliknij go dwukrotnie.  
  
   ![Okno procesów](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Bieżący proces jest oznaczony żółtą strzałką.  
  
  Przełączenie do projektu ustawia go jako bieżący proces do celów debugowania. Każde okno debugera, które zostanie wyświetlone, wyświetli stan bieżącego procesu, a wszystkie polecenia przechodzenia mają wpływ tylko na bieżący proces.  
  
  ![Wróć do najczęstszych](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [procesów przełączania, Przerwij i kontynuuj wykonywanie, przechodzenie krok po kroku](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Polecenia Break, Step i Continue  
  
> [!NOTE]
> Domyślnie polecenia debugera Break, Continue i Step wpływają na wszystkie procesy, które są debugowane. Aby zmienić to zachowanie, zobacz [Konfigurowanie zachowania wykonywania wielu procesów](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
|**Polecenie**|**Przerwij wszystkie procesy w przypadku przerwania jednego procesu**<br /><br /> Zaznaczone (domyślnie)|**Przerwij wszystkie procesy w przypadku przerwania jednego procesu**<br /><br /> Zaznaczenia|  
|-|-|-|
|Menu **Debuguj** :<br /><br /> -   **Przerwij wszystko**|Wszystkie procesy są przerywane.|Wszystkie procesy są przerywane.|  
|Menu **Debuguj** :<br /><br /> -   **Utrzymać**|Wszystkie procesy są wznawiane.|Wszystkie zawieszone procesy są wznawiane.|  
|Menu **Debuguj** :<br /><br /> -   **Wkrocz do**<br />-   **Przekrocz nad**<br />-   **Wyjdź**|Wszystkie procesy są uruchamiane podczas wykonywania bieżących kroków procesu.<br /><br /> Następnie wszystkie procesy są przerywane.|Bieżące etapy procesu.<br /><br /> Zawieszone procesy są wznawiane.<br /><br /> Uruchomione procesy są kontynuowane.|  
|Menu **Debuguj** :<br /><br /> -   **Wkrocz do bieżącego procesu**<br />-   **Przekrocz bieżący proces**<br />-   **Wyjdź z bieżącego procesu**|Brak|Bieżące etapy procesu.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
|Okno źródłowe<br /><br /> -   **Punkt**|Wszystkie procesy są przerywane.|Tylko przerwy w procesie okna źródłowego.|  
|Menu kontekstowe okna źródłowego:<br /><br /> -   **Uruchom do kursora**<br /><br /> Okno źródłowe musi znajdować się w bieżącym procesie.|Wszystkie procesy są uruchamiane, gdy proces okna źródłowego jest uruchamiany do kursora, a następnie do końca.<br /><br /> Następnie wszystkie inne procesy są przerywane.|Proces okna źródłowego jest uruchamiany do kursora.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
|Menu kontekstowe okna **procesów** :<br /><br /> -   **Przerwij proces**|Brak|Wybrane podziały procesu.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
|Menu kontekstowe okna **procesów** :<br /><br /> -   **Kontynuuj proces**|Brak|Wybrany proces zostanie wznowiony.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
  
 ![Wróć do najczęstszych](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [procesów przełączania, Przerwij i kontynuuj wykonywanie, przechodzenie krok po kroku](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Zatrzymaj debugowanie, Przerwij lub odłącz od procesów  
  
- [Polecenia zatrzymywania, kończenia i odłączania](#BKMK_Stop__terminate__and_detach_commands)  
  
  Domyślnie po wybraniu **debugowania**należy **zatrzymać debugowanie** , gdy w debugerze są otwarte wiele procesów, debuger kończy działanie lub odłącza od wszystkich procesów, w zależności od tego, jak proces został otwarty w debugerze:  
  
- Jeśli bieżący proces został uruchomiony w debugerze, ten proces zostanie zakończony.  
  
- W przypadku dołączenia debugera do bieżącego procesu debuger odłącza się od procesu i opuszcza proces uruchomiony.  
  
  Na przykład po rozpoczęciu debugowania procesu z rozwiązania programu Visual Studio dołączenie do innego procesu, który jest już uruchomiony, a następnie wybranie opcji **Zatrzymaj debugowanie**, sesja debugowania kończy się, proces, który został uruchomiony w programie Visual Studio, zostanie przerwany, podczas gdy połączony proces został pozostawiony. Poniższe procedury służą do kontrolowania sposobu zatrzymania debugowania.  
  
> [!NOTE]
> Opcja **Przerwij wszystkie procesy, gdy jeden proces jest podzielony** , nie wpływa na zatrzymanie debugowania ani kończenie i odłączanie od procesów.  
  
 **Aby zmienić sposób, w jaki zatrzymanie debugowania wpływa na proces indywidualny**  
  
- Otwórz okno **procesy** (skrót **Ctrl + Alt + Z**). Wybierz proces, a następnie zaznacz lub wyczyść pole wyboru **Odłącz po zatrzymaniu debugowania** .  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a> Polecenia zatrzymywania, kończenia i odłączania  
  
|**Polecenie**|**Opis**|  
|-|-|  
|Menu **Debuguj** :<br /><br /> -   **Zatrzymaj debugowanie**|O ile zachowanie nie zostanie zmienione **Processes** przez proces **odłączania po zatrzymaniu debugowania** :<br /><br /> 1. procesy uruchomione przez debuger są kończone.<br />2. dołączone procesy są odłączone od debugera.|  
|Menu **Debuguj** :<br /><br /> -   **Przerwij wszystkie**|Wszystkie procesy są przerywane.|  
|Menu **Debuguj** :<br /><br /> -   **Odłącz wszystko**|Debuger odłącza się od wszystkich procesów.|  
|Menu kontekstowe okna **procesów** :<br /><br /> -   **Odłączanie procesu**|Debuger odłącza się od wybranego procesu.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
|Menu kontekstowe okna **procesów** :<br /><br /> -   **Przerwij proces**|Wybrany proces został zakończony.<br /><br /> Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|  
|Menu kontekstowe okna **procesów** :<br /><br /> -   **Odłącz po zatrzymaniu debugowania**|Włącza **lub wyłącza** **debugowanie** dla wybranego procesu:<br /><br /> -Zaznaczone: debuger odłącza się od procesu.<br />-Wyczyszczone: proces został zakończony.|  
  
 ![Z powrotem do góry](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Zatrzymaj debugowanie, Przerwij lub odłącz od procesów](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)   
 [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debuguj wielowątkowe aplikacje](../debugger/debug-multithreaded-applications-in-visual-studio.md)
