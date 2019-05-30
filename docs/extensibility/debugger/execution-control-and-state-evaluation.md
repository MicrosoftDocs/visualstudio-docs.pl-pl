---
title: Kontrola wykonywania i ocena stanu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bda531e94bdea07ee37eed2b0b79e6f0667ba28e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315234"
---
# <a name="execution-control-and-state-evaluation"></a>Wykonanie kontroli i stan oceny
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jako przechodzenie krok po kroku do funkcji, zatrzymanie w punktach przerwania i kontynuowanie wykonywania. Podstawy debugowania programu Visual Studio do jego kontrolki wykonywania zdarzeń wysyłane między składnikami debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Program kontroli](../../extensibility/debugger/program-control.md) następujących procedur, które występują na poziomie program wyświetla: ustawienie następnej instrukcji, wykonywanie, wykonywanie krokowe, kontynuowanie, zawieszanie i wznawianie.

 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md) definiuje granicę i oczekujące na typy punktów przerwania, które obsługuje program Visual Studio.

 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md) w tym artykule omówiono implementacji metod, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie break.

 [Obliczanie wyrażenia](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) wyjaśnia, jak aparat debugowania (DE), Szacowanie wyrażeń (EE) i Menedżer debugowania sesji są zaangażowane podczas analizowania i obliczania wyrażenia wprowadzane do jednego z okien środowiska IDE.

 [Kontrolowanie zdarzeń](../../extensibility/debugger/control-events.md) w tym artykule omówiono interfejsu używane do wysyłania zdarzeń podczas kontrolowanego wykonywanie programu.