---
title: Udtkind — | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 511beae100529f0db555eca0a8ddb995d7a335d1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636583"
---
# <a name="udtkind"></a>UdtKind
W tym artykule opisano różne typy zdefiniowane przez użytkownika (UDT).

## <a name="syntax"></a>Składnia

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elementy
UdtStruct UDT jest strukturą.

UdtClass UDT jest klasą.

UdtUnion UDT jest Unii.

UdtInterface UDT jest interfejsem.

## <a name="remarks"></a>Uwagi
Wartości w tym wyliczeniu są zwracane przez [idiasymbol::get_udtkind —](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: cvconst.h

## <a name="see-also"></a>Zobacz też
- [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
