---
title: 'Instrukcje: ustawianie punktów przerwania w przepływach pracy (starsza wersja) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603593"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Instrukcje: ustawianie punktów przerwania w przepływach pracy (starsza wersja)
W tym temacie opisano sposób ustawiania punktów przerwania w programie [!INCLUDE[wf](../includes/wf-md.md)] Applications Build przy użyciu starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)], gdy aplikacja [!INCLUDE[wf2](../includes/wf2-md.md)] musi kierować [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 W przypadku używania starszej [!INCLUDE[wfd2](../includes/wfd2-md.md)] w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] do kompilowania aplikacji [!INCLUDE[wf2](../includes/wf2-md.md)], można ustawić punkty przerwania C# w i Visual Basic kod, jak w programie Visual Studio. Zgodnie z oczekiwaniami wykonywanie przepływu pracy zostaje zatrzymane w każdym ustawionym punkcie przerwania.

 Punkt przerwania ma trzy stany: *oczekujący*, *powiązany*i *błąd*. Gdy ustawisz punkt przerwania, jest on w stanie oczekiwania i jest reprezentowany przez nieprawidłową czerwoną ikonę. Po załadowaniu typu przepływu pracy środowisko uruchomieniowe zostanie powiązane i jest reprezentowane przez pełną czerwoną ikonę. Jeśli określisz niepoprawny format dla punktu przerwania, jak z nieprawidłową nazwą działania, pojawi się okno błędu. Punkt przerwania jest nadal dodawany do okna punktu przerwania, ale jest oznaczony małą "x".

 Punkty przerwania można ustawić dla działania na powierzchni projektowej przepływu pracy w następujący sposób:

- Kliknij prawym przyciskiem myszy działanie i wybierz pozycję **punkt przerwania \ Wstaw punkt przerwania**.

- Wybierz działanie i naciśnij klawisz F9.

- Wybierz pozycję **nowy punkt przerwania** z menu **Debuguj** .

     Można również użyć tej opcji, aby ustawić nowy punkt przerwania podczas debugowania, gdy debuger zatrzyma się w punkcie przerwania.

    > [!NOTE]
    > Ustawianie punktów przerwania dla wywołanych przepływów pracy nie jest obsługiwane.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Aby ustawić punkt przerwania przy użyciu opcji nowy punkt przerwania w menu Debuguj

1. W menu **Debuguj** wybierz pozycję **nowy punkt przerwania**.

2. Kliknij przycisk **Przerwij w funkcji**.

     Zostanie otwarte okno dialogowe **nowy punkt przerwania** .

3. Określ nazwę działania w polu tekstowym **funkcji** , używając następującej składni: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > Opcjonalnie zamiast używać nazwy działania w polu tekstowym **Funkcja** , można ustawić punkt przerwania, określając ścieżkę bezwzględną działania przepływu pracy. Załóżmy na przykład, że masz rozwiązanie przepływu pracy o nazwie **WorkflowConsoleApplication1** i przepływ pracy w rozwiązaniu o nazwie **Workflow1** , który używa działania o nazwie **Delay1**. Możesz użyć nazwy działania **Delay1** lub określić ścieżkę jako **Delay1: WorkflowConsoleApplication1. Workflow1** lub **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}** .

4. Zaznacz pole wyboru **Użyj IntelliSense** , aby sprawdzić nazwę funkcji.

     Jeśli to pole wyboru nie jest zaznaczone, nie jest przeprowadzana weryfikacja nazw punktów przerwania.

5. Wybierz pozycję **przepływ pracy** z listy **Język** .

6. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 [Debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md) [wywoływanie debugera programu Visual Studio dla Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)