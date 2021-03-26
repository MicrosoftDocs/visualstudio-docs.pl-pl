---
title: Kontrola wykonywania i Ocena stanu | Microsoft Docs
description: Dowiedz się, w jaki sposób debugowanie programu Visual Studio jest podstawą kontroli wykonywania na zdarzeniach przesyłanych między składnikami debugera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 598332ec1e9e1cb270360822ca32792b9a53f5c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096957"
---
# <a name="execution-control-and-state-evaluation"></a>Kontrola wykonywania i Ocena stanu
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jak Krokowe wykonywanie funkcji, zatrzymywanie w punktach przerwania i kontynuowanie wykonywania. Debugowanie programu Visual Studio opiera się na kontroli nad zdarzeniami przesyłanymi między składnikami debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Kontrola programu](../../extensibility/debugger/program-control.md) Wyświetla listę następujących procedur, które pojawiają się na poziomie programu: ustawienie następnej instrukcji, wykonywanie, krokowe, kontynuowanie, wstrzymywanie i wznawianie.

 [Metody związane z punktem przerwania](../../extensibility/debugger/breakpoint-related-methods.md) Definiuje powiązane i oczekujące typy punktów przerwania obsługiwanych przez program Visual Studio.

 [Obliczanie stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md) Omawia implementację metod, które umożliwiają wyświetlanie ramek stosu wywołań stosu w trybie przerwania.

 [Obliczanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Wyjaśnia, w jaki sposób aparat debugowania (DE), obliczanie wyrażeń (EE) i Menedżer debugowania sesji są uwzględniane podczas analizy i oceny wyrażenia wprowadzonego w jednym z okien IDE.

 [Zdarzenia kontroli](../../extensibility/debugger/control-events.md) Omawia interfejs używany do wysyłania zdarzeń podczas kontrolowanego wykonywania programu.
