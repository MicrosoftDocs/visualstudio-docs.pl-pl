---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72510e9e82c1ec6983075880d4335dee8c0ad23c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642225"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
Zwraca wyliczenie symboli dla zmiennej, która odpowiada wartości określonego tagu w obiekcie nadrzędnym funkcji klasy zastępczej akceleratora.

## <a name="syntax"></a>Składnia

```C++
HRESULT findSymbolsForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

[in] Idiasymbol —, która odnosi się do funkcji klasy zastępczej akcelerator ma być przeszukiwany.

 `tagValue`

[in] Wartość tagu wskaźnika.

 `ppResult`

[out] Wskaźnik do `IDiaEnumSymbols` wskaźnik interfejsu, który jest inicjowany z wynikiem.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)