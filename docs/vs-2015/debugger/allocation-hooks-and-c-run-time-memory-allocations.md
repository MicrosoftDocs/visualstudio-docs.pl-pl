---
title: Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8487972c237b9c2ba6bf2594ffc1df43fa0c63cd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702433"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ograniczenie funkcje punktu zaczepienia alokacji z bardzo ważne jest, musisz jawnie Ignoruj `_CRT_BLOCK` bloków (alokacji pamięci dokonanych w wewnętrznie przez funkcje biblioteki wykonawczej języka C) jeśli dokonają wszelkie wywołania funkcji biblioteki wykonawczej języka C, które alokują pamięci wewnętrznej. `_CRT_BLOCK` Bloków można zignorować, dołączając kod, takie jak funkcję podłączania następujące czynności na początku przydziału:  
  
```  
if ( nBlockUse == _CRT_BLOCK )  
    return( TRUE );  
```  
  
 Jeśli Twoje punktu zaczepienia alokacji nie pomija `_CRT_BLOCK` blokuje, a następnie program w pętli nieskończonej może być stosowane do dowolnej funkcji biblioteki wykonawczej C o nazwie w swojej punktów zaczepienia. Na przykład `printf` sprawia, że wewnętrzna alokacja. Wywołuje kod punktu zaczepienia `printf`, a następnie wynikowy alokacji spowoduje, że Twoje zaczepienia volat jen ponownie, co spowoduje wywołanie **printf** ponownie, i tak dalej do momentu przepełnienia stosu. Jeśli potrzebujesz do raportu `_CRT_BLOCK` operacji alokacji jednym ze sposobów obejścia tego ograniczenia jest używać funkcji Windows API, a nie funkcji wykonawczej języka C, formatowania i danych wyjściowych. Ponieważ interfejsy API Windows używa sterty biblioteki wykonawczej C, ich nie będą stosowane, usługi punktu zaczepienia alokacji w pętli nieskończonej.  
  
 Jeśli badania biblioteki wykonawczej pliki źródłowe zobaczysz czy funkcję, podłączania Alokacja domyślna **CrtDefaultAllocHook** (po prostu zwraca ona **TRUE**), znajduje się w oddzielnym pliku własnych, DBGHOOK. C. Jeśli chcesz, aby Twoje punktu zaczepienia alokacji wywoływana, nawet w przypadku alokacji dokonanych przez kod startowy czasu wykonywania, który jest wykonywany przed aplikacji **głównego** funkcji, możesz zastąpić tę funkcję domyślną własny, zamiast za pomocą [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Sample](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
