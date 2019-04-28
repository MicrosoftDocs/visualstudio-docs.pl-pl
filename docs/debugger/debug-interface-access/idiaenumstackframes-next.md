---
title: Idiaenumstackframes::Next — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833311"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Pobiera określoną liczbę elementów w ramce stosu z sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba elementów stackframe modułu wyliczającego do pobrania.

 rgelt

[out] Tablica, która ma być wypełnione z żądanym [idiastackframe —](../../debugger/debug-interface-access/idiastackframe.md) obiektów.

 pceltFetched

[out] Zwraca liczbę stosu ramki elementów w pobrano modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej ramek stosu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)