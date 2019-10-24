---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742869"
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

podczas Liczba identyfikatorów właściwości w `rgpropid`.

 `rgpropid`

podczas Tablica identyfikatorów właściwości, dla których mają zostać pobrane nazwy (`PROPID` jest zdefiniowana w WTypes. h jako `ULONG`).

 `rglpwstrName`

[in. out] Tablica nazw właściwości dla określonych identyfikatorów właściwości. Tablica musi być wstępnie przydzieloną, aby można było przechowywać żądaną liczbę nazw właściwości i musi być w stanie przechowywać co najmniej `cpropid``BSTR` ciągi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwracane nazwy właściwości muszą zostać zwolnione (przez wywołanie funkcji `SysFreeString`), gdy nie są już potrzebne.

## <a name="see-also"></a>Zobacz także
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)