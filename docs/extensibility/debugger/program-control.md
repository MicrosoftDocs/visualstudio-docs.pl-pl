---
title: Program Control | Microsoft Docs
description: Dowiedz się więcej o procedurach Visual Studio debugowania, które występują na poziomie programu, takich jak wykonywanie, krokowe, kontynuowanie i zawieszanie/wznawianie wątków.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900718"
---
# <a name="program-control"></a>Kontrola programu
W Visual Studio debugowania wszystkie następujące procedury krokowe i ciągłe występują na poziomie programu:

- Ustawienie następnej instrukcji, czyli ustawienie na komputerze następnej instrukcji do wykonania w konkretnym środowisku ramowym

- Wykonywanie, czyli kontynuowanie wyjścia z trybu krokowego

- Przechodzenie do następnej instrukcji

- Kontynuowanie bieżącego trybu krokowego

- Zawieszanie wątków zawartych w programie

- Wznawianie wątków zawartych w programie

> [!NOTE]
> Wyświetlanie stosu wywołań jest implementowane na poziomie wątku. Aby wyliczyć informacje o ramce podczas wyświetlania stosu wywołań dla wątku, należy zaimplementować wszystkie metody interfejsu [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metody kontroli programu
 W poniższej tabeli przedstawiono metody [programu IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) które muszą być zaimplementowane dla aparatu debugowania (DE) o minimalnej funkcjonalności i kontroli wykonywania.

|Metoda|Opis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Kontynuuje uruchamianie wszystkich wątków zawartych w programie ze stanu zatrzymania. Wymagane do kontroli wykonywania.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Kontynuuje uruchamianie wszystkich wątków zawartych w programie ze stanu zatrzymania. Wymagane do kontroli wykonywania.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok w danym wątku. Kontynuuje uruchamianie wszystkich innych wątków zawartych w programie. Wymagane do kontroli wykonywania.|

 W przypadku programów wielowątkowych należy również zaimplementować metodę [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) i wszystkie metody interfejsu [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
