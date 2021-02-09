---
title: 'IDiaSymbol:: get_builtInKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7bc90c83ec789920d89bb424e6c7a6464c0ce8f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863537"
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

określoną Wskaźnik do obiektu `DWORD` , który posiada wbudowany rodzaj typu HLSL.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)