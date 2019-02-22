---
title: IDiaStackWalkHelper::readMemory | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: dc89ad289d27579a81e7bbe869aab14e152bd6db
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611025"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Odczytuje blok danych z pliku wykonywalnego obrazu w pamięci.

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

[in] Wartość z zakresu od [memorytypeenum — wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md) wyliczenie opisujące typ pamięci do odczytu.

 va

[in] Wirtualny adres obrazu, w którym ma rozpocząć się odczyt.

 `cbData`

[in] Rozmiar buforu danych w bajtach.

 `pcbData`

[out] Zwraca liczbę bajtów odczytanych w rzeczywistości. Jeśli `pbData` jest `NULL`, a następnie jest to całkowita liczba bajtów dostępnych danych.

 `pbData`
- [out w] Buforu, który jest wypełniane pamięci odczytu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum, wyliczenie](../../debugger/debug-interface-access/memorytypeenum.md)