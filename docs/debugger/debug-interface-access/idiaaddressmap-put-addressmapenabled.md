---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3ebfcc5b76765a8fbfbe2be9ccef2112d351039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865273"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Określa, czy mapa adresów ma być używana do tłumaczenia adresów symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

podczas Ustaw `TRUE` , aby włączyć tłumaczenie symboli lub `FALSE` wyłączyć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wykonywalne przetwórcy czasami aktualizują plik wykonywalny. DIA zawiera mechanizm do obsługi tłumaczenia symboli do nowego układu.

 Po załadowaniu pliku PDB Mapa adresów przechowywana w pliku jest włączona. Istnieją jednak przypadki, gdy aplikacja kliencka może wymagać dostarczenia własnej mapy adresów przez wywołanie metody [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Jeśli metoda zakończy `set_addressMap` się pomyślnie, aplikacja kliencka musi wywołać `put_addressMapEnabled` metodę z `NewVal` parametrem, `TRUE` Aby umożliwić korzystanie z tej mapy adresów.

 Bieżący stan włączonego mapowania adresów można pobrać z wywołaniem metody [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)