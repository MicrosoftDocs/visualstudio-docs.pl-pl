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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021fab07cfaf1ec17821a8ef9a33a03f2d6ec714
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560905"
---
# <a name="execution-control-and-state-evaluation"></a>Kontrola wykonywania i Ocena stanu
Debugowanie aplikacji wymaga implementacji takich funkcji kontroli wykonywania jak Krokowe wykonywanie funkcji, zatrzymywanie w punktach przerwania i kontynuowanie wykonywania. Debugowanie programu Visual Studio opiera się na kontroli nad zdarzeniami przesyłanymi między składnikami debugera.

## <a name="in-this-section"></a>W tej sekcji
 [Kontrola programu](../../extensibility/debugger/program-control.md) Wyświetla listę następujących procedur, które pojawiają się na poziomie programu: ustawienie następnej instrukcji, wykonywanie, krokowe, kontynuowanie, wstrzymywanie i wznawianie.

 [Metody związane z punktem przerwania](../../extensibility/debugger/breakpoint-related-methods.md) Definiuje powiązane i oczekujące typy punktów przerwania obsługiwanych przez program Visual Studio.

 [Obliczanie stosu wywołań](../../extensibility/debugger/call-stack-evaluation.md) Omawia implementację metod, które umożliwiają wyświetlanie ramek stosu wywołań stosu w trybie przerwania.

 [Obliczanie wyrażeń](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Wyjaśnia, w jaki sposób aparat debugowania (DE), obliczanie wyrażeń (EE) i Menedżer debugowania sesji są uwzględniane podczas analizy i oceny wyrażenia wprowadzonego w jednym z okien IDE.

 [Zdarzenia kontroli](../../extensibility/debugger/control-events.md) Omawia interfejs używany do wysyłania zdarzeń podczas kontrolowanego wykonywania programu.
