---
description: Pobiera dodatkowy rozmiar doliczany do każdej funkcji.
title: IDiaSymbol::get_framePadSize | Microsoft Docs
ms.date: 04/27/2021
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePadSize method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d361ec3e144730e49345d3560f815ee5fe0be469
ms.sourcegitcommit: 30c404655fb83ea28f96ab1edb1c09b4d8d7eec4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2021
ms.locfileid: "108217247"
---
# <a name="idiasymbolget_framepadsize"></a>IDiaSymbol::get_framePadSize

Pobiera dodatkowy rozmiar doliczany do każdej funkcji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_framePadSize ( 
   DWORD* pPadSize
);
```

#### <a name="parameters"></a>Parametry

 `pPadSize`

[out] Zwraca dodatkowy rozmiar padu dodany do każdej funkcji.

## <a name="return-value"></a>Wartość zwracana

 Jeśli to się powiedzie, zwraca `S_OK` wartość ; w przeciwnym razie zwraca kod `S_FALSE` błędu lub .

> [!NOTE]
> Wartość zwracana `S_FALSE` oznacza, że właściwość nie jest dostępna dla symbolu .

## <a name="remarks"></a>Uwagi

Dodatkowy rozmiar wkładki jest zwykle używany przez tryby Edytuj i kontynuuj.

Ta metoda jest obsługiwana od wersji Visual Studio 2019 16.10 (wersja zapoznawcza 2).

## <a name="requirements"></a>Wymagania

|Wymaganie|Opis|
|-----------------|-----------------|
|Nagłówka:|dia2.h|
|Wersja:|DIA SDK w wersji 7.0|

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
