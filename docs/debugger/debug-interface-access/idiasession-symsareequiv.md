---
description: Sprawdza, czy dwa symbole są równoważne.
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
ms.openlocfilehash: c5f887b13195bdde133c4bca845291b1255b99ea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156987"
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
