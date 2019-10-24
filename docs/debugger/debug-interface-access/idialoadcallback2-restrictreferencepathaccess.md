---
title: 'IDiaLoadCallback2:: RestrictReferencePathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3406052f4d5466b5b7f52a1da3490d35bbb0508f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742982"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Określa, czy wyszukiwanie pliku. pdb jest dozwolone w ścieżce, w której znajduje się plik. exe.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż `S_OK`, aby zapobiec szukaniu pliku. pdb w ścieżce, w której znajduje się plik. exe.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)