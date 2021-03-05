---
description: Pobiera sumę kontrolną b.
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aac5b35c98b8bb5b11bc623a274949ee32d9229
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147598"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Pobiera sumę kontrolną b.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

podczas Rozmiar buforu danych w bajtach.

 `pcbData`

określoną Zwraca liczbę bajtów sum kontrolnych. Ten parametr nie może być `NULL` .

 `data`

[in. out] Bufor wypełniony sumą kontrolną. Jeśli ten parametr ma `NULL` wartość, `pcbData` zwraca liczbę wymaganych bajtów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby określić typ algorytmu sum kontrolnych, który został użyty do wygenerowania bajtów sumy kontrolnej, wywołaj metodę [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 Suma kontrolna jest zazwyczaj generowana na podstawie obrazu pliku źródłowego, więc zmiany w pliku źródłowym zostaną odzwierciedlone w zmianach w bajtach sum kontrolnych. Jeśli liczba bajtów sum kontrolnych nie jest zgodna z sumą kontrolną wygenerowaną na podstawie załadowanego obrazu pliku, plik powinien być uważany za uszkodzony lub naruszony.

 Typowe sumy kontrolne nigdy nie przekraczają 32 bajtów, ale nie zakładają, że jest to maksymalny rozmiar sumy kontrolnej. Ustaw `data` parametr na `NULL` , aby uzyskać liczbę bajtów potrzebnych do pobrania sumy kontrolnej. Następnie przydziel bufor o odpowiednim rozmiarze i Wywołaj tę metodę jeszcze raz z nowym buforem.

## <a name="see-also"></a>Zobacz też
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
