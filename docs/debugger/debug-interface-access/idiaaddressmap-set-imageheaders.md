---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745014"
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

podczas Liczba bajtów danych nagłówka. Musi być `n*sizeof(IMAGE_SECTION_HEADER)`, gdzie `n` jest liczbą nagłówków sekcji w pliku wykonywalnym.

 dane []

podczas Tablica struktur `IMAGE_SECTION_HEADER`, które mają być używane jako nagłówki obrazu.

 originalHeaders

podczas Ustaw na `FALSE`, jeśli nagłówki obrazu pochodzą z nowego obrazu, `TRUE`, jeśli odzwierciedlają oryginalny obraz przed uaktualnieniem. Zwykle zostanie to ustawione na `TRUE` tylko w połączeniu z wywołaniami metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Struktura `IMAGE_SECTION_HEADER` jest zadeklarowana w Winnt. h i reprezentuje format nagłówka sekcji obrazu pliku wykonywalnego.

 Obliczenia względnych adresów wirtualnych zależą od wartości `IMAGE_SECTION_HEADER`. Zazwyczaj DIA pobiera je z pliku bazy danych programu (. pdb). Jeśli brakuje tych wartości, DIA nie jest w stanie obliczyć względnych adresów wirtualnych, a Metoda [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) zwraca `FALSE`. Klient musi następnie wywołać metodę [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) , aby włączyć względne obliczenia adresów wirtualnych po dostarczeniu brakującego nagłówka obrazu z obrazu.

## <a name="see-also"></a>Zobacz także
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)