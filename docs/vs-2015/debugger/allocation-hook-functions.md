---
title: Funkcje punktu zaczepienia alokacji | Microsoft Docs
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
ms.openlocfilehash: 81135546ffa208a4efb96569cd7968dfe560cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702526"
---
# <a name="allocation-hook-functions"></a>Funkcje punktu zaczepienia alokacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja punktu zaczepienia alokacji, zainstalowana za pomocą [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), jest wywoływana za każdym razem, gdy pamięć zostanie przydzielone, ponownie przydzielone lub zwolnione. Ten typ punktu zaczepienia może być używany w wielu różnych celach. Służy do testowania, w jaki sposób aplikacja obsługuje niewystarczającą ilość pamięci, na przykład lub do zbadania wzorców alokacji lub aby rejestrować informacje o alokacji na potrzeby późniejszej analizy.  
  
> [!NOTE]
> Należy pamiętać o ograniczeniu dotyczącego użycia funkcji biblioteki wykonawczej C w funkcji punktu zaczepienia alokacji, opisanej w obszarze [punkty zaczepienia alokacji i alokacji pamięci w czasie wykonywania c](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkcja punktu zaczepienia alokacji powinna mieć prototyp podobny do następującego:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Wskaźnik przekazany do [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) jest typu **_CRT_ALLOC_HOOK**, zgodnie z definicją w CRTDBG. C  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Gdy Biblioteka wykonawcza wywołuje punkt zaczepienia, argument *nAllocType* wskazuje, jaka operacja alokacji ma zostać wykonana (**_HOOK_ALLOC**, **_HOOK_REALLOC**lub **_HOOK_FREE**). W przypadku bezpłatnej lub ponownej alokacji program `pvData` zawiera wskaźnik do tematu użytkownika bloku, który ma zostać zwolniony. Jednak w przypadku alokacji wskaźnik ten ma wartość null, ponieważ alokacja nie została jeszcze osiągnięta. Pozostałe argumenty zawierają rozmiar danego przydziału, jego typ bloku, sekwencyjny numer żądania skojarzony z nim oraz wskaźnik do nazwy pliku i numer wiersza, w którym wykonano alokację, jeśli jest dostępny. Gdy funkcja podłączania wykonuje dowolną analizę i inne zadania, których autor chce, musi zwrócić **wartość true**, co oznacza, że operacja alokacji może być kontynuowana, lub **false**, co oznacza, że operacja powinna zakończyć się niepowodzeniem. Prosty hak tego typu może sprawdzić ilość pamięci przydzieloną do tej pory i zwrócić **wartość false** , jeśli ta wartość przekracza mały limit. Następnie aplikacja będzie korzystać z rodzaju błędów alokacji, które zwykle występują tylko wtedy, gdy dostępna pamięć była bardzo niska. Bardziej złożone punkty zaczepienia mogą śledzić wzorce alokacji, analizować użycie pamięci lub raportować, gdy wystąpią określone sytuacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty zaczepienia alokacji i alokacje pamięci w czasie wykonywania C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Zapisywanie funkcji punktu zaczepienia debugowania](../debugger/debug-hook-function-writing.md)   
 [Przykład crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
