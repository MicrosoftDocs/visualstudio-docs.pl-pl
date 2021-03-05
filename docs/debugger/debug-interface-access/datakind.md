---
description: Wskazuje konkretny zakres wartości danych.
title: Typ datakind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24f13fc1157dd7f3de723474091a1f80e3717504
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151316"
---
# <a name="datakind"></a>DataKind
Wskazuje konkretny zakres wartości danych.

## <a name="syntax"></a>Składnia

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementy
Nie można określić symbolu danych DataIsUnknown.

Element danych DataIsLocal jest zmienną lokalną.

Element danych DataIsStaticLocal jest statyczną zmienną lokalną.

Element danych DataIsParam jest parametrem formalnym.

Element danych DataIsObjectPtr jest wskaźnikiem obiektu ( `this` ).

Element danych DataIsFileStatic jest zmienną o zakresie pliku.

Element danych DataIsGlobal jest zmienną globalną.

Element danych DataIsMember jest zmienną elementu członkowskiego obiektu.

Element danych DataIsStaticMember jest zmienną statyczną klasy.

Element danych DataIsConstant jest stałą wartością.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez metodę [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst. h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
