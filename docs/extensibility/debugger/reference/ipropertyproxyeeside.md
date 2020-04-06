---
title: IPropertyProxyEESide | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714861"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Ten interfejs zawiera metody wyświetlania danych na skojarzonym obiekcie. Ten interfejs jest częścią obsługi wizualizatorów typu.

## <a name="syntax"></a>Składnia

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie implementuje ten interfejs do obsługi wizualizatorów typów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetPropertyProxy,](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) aby uzyskać ten interfejs. Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [interfejsie IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) w celu uzyskania interfejsu [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicjuje dostawcę źródła danych, aby uzyskać dostęp do danych obiektu.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Pobiera informacje o złożeniu obiektu.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Pobiera dane początkowe dla obiektu.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Tworzy kopię istniejącego magazynu danych.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Tworzy odwołanie do istniejącego magazynu danych.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Pobiera informacje o określonym zestawie w kontekście zestawu zawierającego ten obiekt.|

## <a name="remarks"></a>Uwagi
 Wizualizator typu używa tego interfejsu, aby uzyskać dostęp do wartości skojarzonych z obiektem, którego częścią jest ten interfejs. Dane są dostępne za pośrednictwem interfejsu [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) który zapewnia widok tylko do odczytu danych.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
