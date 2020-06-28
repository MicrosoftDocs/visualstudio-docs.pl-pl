---
title: 'IDiaStackWalkFrame:: ReadMemory — | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: f682f3fe0e300f84dc28b959497138a5019f954b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464829"
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

określoną Zwraca liczbę zwracanych bajtów. Jeśli `data` jest `NULL` , `pcbData` zawiera łączną liczbę dostępnych bajtów danych.

 `data`

określoną Bufor, który ma zostać wypełniony danymi z określonej lokalizacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)