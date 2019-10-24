---
title: 'IDiaSession:: symsAreEquiv | Microsoft Docs'
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
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741868"
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

podczas Drugi obiekt `IDiaSymbol` używany w porównaniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli symbole są równoważne, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`, symbole nie są równoważne. W przeciwnym razie Zwróć kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)