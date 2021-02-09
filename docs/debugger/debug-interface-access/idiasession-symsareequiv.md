---
title: 'IDiaSession:: symsAreEquiv | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10aa5f1b086856793fe32512867834848b6f7162
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855019"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Sprawdza, czy dwa symbole są równoważne.

## <a name="syntax"></a>Składnia

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parametry
 `symbolA`

podczas Pierwszy obiekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) używany w porównaniu.

 `symbolB`

podczas Drugi `IDiaSymbol` obiekt użyty w porównaniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli symbole są równoważne, zwraca `S_OK` ; w przeciwnym razie, `S_FALSE` symbole nie są równoważne. W przeciwnym razie Zwróć kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)