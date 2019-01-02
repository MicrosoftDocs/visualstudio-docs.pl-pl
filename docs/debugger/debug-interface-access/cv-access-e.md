---
title: Cv_access_e — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 373149884078b58926493fd7f37756ddb4eb8829
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838758"
---
# <a name="cvaccesse"></a>CV_access_e
Określa zakres widoczności (poziom dostępu), funkcji składowych i zmiennych.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
typedef enum CV_access_e {   
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
 [Idiasymbol::get_access —](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)