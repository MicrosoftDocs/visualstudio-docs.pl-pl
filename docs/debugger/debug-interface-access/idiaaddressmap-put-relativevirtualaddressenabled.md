---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs
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
ms.openlocfilehash: 371db781cae5c988e6c8ff4c4776c5f43d6f047a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554355"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Pozwoli to klientowi włączyć lub wyłączyć Obliczanie i Użyj względnych adresów wirtualnych (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

[in] Ustaw `TRUE` umożliwiające, lub `FALSE` można wyłączyć.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Adresy dla obiektów debugowania opisane przez interfejsy DIA i względem pliku wykonywalnego obrazu podstawowego, mogą być pobierane jako względnych adresów wirtualnych.

 Użycie RVA jest włączona, gdy segmentów są wstępnie załadowane z pliku PDB. Aby uzyskać bieżący stan użytkowania RVA, należy wywołać [idiaaddressmap::get_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metody.

 `put_relativeVirtualAddress` Można wywołać metody, aby włączyć RVA po pomyślnym wywołaniem [idiaaddressmap::set_imageheaders —](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metoda ustanowiła nowe nagłówki obrazu.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)