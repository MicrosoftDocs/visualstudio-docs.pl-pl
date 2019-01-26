---
title: Wersja debugowania funkcji alokacji sterty | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bf3865d8369b7b3b4a7407f8c54465f93bcc7bd7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920894"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji sterty
Biblioteki wykonawczej C zawiera specjalne wersje do debugowania funkcji alokacji sterty. Te funkcje mają takie same nazwy co wersję, wersje _dbg dołączany do nich. W tym temacie opisano różnice między wersji funkcji CRT i wersja _dbg przy użyciu `malloc` i `_malloc_dbg` jako przykłady.  
  
 Gdy [_DEBUG](/cpp/c-runtime-library/debug) jest zdefiniowany, CRT mapuje wszystkie [— funkcja malloc](/cpp/c-runtime-library/reference/malloc) wywołania [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). W związku z tym, nie trzeba ponownie zapisuje kodzie przy użyciu `_malloc_dbg` zamiast `malloc` otrzymywać korzyści podczas debugowania.  
  
 Należy wywołać `_malloc_dbg` jawnie, jednak. Wywoływanie `_malloc_dbg` jawnie niektóre dodał korzyści:  
  
- Śledzenie `_CLIENT_BLOCK` typu alokacji.  
  
- Przechowywanie źródłowego pliku i numer wiersza której wystąpiło żądanie alokacji.  
  
  Jeśli nie chcesz przekształcać swoje `malloc` wywołania `_malloc_dbg`, można uzyskać informacji o pliku źródłowym, definiując [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), co powoduje, że mapa preprocesora aby bezpośrednio wszystkie wywołania do `malloc` do `_malloc_dbg` zamiast polegania na otokę `malloc`.  
  
  Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustaw `blockType` parametr `_CLIENT_BLOCK`.  
  
  Gdy _DEBUG nie jest zdefiniowany, wywołania `malloc` nie zostaną zakłócone, wywołania `_malloc_dbg` są rozwiązywane do `malloc`, definicja [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) jest ignorowany i źródła odnoszących się do informacji o pliku żądanie alokacji nie została podana. Ponieważ `malloc` , nie ma parametr typu blok, żądań dla `_CLIENT_BLOCK` typy są traktowane jako standardowe alokacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)