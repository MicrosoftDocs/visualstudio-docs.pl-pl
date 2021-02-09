---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63bf56b7749033ecc99c7ba1ef0c9357c95542d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865280"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Ustawia nagłówki obrazu w celu włączenia względnej translacji adresów wirtualnych.

## <a name="syntax"></a>Składnia

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parametry
 cbData

podczas Liczba bajtów danych nagłówka. Musi mieć `n*sizeof(IMAGE_SECTION_HEADER)` miejsce `n` , gdzie jest liczbą nagłówków sekcji w pliku wykonywalnym.

 dane []

podczas Tablica struktur,  `IMAGE_SECTION_HEADER` która ma być używana jako nagłówki obrazu.

 originalHeaders

podczas Ustaw na `FALSE` , jeśli nagłówki obrazu pochodzą z nowego obrazu, `TRUE` Jeśli zostaną one odzwierciedlone przed uaktualnieniem. Zwykle jest to ustawienie `TRUE` tylko w połączeniu z wywołaniami metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `IMAGE_SECTION_HEADER`Struktura jest zadeklarowana w Winnt. h i reprezentuje format nagłówka sekcji obrazu pliku wykonywalnego.

 Obliczenia względnych adresów wirtualnych zależą od `IMAGE_SECTION_HEADER` wartości. Zazwyczaj DIA pobiera je z pliku bazy danych programu (. pdb). Jeśli brakuje tych wartości, DIA nie jest w stanie obliczyć względnych adresów wirtualnych, a Metoda [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) zwraca wartość `FALSE` . Klient musi następnie wywołać metodę [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) , aby włączyć względne obliczenia adresów wirtualnych po dostarczeniu brakującego nagłówka obrazu z obrazu.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)