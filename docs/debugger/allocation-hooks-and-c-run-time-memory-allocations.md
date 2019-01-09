---
title: Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a654c2d86ed0eb598a963b56cd6e3ef16ad91f19
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154098"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
Ograniczenie funkcje punktu zaczepienia alokacji z bardzo ważne jest, musisz jawnie Ignoruj `_CRT_BLOCK` bloków. Te bloki są alokacji pamięci dokonanych wewnętrznie przez funkcje biblioteki wykonawczej języka C, jeśli dokonają wszelkie wywołania do funkcji biblioteki wykonawczej C, które przydzielają pamięć. Możesz zignorować `_CRT_BLOCK` funkcję podłączania bloków, dodając następujący kod na początku przydziału:  
  
```cpp
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Jeśli Twoje punktu zaczepienia alokacji nie Ignoruj `_CRT_BLOCK` blokuje, a następnie program w pętli nieskończonej może być stosowane do dowolnej funkcji biblioteki wykonawczej C o nazwie w swojej punktów zaczepienia. Na przykład `printf` sprawia, że wewnętrzna alokacja. Wywołuje kod punktu zaczepienia `printf`, a następnie wynikowy alokacji spowoduje, że Twoje zaczepienia volat jen ponownie, co spowoduje wywołanie **printf** ponownie, i tak dalej do momentu przepełnienia stosu. Jeśli potrzebujesz do raportu `_CRT_BLOCK` operacji alokacji jednym ze sposobów obejścia tego ograniczenia jest używać funkcji Windows API, a nie funkcji wykonawczej języka C, formatowania i danych wyjściowych. Ponieważ interfejsy API Windows nie jest używana sterty biblioteki wykonawczej C, nie będzie komunikat pułapki Twojego punktu zaczepienia alokacji w pętli nieskończonej.  
  
 Jeśli badania biblioteki wykonawczej pliki źródłowe zobaczysz czy funkcję, podłączania Alokacja domyślna **CrtDefaultAllocHook** (po prostu zwraca ona **TRUE**), znajduje się w oddzielnym pliku własnych, DBGHOOK. C. Jeśli chcesz, aby Twoje punktu zaczepienia alokacji wywoływana, nawet w przypadku alokacji dokonanych przez kod startowy czasu wykonywania, który jest wykonywany przed aplikacji **głównego** funkcji, możesz zastąpić tę funkcję domyślną własny, zamiast za pomocą [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie funkcji debugowania punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
