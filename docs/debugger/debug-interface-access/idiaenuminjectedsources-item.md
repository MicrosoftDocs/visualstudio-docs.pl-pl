---
title: Idiaenuminjectedsources::Item — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf52767a3e68442df1288d644d8d97ebcf78aaa2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890303"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Pobiera wstrzyknięte źródło za pomocą indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 indeks  
 [in] Indeks elementu [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) obiektu do pobrania. Indeks jest z zakresu od 0 do `count`-1, gdzie `count` jest zwracany przez [idiaenuminjectedsources::get_count —](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) metody.  
  
 injectedSource  
 [out] Zwraca [idiainjectedsource —](../../debugger/debug-interface-access/idiainjectedsource.md) obiekt reprezentujący wstrzyknięte źródło.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenuminjectedsources —](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)