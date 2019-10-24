---
title: IDiaAddressMap::p ut_imageAlign | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b1a6bf037dc87d84fab21622571158fb0682f60
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745049"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Ustawia wyrównanie obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parametry
 NewVal

podczas Nowa wartość wyrównania obrazu dla pliku wykonywalnego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obrazy (załadowane pliki wykonywalne) są wyrównane do określonych granic pamięci. Na to wyrównanie może mieć wpływ bieżąca architektura systemu oraz opcje kompilacji i łącznego czasu. Wyrównanie obrazu jest zawsze w granicach bajtów. Następujące wartości wyrównania obrazu są prawidłowe: 1, 2, 4, 8, 16, 32 i 64 bajtów.

 Bieżące wyrównanie obrazu można pobrać przy użyciu wywołania metody [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> Obraz jest już załadowany przez czas, gdy ta metoda może być wywoływana. Metoda `put_imageAlign` jest zwykle używana, gdy obraz został przeniesiony lub zmieniony i jest wymagane nowe wyrównanie.

## <a name="see-also"></a>Zobacz także
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)