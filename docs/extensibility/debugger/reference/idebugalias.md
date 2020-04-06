---
title: IDebugAlias | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736517"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Reprezentuje alias numeryczny dla zmiennej. Alias jest po prostu inną nazwą zmiennej.

## <a name="syntax"></a>Składnia

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie (EE) implementuje ten interfejs do obsługi aliasów numerycznych dla zmiennych.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) tworzy alias dla określonego obiektu. Aby wyszukać aliasy, użyj [findalias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) lub [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W interfejsie `IDebugAlias` zdefiniowano następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Pobiera obiekt, do którego odwołuje się ten alias.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Pobiera nazwę aliasu.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Pobiera `ICorDebugValue` interfejs, który zapewnia dostęp do informacji kodu zarządzanego o tym obiekcie (tylko kod zarządzany).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Oznacza ten alias jako nieużywany.|

## <a name="remarks"></a>Uwagi
 Alias jest liczbą dziesiętną w formie ciągu, po której następuje znak #, na przykład 1001#.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
