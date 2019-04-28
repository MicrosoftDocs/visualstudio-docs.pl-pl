---
title: IDiaSession::findInlineeLinesByAddr | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a40cc8afdb60ad8ad76a0d6ee8e502a6a0b720b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832542"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Pobiera wyliczenie, które umożliwia klientowi iteracyjne przeglądanie informacji o numerze wiersza wszystkich funkcji, które są śródwierszowych, bezpośrednio lub pośrednio, za pomocą symbolu określonego elementu nadrzędnego i znajdują się w obrębie określonego zakresu adresów.

## <a name="syntax"></a>Składnia

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

[in] `IDiaSymbol` Obiekt reprezentujący element nadrzędny.

 `isect`

[in] Określa składnik części adresu.

 `offset`

[in] Określa przesunięcie składnik adresu.

 `length`

[in] Określa zakres adresów w liczbę bajtów, aby pokrywał się z tym zapytaniem.

 `ppResult`

[out] Przechowuje `IDiaEnumLineNumbers` obiektu, który zawiera listę numerów wierszy, które są pobierane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum, wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)