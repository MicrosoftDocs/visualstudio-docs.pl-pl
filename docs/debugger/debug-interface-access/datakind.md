---
title: Datakind — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554925"
---
# <a name="datakind"></a>DataKind
Wskazuje zakresu określonej wartości danych.

## <a name="syntax"></a>Składnia

```C++
enum DataKind {
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
Nie można ustalić symbol DataIsUnknown danych.

Element danych DataIsLocal jest zmienną lokalną.

Element danych DataIsStaticLocal jest statyczna zmienna lokalna.

Element danych DataIsParam jest parametrów formalnych.

Element danych DataIsObjectPtr jest wskaźnikiem obiektu (`this`).

Element danych DataIsFileStatic jest zmienną o zakresie pliku.

Element danych DataIsGlobal jest zmienną globalną.

Element danych DataIsMember jest zmienną elementu członkowskiego obiektu.

Element danych DataIsStaticMember jest zmienna statyczna klasy.

Element danych DataIsConstant jest wartością stałą.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_datakind —](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
