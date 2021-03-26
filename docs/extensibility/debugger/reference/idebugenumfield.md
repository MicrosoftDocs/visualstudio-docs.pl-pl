---
description: Ten interfejs reprezentuje typ wyliczeniowy.
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18671f8f719dc797709677a14417eaa0a54aaea2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092530"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Ten interfejs reprezentuje typ wyliczeniowy.

## <a name="syntax"></a>Składnia

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs, aby reprezentować Wyliczenie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z interfejsu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , jeśli zwraca wartość [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod `IDebugField` `IDebugContainerField` interfejsów i, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujący nazwę tego typu wyliczenia.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Zwraca nazwę stałej wyliczenia skojarzonej z daną wartością.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Zwraca wartość skojarzoną z daną nazwą stałej wyliczenia|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Zwraca wartość skojarzoną z daną nazwą stałej wyliczenia, ale bez uwzględnienia wielkości liter.|

## <a name="remarks"></a>Uwagi
 Jest to podstawowy symbol, który jest faktycznie powiązany z lokalizacją z [powiązaniem](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Węglowodor](../../../extensibility/debugger/reference/idebugbinder-bind.md)
