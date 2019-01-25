---
title: Funkcje punktu zaczepienia alokacji | Dokumentacja firmy Microsoft
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d2aff47737443b998cfae8d16c3d95a5eb1d2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794943"
---
# <a name="allocation-hook-functions"></a>Funkcje punktu zaczepienia alokacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcji podłączania alokacji zainstalowane za pomocą [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), jest wywoływana za każdym razem, gdy przydzielone, ponownie przydzielić lub zwolnienie pamięci. Ten typ punktu zaczepienia może służyć do wielu różnych celów. Użyj go, aby przetestować, jak aplikacja obsługuje sytuacje braku pamięci, na przykład do zbadania wzorców przydziału lub do rejestrowania informacji o alokacji do późniejszej analizy.  
  
> [!NOTE]
>  Należy pamiętać o ograniczeniu dotyczącym używania funkcji biblioteki wykonawczej języka C w funkcji punktu zaczepienia alokacji, opisanego w artykule [Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkcji podłączania alokacji powinny mieć prototypu, jak pokazano poniżej:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Wskaźnik, który jest przekazywany do [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) typu **_crt_alloc_hook —**, zgodnie z definicją w CRTDBG. GODZ.:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Gdy biblioteka środowiska uruchomieniowego wywołuje usługi podłączania *nAllocType* argument wskazuje, jakie alokacji ma być wykonywana operacja (**_HOOK_ALLOC**, **_HOOK_REALLOC**, lub **_HOOK_FREE**). W przypadku bezpłatnej lub realokacja `pvData` zawiera wskaźnik do tematu użytkownika bloku, która będzie zwolniona. Jednak w przypadku alokacji this, wskaźnik ma wartość null, ponieważ nie ma jeszcze wystąpiła Alokacja. Pozostałe argumenty zawierają rozmiar alokacji w danym, jego typ bloku numeru sekwencyjnego żądania, skojarzone z, a także wskaźnik do pliku nazwa i numer wiersza w którym dokonano alokacji, jeśli jest dostępny. Po funkcja podłączania wykonuje niezależnie od analizy i inne zadania chce jego autora, aplikacja musi zwracać jedną **TRUE**, co oznacza, że można kontynuować operacji alokacji, lub **FALSE**oznaczający, operacja powinna zakończyć się niepowodzeniem. Proste punktu zaczepienia tego typu może sprawdzić ilość pamięci przydzielonej do tej pory i powrócić **FALSE** przekroczeniu limitu małych takimi problemami znacznie mniej. Aplikacja następnie doświadczenie rodzaju błędów alokacji, które normalnie mogą się pojawić tylko wtedy, gdy ilość dostępnej pamięci była bardzo niska. Bardziej złożone punkty zaczepienia może informacje o wzorcach alokacji, analiza użycia pamięci lub raportu po wystąpieniu określonych sytuacjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty zaczepienia alokacji i alokacji pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Debugowanie pisanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 Sample](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
