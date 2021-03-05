---
description: Wywoływana, gdy w pliku exe znaleziono katalog debugowania.
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed83b79dea8f488be79a2161968876c9aa2a9a11
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148284"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Wywoływana, gdy w pliku exe znaleziono katalog debugowania.

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

[w] `TRUE` Jeśli katalog debugowania jest odczytywany z pliku wykonywalnego (a nie pliku. dbg).

 `cbData`

podczas Liczba bajtów danych w katalogu debugowania.

 `data[]`

podczas Tablica, która jest wypełniana katalogiem debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Kod powrotny jest zwykle ignorowany.

## <a name="remarks"></a>Uwagi
 Metoda [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) wywołuje to wywołanie zwrotne, gdy odnajdzie katalog debugowania podczas przetwarzania pliku wykonywalnego.

 Ta metoda eliminuje konieczność odtwarzania pliku wykonywalnego i/lub debugowania przez klienta w celu obsługi informacji debugowania innych niż Znalezione w pliku. pdb. Za pomocą tych danych klient może rozpoznać typ dostępnych informacji debugowania i określić, czy znajduje się on w pliku wykonywalnym lub pliku. dbg.

 Większość klientów nie będzie potrzebować tego wywołania zwrotnego, ponieważ `IDiaDataSource::loadDataForExe` Metoda w sposób przezroczysty otwiera zarówno pliki. pdb, jak i. dbg, gdy jest to niezbędne do obsłużynia symboli.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
