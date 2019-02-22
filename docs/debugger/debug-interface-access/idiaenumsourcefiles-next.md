---
title: Idiaenumsourcefiles::Next — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29424c2b12884cae7f803a46e15f7183d9690d96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631786"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Pobiera określoną liczbę plików źródłowych w kolejności wyliczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

[in] Liczba plików źródłowych w modułu wyliczającego do pobrania.

 rgelt

[out] Tablica, która ma zostać wypełniony przy użyciu [idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiektami, które reprezentują pliki źródłowe żądaną.

 pceltFetched

[out] Zwraca liczbę plików źródłowych w pobrano modułu wyliczającego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli nie ma żadnych więcej plików źródłowych. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)