---
title: IDebugFunctionObject2::CreateObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728476"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Tworzy obiekt, który używa konstruktora podane ustawienia flagi oceny i wartość limitu czasu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parametry
`pConstructor`\
[w] [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu, który reprezentuje konstruktora obiektu, który ma zostać utworzony.

`dwArgs`\
[w] Liczba parametrów w `pArg` tablicy. Reprezentuje liczbę parametrów przekazanych do konstruktora.

`pArgs`\
[w] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektów, która reprezentuje parametry przekazywane do konstruktora.

`dwEvalFlags`\
[w] Kombinacja flag z [wyliczenia EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) które określają sposób wykonywania oceny.

`dwTimeout`\
[w] Maksymalny czas ( w milisekundach) oczekiwania przed zwróceniem tej metody. Użyj **INFINITE** czekać przez czas nieokreślony.

`ppObject`\
[na zewnątrz] Zwraca **obiekt IDebugObject** reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody, aby utworzyć obiekt, który reprezentuje wystąpienie klasy lub innego typu złożonego, który wymaga konstruktora, który jest parametrem.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
