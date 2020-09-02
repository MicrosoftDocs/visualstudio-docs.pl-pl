---
title: IDiaStackWalkHelper::p dataForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: d6e9b3e812311ef3d9555584d72ebb966098232a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464710"
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

[in. out] Bufor, który jest wypełniony danymi żądanymi. Nie może być `NULL` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy dla podanego adresu nie ma pdata. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 PDATA (sekcja o nazwie ". pdata") jednostka kompilacji zawiera informacje o obsłudze wyjątków dla funkcji.

 Obiekt wywołujący wie, ile danych ma zostać zwróconych, aby obiekt wywołujący nie musiał żądać ilości dostępnych danych. W związku z tym jest akceptowalny dla implementacji tej metody w celu zwrócenia błędu, jeśli `pbData` parametr ma wartość `NULL` .

## <a name="see-also"></a>Zobacz też
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)