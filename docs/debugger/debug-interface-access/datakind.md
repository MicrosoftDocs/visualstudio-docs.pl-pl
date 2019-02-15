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
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318683"
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
DataIsUnknown  
Nie można ustalić symbol danych.

DataIsLocal  
Element danych jest zmienną lokalną.

DataIsStaticLocal  
Element danych jest statyczna zmienna lokalna.

DataIsParam  
Element danych jest parametrów formalnych.

DataIsObjectPtr  
Element danych jest wskaźnikiem obiektu (`this`).

DataIsFileStatic  
Element danych jest zmienną o zakresie pliku.

DataIsGlobal  
Element danych jest zmienną globalną.

DataIsMember  
Element danych jest zmienną elementu członkowskiego obiektu.

DataIsStaticMember  
Element danych jest zmienna statyczna klasy.

DataIsConstant  
Element danych jest wartością stałą.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_datakind —](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
[Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
