---
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbda02c26018adc4e5f1f3677b75bc2dce25a2e5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339288"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Ten interfejs dostarcza interfejs serwera proxy do wyświetlania i zmieniania danych obiektu.

## <a name="syntax"></a>Składnia

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń (EE) implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu jako część EE wsparcie wizualizatorów typu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugProperty3` interfejsu w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 `IPropertyProxyProvider` Interfejsu implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Pobiera właściwość interfejsu serwera proxy, do wyświetlania danych na obiekcie.|

## <a name="remarks"></a>Uwagi
 Mimo że EE implementuje ten interfejs, implementacja [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) jest zazwyczaj obsługiwana przez [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) szczegółowe informacje na temat uzyskiwania interfejsu IEEVisualizerService.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)