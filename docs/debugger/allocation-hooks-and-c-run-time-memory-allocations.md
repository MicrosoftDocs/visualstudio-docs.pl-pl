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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745798"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
Bardzo ważne ograniczenie dotyczące funkcji punktów zaczepienia alokacji polega na tym, że muszą jawnie ignorować `_CRT_BLOCK` bloki. Te bloki to alokacje pamięci wewnętrznie wykonywane przez funkcje biblioteki wykonawczej C, jeśli wykonają jakiekolwiek wywołania funkcji biblioteki wykonawczej języka C, które przydzielą pamięć wewnętrzną. Bloki można zignorować `_CRT_BLOCK` , dołączając następujący kod na początku funkcji punktu zaczepienia alokacji:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Jeśli punkt zaczepienia alokacji nie ignoruje `_CRT_BLOCK` bloków, wówczas każda funkcja biblioteki wykonawczej języka C wywołana w elemencie Hook może Zalewka programu w pętli nieskończonej. Na przykład program `printf` tworzy wewnętrzną alokację. Jeśli kod punktu zaczepienia wywołuje `printf` , wówczas przydzielone przydziały spowodują ponowne wywołanie punktu zaczepienia, który będzie ponownie wywoływał **printf** i tak dalej, aż do przepełnienia stosu. Jeśli trzeba zgłosić `_CRT_BLOCK` operacje alokacji, jednym ze sposobów obejścia tego ograniczenia jest użycie funkcji interfejsu API systemu Windows, a nie funkcji w czasie wykonywania w języku C do formatowania i wyjścia. Ponieważ interfejsy API systemu Windows nie używają sterty biblioteki wykonawczej języka C, nie będą zalewkować punktu zaczepienia alokacji w pętli nieskończonej.

Jeśli sprawdzisz pliki źródłowe biblioteki wykonawczej, zobaczysz, że domyślna funkcja punktu zaczepienia alokacji, **CrtDefaultAllocHook** (która po prostu zwraca **wartość true**), znajduje się w osobnym pliku, DBGHOOK. C. Jeśli chcesz, aby punkt zaczepienia alokacji był wywoływany nawet w przypadku alokacji dokonanych przez kod uruchomienia w czasie wykonywania, który jest wykonywany przed **główną** funkcją aplikacji, możesz zastąpić tę funkcję domyślną, zamiast korzystać z [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Zobacz też
- [Pisanie debugowanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)
