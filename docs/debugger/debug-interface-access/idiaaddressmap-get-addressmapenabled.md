---
description: Wskazuje, czy mapa adresów została ustanowiona dla konkretnej sesji.
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a55ff89e97d1898ec2ced2b62f7cdfa5a0df817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149110"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Wskazuje, czy mapa adresów została ustanowiona dla konkretnej sesji.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca `TRUE` czy mapowanie adresu jest włączone.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wykonywalne przetwórcy czasami aktualizują plik wykonywalny. DIA zawiera mechanizm do obsługi tłumaczenia symboli do nowego układu.

 Aplikacje klienckie mogą ustawić mapę adresów dla określonej sesji, pobierając Interfejs [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) z interfejsu [IDiaSession](../../debugger/debug-interface-access/idiasession.md) i wywołując metodę [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) , a następnie wywołanie metody [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . `get_addressMapEnabled`Metoda zwraca wyniki wywołania `put_addressMapEnabled` metody.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
