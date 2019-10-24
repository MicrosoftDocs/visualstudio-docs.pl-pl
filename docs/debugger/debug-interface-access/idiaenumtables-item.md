---
title: 'IDiaEnumTables:: Item | Microsoft Docs'
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
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743753"
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

podczas Indeks lub nazwa [IDiaTable](../../debugger/debug-interface-access/idiatable.md) do pobrania. Jeśli używana jest zmienna typu Integer, musi ona należeć do zakresu od 0 do `count`-1, gdzie `count` jest zwracany przez metodę [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

określoną Zwraca obiekt [IDiaTable](../../debugger/debug-interface-access/idiatable.md) reprezentujący pożądaną tabelę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

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

## <a name="see-also"></a>Zobacz także
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Stałe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)