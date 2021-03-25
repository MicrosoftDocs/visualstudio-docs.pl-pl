---
description: Ten interfejs reprezentuje obiekt Array.
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e27f40a3f8a54c9cda285ba30bdcbc53472aab59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078113"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ten interfejs reprezentuje obiekt Array.

## <a name="syntax"></a>Składnia

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs, aby reprezentować tablicę.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) może uzyskać ten interfejs przy użyciu [polecenia QueryInterface](/cpp/atl/queryinterface) , jeśli obiekt reprezentuje tablicę.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod w `IDebugObject` interfejsie, w interfejsie są zaimplementowane następujące metody `IDebugArrayObject` .

|Metoda|Opis|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Pobiera liczbę elementów w tablicy.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Pobiera element tablicy.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Pobiera wszystkie elementy tablicy.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Pobiera rangę tablicy.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Pobiera Wymiary tablicy.|

## <a name="remarks"></a>Uwagi
 Ewaluatora wyrażeń używa tego interfejsu do reprezentowania tablic w drzewie analizy.

## <a name="requirements"></a>Wymagania
 Nagłówek: EE. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
