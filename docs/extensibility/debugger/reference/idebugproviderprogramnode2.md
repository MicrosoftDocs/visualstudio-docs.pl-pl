---
title: IDebugProviderProgramNode2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33c4a4914e15a8ecbea0d4f28c2325a952a042de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353807"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Ten interfejs kieruje związane z interfejsów granice procesu.

## <a name="syntax"></a>Składnia

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) do obsługi organizowania interfejsów granice procesu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejsu w celu uzyskania tego interfejsu. Jeśli nie można uzyskać ten interfejs, DE nie obsługuje organizowanie interfejsów.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Pobiera określonego interfejsu, granice procesu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest implementowany, gdy DE jest uruchamiane w innej przestrzeni procesu debugowanego: na przykład, gdy DE jest uruchomiony w przestrzeni procesu programu Visual Studio, zamiast obszaru debugowanego procesu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)