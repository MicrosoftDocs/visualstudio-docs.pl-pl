---
description: Ten interfejs zapewnia metody do wyświetlania danych na skojarzonym obiekcie.
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce7f950455a6b6a6ae2089e762db1aa02428f6a5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082401"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Ten interfejs zapewnia metody do wyświetlania danych na skojarzonym obiekcie. Ten interfejs jest częścią obsługi wizualizatorów typów.

## <a name="syntax"></a>Składnia

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluatora wyrażeń implementuje ten interfejs do obsługi wizualizatorów typów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) , aby uzyskać ten interfejs. Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na interfejsie [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , aby uzyskać Interfejs [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Następujące metody są implementowane przez ten interfejs:

|Metoda|Opis|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Inicjuje dostawcę źródła danych, aby można było uzyskać dostęp do danych obiektu.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Pobiera informacje o zestawie obiektu.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Pobiera początkowe dane dla obiektu.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Tworzy kopię istniejącego magazynu danych.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Tworzy odwołanie do istniejącego magazynu danych.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Pobiera informacje o określonym zestawie w kontekście zestawu zawierającego ten obiekt.|

## <a name="remarks"></a>Uwagi
 Wizualizator typu używa tego interfejsu, aby uzyskać dostęp do wartości skojarzonych z obiektem, do którego należy ten interfejs. Dostęp do danych uzyskuje się za pomocą interfejsu [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , który zapewnia widok danych tylko do odczytu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
