---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bcdaa7c1896a0ef29706e3650ad8ac56537f778
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742999"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Określa, czy można wyszukać plik. pdb w oryginalnym katalogu debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż `S_OK` uniemożliwia wyszukanie pliku. pdb w oryginalnym katalogu debugowania. Oryginalny katalog debugowania jest ścieżką do pliku symboli skompilowaną w pliku wykonywalnym, gdy debugowanie jest włączone. Ta ścieżka nie musi być taka sama jak ścieżka, w której znajduje się plik wykonywalny.

## <a name="see-also"></a>Zobacz także
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)