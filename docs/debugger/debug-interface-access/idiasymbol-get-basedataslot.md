---
title: 'IDiaSymbol:: get_baseDataSlot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f9ed21b7-9397-4813-926e-ade11914b06b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12aa68a549f47b27fd2b750d41631f4fabd546ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740960"
---
# <a name="idiasymbolget_basedataslot"></a>IDiaSymbol::get_baseDataSlot
Pobiera bazowe miejsce na dane.

## <a name="syntax"></a>Składnia

```C++
HRESULT get_baseDataSlot(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

określoną Wskaźnik do `DWORD`, który zawiera bazowe miejsce na dane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` lub kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)