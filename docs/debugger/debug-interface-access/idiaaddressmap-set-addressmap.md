---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
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
ms.openlocfilehash: 963ee64b639780bae60a4c2655db8b666d87c702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554251"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Zawiera mapę adresu do obsługi obrazów układ tłumaczenia.

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

[in] Liczba elementów w `data` parametru.

 `data[]`

[in] Tablica [diaaddressmapentry — struktura](../../debugger/debug-interface-access/diaaddressmapentry.md) struktur, które definiują mapy tłumaczenia.

 `imagetoSymbols`

[in] `TRUE` Jeśli `data` parametr określa mapowanie z nowego układu obrazu do oryginalnego układu (zgodnie z opisem, za pomocą symboli debugowania). `FALSE` Jeśli `data` mapy do nowego układu obrazu z oryginalnego układu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zazwyczaj DIA pobiera mapy translacji adresów z plik bazy danych (PDB) programu. Jeśli te wartości są spełnione, [idiaaddressmap::set_imageheaders —](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda jest wywoływana dwa razy, jeden raz z `imagetoSymbols` parametr `TRUE` i raz przy użyciu `imagetoSymbols` parametr `FALSE`. Translacje mapy adresów nie można włączyć za pomocą [idiaaddressmap::put_addressmapenabled —](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metody, chyba że znajdują się zarówno mapy tłumaczenia.

## <a name="see-also"></a>Zobacz też
- [DiaAddressMapEntry, struktura](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)