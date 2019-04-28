---
title: Idiasession::findsymbolbytoken — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f342efce1c05e305a3e55d6372d1862b04b1197
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827313"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
Pobiera symbol, który zawiera token określonych metadanych.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolByToken ( 
   ULONG        token,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametry
 `token`

[in] Określa tokenu.

 `symtag`

[in] Typ symbolu, który ma zostać odnaleziona. Wartości są pobierane z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia.

 `ppSymbol`

[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) pobrać obiekt reprezentujący symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)