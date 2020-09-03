---
title: Funkcje punktu zaczepienia alokacji | Microsoft Docs
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745822"
---
# <a name="allocation-hook-functions"></a>Funkcje punktu zaczepienia alokacji
Funkcja punktu zaczepienia alokacji, zainstalowana za pomocą [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), jest wywoływana za każdym razem, gdy pamięć jest przydzielana, ponownie przydzielana lub zwalniana. Tego typu punktu zaczepienia można użyć w wielu różnych celach. Służy do testowania, w jaki sposób aplikacja obsługuje niewystarczającą ilość pamięci, na przykład w celu zbadania wzorców alokacji lub informacji o alokacji dziennika do późniejszej analizy.

> [!NOTE]
> Należy pamiętać o ograniczeniu dotyczącego użycia funkcji biblioteki wykonawczej C w funkcji punktu zaczepienia alokacji, opisanej w obszarze [punkty zaczepienia alokacji i alokacji pamięci w czasie wykonywania c](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Funkcja punktu zaczepienia alokacji powinna mieć prototyp podobny do następującego:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Wskaźnik przekazany do [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) jest typu **_CRT_ALLOC_HOOK**, zgodnie z definicją w CRTDBG. C

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Gdy Biblioteka wykonawcza wywołuje punkt zaczepienia, argument *nAllocType* wskazuje, jaką operację alokacji należy wykonać (**_HOOK_ALLOC**, **_HOOK_REALLOC**lub **_HOOK_FREE**). W przypadku bezpłatnej lub ponownej alokacji program `pvData` ma wskaźnik do artykułu użytkownika bloku, który ma zostać zwolniony. Jednak w przypadku alokacji wskaźnik ten ma wartość null, ponieważ nie nastąpiła alokacja. Pozostałe argumenty zawierają rozmiar danego przydziału, jego typ bloku, sekwencyjny numer żądania skojarzony z nim oraz wskaźnik do nazwy pliku. Jeśli są dostępne, argumenty obejmują również numer wiersza, w którym została wprowadzona alokacja. Gdy funkcja podłączania wykonuje dowolną analizę i inne zadania, których autor chce, musi zwrócić **wartość true**, co oznacza, że operacja alokacji może być kontynuowana, lub **false**, co oznacza, że operacja powinna zakończyć się niepowodzeniem. Prosty hak tego typu może sprawdzić ilość pamięci przydzieloną do tej pory i zwrócić **wartość false** , jeśli ta wartość przekracza mały limit. Następnie aplikacja będzie korzystać z rodzaju błędów alokacji, które zwykle występują tylko wtedy, gdy dostępna pamięć była bardzo niska. Bardziej złożone punkty zaczepienia mogą śledzić wzorce alokacji, analizować użycie pamięci lub raportować, gdy wystąpią określone sytuacje.

## <a name="see-also"></a>Zobacz też

- [Punkty zaczepienia alokacji i alokacja pamięci środowiska wykonawczego języka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Pisanie debugowanie funkcji punktów zaczepienia](../debugger/debug-hook-function-writing.md)