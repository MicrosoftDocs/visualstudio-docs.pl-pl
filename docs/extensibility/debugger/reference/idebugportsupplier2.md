---
title: IDebugPortSupplier2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724477"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Ten interfejs dostarcza porty do menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Dostawca portu niestandardowego implementuje ten interfejs do reprezentowania dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` z dostawcą portu `GUID` zwraca ten interfejs (jest to typowy sposób uzyskania tego interfejsu). Przykład:

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

Wywołanie [getportsupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) zwraca ten interfejs, reprezentujący bieżącego [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]dostawcy portu używanego przez .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) zwraca ten interfejs, reprezentujący dostawcę portu, który utworzył port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) reprezentuje listę `IDebugPortSupplier` interfejsów `IEnumDebugPortSuppliers` (interfejs jest uzyskiwany z [EnumPortSuppliers,](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)reprezentujący wszystkich dostawców portów zarejestrowanych [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]w ).

Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
W poniższej tabeli `IDebugPortSupplier2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Pobiera nazwę dostawcy portu.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Pobiera identyfikator dostawcy portu.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Pobiera port od dostawcy portu.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Wylicza porty, które już istnieją.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Sprawdza, czy dostawca portu obsługuje dodawanie nowych portów.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Dodaje port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Usuwa port.|

## <a name="remarks"></a>Uwagi
Dostawca portu może identyfikować się według nazwy i identyfikatora, dodawać i usuwać porty oraz wyliczać wszystkie porty, które zapewnia dostawca portu.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
