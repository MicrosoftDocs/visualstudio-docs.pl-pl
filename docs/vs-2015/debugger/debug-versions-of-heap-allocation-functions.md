---
title: Wersja debugowania funkcji alokacji sterty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7a649d8afd3ae7bf7d6d9abff98734ac96e05cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802114"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji sterty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biblioteki wykonawczej C zawiera specjalne wersje do debugowania funkcji alokacji sterty. Te funkcje mają takie same nazwy co wersję, wersje _dbg dołączany do nich. W tym temacie opisano różnice między wersji funkcji CRT i wersja _dbg przy użyciu `malloc` i `_malloc_dbg` jako przykłady.  
  
 Gdy [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) jest zdefiniowany, CRT mapuje wszystkie [— funkcja malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) wywołania [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). W związku z tym, nie trzeba ponownie zapisuje kodzie przy użyciu `_malloc_dbg` zamiast `malloc` otrzymywać korzyści podczas debugowania.  
  
 Należy wywołać `_malloc_dbg` jawnie, jednak. Wywoływanie `_malloc_dbg` jawnie niektóre dodał korzyści:  
  
- Śledzenie `_CLIENT_BLOCK` typu alokacji.  
  
- Przechowywanie źródłowego pliku i numer wiersza której wystąpiło żądanie alokacji.  
  
  Jeśli nie chcesz przekształcać swoje `malloc` wywołania `_malloc_dbg`, można uzyskać informacji o pliku źródłowym, definiując [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), co powoduje, że mapa preprocesora aby bezpośrednio wszystkie wywołania do `malloc` do `_malloc_dbg` zamiast polegania na otokę `malloc`.  
  
  Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustaw `blockType` parametr `_CLIENT_BLOCK`.  
  
  Gdy _DEBUG nie jest zdefiniowany, wywołania `malloc` nie zostaną zakłócone, wywołania `_malloc_dbg` są rozwiązywane do `malloc`, definicja [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) jest ignorowany i źródła odnoszących się do informacji o pliku żądanie alokacji nie została podana. Ponieważ `malloc` , nie ma parametr typu blok, żądań dla `_CLIENT_BLOCK` typy są traktowane jako standardowe alokacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki debugowania CRT](../debugger/crt-debugging-techniques.md)



