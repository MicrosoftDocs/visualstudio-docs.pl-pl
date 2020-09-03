---
title: Wersje debugowania funkcji alokacji sterty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691155"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Wersja debugowania funkcji alokacji stosu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Biblioteka wykonawcza C zawiera specjalne wersje debugowania funkcji alokacji sterty. Te funkcje mają takie same nazwy, jak wersje wersji z _dbg dołączone do nich. W tym temacie opisano różnice między wydaną wersją funkcji CRT a wersją _dbg, przy użyciu `malloc` i `_malloc_dbg` jako przykłady.  
  
 Gdy [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) jest zdefiniowany, CRT mapuje wszystkie wywołania [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) do [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). W związku z tym nie trzeba ponownie pisać kodu przy użyciu `_malloc_dbg` zamiast programu, `malloc` Aby uzyskać korzyści podczas debugowania.  
  
 Warto jednak jawnie wywołać metodę `_malloc_dbg` . Wywołanie `_malloc_dbg` jawnie ma pewne dodatkowe korzyści:  
  
- Śledzenie `_CLIENT_BLOCK` alokacji typów.  
  
- Przechowywanie pliku źródłowego i numeru wiersza, w którym wystąpiło żądanie alokacji.  
  
  Jeśli nie chcesz konwertować `malloc` wywołań na `_malloc_dbg` , możesz uzyskać informacje o pliku źródłowym przez zdefiniowanie [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), co powoduje, że preprocesor może bezpośrednio mapować wszystkie wywołania do programu `malloc` `_malloc_dbg` zamiast polegać na otoki `malloc` .  
  
  Aby śledzić oddzielne typy alokacji w blokach klienta, należy wywołać `_malloc_dbg` bezpośrednio i ustawić `blockType` parametr na `_CLIENT_BLOCK` .  
  
  Gdy _DEBUG nie jest zdefiniowany, wywołania `malloc` nie są zakłócane, wywołania `_malloc_dbg` są rozpoznawane jako `malloc` , definicja [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) zostanie zignorowana, a informacje o pliku źródłowym odnoszące się do żądania alokacji nie zostaną podane. Ponieważ nie `malloc` ma parametru typu bloku, żądania dla `_CLIENT_BLOCK` typów są traktowane jako alokacje standardowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Techniki testowania CRT](../debugger/crt-debugging-techniques.md)
