---
title: Kontrolka programu | Microsoft Docs
description: Zapoznaj się z procedurami w programie Visual Studio debugowaniem, które występują na poziomie programu, takich jak wykonywanie, krokowe, kontynuowanie i wstrzymywanie/wznawianie wątków.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 640b09620022d17fd6b7c8758f1dec4f9a3936eb
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606531"
---
# <a name="program-control"></a>Kontrola programu
W przypadku debugowania programu Visual Studio wszystkie następujące procedury krok po kroku są wykonywane na poziomie programu:

- Ustawienie następnej instrukcji, czyli ustawienie komputera na następną instrukcję do wykonania w określonym środowisku klatek

- Wykonywanie, czyli kontynuowanie wyjścia z trybu krokowe

- Przechodzenie do następnej instrukcji

- Kontynuowanie pracy z bieżącym trybem krokowe

- Wstrzymywanie wątków zawartych w programie

- Wznawianie wątków zawartych w programie

> [!NOTE]
> Wyświetlanie stosu wywołań jest implementowane na poziomie wątku. Aby wyliczyć informacje o ramce podczas wyświetlania stosu wywołań dla wątku, należy zaimplementować wszystkie metody interfejsu [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .

## <a name="methods-of-program-control"></a>Metody sterowania programem
 W poniższej tabeli przedstawiono metody [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , które muszą być zaimplementowane dla minimalnej funkcjonalnego aparatu debugowania (de) i kontroli wykonywania.

|Metoda|Opis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Kontynuuje działanie wszystkich wątków zawartych w programie ze stanu zatrzymanego. Wymagane na potrzeby kontroli wykonywania.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Kontynuuje działanie wszystkich wątków zawartych w programie ze stanu zatrzymanego. Wymagane na potrzeby kontroli wykonywania.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok w danym wątku. Kontynuuje działanie wszystkich innych wątków zawartych w programie. Wymagane na potrzeby kontroli wykonywania.|

 W przypadku programów wielowątkowych należy również zaimplementować metodę [IDebugProgram2:: EnumThreads —](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) i wszystkie metody interfejsu [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .

## <a name="see-also"></a>Zobacz także
- [Kontrola wykonywania i Ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
