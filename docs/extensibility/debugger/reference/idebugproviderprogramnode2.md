---
title: IDebugProviderProgramNode2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720682"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Ten interfejs służy do organizowania interfejsów związanych z programem między granicami procesów.

## <a name="syntax"></a>Składnia

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs na tym samym obiekcie, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , aby obsługiwał interfejsy kierujące między różnymi procesami.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejsie, aby uzyskać ten interfejs. Jeśli nie można uzyskać tego interfejsu, usługa DE nie obsługuje organizowania interfejsów.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Pobiera określony interfejs między granicami procesu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest implementowany, gdy działa w oddzielnym obszarze procesu z debugowanym programem: na przykład gdy w obszarze przetwarzania programu Visual Studio nie jest miejsce w debugowanym programie.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
