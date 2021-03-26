---
description: Ten interfejs dostarcza porty do Menedżera debugowania sesji (SDM).
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd28e261c9c74601bd88f2d84e1296a1ed508f37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072029"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Ten interfejs dostarcza porty do Menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Niestandardowy dostawca portu implementuje ten interfejs do reprezentowania dostawcy portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` z dostawcą portów `GUID` zwraca ten interfejs (jest to typowy sposób uzyskania tego interfejsu). Na przykład:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Wywołanie [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) zwraca ten interfejs reprezentujący bieżącego dostawcę portu używanego przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) zwraca ten interfejs reprezentujący dostawcę portu, który utworzył port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) reprezentuje listę `IDebugPortSupplier` interfejsów ( `IEnumDebugPortSuppliers` interfejs jest uzyskiwany z [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), reprezentujący wszystkich dostawców portów zarejestrowanych w systemie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Aparat debugowania zwykle nie współdziała z dostawcą portu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDebugPortSupplier2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Pobiera nazwę dostawcy portów.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Pobiera identyfikator dostawcy portów.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Pobiera port z dostawcy portów.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Wylicza porty, które już istnieją.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Sprawdza, czy dostawca portu obsługuje dodawanie nowych portów.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Dodaje port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Usuwa port.|

## <a name="remarks"></a>Uwagi
Dostawca portu może identyfikować siebie według nazwy i identyfikatora, dodawać i usuwać porty oraz wyliczać wszystkie porty udostępniane przez dostawcę portów.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
