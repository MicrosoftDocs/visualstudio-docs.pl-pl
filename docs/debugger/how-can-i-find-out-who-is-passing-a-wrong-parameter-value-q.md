---
title: Dowiedz się, kto przekazuje błędną wartość parametru | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8d33e1ae22da7980b9f4228243e93568864535ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069203"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak można sprawdzić, kto przekazuje błędną wartość parametru?
## <a name="problem-description"></a>Opis problemu  
 Niewłaściwa wartość parametru jest przekazywany do jednej z moich funkcji. Ta funkcja jest wywoływana z każdego miejsca. Jak można dowiedzieć się, co przekazuje jej wartość niewłaściwą?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-resolve-this-problem"></a>Aby rozwiązać ten problem  
  
1.  Ustaw punkt przerwania na początku funkcji.  
  
2.  Kliknij prawym przyciskiem myszy punkt przerwania i wybierz **warunek**.  
  
3.  W **warunek punktu przerwania** okno dialogowe, kliknij pozycję **warunek** pole wyboru. Zobacz [zaawansowane punkty przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Wprowadź wyrażenie, takie jak `Var==3`, w polu tekstowym, gdzie `Var` to nazwa parametru, która zawiera złą wartość, a `3` jest złą wartością przekazywaną do niego.  
  
5.  Wybierz **ma wartość True** przycisk radiowy, a następnie kliknij przycisk **OK** przycisku.  
  
6.  Teraz ponownie uruchom program. Punkt przerwania powoduje zatrzymanie programu na początku funkcji podczas `Var` parametr ma wartość `3`.  
  
7.  Okno stosu wywołań służy do znajdowania funkcji wywołującej i przejdź do jego kod źródłowy. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Punkty przerwania](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)