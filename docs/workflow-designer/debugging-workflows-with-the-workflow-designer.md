---
title: Debugowanie przepływów pracy za pomocą Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b06ee7101dcb6b227f8e7f0228730fb0668695b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998849"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>Debugowanie przepływów pracy za pomocą projektanta przepływów pracy

**Projektanta przepływów pracy** umożliwia debugowanie przepływów pracy i działania niestandardowe. Ten proces i zachowania są podobne do, domyślny debuger programu Visual Studio.

## <a name="invoke-the-workflow-debugger"></a>Wywoływanie debugera przepływu pracy

Ogólnie rzecz biorąc należy debugowania przepływów pracy, tak samo, jak można debugować programy napisane w różnych językach programowania Visual Studio. Można uruchomić debugera przepływu pracy, w następujący sposób:

- Wybierz **dołączyć do procesu** na **debugowania** menu, aby wybrać uruchomionego procesu hosta dla wystąpienia przepływu pracy. Ta procedura jest taka sama jak dołączanie do procesu hosta w kodzie zarządzanym.

- Naciśnij klawisz **F5** uruchomione wystąpienie przepływu pracy lub będą nadal działać po został trafiony punkt przerwania.

- Użyj zdalnego debugowania. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [jak: Włączanie debugowania zdalnego](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury, która jest hostowana na maszynie z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, chyba że program Visual Studio jest zainstalowany na komputerze zdalnym lub obiekt docelowy dla aplikacji przepływu pracy jest zmieniana na  **Dowolny procesor CPU**.

## <a name="step-through-code"></a>Przejść przez kod

- **Krok**: Krok po kroku do działania, naciskając klawisz **F11**. Debuger nie wchodzi do dowolnej procedury obsługi, który jest zdefiniowany. Jeśli żadna procedura obsługi nie jest zdefiniowany, Przekrocz działania lub za pomocą złożonych działań, które zawierają inne działania, wkroczenia do pierwszego działania wykonywania.

- **Wyjdź:** Wyjdź z działania, naciskając klawisz **Shift**+**F11**. Przechodzenie krok po kroku, poza działanie uruchamia bieżące działanie i jego element równorzędny działania ukończone. Debuger jest następnie przerywa w nadrzędnego bieżącego działania. Przy przechodzeniu od obsługi kodu, debuger przerywa na działaniu, z którą jest skojarzony program obsługi.

- **Przekrocz nad**: Przekrocz nad działania, naciskając klawisz **F10**. Przy przechodzeniu przez działanie złożone, debuger przerywa na pierwszy element podrzędny wykonywalnego działanie złożone. Przy przechodzeniu przez inne niż złożone, takich jak <xref:System.Activities.Statements.Assign> działania, debuger wykonuje działanie i jego związanymi obsługami i przerw na następne działanie. Jeśli działania, który jest wykonywany jest ostatniego działania podrzędne działania złożonego, następnie, po wykonaniu debuger przerywa na działanie nadrzędne.

## <a name="debug-with-f5"></a>Debugowanie za pomocą F5

Jeśli tworzysz aplikację konsoli przepływu pracy, po prostu nacisnąć skrót **F5** aby rozpocząć debugowanie w aplikacji sieci Web i przepływ pracy. Jeśli tworzysz biblioteki działań samodzielnie, należy określić aplikację hosta wykonywalny jako projekt startowy. Aby ustawić projekt startowy w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, hosta i wybierz **Ustaw jako projekt startowy**.