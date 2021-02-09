---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4c4a450522ea97ee5b0b11993e8e4b6474de4a9f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857175"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Udostępnia mapę adresów do obsługi tłumaczenia układu obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

podczas Liczba elementów w `data` parametrze.

 `data[]`

podczas Tablica struktur [struktury DiaAddressMapEntry —](../../debugger/debug-interface-access/diaaddressmapentry.md) , które definiują mapę translacji.

 `imagetoSymbols`

[w] `TRUE` Jeśli `data` parametr definiuje mapę z nowego układu obrazu do oryginalnego układu (zgodnie z opisem przez symbole debugowania). `FALSE` Jeśli `data` jest mapą do nowego układu obrazu pobranego z oryginalnego układu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zazwyczaj DIA Pobiera mapowania translacji adresów z pliku bazy danych programu (. pdb). Jeśli brakuje tych wartości, Metoda [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) jest wywoływana dwukrotnie, raz z `imagetoSymbols` parametrem ustawionym na `TRUE` i jeden raz z `imagetoSymbols` parametrem ustawionym na `FALSE` . Nie można włączyć translacji mapowania adresów przy użyciu metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , chyba że podano oba mapy tłumaczeń.

## <a name="see-also"></a>Zobacz też
- [DiaAddressMapEntry, struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)