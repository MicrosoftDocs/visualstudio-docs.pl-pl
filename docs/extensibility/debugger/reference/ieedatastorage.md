---
title: IEEDataStorage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dbc5228eebb1d70d84c82b4b42f991b84d1f2cb
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224120"
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