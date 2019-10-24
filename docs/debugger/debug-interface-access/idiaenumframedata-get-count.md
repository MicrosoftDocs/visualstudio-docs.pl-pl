---
title: 'IDiaEnumFrameData:: get_Count | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get_Count method
ms.assetid: 94374d27-e335-4e90-a442-233181ab8e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec182918cccb42cf4d1c3cfdb3ae816aeef97a73
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744638"
---
# <a name="idiaenumframedataget_count"></a>IDiaEnumFrameData::get_Count
Pobiera liczbę elementów danych ramek.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

określoną Zwraca liczbę elementów danych ramek.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)