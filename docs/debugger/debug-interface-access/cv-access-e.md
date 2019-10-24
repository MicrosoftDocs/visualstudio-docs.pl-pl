---
title: CV_access_e | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745367"
---
# <a name="cv_access_e"></a>CV_access_e
Określa zakres widoczności (poziom dostępu) funkcji składowych i zmiennych.

## <a name="syntax"></a>Składnia

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementy
Członek CV_private ma prywatny dostęp.

Członek CV_protected ma chroniony dostęp.

Członek CV_public ma dostęp publiczny.

## <a name="remarks"></a>Uwagi
Specyfikator dostępu `friend` nie jest uwzględniony w tym miejscu, ponieważ jest zazwyczaj używany przez funkcje nieczłonkowskie, które mają dostęp zarówno do prywatnych, jak i chronionych elementów klasy. Użyj metody [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) , aby znaleźć symbole z dostępem `SymTagFriend`.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz także
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
