---
title: Wywoływanie debugera dla programu Windows Workflow Foundation (starsza wersja) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 34d935288a0091f0c663a4b9881a6e392952fd46
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054163"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera w celu debugowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Ogólnie rzecz biorąc przepływy pracy w starszej wersji debugowania w sytuacji, tak samo, jak można debugować programy napisane w różnych językach programowania Visual Studio. Możesz rozpocząć [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla Windows Workflow Foundation w następujący sposób:

-   Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego wystąpienia przepływu pracy z dostępne procesy.

-   Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub będą nadal działać po został trafiony punkt przerwania.

## <a name="stepping-through-code"></a>Krokowe wykonywanie kodu
 Debuger obsługuje jeden z typowych procedur debugowania wykonywania krokowego, który jest wykonywanie jednego wiersza kodu naraz. Istnieją trzy polecenia do przechodzenia przez kod:

-   **Wkrocz**: możesz wejść do czynności za pomocą **F11**. Debuger nie wchodzi do dowolnej procedury obsługi, który jest zdefiniowany. Jeśli żadna procedura obsługi nie jest zdefiniowany, Przekrocz działania lub za pomocą złożonych działań, które zawierają inne działania, wkroczenia do pierwszego działania wykonywania. Przechodzenie do kodu obsługi przy użyciu projektanta nie jest obsługiwana dla następujących działań: **IfElseActivity**, **Działanie WhileActivity**, **grupy ConditionedActivityGroup**, lub **ReplicatorActivity**. Aby debugować procedury obsługi skojarzone z tych działań, możesz umieścić jawne punkty przerwania w kodzie.

-   **Step Out**: użytkownik może przechodzić korzyści z używania działania **Shift F11**. Przechodzenie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania ukończone. Debuger jest następnie przerywa w nadrzędnego bieżącego działania. Przy przechodzeniu od obsługi kodu, debuger przerywa na działaniu, z którą jest skojarzony program obsługi.

-   **Step Over**: użytkownik może przechodzić przez działanie przy użyciu **F10**. Przy przechodzeniu przez działanie złożone. Debuger przerywa na pierwszy element podrzędny wykonywalnego działanie złożone. Przy przechodzeniu przez inne niż złożone, takich jak **CodeActivity** działania, debuger wykonuje działanie i jego związanymi obsługami i przerw na następne działanie. Jeśli działania, który jest wykonywany jest ostatniego działania podrzędne działania złożonego, następnie po wykonaniu, debuger przerywa na działanie nadrzędne.

## <a name="attaching-to-a-process"></a>Dołączanie do procesu
 Aby debugować przepływ pracy przez dołączenie do procesu, wybierz dostępne procesu z **dostępne procesy** pola listy w **dołączyć do procesu** okno dialogowe. Jeśli **automatyczne: kod przepływu pracy** nie jest wyświetlana w **dołączyć do** tekst pola, a następnie kliknij przycisk **wybierz**. W **Wybieranie typu kodu** okno dialogowe, kliknij przycisk **debugowania tych typów kodu** i wybierz **przepływu pracy**. Następnie kliknij przycisk **OK** i kliknij przycisk **Dołącz**.

## <a name="debugging-with-f5"></a>Debugowanie za pomocą F5
 Jeśli aplikacja hosta przepływu pracy i przepływu pracy DLL znajdują się w różnych projektach programu Visual Studio, na przykład podczas korzystania z biblioteki działania przepływu pracy, musisz ustawić projekt DLL przepływu pracy jako projekt startowy rozwiązania programu Visual Studio do debugowania przepływu pracy za pomocą **F5**. Można również ustawić ścieżkę do aplikacji hosta w projekcie biblioteki DLL przepływu pracy **uruchomienia programu zewnętrznego** właściwości.

 Aby ustawić projekt startowy w Eksploratorze rozwiązań, kliknij prawym przyciskiem myszy nazwę projektu, a następnie wybierz **Ustaw jako projekt startowy**. Aby ustawić ścieżkę do hosta w **uruchomienia programu zewnętrznego** właściwości, kliknij dwukrotnie projektu przepływu pracy **właściwości** węzła w Eksploratorze rozwiązań i wybierz pozycję **debugowania** Karta. W obszarze **Akcja uruchamiania**, wybierz opcję **uruchomienia programu zewnętrznego** i wprowadź ścieżkę do pliku .exe, który jest hostem przepływu pracy, który chcesz debugować.

 Jeśli aplikacja hosta jest ustawiony jako projekt startowy, tylko debugera programu Visual Studio jest wywoływany dla debugowania. [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla programu Windows Workflow Foundation nie jest wywoływany. Jeśli używany jest debugera programu Visual Studio, C# lub tylko punkty przerwania z kodu języka Visual Basic są osiągane; punkty przerwania ustawione w Projektancie przepływu pracy nie są osiągane. Na przykład punkt przerwania, który został ustawiony na <xref:System.Workflow.Activities.ParallelActivity> działania w Projektancie zostanie osiągnięty, jeśli [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla programu Windows Workflow Foundation jest używana, ale nie kiedy używać debugera programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Porady: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)