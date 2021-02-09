---
title: 'IDiaSymbol:: get_compilerName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 810197226185e848cdc9ace69654e1b40ce05a5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863481"
---
# <a name="idiasymbolget_compilername"></a>IDiaSymbol::get_compilerName
Zwraca nazwę kompilatora użytego do wygenerowania [jednostka kompilacji](../../debugger/debug-interface-access/compiland.md).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_compilerName (
   BSTR *pName
);
```

#### <a name="parameters"></a>Parametry
 `pName` Wskaźnik na element BSTR, który będzie zawierać nazwę Unicode kompilatora.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)