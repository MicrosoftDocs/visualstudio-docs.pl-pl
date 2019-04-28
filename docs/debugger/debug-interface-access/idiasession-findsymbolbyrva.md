---
title: Idiasession::findsymbolbyrva — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf6a32284588163aae57d03ec67c69a9f64663b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839228"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
Pobiera typ określony symbol, który zawiera lub jest najbardziej zbliżony do określonego względny adres wirtualny (RVA).

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolByRVA ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parametry
 `rva`

[in] Określa adres RVA.

 `symtag`

[in] Typ symbolu, który ma zostać odnaleziona. Wartości są pobierane z [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia.

 `ppSymbol`

[out] Zwraca [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) pobrać obiekt reprezentujący symbol.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)