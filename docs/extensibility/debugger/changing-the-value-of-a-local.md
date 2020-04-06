---
title: Zmiana wartości lokalnego | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739135"
---
# <a name="change-the-value-of-a-local"></a>Zmienianie wartości lokalnego
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Gdy nowa wartość jest wpisywany w polu wartości **zmiennych** okna, pakiet debugowania przekazuje ciąg, jak wpisane, do oceniającego wyrażenie (EE). EE ocenia ten ciąg, który może zawierać wartość prostą lub wyrażenie i przechowuje wynikową wartość w skojarzonym lokalnym.

 Jest to przegląd procesu zmiany wartości lokalnego:

1. Po wprowadzeniu przez użytkownika nowej wartości program Visual Studio wywołuje [technologię SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) na obiekcie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) skojarzonym z lokalnym.

2. Metoda `IDebugProperty2::SetValueAsString` wykonuje następujące zadania:

   1. Ocenia ciąg, aby uzyskać wartość.

   2. Wiąże skojarzony [obiekt IDebugField](../../extensibility/debugger/reference/idebugfield.md) w celu uzyskania obiektu [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Konwertuje wartość na serię bajtów.

   4. Wywołuje [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) umieścić bajty wartości w pamięci, dzięki czemu program debugowany można uzyskać do nich dostęp.

3. Visual Studio odświeża wyświetlanie **lokalnych** (zobacz [Wyświetlanie lokalnych dla](../../extensibility/debugger/displaying-locals.md) szczegółów).

   Ta procedura jest również używana do zmiany wartości zmiennej w oknie **Czujka,** z tą różnicą, że jest to `IDebugProperty2` obiekt skojarzony z wartością lokalną, która jest używana zamiast `IDebugProperty2` obiektu skojarzonego z samym lokalem lokalnym.

## <a name="in-this-section"></a>W tej sekcji
 [Przykładowa implementacja zmieniających się wartości](../../extensibility/debugger/sample-implementation-of-changing-values.md) Używa przykładu MyCEE, aby przejść przez proces zmiany wartości.

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wyświetlanie lokalnych](../../extensibility/debugger/displaying-locals.md)
