---
title: 'Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cec06813890523e604234ccefdbcd7d1de31653
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444186"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)
W tym temacie opisano sposób ustawiania punktów przerwania [!INCLUDE[wf](../includes/wf-md.md)] aplikacje tworzyć zawartość przy użyciu starszego [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] podczas Twojej [!INCLUDE[wf2](../includes/wf2-md.md)] aplikację pod kątem albo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Jeśli używasz starszej wersji [!INCLUDE[wfd2](../includes/wfd2-md.md)] w [!INCLUDE[vs2010](../includes/vs2010-md.md)] tworzenie [!INCLUDE[wf2](../includes/wf2-md.md)] aplikacji, można ustawić punktów przerwania w kodzie języka C# i Visual Basic tak jak w programie Visual Studio. Zgodnie z oczekiwaniami, zatrzyma wykonywanie przepływu pracy, w każdym punkcie przerwania, który został ustawiony.  
  
 Punkt przerwania ma trzy stany: *Oczekujące*, *powiązany*, i *błąd*. Po ustawieniu punktu przerwania jest oczekujące i jest reprezentowana przez pusty czerwoną ikonę. Po załadowaniu szablonu przepływu pracy środowiska uruchomieniowego staje się powiązane i jest reprezentowane przez stałe czerwoną ikonę. Jeśli określisz ma niewłaściwy format dla punktu przerwania, podobnie jak w przypadku nazwy działania, który nie jest prawidłowy, pojawi się okno błędu. Punkt przerwania nadal jest dodawany do okna punkt przerwania, ale jest oznaczony za pomocą małych "x".  
  
 Można ustawić punktów przerwania w ramach działania na powierzchni projektowej przepływu pracy, w następujący sposób:  
  
- Kliknij prawym przyciskiem myszy działanie, a następnie wybierz pozycję **punktu przerwania \ Wstaw punkt przerwania**.  
  
- Wybierz działanie, a następnie naciśnij klawisz F9.  
  
- Wybierz **nowego punktu przerwania** z **debugowania** menu.  
  
     Ta opcja umożliwia również ustawić nowy punkt przerwania podczas debugowania, gdy debuger zatrzymuje się w punkcie przerwania.  
  
    > [!NOTE]
    > Ustawianie punktów przerwania w przepływach pracy, wywoływane jest nieobsługiwana.  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Aby ustawić punkt przerwania przy użyciu opcji nowy punkt przerwania w menu Debugowanie  
  
1. Na **debugowania** menu, wybierz opcję **nowego punktu przerwania**.  
  
2. Kliknij przycisk **Przerwij w funkcji**.  
  
     **Nowego punktu przerwania** zostanie otwarte okno dialogowe.  
  
3. Określ nazwę działania w **funkcja** pola tekstowego przy użyciu następującej składni: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    > Opcjonalnie zamiast przy użyciu nazwy działania w **funkcja** pole tekstowe, można ustawić punktu przerwania, określając ścieżkę bezwzględną działania przepływu pracy. Załóżmy, że masz rozwiązaniu usprawniającym przepływ pracy o nazwie **WorkflowConsoleApplication1** i przepływu pracy w rozwiązaniu o nazwie **Workflow1** używającej działania o nazwie **Delay1**. Możesz użyć nazwy działania **Delay1** lub określ ścieżkę jako **Delay1:WorkflowConsoleApplication1.Workflow1** lub **Delay1:WorkflowConsoleApplication1.Workflow1: { 6614886A-608E-412B-BF98-99FF1559DDDF}**.  
  
4. Wybierz **IntelliSense użyj** pole wyboru, aby sprawdzić nazwę funkcji.  
  
     Jeśli to pole wyboru nie jest zaznaczone, odbywa się nie Weryfikacja nazwy punktu przerwania.  
  
5. Wybierz **przepływu pracy** z **języka** listy.  
  
6. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)   
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)