---
title: Idiasession::findlines — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b127cbc5c9ddc5a2aa2d293d1371bab18d191fdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839293"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Pobiera numery wierszy w ramach określonego compiland — i identyfikatory plików źródłowych.

## <a name="syntax"></a>Składnia

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `compiland`

[in] [Idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiekt reprezentujący compiland —. Używaj tego interfejsu, ponieważ kontekst, w których należy szukać numery wierszy.

 `file`

[in] [Idiasourcefile —](../../debugger/debug-interface-access/idiasourcefile.md) obiekt reprezentujący pliku źródłowego, w których należy szukać numerów wierszy.

 `ppResult`

[out] Zwraca [idiaenumlinenumbers —](../../debugger/debug-interface-access/idiaenumlinenumbers.md) pobrać obiekt, który zawiera listę numerów wierszy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)