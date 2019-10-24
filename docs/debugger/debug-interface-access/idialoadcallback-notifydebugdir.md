---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
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
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743093"
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

[in] `TRUE`, jeśli katalog debugowania jest odczytywany z pliku wykonywalnego (a nie pliku. dbg).

 `cbData`

podczas Liczba bajtów danych w katalogu debugowania.

 `data[]`

podczas Tablica, która jest wypełniana katalogiem debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod powrotny jest zwykle ignorowany.

## <a name="remarks"></a>Uwagi
 Metoda [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) wywołuje to wywołanie zwrotne, gdy odnajdzie katalog debugowania podczas przetwarzania pliku wykonywalnego.

 Ta metoda eliminuje konieczność odtwarzania pliku wykonywalnego i/lub debugowania przez klienta w celu obsługi informacji debugowania innych niż Znalezione w pliku. pdb. Za pomocą tych danych klient może rozpoznać typ dostępnych informacji debugowania i określić, czy znajduje się on w pliku wykonywalnym lub pliku. dbg.

 Większość klientów nie będzie potrzebować tego wywołania zwrotnego, ponieważ metoda `IDiaDataSource::loadDataForExe` w sposób przezroczysty otwiera zarówno pliki PDB i. dbg, gdy jest to niezbędne do obsłużynia symboli.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)