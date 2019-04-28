---
title: IDiaAddressMap::get_relativeVirtualAddressEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18a242a47978fbd6acb2b6161ada2199ced8c434
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554299"
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Wskazuje, czy włączono obliczania i Użyj względnych adresów wirtualnych (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

[out] Zwraca `TRUE` Jeśli obliczenie RVA jest włączona.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 RVA są włączone, jeśli segmenty zostały wstępnie załadowane z pliku PDB. Użycie RVA można tymczasowo wyłączyć, wywołując [idiaaddressmap::put_relativevirtualaddressenabled —](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metody.

 Ponadto można nawiązać nowe nagłówki obrazu, wywołując [idiaaddressmap::set_imageheaders —](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) metody następuje po wywołaniu `put_relativeVirtualAddressEnabled` metodę, aby umożliwić użycie RVA przy użyciu nowe nagłówki obrazu.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)