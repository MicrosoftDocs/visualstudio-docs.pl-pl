---
title: Idiasymbol::get_offset — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0016ca267b3eaf2535896aab1ee58a470a192c9a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399454"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
Pobiera przesunięcie lokalizacji symboli. Zastosowania [locationtype — wyliczenie](../../debugger/debug-interface-access/locationtype.md) jest `LocIsRegRel` lub `LocIsBitField`.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Zwraca przesunięcie w bajtach lokalizacji symboli.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

> [!NOTE]
> Zwracana wartość wynosząca `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu.

## <a name="remarks"></a>Uwagi
 Przesunięcie jest w pewnym momencie znane wcześniej określana. Na przykład przesunięcie `LocIsBitField` typ lokalizacji jest zazwyczaj od samego początku zawierający klasy.

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówek:|dia2.h|
|Wersja:|V7.0 DIA SDK|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [LocationType, wyliczenie](../../debugger/debug-interface-access/locationtype.md)