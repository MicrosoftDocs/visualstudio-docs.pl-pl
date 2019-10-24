---
title: 'IDiaSymbol:: get_isSingleInheritance | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96a8ce072fc57dc236dd2025b8ea3c9c5a4b9b79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740057"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Określa, czy `this` wskaźnik wskazuje element członkowski danych z pojedynczym dziedziczeniem.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `BOOL`, który określa, czy `this` wskaźnik wskazuje element członkowski danych z pojedynczym dziedziczeniem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)