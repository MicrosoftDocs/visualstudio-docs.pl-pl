---
description: Wskazuje, czy jest włączone Obliczanie i użycie względnych adresów wirtualnych (RVA).
title: 'IDiaAddressMap:: get_relativeVirtualAddressEnabled | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5383772ca95d3dada7218643b483d2ca5d056613
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158428"
---
# <a name="idiaaddressmapget_relativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Wskazuje, czy jest włączone Obliczanie i użycie względnych adresów wirtualnych (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT get_relativeVirtualAddressEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca `TRUE` czy obliczanie RVA jest włączone.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 RVA są włączone, jeśli segmenty zostały początkowo załadowane z pliku PDB. Korzystanie z RVA może być tymczasowo wyłączone przez wywołanie metody [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) .

 Ponadto nowe nagłówki obrazu można ustalić, wywołując metodę [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) , a następnie wywołanie `put_relativeVirtualAddressEnabled` metody, aby umożliwić korzystanie z RVA przy użyciu nowych nagłówków obrazu.

## <a name="see-also"></a>Zobacz też
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
