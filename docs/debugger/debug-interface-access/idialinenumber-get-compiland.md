---
title: Idialinenumber::get_compiland — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25d990ab019c01daf1f977464211fb72838275a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829046"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
Pobiera odwołanie do symbolu dla compiland —, mówiąca bajtów tekst obrazu.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt compiland —, mówiąca bajtów tekst obrazu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli ta właściwość nie jest obsługiwana. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)