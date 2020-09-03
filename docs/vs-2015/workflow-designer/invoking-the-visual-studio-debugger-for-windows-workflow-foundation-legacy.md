---
title: Wywoływanie debugera dla Windows Workflow Foundation (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658978"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)
W tym temacie opisano, jak używać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera do debugowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Ogólnie rzecz biorąc, można debugować starsze przepływy pracy, podobnie jak debugowanie programów utworzonych w innych językach programowania programu Visual Studio. Można uruchomić [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debuger dla Windows Workflow Foundation w następujący sposób:

- Wybierz pozycję **Dołącz do procesu** w menu **Debuguj** , aby wybrać uruchomione wystąpienie przepływu pracy z dostępnych procesów.

- Naciśnij klawisz **F5** , aby rozpocząć Uruchamianie wystąpienia przepływu pracy lub kontynuować działanie po trafieniu punktu przerwania.

## <a name="stepping-through-code"></a>Krokowe przechodzenie przez kod
 Debuger obsługuje jedną z najbardziej typowych procedur debugowania, wykonując krok, który wykonuje kod jeden wiersz jednocześnie. Istnieją trzy polecenia umożliwiające przechodzenie przez kod:

- **Krok w**: możesz przejść do działania przy użyciu klawisza **F11**. Debuger kroków do dowolnej zdefiniowanej procedury obsługi. Jeśli nie zdefiniowano programu obsługi, przekroczę działanie lub z działaniami złożonymi, które zawierają inne działania, możesz przejść do pierwszego wykonywanego działania. Przechodzenie do programów obsługi kodu z projektanta nie jest obsługiwane w przypadku następujących działań: **IfElseActivity**, **while**, **ConditionedActivityGroup**i **Replikator**. Aby debugować programy obsługi skojarzone z tymi działaniami, należy umieścić w kodzie jawne punkty przerwania.

- **Wyjdź**: możesz przejść na zewnątrz działania przy użyciu **klawisza Shift-F11**. Wychodzenie z działania powoduje uruchomienie bieżącego działania i wszystkich jego elementów równorzędnych do ukończenia. Debuger następnie przerwie w elemencie nadrzędnym bieżącego działania. Podczas wykonywania kroków z programu obsługi kodu debuger przerwie się w działaniu, z którym jest skojarzona procedura obsługi.

- **Przekroczenie: możesz**przekroczyć działanie, używając klawisza **F10**. Podczas wykonywania kroków w ramach działania złożonego. Debuger jest podzielony na pierwszy plik podrzędny działania złożonego. Podczas wykonywania stopniowego wstawiania niezłożonego, takiego jak działanie **elementu CodeActivity** , debuger wykonuje działanie i skojarzone z nim procedury obsługi oraz przerwanie w następnym działaniu. Jeśli wykonywane działanie jest ostatnim działaniem podrzędnym działania złożonego, po wykonaniu debuger przerwie się w działaniu nadrzędnym.

## <a name="attaching-to-a-process"></a>Dołączanie do procesu
 Aby debugować przepływ pracy przez dołączenie do procesu, wybierz dostępny proces z pola listy **dostępne procesy** w oknie dialogowym **Dołącz do procesu** . Jeśli **automatyczny: kod przepływu pracy** nie jest wyświetlany w polu tekstowym **Dołącz do** , a następnie kliknij przycisk **Wybierz**. W oknie dialogowym **Wybierz typ kodu** kliknij pozycję **Debuguj te typy kodu** i wybierz pozycję **przepływ pracy**. Następnie kliknij przycisk **OK** , a następnie kliknij przycisk **Dołącz**.

## <a name="debugging-with-f5"></a>Debugowanie za pomocą klawisza F5
 Jeśli aplikacja hosta przepływu pracy i plik DLL przepływu pracy znajdują się w różnych projektach programu Visual Studio, na przykład w przypadku korzystania z biblioteki działań przepływu pracy należy ustawić projekt DLL przepływu pracy jako projekt startowy rozwiązania Visual Studio do debugowania przepływu pracy przy użyciu klawisza **F5**. Należy również ustawić ścieżkę do aplikacji hosta w właściwości **Uruchom program zewnętrzny** projektu DLL przepływu pracy.

 Aby ustawić projekt startowy w Eksplorator rozwiązań, kliknij prawym przyciskiem myszy nazwę projektu i wybierz pozycję **Ustaw jako projekt startowy**. Aby ustawić ścieżkę do hosta w właściwości **Uruchom program zewnętrzny** , kliknij dwukrotnie węzeł **Właściwości** projektu przepływu pracy w Eksplorator rozwiązań i wybierz kartę **debugowanie** . W obszarze **Akcja początkowa**wybierz pozycję **Uruchom program zewnętrzny** i wprowadź ścieżkę do pliku. exe, który hostuje przepływ pracy, który ma być debugowany.

 Jeśli aplikacja hosta jest ustawiona jako projekt startowy, tylko debuger programu Visual Studio jest wywoływany do debugowania; [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debuger dla Windows Workflow Foundation nie został wywołany. Jeśli jest używany debuger programu Visual Studio, trafisz tylko punkty przerwania kodu C# lub Visual Basic. punkty przerwania ustawione w Projektancie przepływu pracy nie są trafień. Na przykład punkt przerwania ustawiany w <xref:System.Workflow.Activities.ParallelActivity> działaniu projektanta zostaje osiągnięty [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] , jeśli używany jest debuger dla Windows Workflow Foundation, ale nie w przypadku korzystania z debugera programu Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)