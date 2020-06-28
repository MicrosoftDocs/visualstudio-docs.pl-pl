---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c6a65bdca680bac7c3a5b2e6a5a671045cdef093
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467534"
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

podczas Indeks lub nazwa [IDiaTable](../../debugger/debug-interface-access/idiatable.md) do pobrania. Jeśli używana jest zmienna typu Integer, musi ona należeć do zakresu od 0 do `count` -1, gdzie `count` jest zwracany przez metodę [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

określoną Zwraca obiekt [IDiaTable](../../debugger/debug-interface-access/idiatable.md) reprezentujący pożądaną tabelę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli określona jest zmienna typu String, ciąg nazwy określonej tabeli. Nazwa powinna być jedną z nazw tabel, zgodnie z definicją w [stałych (zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Przykład

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Zobacz też
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)