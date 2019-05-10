---
title: Idialoadcallback2::restrictoriginalpathaccess — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 26539d4217682b4d5357f13e9f9368c81297da78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839748"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Określa, czy można szukać pliku .pdb w oryginalny katalog debugowania.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Dowolny kod powrotu innych niż `S_OK` zapobiega szuka pliku .pdb w oryginalny katalog debugowania. Oryginalny katalog debugowania jest ścieżką do pliku symboli, skompilowany do pliku wykonywalnego, jeśli debugowanie jest włączone. Ta ścieżka nie jest zawsze taki sam jak ścieżki, w którym znajduje się plik wykonywalny.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)