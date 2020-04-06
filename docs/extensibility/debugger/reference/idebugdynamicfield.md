---
title: IDebugDynamicField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15f0ddf70849377d37ec74839550de6057b3450c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731312"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Ten interfejs reprezentuje typ zmiennej.

## <a name="syntax"></a>Składnia

```
IDebugDynamicField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawców symboli jako klasa podstawowa dla dowolnego typu, który można określić w czasie wykonywania. Dotyczy to tylko kodu zarządzanego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs reprezentuje klasę podstawową, z której można wyprowadzić bardziej wyspecjalizowane interfejsy.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs nie zawiera żadnych metod innych `IDebugField`niż te odziedziczone po .

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
