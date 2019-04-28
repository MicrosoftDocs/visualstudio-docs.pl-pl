---
title: Program kontrolki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46e41cacafa2251c96ec7a97899b81034f455d6f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414212"
---
# <a name="program-control"></a>Kontrola programu
W programie Visual Studio debugowanie wszystkich następujących przechodzenie krok po kroku i kontynuowanie procedury wykonywane na poziomie programu:

- Oznacza to, że ustawienie następnej instrukcji, ustawienia komputera do następnej instrukcji do wykonania w środowisku określonego ramki

- Wykonywanie, oznacza to, w dalszym ciągu wyjście z trybu przechodzenia krok po kroku

- Przechodzenie do następnej instrukcji

- Kontynuując bieżący tryb wykonywania krokowego

- Zawieszanie wątków zawarte przez program

- Wznawianie wątków zawarte przez program

> [!NOTE]
> Wyświetlanie stosu wywołań jest wdrażany na poziomie wątku. Aby wyliczyć informacji o ramce, podczas wyświetlania stos wywołań dla wątku, należy zaimplementować wszystkie metody [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfejsu.

## <a name="methods-of-program-control"></a>Metody kontroli programu
 W poniższej tabeli przedstawiono metody [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) musi zostać wdrożone dla aparatu debugowania minimalny zestaw funkcjonalności (DE) i kontrola wykonywania.

|Metoda|Opis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Nadal uruchomione wszystkie wątki zawarte przez program w stanie zatrzymania. Wymagane do wykonywania kontroli.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Nadal uruchomione wszystkie wątki zawarte przez program w stanie zatrzymania. Wymagane do wykonywania kontroli.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok dla danego wątku. Nadal uruchomione inne wątki zawartych w programie. Wymagane do wykonywania kontroli.|

 W przypadku programów wielowątkowych, należy także zaimplementować [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody i wszystkie metody [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfejsu.

## <a name="see-also"></a>Zobacz także
- [Wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)