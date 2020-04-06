---
title: IPropertyProxyProvider | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714792"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Ten interfejs dostarcza interfejs serwera proxy do wyświetlania i zmiany danych obiektu.

## <a name="syntax"></a>Składnia

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie (EE) implementuje ten interfejs na tym samym obiekcie, który implementuje interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) jako część obsługi EE wizualizatorów typu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na interfejsie, `IDebugProperty3` aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Interfejs `IPropertyProxyProvider` implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Pobiera interfejs serwera proxy właściwości, aby wyświetlić dane na obiekcie.|

## <a name="remarks"></a>Uwagi
 Chociaż EE implementuje ten interfejs, implementacja [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) jest zazwyczaj obsługiwane przez [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Zobacz [wizualizacji i wyświetlania danych, aby](../../../extensibility/debugger/visualizing-and-viewing-data.md) uzyskać szczegółowe informacje na temat uzyskiwania interfejsu IEEVisualizerService.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
