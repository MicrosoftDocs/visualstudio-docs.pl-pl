---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29b7a8bca687ff2992c5e3fb92cb0cc6c8a1740d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338130"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje liczbowych aliasu dla zmiennej. Alias jest po prostu inną nazwę zmiennej.

## <a name="syntax"></a>Składnia

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń (EE) implementuje ten interfejs do obsługi wartości liczbowych aliasów dla zmiennych.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) tworzy alias dla określonego obiektu. Aby wyszukać aliasy, użyj [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) lub [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Następujące metody są zdefiniowane w `IDebugAlias` interfejsu.

|Metoda|Opis|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Pobiera obiekt, do którego odwołuje się ten alias.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Pobiera nazwę aliasu.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Pobiera `ICorDebugValue` interfejsu, który zapewnia dostęp do zarządzanego kodu informacji dotyczących tego obiektu (tylko kod zarządzany).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Oznacza to, alias jako nie jest już używana.|

## <a name="remarks"></a>Uwagi
 Alias jest liczbą dziesiętną w postaci ciągu, a następnie znak #, na przykład 1001#.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)