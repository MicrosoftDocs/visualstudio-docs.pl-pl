---
description: Zezwala klientowi na włączanie lub wyłączanie obliczeń i użycie względnych adresów wirtualnych (RVA).
title: IDiaAddressMap::p ut_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c3aab1379a39ee6abfd977350743e36c9792efb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158323"
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

podczas Ustaw `TRUE` , aby włączyć lub `FALSE` wyłączyć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Adresy dla obiektów debugowania opisanych przez interfejsy DIA i względne dla bazy obrazu pliku wykonywalnego można pobrać jako względne adresy wirtualne.

 Użycie RVA jest włączone, gdy segmenty są początkowo ładowane z pliku PDB. Aby uzyskać bieżący stan użycia elementu RVA, wywołaj metodę [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) .

 `put_relativeVirtualAddress`Metoda musi zostać wywołana w celu włączenia RVA po pomyślnym wywołaniu metody [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) , która ustanowiła nowe nagłówki obrazu.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
