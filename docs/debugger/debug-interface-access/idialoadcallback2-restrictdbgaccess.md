---
title: 'IDiaLoadCallback2:: RestrictDBGAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 79756c2f9ab9e69fa45041e2ddaa2ff2119c27c5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743014"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Określa, czy wyszukiwanie informacji debugowania jest dozwolone z plików. dbg.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictDBGAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wszelkie wartości zwracające inne niż `S_OK` uniemożliwiają wyszukiwanie informacji debugowania z plików. dbg.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)