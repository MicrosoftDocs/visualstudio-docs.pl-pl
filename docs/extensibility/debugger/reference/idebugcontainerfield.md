---
title: IDebugContainerField | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733218"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Ten interfejs reprezentuje symbol lub typ, który jest kontenerem dla innych symboli lub typów.

## <a name="syntax"></a>Składnia

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symbolu implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Ten interfejs jest również klasą podstawową dla wszystkich interfejsów, które reprezentują kontenery.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wiele metod w wielu interfejsach zwraca ten interfejs. Ponieważ jest to klasa podstawowa dla wszystkich kontenerów, bardziej wyspecjalizowane interfejsy można uzyskać z tego interfejsu przy użyciu [QueryInterface](/cpp/atl/queryinterface). Takie interfejsy obejmują [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)i [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod w interfejsie [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Tworzy wyliczenie dla pól kontenera.|

## <a name="remarks"></a>Uwagi
 Tablice (kontenery dla zmiennych), klasy (kontenery dla metod i zmiennych) i metody (kontenery dla parametrów i zmiennych lokalnych) są przykładami kontenerów.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
