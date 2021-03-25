---
title: Tryby operacyjne | Microsoft Docs
description: Poznaj trzy tryby, w których może działać środowisko IDE, które są trybem projektowania, trybem uruchamiania i trybem przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 563db644069731c5d74088dadf296933c36b0cc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067845"
---
# <a name="operational-modes"></a>Tryby operacyjne
Istnieją trzy tryby, w których środowisko IDE może działać w następujący sposób:

- [Tryb projektowania](#vsconoperationalmodesanchor1)

- [Tryb uruchamiania](#vsconoperationalmodesanchor2)

- [Tryb przerwania](#vsconoperationalmodesanchor3)

  Sposób przejścia niestandardowego aparatu debugowania między tymi trybami jest decyzja o implementacji, która wymaga zapoznania się z mechanizmami przejściowymi. Wszystkie lub nie mogą bezpośrednio zaimplementować tych trybów. Te tryby są w rzeczywistości trybami pakietu debugowania, które są przełączane na podstawie akcji użytkownika lub zdarzeń z DE. Na przykład przejście z trybu uruchamiania do trybu przerwania jest uruchamiane przez zdarzenie zatrzymania z DE. Przejście z przerwania do trybu uruchamiania lub trybu kroku jest uruchamiane przez użytkownika wykonującego operacje, takie jak Step lub Execute. Aby uzyskać więcej informacji na temat DE Transitions, zobacz [Kontrola wykonania](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Tryb projektowania
 Tryb projektowania jest nieuruchomionym stanem debugowania programu Visual Studio, w tym czasie można ustawić funkcje debugowania w aplikacji.

 Tylko niektóre funkcje debugowania są używane w trybie projektowania. Deweloper może zdecydować się na ustawienie punktów przerwania lub utworzyć wyrażenia czujki. Wartość DE nie jest nigdy ładowana lub wywoływana, gdy IDE jest w trybie projektowania. Interakcja z rozmieszczeniem odbywa się tylko w trybach uruchamiania i przerywania.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Tryb uruchamiania
 Tryb uruchamiania występuje, gdy program jest uruchamiany w sesji debugowania w IDE. Aplikacja działa do momentu zakończenia aż do momentu, aż zostanie osiągnięty punkt przerwania lub zostanie zgłoszony wyjątek. Gdy aplikacja zostanie uruchomiona w celu zakończenia, powoduje przejście do trybu projektowania. Gdy punkt przerwania jest trafień lub zgłaszany jest wyjątek, powoduje to przejście do trybu przerwania.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Tryb przerwania
 Tryb przerwania występuje, gdy wykonywanie programu debugowania jest wstrzymane. Tryb przerwania oferuje deweloperowi migawkę aplikacji w momencie przerwania i umożliwia deweloperowi Analizowanie stanu aplikacji oraz zmianę sposobu działania aplikacji. Deweloper może wyświetlać i edytować kod, testować lub modyfikować dane, ponownie uruchamiać aplikację, kończyć wykonywanie lub kontynuować wykonywanie z tego samego punktu.

 Tryb przerwania jest wprowadzany, gdy ANULUJe zdarzenie zatrzymania synchronicznego. Synchroniczne zdarzenia zatrzymywania, nazywane również zatrzymywaniem zdarzeń, powiadamianie Menedżera debugowania sesji (SDM) i IDE, że debugowana aplikacja zatrzymała wykonywanie kodu. Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) i [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zdarzeń zatrzymywania.

 Zdarzenia zatrzymywania są kontynuowane przez wywołanie jednej z następujących metod, które przechodzą przez debuger z trybu przerwania na uruchamianie lub tryb krokowy:

- [Wykonaj polecenie](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Kontynuuj](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Tryb kroku
 Tryb kroku występuje, gdy program przechodzi do następnego wiersza kodu lub do, do lub z funkcji. Krok jest wykonywany przez wywołanie [kroku](../../extensibility/debugger/reference/idebugprocess3-step.md)metody. Ta metoda wymaga `DWORD` , aby określić wyliczenia [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md) jako parametry wejściowe.

 Gdy program pomyślnie wykona kroki do następnego wiersza kodu lub do funkcji, lub przechodzi do kursora lub do zestawu punktów przerwania, automatycznie przechodzi do trybu przerwania.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)
