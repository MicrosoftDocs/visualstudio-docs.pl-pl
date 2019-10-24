---
title: 'IDiaLoadCallback2:: RestrictSystemRootAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cf1a29019de2d3ffdfdb3cc7b9006e964495aa9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742974"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Określa, czy wyszukiwanie plików. pdb jest dozwolone w katalogu głównym systemu.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż `S_OK` uniemożliwia wyszukiwanie w katalogu głównym systemu plików. pdb.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)