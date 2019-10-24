---
title: 'IDiaStackWalkFrame:: ReadMemory — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741478"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Odczytuje pamięć z obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametry
 `type`

podczas Jedna z wartości wyliczenia [memorytypeenum —](../../debugger/debug-interface-access/memorytypeenum.md) , która określa rodzaj pamięci do uzyskania dostępu.

 `va`

podczas Lokalizacja adresu wirtualnego w obrazie do rozpoczęcia odczytywania.

 `cbData`

podczas Rozmiar buforu danych w bajtach.

 `pcbData`

określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` jest `NULL`, `pcbData` zawiera łączną liczbę dostępnych bajtów danych.

 `data`

określoną Bufor, który ma zostać wypełniony danymi z określonej lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)