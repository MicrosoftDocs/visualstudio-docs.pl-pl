---
title: Kontrola programu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738228"
---
# <a name="program-control"></a>Sterowanie programem
W debugowaniu programu Visual Studio na poziomie programu występują wszystkie następujące procedury przechodzenia krokowego i ciągłego:

- Ustawianie następnej instrukcji, czyli ustawianie komputera na następną instrukcję, która ma być wykonana w określonym środowisku ramki

- Wykonywanie, czyli dalsze wyjście z trybu przechodzenia

- Przechodzenie do następnej instrukcji

- Kontynuowanie bieżącego trybu krokowego

- Zawieszanie wątków zawartych w programie

- Wznowienie wątków zawartych w programie

> [!NOTE]
> Wyświetlanie stosu wywołań jest zaimplementowana na poziomie wątku. Aby wyliczyć informacje o ramce podczas wyświetlania stosu wywołań dla wątku, należy zaimplementować wszystkie metody interfejsu [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Metody sterowania programem
 W poniższej tabeli przedstawiono metody [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) które muszą zostać zaimplementowane dla minimalnie funkcjonalnego aparatu debugowania (DE) i kontroli wykonywania.

|Metoda|Opis|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Kontynuuje uruchamianie wszystkich wątków zawartych przez program ze stanu zatrzymanego. Wymagane do kontroli wykonania.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Kontynuuje uruchamianie wszystkich wątków zawartych przez program ze stanu zatrzymanego. Wymagane do kontroli wykonania.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Wykonuje krok na danym wątku. Kontynuuje uruchamianie wszystkich innych wątków zawartych w programie. Wymagane do kontroli wykonania.|

 W przypadku programów wielowątkowych należy również zaimplementować metodę [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) i wszystkie metody interfejsu [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
