---
title: IDebugParsedExpression | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56c0547d348c4fb3de387ac0ffce465b7bf5e90
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311788"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje wyrażenie przeanalizowany, gotowy do obliczenia.

## <a name="syntax"></a>Składnia

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs do reprezentowania przeanalizowany wyrażenie, które jest gotowe do oceny.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zwraca ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugParsedExpression`.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Oblicza wyrażenie przeanalizowany.|

## <a name="remarks"></a>Uwagi
 Jeżeli obiekt wywołujący jest gotowy do obliczenia wyrażenia, wywołuje [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) do zwrócenia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) zawierającą wynik obliczenia. Takie podejście legalną dwuczęściową do oceny, analizowanie, a następnie ocenę, umożliwia przeanalizowany wyrażenie do obliczenia wiele razy, z pominięciem czasochłonnym procesem analizowania wyrażenia.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)