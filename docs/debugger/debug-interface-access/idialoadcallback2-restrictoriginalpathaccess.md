---
description: Określa, czy można wyszukać plik. pdb w oryginalnym katalogu debugowania.
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7af6794b57dfe5efe8d2e85f8e74febcede5ef23
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157428"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Określa, czy można wyszukać plik. pdb w oryginalnym katalogu debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy kod powrotny inny niż `S_OK` zapobiega szukaniu pliku. pdb w oryginalnym katalogu debugowania. Oryginalny katalog debugowania jest ścieżką do pliku symboli skompilowaną w pliku wykonywalnym, gdy debugowanie jest włączone. Ta ścieżka nie musi być taka sama jak ścieżka, w której znajduje się plik wykonywalny.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
