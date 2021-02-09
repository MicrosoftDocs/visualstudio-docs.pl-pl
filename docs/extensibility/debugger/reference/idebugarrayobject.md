---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 83d6a37a5b83cd71123521db70920fd3d454e059
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870067"
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
