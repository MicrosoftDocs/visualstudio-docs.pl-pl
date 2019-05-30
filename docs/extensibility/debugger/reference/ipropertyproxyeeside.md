---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f6528b146ad3128dd880e594b25ebb5df88bb8f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353438"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Ten interfejs zapewnia metody do wyświetlania danych na skojarzonego obiektu. Ten interfejs jest częścią obsługę wizualizatorów typu.

## <a name="syntax"></a>Składnia

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs do obsługi wizualizatorów typu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uzyskać ten interfejs. Wywołaj [QueryInterface](/cpp/atl/queryinterface) na [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs w celu uzyskania [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Następujące metody są implementowane przez ten interfejs:

|Metoda|Opis|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicjuje dostawcy źródła danych, dzięki czemu można można uzyskać dostępu do danych obiektu.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Pobiera informacje o zestawie obiektu.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Pobiera dane początkowe dla obiektu.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Tworzy kopię istniejącego magazynu danych.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Tworzy odwołanie do istniejącego magazynu danych.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Pobiera informacje o określony zestaw w kontekście zestawu zawierającego ten obiekt.|

## <a name="remarks"></a>Uwagi
 Wizualizator typów używa ten interfejs, aby uzyskać dostęp do wartości skojarzone z obiektem, który ten interfejs jest częścią. Dostęp do danych za pośrednictwem [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfejs, który udostępnia widok tylko do odczytu danych.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)