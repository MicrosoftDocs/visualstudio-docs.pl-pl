---
title: IDebugDynamicField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d94a685b9c79069a047e32155234f9bf6a50d5c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875390"
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

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)