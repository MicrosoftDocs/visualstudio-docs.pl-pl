---
title: IDebugCustomAttributeQuery2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732487"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Określa istnienie atrybutu niestandardowego dla tego pola i, jeśli istnieje, zwraca informacje o atrybucie.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) w celu obsługi atrybutów niestandardowych.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać ten interfejs z interfejsu [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli przedstawiono metody interfejsu **IDebugCustomAttributeQuery.**

|Metoda|Opis|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Określa, czy atrybut niestandardowy istnieje według nazwy.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Pobiera informacje o atrybutach dla danego atrybutu niestandardowego.|

 Oprócz metod **IDebugCustomAttributeQuery** implementuje `IDebugCustomAttributeQuery2` następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Pobiera wyliczenia dla wszystkich atrybutów niestandardowych dołączonych do tego pola.|

## <a name="remarks"></a>Uwagi
 Metoda [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) może zwrócić inicjatora dla wszystkich atrybutów niestandardowych zdefiniowanych dla tego pola.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
