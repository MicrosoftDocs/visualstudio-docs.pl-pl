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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738370"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji stosu
Biblioteka wykonawcza C zawiera specjalne wersje debugowania funkcji alokacji sterty. Te funkcje mają takie same nazwy, jak wersje wersji z _dbg dołączone do nich. W tym temacie opisano różnice między wydaną wersją funkcji CRT a wersją _dbg, przy użyciu `malloc` i `_malloc_dbg` jako przykłady.

 Gdy [_DEBUG](/cpp/c-runtime-library/debug) jest zdefiniowany, CRT mapuje wszystkie wywołania [malloc](/cpp/c-runtime-library/reference/malloc) do [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). W związku z tym nie trzeba ponownie pisać kodu przy użyciu `_malloc_dbg` zamiast programu, `malloc` Aby uzyskać korzyści podczas debugowania.

 Warto jednak jawnie wywołać metodę `_malloc_dbg` . Wywołanie `_malloc_dbg` jawnie ma pewne dodatkowe korzyści:

- Śledzenie `_CLIENT_BLOCK` alokacji typów.

- Przechowywanie pliku źródłowego i numeru wiersza, w którym wystąpiło żądanie alokacji.

  Jeśli nie chcesz konwertować `malloc` wywołań na `_malloc_dbg` , możesz uzyskać informacje o pliku źródłowym przez zdefiniowanie [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), co powoduje, że preprocesor może bezpośrednio mapować wszystkie wywołania do programu `malloc` `_malloc_dbg` zamiast polegać na otoki `malloc` .

  Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustawić `blockType` parametr na `_CLIENT_BLOCK` .

  Gdy _DEBUG nie jest zdefiniowany, wywołania `malloc` nie są zakłócane, wywołania `_malloc_dbg` są rozpoznawane jako `malloc` , definicja [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) zostanie zignorowana, a informacje o pliku źródłowym odnoszące się do żądania alokacji nie zostaną podane. Ponieważ nie `malloc` ma parametru typu bloku, żądania dla `_CLIENT_BLOCK` typów są traktowane jako alokacje standardowe.

## <a name="see-also"></a>Zobacz też

- [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)