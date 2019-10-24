---
title: Dowiedz się, kto przekazuje nieprawidłową wartość parametru | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42884cd6498f00cfe2df2d0396ff9ea6b03c2f98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734237"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak można sprawdzić, kto przekazuje błędną wartość parametru?
## <a name="problem-description"></a>Opis problemu
 Nieprawidłowa wartość parametru jest przesyłana do jednej z moich funkcji. Ta funkcja jest wywoływana ze wszystkich w miejscu. Jak można dowiedzieć się, co przekazuje do niewłaściwej wartości?

## <a name="solution"></a>Rozwiązanie

#### <a name="to-resolve-this-problem"></a>Aby rozwiązać ten problem

1. Ustaw punkt przerwania lokalizacji na początku funkcji.

2. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **warunek**.

3. W oknie dialogowym **warunek punktu przerwania** kliknij pole wyboru **warunek** . Zobacz [Zaawansowane punkty przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

4. Wprowadź wyrażenie, takie jak `Var==3`, w polu tekstowym, gdzie `Var` jest nazwą parametru, który zawiera nieprawidłową wartość, a `3` jest nieprawidłową wartością przekazaną do niego.

5. Wybierz przycisk radiowy **ma wartość true** , a następnie kliknij przycisk **OK** .

6. Teraz ponownie uruchom program. Punkt przerwania powoduje zatrzymanie programu na początku funkcji, gdy parametr `Var` ma wartość `3`.

7. Użyj okna stosu wywołań, aby znaleźć funkcję wywołującą i przejść do jej kodu źródłowego. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Punkty przerwania](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)