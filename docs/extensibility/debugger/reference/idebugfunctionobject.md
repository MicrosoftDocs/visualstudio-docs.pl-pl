---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab1462c30f1012eb1002f692672fc470cac3b39a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921013"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje funkcję.

## <a name="syntax"></a>Składnia

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować funkcję.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest specjalizacją interfejsu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) i jest uzyskiwany przy użyciu funkcji [QueryInterface](/cpp/atl/queryinterface) w `IDebugObject` interfejsie.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` interfejs uwidacznia następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Tworzy obiekt danych pierwotnych.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Tworzy obiekt przy użyciu konstruktora.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Tworzy obiekt bez konstruktora.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Tworzy obiekt Array.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Tworzy obiekt String.|
|[Oceny](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Wywołuje funkcję i zwraca wynikową wartość jako obiekt.|

## <a name="remarks"></a>Uwagi
 Ten interfejs umożliwia ewaluatora wyrażeń reprezentowania funkcji w drzewie analizy. `Create`Metody w tym interfejsie są używane do konstruowania obiektów reprezentujących parametry wejściowe do metody. Funkcję można następnie wykonać, wywołując metodę [szacowania](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) , która zwraca obiekt reprezentujący wartość zwracaną funkcji.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
