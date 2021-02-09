---
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
ms.openlocfilehash: 8ed505938636c9cccb69a927cdafbcb9589b35bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863803"
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