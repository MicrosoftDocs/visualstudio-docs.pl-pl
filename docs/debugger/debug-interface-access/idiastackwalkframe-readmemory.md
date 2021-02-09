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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffd85fd1a6878fd378931901098d90f2a24c8ccc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854802"
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