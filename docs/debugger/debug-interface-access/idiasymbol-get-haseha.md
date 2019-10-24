---
title: 'IDiaSymbol:: get_hasEHa | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasEHa method
ms.assetid: cb61dfd9-fe69-461c-8185-288440454864
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f010fee3243a9ce202451fc9cc5cff1ed908118
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740530"
---
# <a name="idiasymbolget_haseha"></a>IDiaSymbol::get_hasEHa
Pobiera flagę, która określa, czy funkcja zawiera asynchroniczną (strukturalną) obsługę wyjątków.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_hasEHa(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametry
 `pFlag`

określoną Zwraca `TRUE`, jeśli funkcja ma jakąkolwiek asynchroniczną obsługę wyjątków; w przeciwnym razie zwraca `FALSE`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

> [!NOTE]
> Wartość zwracana przez `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Istnieje możliwość mieszania obsługi wyjątków asynchronicznych lub strukturalnych z obsługą wyjątków w C++stylu, ale wymaga określonego przełącznika kompilatora,/EHa, aby go włączyć.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówki|dia2. h|
|Wersja:|DIA SDK v 8.0|

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)