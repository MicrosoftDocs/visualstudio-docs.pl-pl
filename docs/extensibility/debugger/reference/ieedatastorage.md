---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718186"
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
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczbę dostępnych bajtów danych.|

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
