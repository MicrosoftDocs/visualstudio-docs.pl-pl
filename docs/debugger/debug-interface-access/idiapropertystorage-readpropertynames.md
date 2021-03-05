---
description: Pobiera odpowiednie nazwy ciągów dla danego identyfikatora właściwości.
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbb6d511a6be9ed408b076162a3d00d22705075a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148144"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Pobiera odpowiednie nazwy ciągów dla danego identyfikatora właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parametry
 `cpropid`

podczas Liczba identyfikatorów właściwości w `rgpropid` .

 `rgpropid`

podczas Tablica identyfikatorów właściwości, dla których mają zostać pobrane nazwy ( `PROPID` jest definiowana w WTypes. h jako `ULONG` ).

 `rglpwstrName`

[in. out] Tablica nazw właściwości dla określonych identyfikatorów właściwości. Tablica musi być wstępnie przydzieloną, aby można było przechowywać żądaną liczbę nazw właściwości i musi być w stanie przechowywać co najmniej `cpropid``BSTR` ciągi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwracane nazwy właściwości muszą być zwolnione (przez wywołanie `SysFreeString` funkcji), gdy nie są już potrzebne.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
