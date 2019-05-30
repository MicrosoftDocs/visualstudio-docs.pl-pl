---
title: IDebugEnumField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14ea4834619d9e28d4b8a15206b3ea9411f50017
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345109"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Ten interfejs reprezentuje typ wyliczenia.

## <a name="syntax"></a>Składnia

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs do reprezentowania wyliczenia.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_ENUM`.

## <a name="methods-in-vtable-order"></a>Metody w VTable kolejności
 Oprócz metod na `IDebugField` i `IDebugContainerField` interfejsów, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące nazwę dla tego typu wyliczeniowego.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Zwraca nazwę stała wyliczenia skojarzone z danej wartości.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Zwraca wartość skojarzoną z nazwa stałej wyliczenia danego|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Zwraca wartość skojarzoną z nazwą stała wyliczenia danego, ale bez uwzględnienia wielkości liter.|

## <a name="remarks"></a>Uwagi
 Jest podstawowym symbol, który faktycznie jest powiązane z lokalizacją z [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)