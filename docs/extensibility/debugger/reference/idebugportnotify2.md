---
description: Ten interfejs rejestruje lub wyrejestrowuje program, który może być debugowany przy użyciu portu, na którym jest uruchomiony.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 759be0ff57da7c6bb65ed6ca8191720f835b894a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169343"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Ten interfejs rejestruje lub wyrejestrowuje program, który może być debugowany przy użyciu portu, na którym jest uruchomiony.

## <a name="syntax"></a>Składnia

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs, aby obsługiwać Dodawanie i usuwanie programów z portu. Jest zazwyczaj zaimplementowany dla tego samego obiektu, który implementuje interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [polecenia QueryInterface](/cpp/atl/queryinterface) w `IDebugPort2` interfejsie zwraca ten interfejs. Ponadto wywołanie [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) zwraca ten interfejs. Aparat debugowania może zobaczyć ten interfejs jako parametr do [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugPortNotify2` .

|Metoda|Opis|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Rejestruje program, który może być debugowany przy użyciu portu, na którym jest uruchomiony.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Wyrejestrowuje program, który może być debugowany z portu, w którym jest uruchomiony.|

## <a name="remarks"></a>Uwagi
 Jeśli port debugowania nie ma sposobu, aby wiedzieć, kiedy programy są ładowane lub zwalniane, dostawca portu niestandardowego musi zaimplementować ten interfejs. Wszystkie programy, które są ładowane do debugowania za pośrednictwem określonego portu są śledzone przy użyciu tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
