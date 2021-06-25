---
title: Tryby operacyjne | Microsoft Docs
description: Poznaj trzy tryby, w których może działać idee, czyli tryb projektowania, tryb uruchamiania i tryb przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899111"
---
# <a name="operational-modes"></a>Tryby operacyjne
Istnieją trzy tryby, w których może działać idee, w następujący sposób:

- [Tryb projektowania](#vsconoperationalmodesanchor1)

- [Tryb uruchamiania](#vsconoperationalmodesanchor2)

- [Tryb przerwania](#vsconoperationalmodesanchor3)

  Sposób, w jaki niestandardowy aparat debugowania przechodzi między tymi trybami, jest decyzją implementacji, która wymaga znajomości mechanizmów przejścia. De może lub nie może bezpośrednio zaimplementować tych trybów. Te tryby to tak naprawdę tryby debugowania pakietów, które są przełączane na podstawie akcji użytkownika lub zdarzeń z DE. Na przykład przejście z trybu uruchamiania do trybu przerwania jest instigated przez zdarzenie zatrzymania z DE. Przejście z przerwania do trybu uruchamiania lub trybu kroku jest instigated przez użytkownika wykonującego operacje, takie jak Krok lub Wykonanie. Aby uzyskać więcej informacji na temat przejść DE, zobacz [Control of execution (Kontrola wykonywania).](../../extensibility/debugger/control-of-execution.md)

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Tryb projektowania
 Tryb projektowania to stan Visual Studio debugowania, w którym można ustawić funkcje debugowania w aplikacji.

 Tylko kilka funkcji debugowania jest używanych w trybie projektowania. Deweloper może ustawić punkty przerwania lub utworzyć wyrażenia wyrażeń kontrolnych. De nigdy nie jest ładowany lub wywoływany, gdy ide jest w trybie projektowania. Interakcja z DE odbywa się tylko w trybach uruchamiania i przerwania.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Tryb uruchamiania
 Tryb uruchamiania występuje, gdy program jest uruchamiany w sesji debugowania w idee. Aplikacja jest uruchamiana do momentu zakończenia, do momentu trafienia punktu przerwania lub zgłoszenia wyjątku. Gdy aplikacja zostanie uruchomiona do zakończenia, de przechodzi do trybu projektowania. Gdy punkt przerwania zostanie trafiony lub zostanie zgłoszony wyjątek, de przechodzi do trybu przerwania.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Tryb przerwania
 Tryb przerwania występuje po wstrzymaniu wykonywania programu debugowania. Tryb przerwania oferuje deweloperowi migawkę aplikacji w momencie przerwania i umożliwia deweloperowi analizowanie stanu aplikacji i zmianę sposobu jej działania. Deweloper może wyświetlać i edytować kod, badać lub modyfikować dane, ponownie uruchamiać aplikację, kończyć wykonywanie lub kontynuować wykonywanie od tego samego punktu.

 Tryb przerwania jest wprowadzany, gdy de wysyła zdarzenie synchronicznego zatrzymywania. Zdarzenia synchronicznego zatrzymywania, nazywane również zdarzeniami zatrzymywania, powiadamiają menedżera debugowania sesji (SDM) i środowiska IDE, że debugowana aplikacja zatrzymała wykonywanie kodu. Interfejsy [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [i IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) są przykładami zatrzymywania zdarzeń.

 Zatrzymywanie zdarzeń jest kontynuowane przez wywołanie jednej z następujących metod, które przejmują debuger z trybu przerwania do trybu uruchomienia lub kroku:

- [Wykonaj polecenie](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Krok](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Kontynuuj](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Tryb kroku
 Tryb kroku występuje, gdy program wchodzi do następnego wiersza kodu, do, przez lub z funkcji. Krok jest wykonywany przez wywołanie metody [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Ta metoda wymaga `DWORD` s, aby określić [wyliczenia STEPUNIT](../../extensibility/debugger/reference/stepunit.md) i [STEPKIND](../../extensibility/debugger/reference/stepkind.md) jako parametry wejściowe.

 Gdy program pomyślnie przechodzi do następnego wiersza kodu lub do funkcji albo jest uruchamiany do kursora lub do ustawionego punktu przerwania, de automatycznie przechodzi z powrotem do trybu przerwania.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania](../../extensibility/debugger/control-of-execution.md)
