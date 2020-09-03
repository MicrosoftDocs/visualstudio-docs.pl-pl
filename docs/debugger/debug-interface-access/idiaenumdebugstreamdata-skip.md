---
title: 'IDiaEnumDebugStreamData:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1df1f15e87275da05467de76221d9de2ac6bf237
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468435"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
Pomija określoną liczbę rekordów w wyliczonej kolejności.

## <a name="syntax"></a>Składnia

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametry
 celt

podczas Liczba rekordów do pominięcia w wyliczonej kolejności.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca, `S_FALSE` czy nie ma więcej rekordów do pominięcia.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)