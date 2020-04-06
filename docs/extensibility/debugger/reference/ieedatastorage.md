---
title: IEEDataStorage | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718186"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Ten interfejs reprezentuje tablicę bajtów.

## <a name="syntax"></a>Składnia

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Oceniający wyrażenie (EE) implementuje ten interfejs do reprezentowania tablicy bajtów (używane przez wizualizatorów typu do pobierania i zmiany danych za pośrednictwem interfejsu [IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) EE zazwyczaj implementuje ten interfejs do obsługi wizualizatorów typów zewnętrznych.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Metody w `IPropertyProxyEESide` interfejsie wszystkie zwracają tego interfejsu. Wywołanie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) uzyskać [interfejs IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [interfejsie IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) w celu uzyskania interfejsu [IPropertyProxyProvider.](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Interfejs `IEEDataStorage` implementuje następujące metody:

|Metoda|Opis|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Pobiera określoną liczbę bajtów danych do dostarczonego buforu.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Pobiera liczbę dostępnych bajtów danych.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany przez wizualizator typu, aby uzyskać dostęp do danych przechowywanych przez określony obiekt. Dane są traktowane jako tablica bajtów, dzięki czemu wizualizator typu manipulować nim w jakikolwiek sposób jest wymagane do przedstawienia go użytkownikowi.

 Przeglądarka niestandardowa może również używać tego interfejsu, w razie potrzeby, chociaż bardziej typowo, niestandardowa przeglądarka będzie używać niestandardowego [interfejsu, GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) lub [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (dla danych zorientowanych na ciąg).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
