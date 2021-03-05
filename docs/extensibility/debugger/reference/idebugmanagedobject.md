---
description: Ten interfejs umożliwia ewaluatora wyrażeń (EE) wywoływanie właściwości lub metod w wystąpieniach klasy wartości (na przykład system. Decimal) i Ustawianie ich wartości bez wywoływania funkcji szacowania dla debugowanego programu.
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7cb90893ab39a95dd3bd8046d8ba61a32064ccf7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165228"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs umożliwia ewaluatora wyrażeń (EE) wywoływanie właściwości lub metod w wystąpieniach klasy wartości (na przykład `System.Decimal` ) i Ustawianie ich wartości bez wywoływania funkcji [szacowania](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) dla debugowanego programu.

## <a name="syntax"></a>Składnia

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs do reprezentowania obiektu kodu zarządzanego, takiego jak zmienna.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aby uzyskać ten interfejs, należy wywołać [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) na [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , który reprezentuje wystąpienie klasy wartości.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` interfejs uwidacznia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Zwraca interfejs reprezentujący obiekt kodu zarządzanego i, z którego można uzyskać dowolny odpowiedni interfejs kodu zarządzanego.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Ustawia wartość tego obiektu na wartość określonego obiektu kodu zarządzanego.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu do przechowywania obiektu kodu zarządzanego w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Oceny](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
