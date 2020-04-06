---
title: IDebugArrayField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736291"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Ten interfejs opisuje symbol lub typ tablicy.

## <a name="syntax"></a>Składnia

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Ten interfejs jest specjalizacji, która reprezentuje obiekty tablicy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_ARRAY`.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na [interfejsach IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Pobiera liczbę elementów w tablicy.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Pobiera typ elementu w tablicy.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Pobiera rangę tablicy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
