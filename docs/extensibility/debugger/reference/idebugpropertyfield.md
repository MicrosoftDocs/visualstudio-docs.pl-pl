---
title: IDebugPropertyField | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720696"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Ten interfejs udostępnia funkcje, które umożliwiają pobieranie i Ustawianie właściwości.

## <a name="syntax"></a>Składnia

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md). Ten interfejs jest specjalizacją, która obsługuje koncepcję właściwości klasy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [polecenia QueryInterface](/cpp/atl/queryinterface) , aby uzyskać ten interfejs z interfejsu [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , jeśli metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca wartość `FIELD_KIND_PROP` .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod w interfejsach [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Pobiera metodę, która pobiera właściwość.|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Pobiera metodę, która ustawia właściwość.|

## <a name="remarks"></a>Uwagi
 Właściwość jest koncepcją kodu zarządzanego i reprezentuje metodę, która jest traktowana jako zmienna. Właściwości nie istnieją w niezarządzanym języku C++.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
