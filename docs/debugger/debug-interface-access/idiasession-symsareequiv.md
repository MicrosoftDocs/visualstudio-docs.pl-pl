---
title: Idiasession::symsareequiv — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0253104cf29e86825fadc8c8bd18133e0d3cf593
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613053"
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

[in] Pierwszy [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt używany do porównania.

 `symbolB`

[in] Drugi `IDiaSymbol` obiekt używany do porównania.

## <a name="return-value"></a>Wartość zwracana
 Symbole są równoważne, funkcja zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`, symbole nie są równoważne. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)