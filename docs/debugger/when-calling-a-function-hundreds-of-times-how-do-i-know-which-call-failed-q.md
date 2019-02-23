---
title: Dowiedz się, które wywołanie nie powiodło się podczas wywoływania funkcji wiele razy | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa6fb9613df5f5bffb50c9a161eaa0a0254f26dd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696899"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się?
## <a name="problem-description"></a>Opis problemu
 Program kończy się niepowodzeniem na wywołanie funkcji `CnvtV`. Program prawdopodobnie wywołuje tę funkcję kilka kilkaset razy przed zakończy się niepowodzeniem. Jeśli I Ustaw punkt przerwania na `CnvtV`, program zatrzymuje działanie przy każdym wywołaniu tej funkcji i nie chcesz. Nie wiem, jakie warunki powoduje niepowodzenie, wywołania, dlatego nie można ustawić warunkowego punktu przerwania. Co mogę zrobić?

## <a name="solution"></a>Rozwiązanie
 Można ustawić punkt przerwania w przypadku funkcji z **liczba trafień** pola na wartość tak duży, czy go będzie nigdy nie można połączyć się. W tym przypadku ponieważ uważasz, że funkcja `CnvtV` nazywa się kilka kilkaset razy, możesz ustawić **liczba trafień** do 1000 lub większej liczby. Następnie uruchom program i poczekaj, aż wywołanie się nie powieść. Kiedy ulegnie awarii, Otwórz okno punktów przerwania i przyjrzyj się liście punktów przerwania. Punkt przerwania ustawiony na `CnvtV` pojawi się, że następuje liczba trafień i liczba iteracji, pozostałe:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Teraz wiesz, że funkcja nie powiodło się na 101st wywołania. Jeśli zresetujesz punkt przerwania z liczbą trafień 101 i ponownie uruchom program, program zatrzymuje się w wywołaniu `CnvtV` , która spowodowała, aby zakończyć się niepowodzeniem.

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Ustawianie punktów przerwania](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
