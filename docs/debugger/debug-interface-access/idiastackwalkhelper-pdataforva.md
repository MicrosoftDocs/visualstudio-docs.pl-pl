---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741405"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Zwraca blok danych PDATA skojarzony z adresem wirtualnym.

## <a name="syntax"></a>Składnia

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parametry
 `va`

podczas Określa adres wirtualny danych do uzyskania.

 `cbData`

podczas Rozmiar danych w bajtach do uzyskania.

 `pcbData`

określoną Zwraca rzeczywisty rozmiar danych uzyskanych w bajtach.

 `pbData`

[in. out] Bufor, który jest wypełniony danymi żądanymi. Nie można `NULL`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`. Zwraca `S_FALSE`, jeśli nie ma żadnych PDATA dla podanego adresu. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 PDATA (sekcja o nazwie ". pdata") jednostka kompilacji zawiera informacje o obsłudze wyjątków dla funkcji.

 Obiekt wywołujący wie, ile danych ma zostać zwróconych, aby obiekt wywołujący nie musiał żądać ilości dostępnych danych. W związku z tym jest akceptowalny dla implementacji tej metody w celu zwrócenia błędu, jeśli parametr `pbData` jest `NULL`.

## <a name="see-also"></a>Zobacz także
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)