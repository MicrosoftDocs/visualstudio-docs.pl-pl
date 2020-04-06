---
title: IDebugFunctionObject::CreateObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728597"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Tworzy obiekt przy użyciu konstruktora.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parametry
`pConstructor`\
[w] [Obiekt IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) reprezentujący konstruktor obiektu, który ma zostać utworzony.

`dwArgs`\
[w] Liczba parametrów w `pArg` tablicy. Reprezentuje liczbę parametrów przekazanych do konstruktora.

`pArg`\
[w] Tablica [obiektów IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujących parametry przekazywane do konstruktora.

`ppObject`\
[na zewnątrz] Zwraca `IDebugObject` reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody, aby utworzyć obiekt, który reprezentuje wystąpienie klasy (lub innego typu złożonego, który wymaga konstruktora), który jest parametrem funkcji, która jest reprezentowana przez interfejs [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Jeśli parametr obiektu nie wymaga konstruktora, [wywołaj metodę CreateObjectNoConstructor.](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
