---
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00220574ac9c16bdab9abd64adde1877ee0fd9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335802"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Określa obecność atrybutu niestandardowego dla tego pola i, jeśli istnieje, zwraca informacje o atrybutach.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) w celu obsługi niestandardowych atrybutów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody **IDebugCustomAttributeQuery** interfejsu.

|Metoda|Opis|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Określa, czy atrybut niestandardowy istnieje według nazwy.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Pobiera informacje o atrybutach dotyczące danego atrybutu niestandardowego.|

 Oprócz **IDebugCustomAttributeQuery** metod `IDebugCustomAttributeQuery2` implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Pobiera moduł wyliczający dla wszystkich atrybutów niestandardowych, dołączony do tego pola.|

## <a name="remarks"></a>Uwagi
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) metoda może zwracać moduł wyliczający dla wszystkich atrybutów niestandardowych zdefiniowanych dla tego pola.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)