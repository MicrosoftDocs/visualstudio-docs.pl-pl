---
title: IDebugPropertyField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720696"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Ten interfejs zapewnia funkcje, które umożliwiają uzyskanie i ustawienie właściwości.

## <a name="syntax"></a>Składnia

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Ten interfejs jest specjalizacji, która obsługuje pojęcie właściwości w klasie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) jeśli zwraca metodę [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_KIND_PROP`.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na [interfejsach IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Pobiera metodę, która pobiera właściwość.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Pobiera metodę, która ustawia właściwość.|

## <a name="remarks"></a>Uwagi
 Właściwość jest pojęciem kodu zarządzanego i reprezentuje metodę, która jest traktowana jako zmienna. Właściwości nie istnieją w niezarządzanym języku C++.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
