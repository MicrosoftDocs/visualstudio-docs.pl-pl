---
title: IDebugProviderProgramNode2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720682"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Ten interfejs marshals interfejsów związanych z programem w granicach procesu.

## <a name="syntax"></a>Składnia

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) do obsługi interfejsów kierowanie przez granice procesu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na interfejsie, `IDebugProgramNode2` aby uzyskać ten interfejs. Jeśli nie można uzyskać tego interfejsu, DE nie obsługuje organizowania interfejsów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Pobiera określony interfejs w granicach procesu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest implementowany, gdy DE działa w oddzielnej przestrzeni procesu z programu są debugowane: na przykład, gdy DE jest uruchomiony w przestrzeni procesu programu Visual Studio zamiast przestrzeni procesu programu jest debugowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
