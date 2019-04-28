---
title: IDebugMethodField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5373be45884e5229fe03f88f364e75a9cb81f20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918711"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Ten interfejs opisuje metodę.

## <a name="syntax"></a>Składnia

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu. Ten interfejs jest specjalizacji, która przedstawia metodę.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsu, jeśli [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_METHOD`. Ponadto, metody, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), i [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), wszystkie zwrot `IDebugMethodField` interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfejsów, ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Tworzy moduł wyliczający dla parametrów metody.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Pobiera wskaźnika "this" w obiekt zawierający metodę.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Tworzy moduł wyliczający dla wszystkich zmiennych lokalnych metody.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Tworzy moduł wyliczający wybrane zmienne lokalne, metody.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Określa, czy zdefiniowano określonego atrybutu niestandardowego.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Tworzy moduł wyliczający statyczne zmienne lokalne, metody.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Pobiera kontener globalnego metody.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Tworzy moduł wyliczający typ każdego argumentu wymaganych do wywołania metody.|

## <a name="remarks"></a>Uwagi
 Metoda może zawierać parametrów, a także zmienne lokalne.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)