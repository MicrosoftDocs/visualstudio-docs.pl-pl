---
title: Debugowanie wielu procesów | Microsoft Docs
description: Debuguj wiele procesów w programie Visual Studio. Uruchamiaj i przełączaj między procesami, przerywaj, Kontynuuj, przechodzenia przez źródło i Zakończ lub odłączaj od poszczególnych procesów.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
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
ms.openlocfilehash: 214025c2d128443223594fdb00fcf730e5a8091a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728634"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Debugowanie wielu procesów (C#, Visual Basic, C++)

Program Visual Studio może debugować rozwiązanie, które ma kilka procesów. Można uruchamiać i przełączać między procesami, przerywać, kontynuować i przechodzić przez źródło, zatrzymywać debugowanie oraz kończyć lub odłączać się od poszczególnych procesów.

## <a name="start-debugging-with-multiple-processes"></a>Rozpocznij debugowanie z wieloma procesami

Jeśli więcej niż jeden projekt w rozwiązaniu programu Visual Studio może działać niezależnie, można wybrać projekt, który zostanie uruchomiony przez debuger. Bieżący projekt startowy jest wyświetlany pogrubiony w **Eksplorator rozwiązań**.

Aby zmienić projekt startowy, w **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy inny projekt i wybierz polecenie **Ustaw jako projekt startowy**.

Aby rozpocząć debugowanie projektu z **Eksplorator rozwiązań** bez tworzenia projektu startowego, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Debuguj**  >  **Uruchom nowe wystąpienie** lub **Przejdź do nowego wystąpienia**.

**Aby ustawić projekt startowy lub wiele projektów na podstawie właściwości rozwiązania:**

1. Wybierz rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz ikonę **Właściwości** na pasku narzędzi lub kliknij rozwiązanie prawym przyciskiem myszy, a następnie wybierz pozycję **Właściwości**.

1. Na stronie **Właściwości** wybierz   >  **projekt startowy** wspólne właściwości.

   ![Zmiana typu uruchomienia dla projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Wybierz **bieżące zaznaczenie**, **pojedynczy projekt startowy** i plik projektu lub **wiele projektów startowych**.

   W przypadku wybrania **wielu projektów startowych** można zmienić kolejność uruchamiania i akcję do wykonania dla każdego projektu: **Uruchom**, **Uruchom bez debugowania** lub **Brak**.

1. Wybierz pozycję **Zastosuj**, lub **przycisk OK** , aby zastosować i zamknąć okno dialogowe.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Dołącz do procesu

Debuger może również *dołączać* do aplikacji działających w procesach poza programem Visual Studio, w tym na urządzeniach zdalnych. Po dołączeniu do aplikacji możesz użyć debugera programu Visual Studio. Funkcje debugowania mogą być ograniczone. Jest to zależne od tego, czy aplikacja została skompilowana przy użyciu informacji debugowania, czy masz dostęp do kodu źródłowego aplikacji oraz czy kompilator JIT śledzi informacje debugowania.

Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Aby dołączyć do uruchomionego procesu:**

1. Po uruchomieniu aplikacji wybierz pozycję **Debuguj**  >  **Dołącz do procesu**.

   ![Okno dialogowe Dołączanie do procesu](../debugger/media/dbg_attachtoprocessdlg.png "Okno dialogowe Dołączanie do procesu")

1. W oknie dialogowym **Dołącz do procesu** wybierz proces z listy **dostępne procesy** , a następnie wybierz pozycję **Dołącz**.

>[!NOTE]
>Debuger nie dołącza automatycznie do procesu podrzędnego, który jest uruchamiany przez debugowany proces, nawet jeśli projekt podrzędny znajduje się w tym samym rozwiązaniu. Aby debugować proces podrzędny, należy dołączyć do procesu podrzędnego po jego rozpoczęciu lub skonfigurować Edytor rejestru systemu Windows, aby uruchamiał proces podrzędny w nowym wystąpieniu debugera.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Użyj edytora rejestru, aby automatycznie uruchomić proces w debugerze

Czasami może być konieczne Debugowanie kodu startowego dla aplikacji, która jest uruchamiana przez inny proces. Przykłady obejmują usługi i akcje instalacji niestandardowej. Debuger może być uruchamiany i automatycznie dołączany do aplikacji.

1. Uruchom Edytor rejestru systemu Windows, uruchamiając *regedit.exe*.

1. W Edytorze rejestru przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Wybierz folder aplikacji, którą chcesz uruchomić w debugerze.

   Jeśli aplikacja nie jest wymieniona jako folder podrzędny, kliknij prawym przyciskiem myszy **Opcje wykonywania pliku obrazu**, wybierz pozycję **Nowy**  >  **klucz** i wpisz nazwę aplikacji. Możesz też kliknąć prawym przyciskiem myszy nowy klucz w drzewie, wybrać polecenie **Zmień** nazwę, a następnie wprowadzić wartość Nazwa aplikacji.

1. Kliknij prawym przyciskiem myszy nowy klucz w drzewie i wybierz pozycję **Nowa**  >  **wartość ciągu**.

1. Zmień nazwę nowej wartości z **nowej wartości #1** na `debugger` .

1. Kliknij prawym przyciskiem myszy **debuger** i wybierz polecenie **Modyfikuj**.

   ![Okno dialogowe Edytowanie ciągu](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Okno dialogowe Edytowanie ciągu")

1. W oknie dialogowym **Edytowanie ciągu** wpisz `vsjitdebugger.exe` w polu **dane wartości** , a następnie wybierz przycisk **OK**.

   ![Wpis początkowy debugera automatycznego w regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Wpis początkowy debugera automatycznego w regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Debugowanie z wieloma procesami
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Podczas debugowania aplikacji z kilkoma procesami polecenia debugera przerywania, krokowe i kontynuowania mają domyślnie wpływ na wszystkie procesy. Na przykład gdy proces jest zawieszony w punkcie przerwania, wykonywanie wszystkich innych procesów również zostaje zawieszone. To zachowanie domyślne można zmienić, aby uzyskać większą kontrolę nad obiektami docelowymi poleceń wykonywania.

**Aby zmienić, czy wszystkie procesy są zawieszane po przerwaniu jednego procesu:**

- W obszarze **Narzędzia** (lub **Debuguj**) > **Opcje**  >  **debugowania**  >  **Ogólne** zaznacz lub usuń zaznaczenie pola wyboru **Przerwij wszystkie procesy w przypadku, gdy jest to jedno przerwanie procesu** .

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Polecenia Break, Step i Continue

W poniższej tabeli opisano zachowania poleceń debugowania po zaznaczeniu pola wyboru **Przerwij wszystkie procesy, gdy** jest zaznaczone lub jest ono odtworzone:

|**Polecenie**|Wybrane|Niezaznaczone|
|-|-|-|
|**Debuguj**   >  **Przerwij wszystko**|Wszystkie procesy są przerywane.|Wszystkie procesy są przerywane.|
|**Debuguj**  >  **Kontynuuj**|Wszystkie procesy są wznawiane.|Wszystkie zawieszone procesy są wznawiane.|
|**Debuguj**  >  **Wkrocz do**, **Przekrocz lub** **Wyjdź**|Wszystkie procesy są uruchamiane podczas wykonywania bieżących kroków procesu. <br />Następnie wszystkie procesy są przerywane.|Bieżące etapy procesu. <br />Zawieszone procesy są wznawiane. <br />Uruchomione procesy są kontynuowane.|
|**Debuguj**  >  **Wkrocz do bieżącego procesu**, **Przekrocz bieżący** proces lub **Wyjdź z bieżącego procesu**|Nie dotyczy|Bieżące etapy procesu.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|
|**Punkt przerwania** okna źródłowego|Wszystkie procesy są przerywane.|Tylko przerwy w procesie okna źródłowego.|
|Okno źródłowe **uruchamia do kursora**<br />Okno źródłowe musi znajdować się w bieżącym procesie.|Wszystkie procesy są uruchamiane, gdy proces okna źródłowego jest uruchamiany do kursora, a następnie do końca.<br />Następnie wszystkie inne procesy są przerywane.|Proces okna źródłowego jest uruchamiany do kursora.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|
|**Proces przerwania** > okna **procesów**|Nie dotyczy|Wybrane podziały procesu.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|
|Okno **procesów** > **kontynuować procesu**|Nie dotyczy|Wybrany proces zostanie wznowiony.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Znajdowanie plików źródłowych i symboli (. pdb)
Aby nawigować po kodzie źródłowym procesu, debuger musi mieć dostęp do plików źródłowych i plików symboli. Aby uzyskać więcej informacji, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Jeśli nie możesz uzyskać dostępu do plików dla procesu, możesz nawigować przy użyciu okna **demontażu** . Aby uzyskać więcej informacji, zobacz [How to: Use the deassembly Window](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Przełączanie między procesami

Podczas debugowania można dołączyć do wielu procesów, ale tylko jeden proces jest aktywny w debugerze w danym momencie. Można ustawić aktywny lub *bieżący* proces na pasku narzędzi **lokalizacji debugowania** lub w oknie **procesy** . Aby przełączać się między procesami, oba procesy muszą być w trybie przerwania.

**Aby ustawić bieżący proces na pasku narzędzi lokalizacji debugowania:**

1. Aby otworzyć pasek narzędzi **Lokalizacja debugowania** , wybierz pozycję **Wyświetl**  >  **paski narzędzi**  >  **Lokalizacja debugowania**.

1. Podczas debugowania na pasku narzędzi **Lokalizacja debugowania** wybierz proces, który chcesz ustawić jako bieżący proces z listy rozwijanej **proces** .

   ![Przełączanie między procesami](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Aby ustawić bieżący proces z okna procesy:**

1. Aby otworzyć okno **procesy** , podczas debugowania wybierz kolejno opcje **Debuguj**  >  procesy **systemu Windows**  >  .

1. W oknie **procesy** bieżący proces jest oznaczony żółtą strzałką. Kliknij dwukrotnie proces, który ma zostać ustawiony jako bieżący proces.

   ![Okno procesów](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Przełączenie do procesu ustawia go jako bieżący proces do celów debugowania. Okna debugera pokazują stan bieżącego procesu, a polecenia krok po kroku mają wpływ tylko na bieżący proces.

## <a name="stop-debugging-with-multiple-processes"></a>Zatrzymaj debugowanie z wieloma procesami

Domyślnie po wybraniu opcji **Debuguj**  >  **Zatrzymaj debugowanie** debuger zostaje zakończony lub odłączany od wszystkich procesów.

- Jeśli bieżący proces został uruchomiony w debugerze, proces zostanie zakończony.

- W przypadku dołączenia debugera do bieżącego procesu debuger odłącza się od procesu i opuszcza proces uruchomiony.

Po rozpoczęciu debugowania procesu z rozwiązania programu Visual Studio, dołączenie do innego procesu, który jest już uruchomiony, a następnie wybranie opcji **Zatrzymaj debugowanie** spowoduje zakończenie sesji debugowania. Proces, który został uruchomiony w programie Visual Studio, został zakończony, podczas gdy dołączono proces, aby nadal działał.

Aby kontrolować sposób, w jaki **zatrzymanie debugowania** wpływa na poszczególne procesy, w oknie **procesy** kliknij prawym przyciskiem myszy proces, a następnie zaznacz lub usuń zaznaczenie pola wyboru **Odłącz po zatrzymaniu debugowania** .

>[!NOTE]
>Opcja **Przerwij wszystkie procesy, gdy jeden proces** jest debugerem, nie ma wpływu na zatrzymywanie, Kończenie lub odłączanie od procesów.

### <a name="stop-terminate-and-detach-commands"></a>Polecenia zatrzymywania, kończenia i odłączania

Poniższa tabela zawiera opis zachowań poleceń zatrzymywanie, kończenie i odłączanie debugera z wieloma procesami:

|**Polecenie**|**Opis**|
|-|-|
|**Debuguj**  >  **Zatrzymaj debugowanie**|O ile zachowanie nie zostanie zmienione w oknie **procesy** , procesy uruchomione przez debuger są zakończone, a dołączone procesy są odłączone.|
|**Debuguj**  >  **Przerwij wszystkie**|Wszystkie procesy zostały zakończone.|
|**Debuguj**  >  **Odłącz wszystko**|Debuger odłącza się od wszystkich procesów.|
|**Proces Odłączania** > okna **procesów**|Debuger odłącza się od wybranego procesu.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|
|**Proces kończenia** okna **procesów** >|Wybrany proces został zakończony.<br />Inne procesy utrzymują swój istniejący stan (zawieszone lub działające).|
|Okno **procesów** > **Odłącz po zatrzymaniu debugowania**|W przypadku wybrania tej operacji **debugowanie**  >  **Zatrzymaj debugowanie** odłącza się od wybranego procesu. <br />Jeśli nie jest zaznaczone **,**  >  **debugowanie zatrzymania debugowania** zakończy wybrany proces. |

## <a name="see-also"></a>Zobacz też

- [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)