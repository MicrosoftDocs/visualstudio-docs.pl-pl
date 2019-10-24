---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745027"
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

podczas Liczba elementów w parametrze `data`.

 `data[]`

podczas Tablica struktur [struktury DiaAddressMapEntry —](../../debugger/debug-interface-access/diaaddressmapentry.md) , które definiują mapę translacji.

 `imagetoSymbols`

[in] `TRUE`, jeśli parametr `data` definiuje mapę z nowego układu obrazu do oryginalnego układu (zgodnie z opisem przez symbole debugowania). `FALSE`, jeśli `data` jest mapą do nowego układu obrazu pobranego z oryginalnego układu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zazwyczaj DIA Pobiera mapowania translacji adresów z pliku bazy danych programu (. pdb). Jeśli brakuje tych wartości, Metoda [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) jest wywoływana dwukrotnie, raz z parametrem `imagetoSymbols` ustawionym na `TRUE` i jeden raz z parametrem `imagetoSymbols` ustawionym na `FALSE`. Nie można włączyć translacji mapowania adresów przy użyciu metody [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , jeśli nie podano obydwu map tłumaczeń.

## <a name="see-also"></a>Zobacz także
- [DiaAddressMapEntry, struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)