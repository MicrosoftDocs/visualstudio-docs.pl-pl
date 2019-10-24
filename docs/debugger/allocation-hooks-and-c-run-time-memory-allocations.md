---
title: Punkty zaczepienia alokacji i alokacje pamięci w czasie wykonywania C | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e55ec521de098a7ae0339c4460502dde3d482d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745798"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
Bardzo ważne ograniczenie dotyczące funkcji punktów zaczepienia alokacji polega na tym, że muszą jawnie ignorować bloki `_CRT_BLOCK`. Te bloki to alokacje pamięci wewnętrznie wykonywane przez funkcje biblioteki wykonawczej C, jeśli wykonają jakiekolwiek wywołania funkcji biblioteki wykonawczej języka C, które przydzielą pamięć wewnętrzną. Bloki `_CRT_BLOCK` można zignorować, dołączając następujący kod na początku funkcji punktu zaczepienia alokacji:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Jeśli punkt zaczepienia alokacji nie ignoruje bloków `_CRT_BLOCK`, wówczas każda funkcja biblioteki wykonawczej C wywołana w elemencie Hook może Zalewka programu w pętli nieskończonej. Na przykład `printf` wykonuje alokację wewnętrzną. Jeśli kod punktu zaczepienia wywoła `printf`, wówczas przydziały będą powodowały ponowne wywoływanie punktu zaczepienia, który będzie ponownie wywoływał **printf** i tak dalej, aż do przepełnienia stosu. Jeśli zachodzi potrzeba raportowania `_CRT_BLOCK` operacji alokacji, jednym ze sposobów obejścia tego ograniczenia jest użycie funkcji interfejsu API systemu Windows, a nie funkcji czasu wykonywania języka C, do formatowania i wyjścia. Ponieważ interfejsy API systemu Windows nie używają sterty biblioteki wykonawczej języka C, nie będą zalewkować punktu zaczepienia alokacji w pętli nieskończonej.

Jeśli sprawdzisz pliki źródłowe biblioteki wykonawczej, zobaczysz, że domyślna funkcja podłączania alokacji, **CrtDefaultAllocHook** (która po prostu zwraca **wartość true**), znajduje się w osobnym pliku, DBGHOOK. S. Jeśli chcesz, aby punkt zaczepienia alokacji był wywoływany nawet w przypadku alokacji wykonanych przez kod uruchomienia w czasie wykonywania, który jest wykonywany przed **główną** funkcją aplikacji, można zastąpić tę funkcję domyślną, zamiast używać [_ CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Zobacz także
- [Pisanie funkcji debugowania punktów zaczepienia](../debugger/debug-hook-function-writing.md)
