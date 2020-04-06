---
title: IDebugMethodField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727060"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Ten interfejs opisuje metodę.

## <a name="syntax"></a>Składnia

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Ten interfejs jest specjalizacji, która przedstawia metodę.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) jeśli [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) zwraca `FIELD_TYPE_METHOD`. Ponadto metody [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)i [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), `IDebugMethodField` wszystkie zwracają interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod na [interfejsach IDebugField](../../../extensibility/debugger/reference/idebugfield.md) i [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Tworzy wyliczyć dla parametrów metody.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Pobiera wskaźnik "this" obiektu zawierającego metodę.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Tworzy wyliczyć dla wszystkich zmiennych lokalnych metody.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Tworzy wyliczyć dla wybranych zmiennych lokalnych metody.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Określa, czy zdefiniowano określony atrybut niestandardowy.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Tworzy wyliczyć dla statycznych zmiennych lokalnych metody.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Pobiera globalnego kontenera metody.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Tworzy wyliczyć dla typu każdego argumentu wymagane do wywołania metody.|

## <a name="remarks"></a>Uwagi
 Metoda może zawierać parametry, a także zmienne lokalne.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
