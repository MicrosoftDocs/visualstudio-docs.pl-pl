---
title: Debugowanie wielu procesów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5d9c592663e32b8050644d459b8db45f3f0f5307
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630746"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Debugowanie wielu procesów (C#, Visual Basic, C++)

Visual Studio umożliwia debugowanie rozwiązanie, które ma kilka procesów. Możesz rozpocząć i przełączać się między procesami, podzielić, kontynuować i przejść przez źródło, Zatrzymaj debugowanie i zakończenia lub odłączyć od poszczególnych procesów.

## <a name="start-debugging-with-multiple-processes"></a>Rozpocznij debugowanie z wieloma procesami

Jeśli więcej niż jednego projektu w rozwiązaniu Visual Studio można uruchomić niezależnie, można wybrać projekt, który uruchamia debuger. Bieżący projekt startowy, który pojawia się w pogrubieniem w **Eksploratora rozwiązań**.

Aby zmienić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy inny projekt i wybierz **Ustaw jako projekt startowy**.

Aby rozpocząć debugowanie projektu z **Eksploratora rozwiązań** bez wprowadzania projekt startowy, kliknij prawym przyciskiem myszy projekt i wybierz **debugowania** > **Uruchom nowe wystąpienie** lub **Wkrocz do nowego wystąpienia**.

**Aby ustawić projekt startowy lub wielu projektów w rozwiązaniu właściwości:**

1. Wybierz rozwiązanie w **Eksploratora rozwiązań** , a następnie wybierz **właściwości** ikonę na pasku narzędzi lub kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **właściwości**.

1. Na **właściwości** wybierz opcję **wspólne właściwości** > **projekt startowy**.

   ![Zmiana typu uruchamiania dla projektu](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Wybierz **bieżące zaznaczenie**, **pojedynczy projekt startowy** i plik projektu lub **wiele projektów startowych**.

   Jeśli wybierzesz **wiele projektów startowych**, możesz zmienić kolejność uruchamiania i akcji, które można wykonać dla każdego projektu: **Rozpocznij**, **Uruchom bez debugowania**, lub **Brak**.

1. Wybierz **Zastosuj**, lub **OK** stosowania i zamknąć okno dialogowe.

###  <a name="BKMK_Attach_to_a_process"></a> Dołącz do procesu

Debuger może również *dołączyć* do aplikacji działających w procesach poza programem Visual Studio, w tym na urządzeniach zdalnych. Po dołączeniu do aplikacji, należy użyć debugera programu Visual Studio. Funkcje debugowania może być ograniczona. To zależy od tego, czy aplikacja został skompilowany według informacji o debugowaniu, czy masz dostęp do kodu źródłowego aplikacji i czy kompilator JIT śledzi informacje debugowania.

Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Aby dołączyć do uruchomionego procesu:**

1. Gdy aplikacja jest uruchomiona, wybierz **debugowania** > **dołączyć do procesu**.

   ![Dołącz do procesu, okno dialogowe](../debugger/media/dbg_attachtoprocessdlg.png "dołączanie do procesu, okno dialogowe")

1. W **dołączyć do procesu** okna dialogowego Wybierz proces na **dostępne procesy** listy, a następnie wybierz **Dołącz**.

>[!NOTE]
>Debuger nie dołącza automatycznie do procesu podrzędnego uruchomionego przez proces debugowania, nawet jeśli projekt podrzędny znajduje się w tym samym rozwiązaniu. Aby debugować proces podrzędny, Dołącz do procesu podrzędnego, po uruchomieniu lub skonfigurować Edytor rejestru Windows, aby rozpocząć proces podrzędny w nowym wystąpieniu debugera.

###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Użyj Edytora rejestru do automatycznego uruchamiania procesu w debugerze

Czasami może być konieczne zdebugowanie kodu startowego dla aplikacji, który jest uruchamiany przez inny proces. Przykładami są usługi i akcje instalacji niestandardowej. Może mieć debugera, uruchom i automatyczne dołączanie do aplikacji.

1. Uruchom Edytor rejestru Windows przez uruchomienie *regedit.exe*.

1. W Edytorze rejestru przejdź do **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Wybierz folder aplikacji, które mają być uruchamiane w debugerze.

   Jeśli aplikacja nie jest wymieniony jako folder podrzędny, kliknij prawym przyciskiem myszy **Image File Execution Options**, wybierz opcję **New** > **klucz**, a następnie wpisz nazwę aplikacji. Lub kliknij prawym przyciskiem myszy nowy klucz w drzewie, wybierz opcję **Zmień nazwę**, a następnie wprowadź nazwę aplikacji.

1. Kliknij prawym przyciskiem myszy nowy klucz, drzewa i wybierz **New** > **wartość ciągu**.

1. Zmień nazwę nowej wartości z **nowa wartość #1** do `debugger`.

1. Kliknij prawym przyciskiem myszy **debugera** i wybierz **Modyfikuj**.

   ![Ciąg, okno dialogowe Edytowanie](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "okno dialogowe Edytowanie ciągu")

1. W **Edytowanie ciągu** okno dialogowe, typ `vsjitdebugger.exe` w **dane wartości** , a następnie wybierz **OK**.

   ![Debuger automatycznego uruchamiania wpis w regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "debugera automatycznego uruchamiania wpis w regedit.exe")

##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Debugowanie wielu procesów
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Podczas debugowania aplikacji za pomocą wielu procesów, polecenia debugera powodująca niezgodność, przechodzenia krok po kroku i kontynuowanie wpływają na wszystkie procesy domyślnie. Na przykład gdy proces jest zawieszony w punkcie przerwania, wykonanie wszystkich innych procesów jest również zawieszone. Można zmienić to zachowanie domyślne, aby uzyskać większą kontrolę nad obiektami docelowymi poleceń wykonywania.

**Aby określić, czy wszystkie procesy są wstrzymywane, gdy jeden proces zostanie przerwany:**

- W obszarze **narzędzia** (lub **debugowania**) > **opcje** > **debugowania** > **ogólne**, zaznacz lub wyczyść **Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** pole wyboru.

###  <a name="BKMK_Break__step__and_continue_commands"></a> BREAK, step and Kontynuuj

W poniższej tabeli przedstawiono zachowania debugowania polecenia, kiedy **Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** pole wyboru jest zaznaczenia lub usunięcia zaznaczenia:

|**Polecenie**|Wybrane|Niezaznaczone|
|-|-|-|
|**Debugowanie**  > **Przerwij wszystko**|Wszystkie procesy zostaną przerwane.|Wszystkie procesy zostaną przerwane.|
|**Debugowanie** > **kontynuować**|Wszystkie procesy są wznawiane.|Wszystkie wstrzymane procesy wznawiają działanie.|
|**Debugowanie** > **Wkrocz**, **Przekrocz**, lub **Wyjdź**|Wszystkie procesy trwają postępem aktualnego procesu. <br />Następnie wszystkie procesy zostaną przerwane.|Kroki bieżącego procesu. <br />Wstrzymane procesy wznawiają działanie. <br />Działające procesy kontynuują działanie.|
|**Debugowanie** > **Wkrocz do bieżącego procesu**, **Przekrocz bieżący proces**, lub **Wyjdź z bieżącego procesu**|Brak|Kroki bieżącego procesu.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|
|Okno źródłowe **punktu przerwania**|Wszystkie procesy zostaną przerwane.|Tylko proces okna źródła przerywa.|
|Okno źródłowe **Uruchom do kursora**<br />Okno źródłowe musi znajdować się w bieżącym procesie.|Wszystkie procesy działają, podczas gdy procesu okna źródła działa do kursora, a następnie przerywa.<br />Następnie inne procesy zostaną przerwane.|Proces okna źródłowego działa do kursora.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|
|**Procesy** okna > **Przerwij proces**|Brak|Wybrany proces przerywa działanie.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|
|**Procesy** okna > **Kontynuuj proces**|Brak|Wybrany proces wznawia działanie.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|

###  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Znajdowanie symboli i źródłowych plików (.pdb)
Aby nawigować po kodzie źródłowym procesu, debuger musi mieć dostęp do plików źródłowych i plików symboli. Aby uzyskać więcej informacji, zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Jeśli nie masz dostępu plików dla procesu, można nawigować przy użyciu **dezasemblacji** okna. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md).

###  <a name="BKMK_Switch_between_processes"></a> Przełączać się między procesami

Podczas debugowania, ale tylko jeden proces jest aktywny w debugerze w danym momencie, można dołączyć wiele procesów. Można ustawić aktywny lub *bieżącego* procesu w **Lokalizacja debugowania** narzędzi lub **procesy** okna. Aby przełączyć się między procesami, oba procesy muszą być w trybie przerwania.

**Aby ustawić bieżący proces z poziomu paska narzędzi debugowania lokalizacji:**

1. Aby otworzyć **Lokalizacja debugowania** narzędzi, wybierz opcję **widoku** > **pasków narzędzi** > **Lokalizacja debugowania**.

1. Podczas debugowania na **Lokalizacja debugowania** narzędzi, wybierz proces, którego chcesz ustawić jako bieżący proces z **procesu** listy rozwijanej.

   ![Przełączanie się między procesami](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Aby ustawić bieżący proces z okna procesów:**

1. Aby otworzyć **procesy** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **procesy**.

1. W **procesy** okna, bieżący proces jest oznaczona żółtą strzałką. Kliknij dwukrotnie procesu, który chcesz ustawić jako bieżący proces.

   ![Okno procesów](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Przełączanie do procesu ustawia go jako bieżący proces na potrzeby debugowania. Okna debugera wyświetlają stan dla bieżącego procesu i polecenia dotyczą tylko bieżącego procesu.

## <a name="stop-debugging-with-multiple-processes"></a>Zatrzymaj debugowanie z wieloma procesami

Domyślnie po wybraniu **debugowania** > **Zatrzymaj debugowanie**, debuger kończy pracę lub odłącza się od wszystkich procesów.

- Jeśli bieżący proces został uruchomiony w debugerze, ten proces jest kończona.

- Jeśli Debuger jest dołączony do bieżącego procesu, debuger odłączy się od procesu i pozostawia proces uruchomiony.

Jeśli uruchomisz debugowanie procesu z rozwiązania programu Visual Studio, następnie dołącz do innego procesu, który jest już uruchomiony, a następnie wybierz **Zatrzymaj debugowanie**, zakończenia sesji debugowania. Proces, który został uruchomiony w programie Visual Studio kończy się, gdy jest uruchomiony proces, który jest dołączony do.

Aby kontrolować sposób, **Zatrzymaj debugowanie** ma wpływ na poszczególne procesy w **procesy** okna, kliknij prawym przyciskiem myszy proces, a następnie zaznacz lub wyczyść **Odłącz po zatrzymaniu debugowania** pole wyboru.

>[!NOTE]
>**Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu** opcja debugera nie wpływa na zatrzymywanie, kończenie lub odłączanie od procesów.

### <a name="stop-terminate-and-detach-commands"></a>Zatrzymaj, kończenia i odłączania poleceń

W poniższej tabeli przedstawiono zachowania zatrzymanie debugera, kończenia i odłączania poleceń z wieloma procesami:

|**Polecenie**|**Opis**|
|-|-|
|**Debugowanie** > **Zatrzymaj debugowanie**|Jeśli zachowanie nie zostało zmienione w **procesów** , zostaną zakończone procesy uruchomione przez debugera, a dołączone procesy są odłączone.|
|**Debugowanie** > **Zakończ wszystkie**|Wszystkie procesy zostaną zakończone.|
|**Debugowanie** > **Odłącz wszystko**|Debuger odłączy się od wszystkich procesów.|
|**Procesy** okna > **Odłącz proces**|Debuger odłączy się od wybranych procesów.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|
|**Procesy** okna > **zakończenie procesu**|Wybrany proces zostanie zakończona.<br />Inne procesy utrzymują istniejący stan (zawieszone lub uruchomione).|
|**Procesy** okna > **Odłącz po zatrzymaniu debugowania**|Jeśli zaznaczone, **debugowania** > **Zatrzymaj debugowanie** odłączy się od wybranych procesów. <br />Jeśli nie jest zaznaczone, **debugowania** > **Zatrzymaj debugowanie** kończy wybranego procesu. |

## <a name="see-also"></a>Zobacz także

- [Określanie plików symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Debugowanie Just In Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)