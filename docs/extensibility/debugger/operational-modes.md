---
title: Tryby pracy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738277"
---
# <a name="operational-modes"></a>Tryby pracy
Istnieją trzy tryby, w których IDE może działać, w następujący sposób:

- [Tryb projektowania](#vsconoperationalmodesanchor1)

- [Tryb uruchamiania](#vsconoperationalmodesanchor2)

- [Tryb przerwania](#vsconoperationalmodesanchor3)

  Jak niestandardowe przejścia aparatu debugowania (DE) między tymi trybami jest decyzja implementacji, która wymaga zapoznania się z mechanizmami przejścia. DE może lub nie może bezpośrednio wdrożyć te tryby. Te tryby są naprawdę debugowania trybów pakietu, które przełączają się na podstawie akcji użytkownika lub zdarzeń z DE. Na przykład przejście z trybu uruchamiania do trybu przerwania jest instigated przez zatrzymanie zdarzenia z DE. Przejście z przerwy do trybu uruchamiania lub trybu kroku jest instigated przez użytkownika wykonywania operacji, takich jak Krok lub Wykonaj. Aby uzyskać więcej informacji na temat przejść DE, zobacz [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Tryb projektowania
 Tryb projektowania jest stan nieruszny debugowania programu Visual Studio, w którym można ustawić funkcje debugowania w aplikacji.

 Tylko kilka funkcji debugowania są używane w trybie projektowania. Deweloper może wybrać ustawienie punktów przerwania lub tworzenie wyrażeń zegarka. DE nigdy nie jest ładowany lub wywoływane, gdy IDE jest w trybie projektowania. Interakcja z DE odbywa się tylko podczas uruchamiania i przerywania trybów.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Tryb uruchamiania
 Tryb uruchamiania występuje, gdy program jest uruchamiany w sesji debugowania w IDE. Aplikacja jest uruchamiana do zakończenia, dopóki punkt przerwania nie zostanie trafiony lub dopóki nie zostanie zgłoszony wyjątek. Gdy aplikacja jest uruchamiana do zakończenia, DE przechodzi w tryb projektowania. Po trafieniu punktu przerwania lub wyjątek, DE przejścia do trybu przerwania.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Tryb przerwania
 Tryb przerwania występuje, gdy wykonanie programu debugowania jest zawieszony. Tryb przerwania oferuje deweloperowi migawkę aplikacji w momencie przerwy i umożliwia deweloperowi analizowanie stanu aplikacji i zmienianie sposobu działania aplikacji. Deweloper może wyświetlać i edytować kod, badać lub modyfikować dane, ponownie uruchamiać aplikację, kończyć wykonywanie lub kontynuować wykonywanie z tego samego punktu.

 Tryb przerwania jest wprowadzany, gdy DE wysyła synchroniczne zatrzymanie zdarzenia. Synchroniczne zatrzymania zdarzeń, nazywanych również zdarzeniami zatrzymania, powiadamiaj menedżera debugowania sesji (SDM) i IDE, że aplikacja jest debugowana przestała wykonywać kod. Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zatrzymywania zdarzeń.

 Zatrzymywanie zdarzeń są kontynuowane przez wywołanie jednej z następujących metod, które przerywają debuger z trybu przerwania do uruchomienia lub trybu kroku:

- [Realizacja](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Kontynuować](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Tryb krokowy
 Tryb kroku występuje, gdy program przechodzi do następnego wiersza kodu lub do, nad lub z funkcji. Krok jest wykonywany przez wywołanie metody [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Ta metoda `DWORD`wymaga s, które określają wyliczenia [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md) jako parametry wejściowe.

 Gdy program pomyślnie przechodzi do następnego wiersza kodu lub do funkcji lub biegnie do kursora lub ustawionego punktu przerwania, DE automatycznie przechodzi z powrotem do trybu przerwania.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania](../../extensibility/debugger/control-of-execution.md)
