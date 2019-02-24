---
title: Idialoadcallback::restrictsymbolserveraccess — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0de567f0417714e1246e11ba074c9b0134e92ce8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618630"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Określa, jeśli jest dozwolony dostęp do serwera symboli można rozpoznać symboli.

## <a name="syntax"></a>Składnia

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Dowolny kod powrotu innych niż `S_OK` uniemożliwia korzystanie z serwera symboli w celu rozpoznania symboli.

## <a name="see-also"></a>Zobacz też
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)