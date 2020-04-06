---
title: IEnumDebugPropertyInfo2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715353"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Ten interfejs wylicza [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur.

## <a name="syntax"></a>Składnia

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania informacji dla określonej właściwości.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [EnumChildren,](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) aby uzyskać ten interfejs reprezentujący elementy podrzędne określonej właściwości. Wywołaj [EnumProperties,](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) aby uzyskać ten interfejs reprezentujący właściwości ramki określonego stosu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IEnumDebugPropertyInfo2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dalej](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Pobiera określoną liczbę [struktur DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w sekwencji wyliczenia.|
|[Pominąć](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Pomija określoną liczbę [struktur DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w sekwencji wyliczenia.|
|[Resetuj](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Resetuje sekwencję wyliczenia do początku.|
|[Klonowanie](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Tworzy wyliczenia, który zawiera ten sam stan wyliczenia jako bieżącego wylicznika.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Pobiera liczbę [struktur DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) w wyliczacza.|

## <a name="remarks"></a>Uwagi
 Ogólnie rzecz biorąc właściwość jest hierarchią informacji, które mogą zawierać nazwę, wartość, adres i typ, a także wszelkie inne informacje odpowiednie dla skojarzonego obiektu właściwości lub ramki stosu. Zobacz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) aby uzyskać więcej informacji.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
