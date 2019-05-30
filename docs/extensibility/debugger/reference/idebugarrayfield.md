---
title: IDebugArrayField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 088ff752513feb9d73e35c3174492bc34a5034f5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349139"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Ten interfejs w tym artykule opisano symbol tablicy lub typu.

## <a name="syntax"></a>Składnia

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu. Ten interfejs jest specjalizację, który reprezentuje tablicę obiektów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_ARRAY`.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsów, ten interfejs wykonuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Pobiera liczbę elementów w tablicy.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Pobiera typ elementu w tablicy.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Pobiera rangę tablicy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)