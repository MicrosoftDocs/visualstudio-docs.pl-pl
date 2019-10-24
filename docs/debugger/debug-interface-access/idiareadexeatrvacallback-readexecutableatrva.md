---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742785"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Odczytuje określoną liczbę bajtów, zaczynając od określonego względnego adresu wirtualnego (RVA) z pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `relativeVirtualAddress`

podczas Adres RVA w pliku wykonywalnym, aby rozpocząć odczytywanie.

 `cbData`

podczas Liczba bajtów do odczytu.

 `pcbData`

określoną Zwraca liczbę odczytanych bajtów.

 `data[]`

[in. out] Tablica, która jest uzupełniona o Bajty odczytane z pliku.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana przez kod obsługi DIA do ładowania bajtów danych z pliku wykonywalnego przy użyciu względnego adresu wirtualnego. Ta metoda jest wywoływana w ramach obsługi metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)