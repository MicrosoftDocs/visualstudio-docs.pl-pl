---
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d733a51bd599b85dcc6d1121b8d21e1a687a351
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745043"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Zezwala klientowi na włączanie lub wyłączanie obliczeń i użycie względnych adresów wirtualnych (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

podczas Ustaw wartość `TRUE`, aby włączyć lub `FALSE` wyłączyć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Adresy dla obiektów debugowania opisanych przez interfejsy DIA i względne dla bazy obrazu pliku wykonywalnego można pobrać jako względne adresy wirtualne.

 Użycie RVA jest włączone, gdy segmenty są początkowo ładowane z pliku PDB. Aby uzyskać bieżący stan użycia elementu RVA, wywołaj metodę [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .

 Należy wywołać metodę `put_relativeVirtualAddress`, aby włączyć RVA po pomyślnym wywołaniu metody [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) , która ustanowiła nowe nagłówki obrazu.

## <a name="see-also"></a>Zobacz także
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)