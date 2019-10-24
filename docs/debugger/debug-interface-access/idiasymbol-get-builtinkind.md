---
title: 'IDiaSymbol:: get_builtInKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 183e4da9eebb1a6b26bceb38a3f00a5a64864c8a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740896"
---
# <a name="idiasymbolget_builtinkind"></a>IDiaSymbol::get_builtInKind
Pobiera wbudowany rodzaj typu HLSL.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_buildInKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `DWORD`, który posiada wbudowany rodzaj typu HLSL.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)