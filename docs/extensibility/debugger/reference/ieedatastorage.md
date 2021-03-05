---
description: Ten interfejs reprezentuje tablicę bajtów.
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9434138114f2b4b0615e20c1b556ff6387c715de
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227336"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Ten interfejs reprezentuje tablicę bajtów.

## <a name="syntax"></a>Składnia

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Expression ewaluatora (EE) implementuje ten interfejs, aby reprezentować tablicę bajtów (wykorzystywaną przez Wizualizatory typów do pobierania i zmieniania danych za pomocą interfejsu [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) ). Na stronie EE zazwyczaj jest implementowany ten interfejs do obsługi wizualizatorów typu zewnętrznego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody `IPropertyProxyEESide` interfejsu wszystkie zwracają ten interfejs. Wywołaj [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) , aby uzyskać Interfejs [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na interfejsie [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , aby uzyskać Interfejs [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 `IEEDataStorage`Interfejs implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Pobiera określoną liczbę bajtów danych do podanego buforu.|
|[GetSize —](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczbę dostępnych bajtów danych.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany przez wizualizator typu w celu uzyskania dostępu do danych przechowywanych przez określony obiekt. Dane są traktowane jako tablica bajtów, co umożliwia wizualizatorowi typu manipulowanie nim w dowolny sposób, aby przedstawić go użytkownikowi.

 Niestandardowa przeglądarka może również używać tego interfejsu, w razie potrzeby, mimo że zwykle, niestandardowa przeglądarka użyje niestandardowego interfejsu, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) lub [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dla danych zorientowanych na ciąg).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
