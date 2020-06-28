---
title: 'IDiaLoadCallback:: RestrictRegistryAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18436d28fbee7ba12cea2398eb1fa6abbd8ac23b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466736"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Określa, czy zapytania rejestru mogą służyć do lokalizowania ścieżek wyszukiwania symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż zapobiega wysyłaniu `S_OK` zapytań do rejestru pod kątem ścieżek wyszukiwania symboli.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)