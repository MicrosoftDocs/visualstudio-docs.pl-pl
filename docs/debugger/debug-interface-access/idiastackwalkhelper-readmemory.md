---
title: 'IDiaStackWalkHelper:: ReadMemory — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741362"
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

określoną Zwraca liczbę bajtów, które są faktycznie odczytywane. Jeśli `pbData` jest `NULL`, to całkowita liczba dostępnych bajtów danych.

 `pbData`

[in. out] Bufor, który jest wypełniony za pomocą odczytu pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum, wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md)