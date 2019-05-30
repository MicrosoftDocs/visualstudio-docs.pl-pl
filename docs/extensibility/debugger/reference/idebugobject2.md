---
title: IDebugObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3f027fd08c38433d5f1357e56d90df96e223854
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317260"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs zapewnia dodatkowe informacje na temat obiektu.

## <a name="syntax"></a>Składnia

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń implementuje ten interfejs, oferującej obsługę aliasów i dostęp do informacji o obiekcie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu można uzyskać ten interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface). Ponadto [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu `IDebugObject2` interfejsu wykonuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Pobiera pola lub zmiennej (jeśli istnieje), mogą tworzyć kopię właściwość reprezentowany przez ten obiekt.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Pobiera kod zarządzany obiekt reprezentujący wartość tego obiektu.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Tworzy unikatowy identyfikator dla tego obiektu lub zwraca istniejącego aliasu.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Pobiera alias skojarzony z tym obiektem, jeśli istnieje.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Pobiera typ tego obiektu.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Określa, czy ten obiekt reprezentuje dane użytkownika.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Określa, czy stan Edytuj i Kontynuuj nie jest już prawidłowy.<br /><br /> Ewaluator wyrażeń niestandardowych nie obsługuje tej metody (zawsze powinna zwrócić `E_NOTIMPL`).|

## <a name="remarks"></a>Uwagi
 Zobacz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) do dyskusji na temat aliasów.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)