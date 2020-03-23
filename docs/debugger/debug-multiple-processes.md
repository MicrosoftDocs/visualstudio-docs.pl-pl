---
title: Debugowanie wielu procesów | Dokumenty firmy Microsoft
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302225"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Debugowanie wielu procesów (C#, Visual Basic, C++)

Visual Studio można debugować rozwiązanie, które ma kilka procesów. Można rozpocząć i przełączać się między procesami, przerwać, kontynuować i krok po kroku przez źródło, zatrzymać debugowanie i zakończyć lub odłączyć od poszczególnych procesów.

## <a name="start-debugging-with-multiple-processes"></a>Rozpoczynanie debugowania za pomocą wielu procesów

Gdy więcej niż jeden projekt w rozwiązaniu programu Visual Studio można uruchomić niezależnie, można wybrać projekt, który uruchamia debuger. Bieżący projekt uruchamiania jest wyświetlany pogrubioną czcionką w **Eksploratorze rozwiązań**.

Aby zmienić projekt startowy, w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy inny projekt i wybierz polecenie **Ustaw jako projekt startowy**.

Aby rozpocząć debugowanie projektu z **Eksploratora rozwiązań** bez przekształcania go w projekt startowy, kliknij prawym przyciskiem myszy projekt i wybierz polecenie**Rozpocznij nowe wystąpienie** **debugowania** > lub **Krok do nowego wystąpienia**.

**Aby ustawić projekt startowy lub wiele projektów z właściwości rozwiązania:**

1. Wybierz rozwiązanie w **Eksploratorze rozwiązań,** a następnie wybierz ikonę **Właściwości** na pasku narzędzi lub kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Właściwości**.

1. Na stronie **Właściwości** wybierz pozycję**Projekt uruchamiania** **wspólnych właściwości** > .

   ![Zmienianie typu uruchamiania projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Wybierz **bieżące zaznaczenie,** **Pojedynczy projekt startowy** i plik projektu lub Wiele projektów **startowych**.

   W przypadku **wybrania opcji Wiele projektów startowych**można zmienić kolejność uruchamiania i akcję do wykonania dla każdego projektu: **Start**, Start **bez debugowania**lub **Brak**.

1. Wybierz **opcję Zastosuj**lub **OK,** aby zastosować i zamknąć okno dialogowe.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Dołączanie do procesu

Debuger można również *dołączyć* do aplikacji działających w procesach poza programem Visual Studio, w tym na urządzeniach zdalnych. Po dołączeniu do aplikacji można użyć debugera programu Visual Studio. Funkcje debugowania mogą być ograniczone. To zależy od tego, czy aplikacja została zbudowana z informacjami debugowania, czy masz dostęp do kodu źródłowego aplikacji i czy kompilator JIT śledzi informacje debugowania.

Aby uzyskać więcej informacji, zobacz [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Aby dołączyć do uruchomionego procesu:**

1. Po uruchomieniu aplikacji wybierz pozycję **Debug** > **dołącz do procesu**.

   ![Okno dialogowe Dołączanie do procesu](../debugger/media/dbg_attachtoprocessdlg.png "Okno dialogowe Dołączanie do procesu")

1. W oknie dialogowym **Dołączanie do procesu** wybierz proces z listy **Dostępne procesy,** a następnie wybierz pozycję **Dołącz**.

>[!NOTE]
>Debuger nie automatycznie dołączyć do procesu podrzędnego, który jest uruchamiany przez debugowany proces, nawet jeśli projekt podrzędny jest w tym samym rozwiązaniu. Aby debugować proces podrzędny, dołącz do procesu podrzędnego po jego uruchomieniu lub skonfiguruj Edytor rejestru systemu Windows, aby uruchomić proces podrzędny w nowym wystąpieniu debugera.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Automatyczne uruchamianie procesu w debugerze za pomocą Edytora rejestru

Czasami może być konieczne debugowanie kodu startowego dla aplikacji, która jest uruchamiana przez inny proces. Przykłady obejmują usługi i akcje konfiguracji niestandardowej. Możesz uruchomić debuger i automatycznie dołączyć do aplikacji.

1. Uruchom Edytor rejestru systemu Windows, uruchamiając *plik regedit.exe*.

1. W Edytorze rejestru przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Wybierz folder aplikacji, który chcesz uruchomić w debugerze.

   Jeśli aplikacji nie ma na liście jako folderu podrzędnego, kliknij prawym przyciskiem myszy **pozycję Opcje wykonywania plików obrazu**, wybierz pozycję **Nowy** > **klucz**i wpisz nazwę aplikacji. Możesz też kliknąć prawym przyciskiem myszy nowy klucz w drzewie, wybrać **pozycję Zmień nazwę**, a następnie wprowadź nazwę aplikacji.

1. Kliknij prawym przyciskiem myszy nowy klucz w drzewie i wybierz polecenie **Nowa** > **wartość ciągu**.

1. Zmień nazwę nowej wartości z **Nowa wartość** `debugger`#1 na .

1. Kliknij prawym przyciskiem myszy **debuger** i wybierz polecenie **Modyfikuj**.

   ![Okno dialogowe Edytowanie ciągu](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Okno dialogowe Edytowanie ciągu")

1. W oknie dialogowym **Edytowanie ciągu** wpisz `vsjitdebugger.exe` pole **Dane wartość,** a następnie wybierz przycisk **OK**.

   ![Automatyczny wpis startowy debugera w pliku regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Automatyczny wpis startowy debugera w pliku regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Debugowanie z wieloma procesami
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Podczas debugowania aplikacji z kilku procesów, podział, stepping i ciągłe debuger polecenia wpływają na wszystkie procesy domyślnie. Na przykład, gdy proces jest zawieszony w punkcie przerwania, wykonywanie wszystkich innych procesów jest również zawieszone. Można zmienić to domyślne zachowanie, aby uzyskać większą kontrolę nad celami poleceń wykonywania.

**Aby zmienić, czy wszystkie procesy są zawieszone, gdy jeden proces się zepsuje:**

- W obszarze **Narzędzia** (lub **Debugowanie)**> **opcje** > **debugowania** > **ogólne**zaznacz lub wyczyść pole wyboru **Przerwij wszystkie procesy, gdy jeden proces przerywa.**

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Przerywanie, krok i kontynuowanie poleceń

W poniższej tabeli opisano zachowania poleceń debugowania, gdy pole wyboru **Przerwij wszystkie procesy, gdy zaznaczono** lub nie zaznaczono wyboru jednego procesu:

|**Polecenie**|Wybrano|Zaznaczona|
|-|-|-|
|**Debugowanie**  > **break all**|Wszystkie procesy pękają.|Wszystkie procesy pękają.|
|**Debugowanie** > **kontynuuj**|Wszystkie procesy wznawiają się.|Wszystkie zawieszone procesy zostaną wznowione.|
|**Krok debugowania** > **do**, Krok **na**, lub **Wyjść**|Wszystkie procesy są uruchamiane podczas bieżących kroków procesu. <br />Następnie wszystkie procesy pękają.|Bieżące etapy procesu. <br />Zawieszone procesy wznowić. <br />Procesy uruchomione są kontynuowane.|
|**Krok debugowania** > **do bieżącego procesu,** **krok nad bieżącym procesem**lub **Wysuń bieżący proces**|Nie dotyczy|Bieżące etapy procesu.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|
|Punkt **przerwania** okna źródłowego|Wszystkie procesy pękają.|Tylko podziały procesu okna źródła.|
|Okno źródłowe **Uruchom do kursora**<br />Okno źródłowe musi być w bieżącym procesie.|Wszystkie procesy są uruchamiane, gdy proces okna źródłowego jest uruchamiany do kursora, a następnie przerywa.<br />Następnie wszystkie inne procesy pękają.|Proces okna źródłowego jest uruchamiany do kursora.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|
|**Procesy** > **proces podziału** okna|Nie dotyczy|Wybrane przerwy procesu.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|
|**Okno Procesy** > **kontynuuj proces**|Nie dotyczy|Wznawia się wybrany proces.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Znajdowanie plików źródłowych i symboli (pdb)
Aby poruszać się po kodzie źródłowym procesu, debuger potrzebuje dostępu do swoich plików źródłowych i plików symboli. Aby uzyskać więcej informacji, zobacz [Określanie symbolu (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Jeśli nie możesz uzyskać dostępu do plików dla procesu, możesz nawigować za pomocą okna **Demontaż.** Aby uzyskać więcej informacji, zobacz [Jak: Użyj okna Demontaż](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>Przełączanie między procesami

Można dołączyć do wielu procesów podczas debugowania, ale tylko jeden proces jest aktywny w debugerze w danym momencie. Aktywny lub *bieżący* proces można ustawić na pasku narzędzi **Lokalizacja debugowania** lub w oknie **Procesy.** Aby przełączać się między procesami, oba procesy muszą być w trybie przerwania.

**Aby ustawić bieżący proces z paska narzędzi Lokalizacja debugowania:**

1. Aby otworzyć pasek narzędzi **Lokalizacja debugowania,** wybierz pozycję **Wyświetl** > **położenie debugowania pasków** > **Debug Location**narzędzi .

1. Podczas debugowania na pasku narzędzi **Lokalizacja debugowania** wybierz proces, który chcesz ustawić jako bieżący proces z listy rozwijanej **Proces.**

   ![Przełączanie między procesami](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Aby ustawić bieżący proces z okna Procesy:**

1. Aby otworzyć okno **Procesy** podczas debugowania, wybierz opcję **Debugowanie** > **procesów****systemu Windows** > .

1. W oknie **Procesy** bieżący proces jest oznaczony żółtą strzałką. Kliknij dwukrotnie proces, który chcesz ustawić jako bieżący proces.

   ![Okno Procesy](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Przełączanie do procesu ustawia go jako bieżący proces do celów debugowania. Okna debugera pokazują stan bieżącego procesu, a polecenia krokowe wpływają tylko na bieżący proces.

## <a name="stop-debugging-with-multiple-processes"></a>Zatrzymywać debugowanie za pomocą wielu procesów

Domyślnie po wybraniu **debugowania** > **zatrzymaj debugowanie debugowanie**debuger kończy się lub odłącza od wszystkich procesów.

- Jeśli bieżący proces został uruchomiony w debugerze, proces zostanie zakończony.

- Jeśli debuger został dołączony do bieżącego procesu, debuger odłącza się od procesu i pozostawia proces uruchomiony.

Jeśli zaczniesz debugowania procesu z rozwiązania programu Visual Studio, a następnie dołączyć do innego procesu, który jest już uruchomiony, a następnie wybierz **pozycję Zatrzymaj debugowanie**, sesja debugowania kończy. Proces, który został uruchomiony w programie Visual Studio kończy się, podczas gdy proces dołączony do utrzymuje uruchomiony.

Aby kontrolować sposób, w jaki **zatrzymanie debugowania** wpływa na pojedynczy proces, w oknie **Procesy** kliknij prawym przyciskiem myszy proces, a następnie zaznacz lub wyczyść pole wyboru **Odłącz podczas debugowania zatrzymanego.**

>[!NOTE]
>**Przerwać wszystkie procesy, gdy jeden proces przerywa** debugera opcja nie wpływa na zatrzymywanie, kończenie lub odłączanie od procesów.

### <a name="stop-terminate-and-detach-commands"></a>Polecenia zatrzymania, zakończenia i odłączyć

W poniższej tabeli opisano zachowania poleceń zatrzymania, zakończenia i odłączania debugera za pomocą wielu procesów:

|**Polecenie**|**Opis**|
|-|-|
|**Debugowanie** > **zatrzymania debugowania**|O ile zachowanie nie zostanie zmienione w oknie **Procesy,** procesy uruchamiane przez debuger są kończyne, a dołączone procesy są odłączane.|
|**Debugowanie** > **zakończ wszystko**|Wszystkie procesy zostały zakończone.|
|**Debuguj** > **wszystkie**|Debuger odłącza się od wszystkich procesów.|
|**Procesy** > **proces odłączyć okno**|Debuger odłącza się od wybranego procesu.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|
|**Okno Procesy** > **zakończenie procesu**|Wybrany proces zostanie zakończony.<br />Inne procesy zachowują swój istniejący stan (zawieszony lub uruchomiony).|
|**Okno procesów** > **odłączyć po zatrzymaniu debugowania**|Jeśli ta opcja jest zaznaczona, **debugowanie** > **zatrzyma debugowanie** odłącza się od wybranego procesu. <br />Jeśli nie jest zaznaczona, **debugowanie** > **debugowania** kończy wybrany proces. |

## <a name="see-also"></a>Zobacz też

- [Określanie symbolu (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Przechodzenie przez kod za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Debugowanie just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)