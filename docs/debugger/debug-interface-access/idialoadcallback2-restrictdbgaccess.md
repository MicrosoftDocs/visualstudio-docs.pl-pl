---
title: 'IDiaLoadCallback2:: RestrictDBGAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd54587127d434f79cf8d80aa130f5135bb7aeb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466715"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Określa, czy wyszukiwanie informacji debugowania jest dozwolone z plików. dbg.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictDBGAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszystkie wartości zwracane `S_OK` od, aby zapobiec szukaniu informacji debugowania z plików. dbg.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)