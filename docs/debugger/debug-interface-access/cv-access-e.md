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
ms.openlocfilehash: 2b5fa908692167b49c6bb92c892fb143b882d231
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318579"
---
# <a name="cvaccesse"></a>CV_access_e
Określa zakres widoczności (poziom dostępu), funkcji składowych i zmiennych.

## <a name="syntax"></a>Składnia

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elementy
CV_private  
Element członkowski ma prywatnie.

CV_protected  
Element członkowski zabezpieczył dostępu.

CV_public  
Element członkowski ma dostęp publiczny.

## <a name="remarks"></a>Uwagi
`friend` Specyfikator dostępu nie jest uwzględniony w tym miejscu, ponieważ jest ona zwykle używana przez funkcje nieczłonkowskie, które mają dostęp do prywatnej i chronionych elementów klasy. Użyj [idiasymbol::get_symtag —](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metody do znalezienia symboli z `SymTagFriend` dostępu.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
[Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)  
[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
