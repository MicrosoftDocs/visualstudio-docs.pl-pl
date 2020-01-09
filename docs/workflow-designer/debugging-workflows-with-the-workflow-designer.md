---
title: Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8de1ff9875d175c956a45b87d459d0943e783c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597064"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Debuguj przepływy pracy za pomocą Projektant przepływu pracy

**Projektant przepływu pracy** zapewnia możliwość debugowania przepływów pracy i działań niestandardowych. Proces i zachowanie są podobne do tego, że jest to domyślny debuger programu Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Wywoływanie debugera przepływu pracy

Ogólnie rzecz biorąc, można debugować przepływy pracy, podobnie jak debugowanie programów utworzonych w innych językach programowania programu Visual Studio. Debuger przepływu pracy można uruchomić w następujący sposób:

- Wybierz opcję **Dołącz do procesu** w menu **Debuguj** , aby wybrać uruchomiony proces hosta dla wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

- Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub będą nadal działać po został trafiony punkt przerwania.

- Używaj zdalnego debugowania. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [How to: Enable Remote Debug](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Jeśli aplikacja przepływu pracy jest ukierunkowana na architekturę x86 i jest hostowana na maszynie z 64-bitowym systemem operacyjnym, debugowanie zdalne nie będzie działać, jeśli program Visual Studio nie jest zainstalowany na maszynie zdalnej lub obiekt docelowy dla aplikacji przepływu pracy zostanie zmieniony na **dowolny procesor**.

## <a name="step-through-code"></a>Przejść przez kod

- **Krok w**: Wkrocz do działania przez naciśnięcie klawisza **F11**. Debuger nie wchodzi do dowolnej procedury obsługi, który jest zdefiniowany. Jeśli żadna procedura obsługi nie jest zdefiniowany, Przekrocz działania lub za pomocą złożonych działań, które zawierają inne działania, wkroczenia do pierwszego działania wykonywania.

- **Wyjdź:** Wyjdź z działania, naciskając klawisz **Shift**+**F11**. Przechodzenie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania ukończone. Debuger jest następnie przerywa w nadrzędnego bieżącego działania. Przy przechodzeniu od obsługi kodu, debuger przerywa na działaniu, z którą jest skojarzony program obsługi.

- Przechodzenie **krok**po kroku: przekroczenie działania przez naciśnięcie klawisza **F10**. Podczas wykonywania stopniowego działania złożonego debuger przerwie się w pierwszym pliku podrzędnym działania złożonego. Podczas wykonywania stopniowego wstawiania niezłożonego, takiego jak działanie <xref:System.Activities.Statements.Assign>, debuger wykonuje działanie i skojarzone z nim procedury obsługi oraz przerwie w następnym działaniu. Jeśli wykonywane działanie jest ostatnim działaniem podrzędnym działania złożonego, po wykonaniu debuger przerwie w działaniu nadrzędnym.

## <a name="debug-with-f5"></a>Debuguj za pomocą klawisza F5

W przypadku kompilowania aplikacji konsolowej przepływu pracy wystarczy nacisnąć klawisz **F5** , aby rozpocząć debugowanie do aplikacji i przepływu pracy. Jeśli tworzysz bibliotekę działań samodzielnie, musisz określić wykonywalną aplikację hosta jako projekt startowy. Aby ustawić projekt startowy w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu hosta i wybierz pozycję **Ustaw jako projekt startowy**.
