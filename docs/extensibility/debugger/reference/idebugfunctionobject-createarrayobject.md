---
description: Tworzy obiekt Array.
title: 'IDebugFunctionObject:: xmlarrayobject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94216521f0a57a76f83c68f168ed1afcac199a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073550"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Tworzy obiekt Array. Ta tablica może zawierać wartości pierwotne lub wystąpienia obiektu.

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
podczas Określa wartość z wyliczenia [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) wskazującego typ nowego obiektu tablicy.

`pClassField`\
podczas Obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący klasę obiektu, jeśli tworzysz tablicę wartości wystąpienia obiektu. Jeśli tworzysz tablicę obiektów pierwotnych, ten parametr jest wartością null.

`dwRank`\
podczas Ranga lub liczba wymiarów tablicy.

`dwDims`\
podczas Rozmiary każdego wymiaru tablicy.

`dwLowBounds`\
podczas Początek każdego wymiaru (zwykle 0 lub 1).

`ppObject`\
określoną Zwraca obiekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzoną tablicę. Jest to obiekt [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje parametr Array do funkcji reprezentowanej przez interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
