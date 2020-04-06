---
title: IDebugManagedObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727691"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład ewaluatora zarządzanych wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs umożliwia oceniającemu wyrażenie (EE) wywoływanie właściwości lub metod `System.Decimal`w wystąpieniach klasy wartości (na przykład) i ustawianie ich wartości bez wywoływania [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) w debugowanym programie.

## <a name="syntax"></a>Składnia

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs do reprezentowania obiektu kodu zarządzanego, takiego jak zmienna.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aby uzyskać ten interfejs, należy wywołać [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) na [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) który reprezentuje wystąpienie klasy wartości.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) `IDebugManagedObject` interfejs udostępnia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Zwraca interfejs, który reprezentuje obiekt kodu zarządzanego i z którego można uzyskać dowolny odpowiedni interfejs kodu zarządzanego.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Ustawia wartość tego obiektu na wartość określonego obiektu kodu zarządzanego.|

## <a name="remarks"></a>Uwagi
 Oceniający wyrażenie używa tego interfejsu do przechowywania obiektu kodu zarządzanego w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Oceny](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
