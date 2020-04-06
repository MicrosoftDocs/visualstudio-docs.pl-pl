---
title: IDebugFunctionObject::CreateArrayObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728617"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Tworzy obiekt tablicy. Ta tablica może zawierać wartości pierwotne lub wystąpienia obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ot`\
[w] Określa wartość z [wyliczenia OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) wskazujące typ nowego obiektu tablicy.

`pClassField`\
[w] [Obiekt IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący klasę obiektu, jeśli tworzy tablicę wartości wystąpienia obiektu. W przypadku tworzenia tablicy obiektów pierwotnych, ten parametr jest wartością null.

`dwRank`\
[w] Ranga lub liczba wymiarów tablicy.

`dwDims`\
[w] Rozmiary każdego wymiaru tablicy.

`dwLowBounds`\
[w] Początek każdego wymiaru (zazwyczaj 0 lub 1).

`ppObject`\
[na zewnątrz] Zwraca obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzoną tablicę. To jest rzeczywiście [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody, aby utworzyć obiekt, który reprezentuje parametr tablicy do funkcji, która jest reprezentowana przez interfejs [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
