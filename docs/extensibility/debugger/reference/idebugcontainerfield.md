---
title: IDebugContainerField | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d633b7e42f8c7f64a818539694837b954ea31e72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332515"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Ten interfejs reprezentuje symbol lub typ, który jest kontenerem dla innych symboli lub typów.

## <a name="syntax"></a>Składnia

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu. Ten interfejs jest również klasę bazową dla wszystkich interfejsów, które reprezentują kontenery.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wiele metod w wielu interfejsach zwraca ten interfejs. Ponieważ jest to klasa bazowa dla wszystkich kontenerów, bardziej wyspecjalizowane interfejsy można uzyskać w tym interfejsie za pomocą [QueryInterface](/cpp/atl/queryinterface). Takie interfejsy zawierają [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), i [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu, ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Tworzy moduł wyliczający dla pól kontenera.|

## <a name="remarks"></a>Uwagi
 Tablice (kontenery dla zmiennych), klasy (kontenery dla metody i zmienne) i metody (kontenery parametry i zmienne lokalne) są przykładami kontenerów.

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)