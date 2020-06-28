---
title: 'IDiaSymbol:: get_builtInKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d32b4264047fe8dc787b3eac8e33877c883b200e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464157"
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