---
title: 'IDiaSymbol:: get_hasDebugInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasDebugInfo method
ms.assetid: 84cd2b67-0d83-4589-9ecb-a4bcbeed55f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7c158d15f7d60000bfd022e8cab10c3f2bc060c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85463772"
---
# <a name="idiasymbolget_hasdebuginfo"></a>IDiaSymbol::get_hasDebugInfo
Pobiera flagę, która określa, czy [jednostka kompilacji](../../debugger/debug-interface-access/compiland.md) zawiera informacje o debugowaniu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE` czy jednostka kompilacji zawiera informacje o debugowaniu; w przeciwnym razie zwraca `FALSE` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)