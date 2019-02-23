---
title: Kontrola wykonywania i ocena stanu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd04cfa1e271f94f1b37aa0fbd62e9b846d9a70d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714689"
---
# <a name="execution-control-and-state-evaluation"></a>Wykonanie kontroli i stan oceny
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jako przechodzenie krok po kroku do funkcji, zatrzymanie w punktach przerwania i kontynuowanie wykonywania. Podstawy debugowania programu Visual Studio do jego kontrolki wykonywania zdarzeń wysyłane między składnikami debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Program kontroli](../../extensibility/debugger/program-control.md) następujących procedur, które występują na poziomie program wyświetla: ustawienie następnej instrukcji, wykonywanie, wykonywanie krokowe, kontynuowanie, zawieszanie i wznawianie.

 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md) definiuje granicę i oczekujące na typy punktów przerwania, które obsługuje program Visual Studio.

 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md) w tym artykule omówiono implementacji metod, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie break.

 [Obliczanie wyrażenia](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) wyjaśnia, jak aparat debugowania (DE), Szacowanie wyrażeń (EE) i Menedżer debugowania sesji są zaangażowane podczas analizowania i obliczania wyrażenia wprowadzane do jednego z okien środowiska IDE.

 [Kontrolowanie zdarzeń](../../extensibility/debugger/control-events.md) w tym artykule omówiono interfejsu używane do wysyłania zdarzeń podczas kontrolowanego wykonywanie programu.