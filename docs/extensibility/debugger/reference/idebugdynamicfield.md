---
description: Ten interfejs reprezentuje typ zmiennej.
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dcf148294a7c18c2b717bb4de63dac7e656e25d6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167233"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Ten interfejs reprezentuje typ zmiennej.

## <a name="syntax"></a>Składnia

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców symboli jako klasa bazowa dla dowolnego typu, który może być ustalony w czasie wykonywania. Jest to tylko kod zarządzany.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs reprezentuje klasę bazową, z której można utworzyć bardziej wyspecjalizowane interfejsy.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs nie dostarcza żadnych metod innych niż dziedziczone z `IDebugField` .

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
