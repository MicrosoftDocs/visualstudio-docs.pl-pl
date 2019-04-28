---
title: IDiaSession::findInlineeLines | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeed8047cd04e3cfedb5a3beed8dc42c87b551e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827775"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLines ( 
   IDiaSymbol*       parent,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

[in] `IDiaSymbol` Obiekt reprezentujący element nadrzędny.

 `ppResult`

[out] Przechowuje `IDiaEnumLineNumbers` obiektu, który zawiera listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)