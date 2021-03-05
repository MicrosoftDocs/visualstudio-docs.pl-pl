---
description: Pobiera nazwę strumienia danych debugowania.
title: 'IDiaEnumDebugStreamData:: get_name | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50a3209a9ba73bc83aa24b26575ad04617453254
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158170"
---
# <a name="idiaenumdebugstreamdataget_name"></a>IDiaEnumDebugStreamData::get_name
Pobiera nazwę strumienia danych debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_Name ( 
   BSTR * pRetVal
)
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca nazwę strumienia danych debugowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
