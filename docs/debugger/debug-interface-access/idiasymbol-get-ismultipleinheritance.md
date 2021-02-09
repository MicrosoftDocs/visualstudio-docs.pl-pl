---
title: 'IDiaSymbol:: get_isMultipleInheritance | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a50966270f91d941d825712938851ec5a06f0892
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99854074"
---
# <a name="idiasymbolget_ismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Określa, czy `this` wskaźnik wskazuje element członkowski danych z wielokrotnym dziedziczeniem.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do elementu `BOOL` , który określa, czy `this` wskaźnik wskazuje element członkowski danych z wielokrotnym dziedziczeniem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)