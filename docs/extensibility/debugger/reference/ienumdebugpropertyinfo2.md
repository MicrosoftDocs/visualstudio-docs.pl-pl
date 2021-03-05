---
description: Ten interfejs wylicza DEBUG_PROPERTY_INFO struktur.
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fea2dc5cf958f87463af9dfca9f29bec5d01a82b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224190"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Ten interfejs wylicza [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur.

## <a name="syntax"></a>Składnia

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować informacje dla konkretnej właściwości.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) , aby uzyskać ten interfejs reprezentujący elementy podrzędne określonej właściwości. Wywołaj [EnumProperties —](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) , aby uzyskać ten interfejs reprezentujący właściwości określonej ramki stosu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IEnumDebugPropertyInfo2` .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Pobiera określoną liczbę struktur [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w sekwencji wyliczenia.|
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Pomija określoną liczbę struktur [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w sekwencji wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Resetuje sekwencję wyliczenia na początek.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczania co bieżący moduł wyliczający.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Pobiera liczbę struktur [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w module wyliczającym.|

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc właściwość jest hierarchią informacji, które mogą zawierać nazwę, wartość, adres i typ, a także inne informacje odpowiednie do obiektu właściwości skojarzonego lub ramki stosu. Aby uzyskać więcej informacji, zobacz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
