---
title: IDebugBinder3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 733ede7b7bad73419fc160f4c15b660b50b26b7e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707552"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs zapewnia dostęp do typów, aliasów i usług niestandardowego wizualizatora.

## <a name="syntax"></a>Składnia

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania implementuje ten interfejs do obsługi aliasów, niestandardowego wizualizatora usług i dostęp do informacji o typie obiektu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu uzyskuje ten interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod dostarczonych przez [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu, ten interfejs wykonuje następujące czynności:

|Metoda|Opis|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Pobiera obiekt pamięci reprezentująca pamięci, z którym powiązany jest ten obiekt.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Pobiera wyjątek skojarzone z tym obiektem (jeśli istnieje)|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Pobiera nadać jej nazwę aliasu|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Pobiera tablicę wszystkie aliasy dla tego obiektu|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Pobiera liczbę typów argumentów skojarzonych z tym obiektem|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Pobiera listę typów argumentów skojarzonych z tym obiektem|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Pobiera interfejs do niej wizualizatora|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konwertuje lokalizacji obiektu lub adresów pamięci 64-bitowych w kontekście pamięci.|

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)