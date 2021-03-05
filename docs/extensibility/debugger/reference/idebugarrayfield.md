---
description: Ten interfejs opisuje symbol lub typ tablicy.
title: IDebugArrayField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3926bb47e1ea8a91289a7454f289cd3806e97f7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158725"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Ten interfejs opisuje symbol lub typ tablicy.

## <a name="syntax"></a>Składnia

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Ten interfejs jest specjalizacją reprezentującą obiekty tablicowe.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z interfejsu [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca flagę `FIELD_TYPE_ARRAY` .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod w interfejsach [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące elementy:

|Metoda|Opis|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Pobiera liczbę elementów w tablicy.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Pobiera typ elementu w tablicy.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Pobiera rangę tablicy.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
