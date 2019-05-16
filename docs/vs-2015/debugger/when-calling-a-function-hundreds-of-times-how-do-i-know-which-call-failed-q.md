---
title: Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fba5032860e21bbd323b8e49d5f32ab9b6f90540
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688135"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Program kończy się niepowodzeniem na wywołanie funkcji `CnvtV`. Program prawdopodobnie wywołuje tę funkcję kilka kilkaset razy przed zakończy się niepowodzeniem. Jeśli I Ustaw punkt przerwania na `CnvtV`, program zatrzymuje działanie przy każdym wywołaniu tej funkcji i nie chcesz. Nie wiem, jakie warunki powoduje niepowodzenie, wywołania, dlatego nie można ustawić warunkowego punktu przerwania. Co mogę zrobić?  
  
## <a name="solution"></a>Rozwiązanie  
 Można ustawić punkt przerwania w przypadku funkcji z **liczba trafień** pola na wartość tak duży, czy go będzie nigdy nie można połączyć się. W tym przypadku ponieważ uważasz, że funkcja `CnvtV` nazywa się kilka kilkaset razy, możesz ustawić **liczba trafień** do 1000 lub większej liczby. Następnie uruchom program i poczekaj, aż wywołanie się nie powieść. Kiedy ulegnie awarii, Otwórz okno punktów przerwania i przyjrzyj się liście punktów przerwania. Punkt przerwania ustawiony na `CnvtV` pojawi się, że następuje liczba trafień i liczba iteracji, pozostałe:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Teraz wiesz, że funkcja nie powiodło się na 101st wywołania. Jeśli zresetujesz punkt przerwania z liczbą trafień 101 i ponownie uruchom program, program zatrzymuje się w wywołaniu `CnvtV` , która spowodowała, aby zakończyć się niepowodzeniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Ustawianie punktów przerwania](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
