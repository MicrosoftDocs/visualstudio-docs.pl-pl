---
description: Odczytuje blok danych z obrazu pliku wykonywalnego w pamięci.
title: 'IDiaStackWalkHelper:: ReadMemory — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a70cc9660e872a3e64e202d7498814b3aa24daa3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158888"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Odczytuje blok danych z obrazu pliku wykonywalnego w pamięci.

## <a name="syntax"></a>Składnia

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parametry
 `type`

podczas Wartość z wyliczenia [Memorytypeenum — Wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md) określa typ pamięci do odczytania.

 VA

podczas Adres wirtualny w obrazie, od którego ma się zacząć odczytywanie.

 `cbData`

podczas Rozmiar buforu danych w bajtach.

 `pcbData`

określoną Zwraca liczbę bajtów, które są faktycznie odczytywane. Jeśli `pbData` jest `NULL` , jest to całkowita liczba dostępnych bajtów danych.

 `pbData`

[in. out] Bufor, który jest wypełniony za pomocą odczytu pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum, wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md)
