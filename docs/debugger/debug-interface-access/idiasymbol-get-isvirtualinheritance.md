---
title: IDiaSymbol::get_isVirtualInheritance | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5d1630b46ca2203e9f935517e96b11856b273b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842127"
---
# <a name="idiasymbolgetisvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
Określa, czy `this` wskaźnik wskazuje na element członkowski danych za pomocą wirtualnego dziedziczenia.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

[out] Wskaźnik do `BOOL` określająca czy `this` wskaźnik wskazuje na element członkowski danych za pomocą wirtualnego dziedziczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` albo kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)