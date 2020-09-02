---
title: Jak można sprawdzić, kto przekazuje błędną wartość parametru? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b0787a0d700859e7728762fd7846911fcd41e369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704551"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak można sprawdzić, kto przekazuje błędną wartość parametru?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Nieprawidłowa wartość parametru jest przesyłana do jednej z moich funkcji. Ta funkcja jest wywoływana ze wszystkich w miejscu. Jak można dowiedzieć się, co przekazuje do niewłaściwej wartości?  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-resolve-this-problem"></a>Aby rozwiązać ten problem  
  
1. Ustaw punkt przerwania lokalizacji na początku funkcji.  
  
2. Kliknij prawym przyciskiem myszy punkt przerwania i wybierz pozycję **warunek**.  
  
3. W oknie dialogowym **warunek punktu przerwania** kliknij pole wyboru **warunek** . Zobacz [Zaawansowane punkty przerwania](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4. Wprowadź wyrażenie, takie jak `Var==3` , w polu tekstowym, gdzie `Var` jest nazwą parametru, który zawiera nieprawidłową wartość, i `3` jest nieprawidłową wartością przekazaną do niego.  
  
5. Wybierz przycisk radiowy **ma wartość true** , a następnie kliknij przycisk **OK** .  
  
6. Teraz ponownie uruchom program. Punkt przerwania powoduje zatrzymanie programu na początku funkcji, gdy `Var` parametr ma wartość `3` .  
  
7. Użyj okna stosu wywołań, aby znaleźć funkcję wywołującą i przejść do jej kodu źródłowego. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Punkty przerwania](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
