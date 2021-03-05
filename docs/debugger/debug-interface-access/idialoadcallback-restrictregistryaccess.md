---
description: Określa, czy zapytania rejestru mogą służyć do lokalizowania ścieżek wyszukiwania symboli.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b94821dc2ebf3a3af6b6b560d972c8376e56e6a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157463"
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
