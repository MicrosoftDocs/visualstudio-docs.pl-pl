---
title: Idiaenumtables::Item — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5bd6f5f431b7f631ad02be7ed3d31268a3645a8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735728"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pobiera tabelę przy użyciu indeksu lub nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Idiaenumtables —](../../debugger/debug-interface-access/idiaenumtables.md)   
 [Idiatable —](../../debugger/debug-interface-access/idiatable.md)   
 [Idiaenumtables::get_count —](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)



