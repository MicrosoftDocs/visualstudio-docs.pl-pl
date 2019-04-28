---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce251da3c1cb7b1da00971d46cc0801ad24b8985
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839826"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Wywołuje się, gdy katalog debugowania został znaleziony w pliku .exe.

## <a name="syntax"></a>Składnia

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametry
 `fExecutable`

[in] `TRUE` Jeśli katalog debugowania są odczytywane z pliku wykonywalnego (a nie plikiem .dbg).

 `cbData`

[in] Liczba bajtów danych w katalogu debugowania.

 `data[]`

[in] Tablica, która jest wypełniane katalog debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod powrotny zwykle jest ignorowany.

## <a name="remarks"></a>Uwagi
 [Idiadatasource::loaddataforexe —](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoda wywołuje to wywołanie zwrotne, gdy znajdzie katalog debugowania podczas przetwarzania pliku wykonywalnego.

 Ta metoda usuwa potrzebę informacje debugowania innych niż znajdującą się w pliku .pdb pomocy technicznej dla klienta w celu odtworzenia pliku wykonywalnego i/lub debugowania. Dzięki tym danym klienta można rozpoznać typu dostępne informacje o debugowaniu i czy znajduje się on w pliku .dbg lub pliku wykonywalnego.

 Większość klientów nie wymaga to wywołanie zwrotne, ponieważ `IDiaDataSource::loadDataForExe` metody przezroczyste otwiera pliki .pdb i .dbg, gdy jest to niezbędne do obsługi symboli.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)