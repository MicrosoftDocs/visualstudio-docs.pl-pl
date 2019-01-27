---
title: Idiaenumsymbols::Item — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3cc898d989c345ba7691252562fac820eec1c18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924113"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
Pobiera symbol za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks elementu [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu do pobrania. Indeks znajduje się w zakresie od 0 do `count`-1, gdzie `count` jest zwracany przez [idiaenumsymbols::get_count —](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) metody.  
  
  — symbol  
 [out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący symbol żądaną.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)