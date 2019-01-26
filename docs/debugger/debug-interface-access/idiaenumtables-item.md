---
title: Idiaenumtables::Item — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 805be4cd9f40bdbdb0f02521a0d946c7121847c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939702"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Pobiera tabelę przy użyciu indeksu lub nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Indeks lub nazwę [idiatable —](../../debugger/debug-interface-access/idiatable.md) do pobrania. Jeśli jest używany typ variant liczby całkowitej, musi być z zakresu od 0 do `count`-1, gdzie `count` jest zwracana przez [idiaenumtables::get_count —](../../debugger/debug-interface-access/idiaenumtables-get-count.md) metody.  
  
 `table`  
 [out] Zwraca [idiatable —](../../debugger/debug-interface-access/idiatable.md) obiekt reprezentujący odpowiednią tabelę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli określono wariant ciąg, ciąg nazwy określonej tabeli. Nazwa musi mieć jedną z nazw tabel, zgodnie z definicją w [— stałe (debugowanie interfejsu Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Przykład  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)