---
title: IDebugManagedObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6744ae98a0210a6832bce1bdb0cd68f08145f3eb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349415"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs umożliwia Ewaluator wyrażeń (EE) do wywołania właściwości lub metody na instancji klasy wartości (na przykład `System.Decimal`) oraz określić ich wartości bez wywoływania [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) na debugowanego programu.

## <a name="syntax"></a>Składnia

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs do reprezentowania obiektów kodu zarządzanego, jak w przypadku zmiennej.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aby uzyskać ten interfejs, należy wywołać [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wystąpienie klasy wartości.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod odziedziczone [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` interfejsu udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Zwraca interfejs, który reprezentuje obiekt kodu zarządzanego i z których wszystkie odpowiednie kodu zarządzanego można uzyskać interfejsu.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Ustawia wartość tego obiektu. wartość obiektu określonego kodu zarządzanego.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu do przechowywania obiektów kodu zarządzanego w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)