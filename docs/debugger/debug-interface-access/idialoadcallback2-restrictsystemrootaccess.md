---
description: Określa, czy wyszukiwanie plików. pdb jest dozwolone w katalogu głównym systemu.
title: 'IDiaLoadCallback2:: RestrictSystemRootAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7d38f18a9e0cc0510e237780c4361acb086125eb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157386"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
Określa, czy wyszukiwanie plików. pdb jest dozwolone w katalogu głównym systemu.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictSystemRootAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż `S_OK` uniemożliwia wyszukiwanie w katalogu głównym systemu plików. pdb.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
