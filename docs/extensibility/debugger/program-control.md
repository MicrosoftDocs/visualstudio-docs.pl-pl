---
title: Program kontrolki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a19769925689ae8131c6443ab80ccefeefa82290
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351442"
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