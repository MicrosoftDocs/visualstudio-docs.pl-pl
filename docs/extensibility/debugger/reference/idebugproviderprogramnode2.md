---
title: IDebugProviderProgramNode2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb717363266b95397ea749e7465b07df75f60da2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916425"
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

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)