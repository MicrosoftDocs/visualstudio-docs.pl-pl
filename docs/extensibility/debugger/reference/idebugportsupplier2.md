---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 947a311cb1e83eaa131730725aeb7938e5615f0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340049"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Ten interfejs dostarcza portów Menedżer debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Dostawcy niestandardowego portu implementuje ten interfejs do reprezentowania dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` przy użyciu dostawcy portu `GUID` zwraca ten interfejs (jest to typowy sposób, aby uzyskać ten interfejs). Na przykład:

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

Wywołanie [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) zwraca ten interfejs reprezentujący bieżącego dostawcy port używany przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) zwraca ten interfejs reprezentujący dostawcy portu, który utworzony port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) reprezentuje listę `IDebugPortSupplier` interfejsów ( `IEnumDebugPortSuppliers` interfejsu są uzyskiwane z [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), reprezentujący wszyscy dostawcy portu zarejestrowane w usłudze [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Aparat debugowania zwykle nie wchodzi w interakcję z dostawcą portu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDebugPortSupplier2`.

|Metoda|Opis|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Pobiera nazwę dostawcy portu.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Pobiera identyfikator dostawcy portów.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Pobiera portu z portu dostawcy.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Wylicza porty, które już istnieją.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Sprawdza, czy dostawcy portu obsługuje dodawanie nowych portów.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Dodaje port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Usuwa portu.|

## <a name="remarks"></a>Uwagi
Dostawcy portu można zidentyfikować się za pomocą nazwy i Identyfikatora, dodawania i usuwania portów oraz wyliczyć wszystkie porty, które zapewnia dostawcy portu.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
