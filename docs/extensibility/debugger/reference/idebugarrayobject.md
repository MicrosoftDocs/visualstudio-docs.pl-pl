---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5943aae9fb8ef848bdaeecdebc0f1354be2c0e7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697081"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt array.

## <a name="syntax"></a>Składnia

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń implementuje ten interfejs reprezentujący tablicę.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfejsu można uzyskać ten interfejs, za pomocą [QueryInterface](/cpp/atl/queryinterface) Jeśli obiekt reprezentuje tablicę.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Oprócz metod na `IDebugObject` następujących metod interfejsu, są implementowane w `IDebugArrayObject` interfejsu.

|Metoda|Opis|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Pobiera liczbę elementów w tablicy.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Pobiera element tablicy.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Pobiera wszystkie elementy tablicy.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Pobiera rangę tablicy.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Pobiera wymiary tablicy.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu, który reprezentuje tablic w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: ee.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)