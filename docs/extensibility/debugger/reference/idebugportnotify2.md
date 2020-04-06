---
title: IDebugPortNotify2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724918"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Ten interfejs rejestruje lub wyrejestrowyje program, który może być debugowany za pomocą portu, na który jest uruchomiony.

## <a name="syntax"></a>Składnia

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs do obsługi dodawania i usuwania programów z portu. Zazwyczaj jest zaimplementowany na tym samym obiekcie, który implementuje interfejs [IDebugPort2.](../../../extensibility/debugger/reference/idebugport2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) w `IDebugPort2` interfejsie zwraca ten interfejs. Ponadto wywołanie [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) zwraca ten interfejs. Aparat debugowania może zobaczyć ten interfejs jako parametr [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPortNotify2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Rejestruje program, który może być debugowany za pomocą portu, na który jest uruchomiony.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Wyrejestrowanie programu, który może być debugowany z portu, na który jest uruchomiony.|

## <a name="remarks"></a>Uwagi
 O ile port debugowania nie ma sposobu, aby wiedzieć, kiedy programy są ładowane lub zwalniane, dostawca portu niestandardowego musi zaimplementować ten interfejs. Wszystkie programy, które są ładowane do debugowania za pośrednictwem określonego portu są śledzone za pomocą tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
