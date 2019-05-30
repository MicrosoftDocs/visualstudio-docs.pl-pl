---
title: IEEDataStorage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab42216df5c7d5f3d2d349ccf07e595ab3fc616c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335636"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Ten interfejs reprezentuje tablicę bajtów.

## <a name="syntax"></a>Składnia

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ewaluator wyrażeń (EE) implementuje ten interfejs reprezentujący tablicę bajtów (używane przez wizualizatorów typu do pobierania danych i ich zmienianie za pośrednictwem [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu). EE zwykle implementuje ten interfejs obsługuje wizualizatorów typu zewnętrznego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody na `IPropertyProxyEESide` interfejsu wszystkie zwracać ten interfejs. Wywołaj [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uzyskać [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfejsu. Wywołaj [QueryInterface](/cpp/atl/queryinterface) na [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs w celu uzyskania [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 `IEEDataStorage` Interfejsu implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Pobiera określoną liczbę bajtów danych do dostarczony bufor.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczba dostępnych bajtów danych.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany przez Wizualizator typów dostępu do danych przechowywanych przez konkretnego obiektu. Dane są traktowane jako tablicę bajtów, dzięki czemu Wizualizator typów do manipulowania je w sposób, który jest wymagany do zaprezentowania użytkownikowi.

 Przeglądarka niestandardowa umożliwia również tego interfejsu, jeśli to konieczne, chociaż zazwyczaj Przeglądarka niestandardowa wykorzystany niestandardowy interfejs [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) lub [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (Aby uzyskać dane zorientowane na ciąg znaków).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)