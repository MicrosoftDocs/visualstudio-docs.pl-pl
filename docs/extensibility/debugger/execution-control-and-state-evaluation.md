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
ms.openlocfilehash: e71fb57a4890c29652473338391a0f7181d19ac0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010418"
---
# <a name="execution-control-and-state-evaluation"></a>Wykonanie kontroli i stan oceny
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jako przechodzenie krok po kroku do funkcji, zatrzymanie w punktach przerwania i kontynuowanie wykonywania. Podstawy debugowania programu Visual Studio do jego kontrolki wykonywania zdarzeń wysyłane między składnikami debugera.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kontrola programu](../../extensibility/debugger/program-control.md)  
 Wyświetla listę następujących procedur, które występują na poziomie programu: ustawienie następnej instrukcji, wykonywanie, wykonywanie krokowe, kontynuowanie, zawieszanie i wznawianie.  
  
 [Metody dotyczące punktu przerwania](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiuje granicę i oczekujące na typy punktów przerwania, które obsługuje program Visual Studio.  
  
 [Ocena stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md)  
 W tym artykule omówiono implementacji metod, które umożliwiają wyświetlanie ramek stosu stosu wywołań w trybie break.  
  
 [Szacowanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Przedstawia sposób aparat debugowania (DE) Menedżer wyrażenie oceny (EE) i sesja debugowania są zaangażowane w analizę i obliczania wyrażenia wprowadzane do jednego z okien środowiska IDE.  
  
 [Zdarzenia obiektu Controls](../../extensibility/debugger/control-events.md)  
 W tym artykule omówiono interfejsu używane do wysyłania zdarzeń podczas kontrolowanego wykonywanie programu.