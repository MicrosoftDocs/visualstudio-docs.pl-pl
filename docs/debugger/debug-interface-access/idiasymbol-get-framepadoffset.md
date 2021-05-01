---
description: Pobiera przesunięcie podkładki stosu z rejestru wskaźnika ramki.
title: IDiaSymbol::get_framePadOffset | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadOffset method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 455e617188a58090f3bd6229ab008847912b1f19
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217251"
---
# <a name="idiasymbolget_framepadoffset"></a>IDiaSymbol::get_framePadOffset

Pobiera przesunięcie podkładki stosu z rejestru wskaźnika ramki.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_framePadOffset ( 
   DWORD* pPadOffset
);
```

#### <a name="parameters"></a>Parametry

 `pPadOffset`

[out] Zwraca przesunięcie stosu.

## <a name="return-value"></a>Wartość zwracana

 Jeśli to się powiedzie, zwraca `S_OK` wartość ; w przeciwnym razie zwraca kod `S_FALSE` błędu lub .

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu .

## <a name="remarks"></a>Uwagi

Ta metoda jest obsługiwana od wersji Visual Studio 2019 16.10 (wersja zapoznawcza 2).

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówka:|dia2.h|
|Wersja:|DIA SDK w wersji 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
