---
title: IDebugDynamicField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58a4838afc0d52ab60ae0a11de419393d68dfc06
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351344"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Ten interfejs reprezentuje typ zmiennej.

## <a name="syntax"></a>Składnia

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców symbol jako klasę bazową dla dowolnego typu, który może być ustalony w czasie wykonywania. Te informacje dotyczą tylko kodu zarządzanego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs reprezentuje klasę bazową, z którego mogą być uzyskane bardziej wyspecjalizowane interfejsy.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Ten interfejs nie dostarcza żadnych metod innych niż odziedziczone z `IDebugField`.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)