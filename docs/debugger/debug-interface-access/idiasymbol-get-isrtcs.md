---
description: Pobiera wartość, która informuje, czy funkcja została skompilowana za pomocą sprawdzania błędów w czasie działania ramki stosu. Jest to flaga /RTCs.
title: IDiaSymbol::get_isRTCs | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isRTCs method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9a297abe6326af6f04058e6095f59f880f526adb
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217250"
---
# <a name="idiasymbolget_isrtcs"></a>IDiaSymbol::get_isRTCs

Zwraca wartość, która informuje, czy funkcja została skompilowana za pomocą sprawdzania błędów w czasie działania ramki stosu. Jest to flaga /RTCs.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isRTCs ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry

 `pRetVal`

[out] Wskaźnik do wartości boOL, który określa, czy funkcja została skompilowana za pomocą sprawdzania błędów w czasie działania ramki stosu.

## <a name="return-value"></a>Wartość zwracana

 Jeśli to się powiedzie, `S_OK` zwraca wartość ; w przeciwnym razie zwraca kod `S_FALSE` błędu lub .

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi

Ta metoda jest obsługiwana od wersji Visual Studio 2019 16.10 (wersja zapoznawcza 2).

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówka:|dia2.h|
|Wersja:|DIA SDK w wersji 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
