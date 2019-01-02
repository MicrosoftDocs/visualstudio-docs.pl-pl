---
title: Idiaenumtables::Next — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27d9811fe55a3b942cd020ae8038f07df8bf7a2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949411"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Pobiera określoną liczbę tabel w kolejności wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba tabel w modułu wyliczającego do pobrania.  
  
 `rgelt`  
 [out] Tablica, która ma zostać wypełniony przy użyciu [idiatable —](../../debugger/debug-interface-access/idiatable.md) obiekty, które reprezentują tabele żądaną.  
  
 `pceltFetched`  
 [out] Zwraca liczbę tabel w pobrano modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej tabel. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)