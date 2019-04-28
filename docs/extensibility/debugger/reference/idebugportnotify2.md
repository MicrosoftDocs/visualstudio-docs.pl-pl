---
title: IDebugPortNotify2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2427bfbc70c992cfcd41217aec56aa94d825faae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918172"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Ten interfejs rejestry lub wyrejestrowuje program, który może być debugowany przy użyciu portu, na którym jest uruchomiona na.

## <a name="syntax"></a>Składnia

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs obsługuje dodawanie i usuwanie programów z portu. Jest on zwykle implementowany w ten sam obiekt, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interfejsu zwraca ten interfejs. Ponadto po wywołaniu [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) zwraca ten interfejs. Aparat debugowania można zobaczyć ten interfejs jako parametr do [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugPortNotify2`.

|Metoda|Opis|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Rejestruje program, który może być debugowany przy użyciu portu, na którym jest uruchomiona na.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Wyrejestrowuje program, który może być debugowany z portu, na którym jest uruchomiona na.|

## <a name="remarks"></a>Uwagi
 Jeśli port debugowania nie ma sposobu określenia, kiedy załadowany lub zwolnione programy, dostawca port niestandardowy, należy zaimplementować ten interfejs. Wszystkie programy, które są ładowane do debugowania za pośrednictwem określonego portu są śledzone za pomocą tego interfejsu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)