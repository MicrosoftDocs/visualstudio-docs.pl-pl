---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745062"
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

podczas Ustaw wartość `TRUE`, aby umożliwić tłumaczenie symboli lub `FALSE` do wyłączenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wykonywalne przetwórcy czasami aktualizują plik wykonywalny. DIA zawiera mechanizm do obsługi tłumaczenia symboli do nowego układu.

 Po załadowaniu pliku PDB Mapa adresów przechowywana w pliku jest włączona. Czasami jednak, gdy aplikacja kliencka może potrzebować własnej mapy adresów, wywołując metodę [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Jeśli `set_addressMap` Metoda zakończy się pomyślnie, aplikacja kliencka musi wywołać metodę `put_addressMapEnabled` za pomocą `NewVal` parametru `TRUE`, aby umożliwić korzystanie z tej mapy adresów.

 Bieżący stan włączonego mapowania adresów można pobrać z wywołaniem metody [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Zobacz także
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)