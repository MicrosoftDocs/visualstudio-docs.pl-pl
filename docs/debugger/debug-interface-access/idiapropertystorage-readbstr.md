---
title: 'IDiaPropertyStorage:: ReadBSTR | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f83d31d36f7d6c067cd3dbd4d64f804ca6f9ebd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864643"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Odczytuje `BSTR` wartości w zestawie właściwości.

## <a name="syntax"></a>Składnia

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametry
 `id`

podczas Identyfikator właściwości do odczytania ( `PROPID` jest zdefiniowany w WTypes. h jako `ULONG` ).

 `pValue`

określoną Zwraca wartość właściwości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_INVALIDARG` czy właściwość nie jest typu `BSTR` .

## <a name="remarks"></a>Uwagi
 A `BSTR` jest definiowana przez system Windows jako ciąg znaków dwubajtowych zakończony zerem.

## <a name="see-also"></a>Zobacz też
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)