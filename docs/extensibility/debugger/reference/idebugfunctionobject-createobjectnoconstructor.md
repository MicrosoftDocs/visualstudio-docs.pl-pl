---
description: Tworzy obiekt bez konstruktora.
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2a35cab590ab763a3598f45ebe79543e66c2fa4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073524"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Tworzy obiekt bez konstruktora.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pClassObject`\
podczas Obiekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący typ obiektu, który ma zostać utworzony.

`ppObject`\
określoną Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje wystąpienie struktury lub typu złożonego (który nie wymaga konstruktora), który jest parametrem funkcji reprezentowanej przez interfejs [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Jeśli parametr obiektu wymaga konstruktora, wywołaj metodę [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
