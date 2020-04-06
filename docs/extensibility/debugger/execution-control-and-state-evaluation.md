---
title: Kontrola wykonania i ocena państwa | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738753"
---
# <a name="execution-control-and-state-evaluation"></a>Kontrola wykonania i ocena stanu
Debugowanie aplikacji wymaga zaimplementowania takich funkcji kontroli wykonywania, jak przechodzenie do funkcji, zatrzymywanie w punktach przerwania i ciągłe wykonywanie. Debugowanie programu Visual Studio opiera swoją kontrolę nad wykonywaniem zdarzeń wysyłanych między składnikami debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Sterowanie programem](../../extensibility/debugger/program-control.md) Wyświetla listę następujących procedur, które występują na poziomie programu: ustawianie następnej instrukcji, wykonywanie, przechodzenie krok po kroku, kontynuowanie, zawieszanie i wznawianie.

 [Metody związane z punktem przerwania](../../extensibility/debugger/breakpoint-related-methods.md) Definiuje powiązane i oczekujące typy punktów przerwania, które obsługuje program Visual Studio.

 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md) W tym artykule omówiono implementacji metod, które umożliwiają wyświetlanie ramki stosu stosu wywołań w trybie przerwania.

 [Ocena wyrażenia](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) W tym artykule wyjaśniono, jak aparat debugowania (DE), ocena wyrażeń (EE) i menedżer debugowania sesji są zaangażowane w analizowanie i ocenę wyrażenia wprowadzone do jednego z okien IDE.

 [Sterowanie zdarzeniami](../../extensibility/debugger/control-events.md) W tym artykule omówiono interfejs używany do wysyłania zdarzeń podczas kontrolowanego wykonywania programu.
