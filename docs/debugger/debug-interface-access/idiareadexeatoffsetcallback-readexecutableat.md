---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742832"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Odczytuje określoną liczbę bajtów rozpoczynając od określonego przesunięcia z pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametry
 fileOffset

podczas Przesunięcie w pliku wykonywalnym, aby rozpocząć odczytywanie.

 cbData

podczas Liczba bajtów do odczytu.

 pcbData

określoną Zwraca liczbę odczytanych bajtów.

 dane []

[in. out] Tablica, która jest uzupełniona o bajty odczytywane z pliku.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana przez kod obsługi DIA do ładowania bajtów danych z pliku wykonywalnego przy użyciu bezwzględnego przesunięcia pliku. Ta metoda jest wywoływana w ramach obsługi metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)