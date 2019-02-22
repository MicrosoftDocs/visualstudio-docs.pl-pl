---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bcf399dcf80cb574b6018dde5ffa44e72a4c988
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623934"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Biorąc pod uwagę odpowiadająca wartość tagu, Metoda ta zwraca wyliczenie symboli, które są zawarte w funkcji klasy zastępczej akceleratora określonego elementu nadrzędnego w określonym względny adres wirtualny.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

[in] `IDiaSymbol` Odnosi się do funkcji klasy zastępczej akcelerator ma być przeszukiwany.

 `tagValue`

[in] Wartość tagu wskaźnika.

 `rva`

[in] Względny adres wirtualny.

 `ppResult`

[out] Wskaźnik do `IDiaEnumSymbols` wskaźnik interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Tę metodę należy wywołać tylko w systemach `IDiaSymbol` interfejs, który odnosi się do funkcji klasy zastępczej akceleratora.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)