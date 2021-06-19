---
title: Dowiedz się, kto przekazując nieprawidłową wartość parametru | Microsoft Docs
description: Możesz dowiedzieć się, jaki kod wywołują funkcję i jaka wartość parametru jest niepoprawna. Dowiedz się, jak to zrobić za pomocą warunkowego punktu przerwania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2f747e2f92b7817530fe12e14f8f95a9bfbe791
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386920"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak można sprawdzić, kto przekazuje błędną wartość parametru?
## <a name="problem-description"></a>Opis problemu
 Nieprawidłowa wartość parametru jest przekazywana do jednej z moich funkcji. Ta funkcja jest wywoływana z całego miejsca. Jak sprawdzić, co jest przekazywaniem nieprawidłowej wartości?

## <a name="solution"></a>Rozwiązanie

#### <a name="to-resolve-this-problem"></a>Aby rozwiązać ten problem

1. Ustaw punkt przerwania lokalizacji na początku funkcji.

2. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **Warunek.**

3. W **warunku punktu przerwania okno** dialogowe, kliknij przycisk **warunek** pole wyboru. Zobacz [Zaawansowane punkty przerwania.](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)

4. Wprowadź wyrażenie, takie jak , w polu tekstowym, gdzie jest nazwą parametru zawierającego złą wartość i jest przekazywaną do niej złą `Var==3` `Var` `3` wartością.

5. Wybierz przycisk **radiowy Ma** wartość True, a następnie kliknij przycisk **OK.**

6. Teraz ponownie uruchom program. Punkt przerwania powoduje zatrzymanie programu na początku funkcji, gdy `Var` parametr ma wartość `3` .

7. Użyj okna Stos wywołań, aby znaleźć funkcję wywołującą i przejść do jej kodu źródłowego. Aby uzyskać więcej informacji, zobacz How to: Use the Call Stack Window (Jak [używać okna stosu wywołań).](../debugger/how-to-use-the-call-stack-window.md)

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Punkty przerwania](/previous-versions/ktf38f66(v=vs.100))
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
