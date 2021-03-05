---
description: Ten interfejs reprezentuje typ wskaźnika.
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 86b2b1902532a3ab827d8e8d65ebc285973ff0bd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169720"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Ten interfejs reprezentuje typ wskaźnika.

## <a name="syntax"></a>Składnia

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs, aby reprezentować wskaźnik.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z interfejsu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , jeśli zwraca wartość [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod `IDebugField` `IDebugContainerField` interfejsów i, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujący element docelowy wskaźnika.|

## <a name="remarks"></a>Uwagi
 W C/C++, wskaźnik może być kontenerem, jeśli jest używany z notacją tablicową. Na przykład, `char *pString` `pString` ma typ wskaźnika do `char` . `pString[3]` ma typ kontenera, który jest wskaźnikiem `char` , który odwołuje się do czwartego elementu tego kontenera.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
