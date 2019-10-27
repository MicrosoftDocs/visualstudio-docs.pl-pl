---
title: Wersje debugowania funkcji alokacji sterty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738370"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji stosu
Biblioteka wykonawcza C zawiera specjalne wersje debugowania funkcji alokacji sterty. Te funkcje mają takie same nazwy, jak wersje wersji z dołączonym _dbg. W tym temacie opisano różnice między wydaniem wersji funkcji CRT a wersją _dbg przy użyciu `malloc` i `_malloc_dbg` jako przykładów.

 Gdy [_DEBUG](/cpp/c-runtime-library/debug) jest zdefiniowany, CRT mapuje wszystkie wywołania [malloc](/cpp/c-runtime-library/reference/malloc) do [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). W związku z tym nie trzeba ponownie pisać kodu przy użyciu `_malloc_dbg`, a nie `malloc`, aby uzyskać korzyści podczas debugowania.

 Warto jednak jawnie wywołać `_malloc_dbg`. Wywołanie `_malloc_dbg` jawnie ma pewne dodatkowe korzyści:

- Śledzenie alokacji typu `_CLIENT_BLOCK`.

- Przechowywanie pliku źródłowego i numeru wiersza, w którym wystąpiło żądanie alokacji.

  Jeśli nie chcesz konwertować `malloc` wywołań na `_malloc_dbg`, możesz uzyskać informacje o pliku źródłowym przez zdefiniowanie [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), co spowoduje, że preprocesor będzie bezpośrednio mapować wszystkie wywołania `malloc` do `_malloc_dbg` zamiast polegać na otoki dookoła `malloc`.

  Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustawić parametr `blockType` na `_CLIENT_BLOCK`.

  Gdy _DEBUG nie jest zdefiniowany, wywołania do `malloc` nie są zakłócone, wywołania `_malloc_dbg` są rozpoznawane jako `malloc`, definicja [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) zostanie zignorowana, a informacje o pliku źródłowym odnoszące się do żądania alokacji nie zostaną dostarczone. Ponieważ `malloc` nie ma parametru typu bloku, żądania dla typów `_CLIENT_BLOCK` są traktowane jako alokacje standardowe.

## <a name="see-also"></a>Zobacz także

- [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)