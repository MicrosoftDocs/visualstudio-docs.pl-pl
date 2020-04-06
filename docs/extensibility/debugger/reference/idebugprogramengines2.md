---
title: IDebugProgramEngines2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722400"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Ten interfejs jest używany przez węzły programu, aby określić wszystkie możliwe aparaty debugowania (DE), które mogą debugować ten program.

## <a name="syntax"></a>Składnia

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE lub dostawca portu niestandardowego implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) do obsługi ustanowienia określonego DE do użycia dla określonego programu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na interfejsie, `IDebugProgramNode2` aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProgramEngines2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Wskazuje wszystkie możliwe dane DEs, które można debugować ten program.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wybiera DE do debugowania tego programu.|

## <a name="remarks"></a>Uwagi
 Po de jest wybrany przez użytkownika, że wybór jest zarejestrowany w węźle programu, wywołując [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Wybrany silnik staje się silnikiem zwróconym przez [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
