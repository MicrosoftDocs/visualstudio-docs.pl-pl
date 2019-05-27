---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae31296d1264715c23a05ef893c159392baf245d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199093"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Tworzy obiekt danych pierwotnych, takie jak proste liczby całkowitej.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ot`\
[in] Wartość z zakresu od [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) wyliczenie przedstawiające typ pierwotny, aby utworzyć.

`ppObject`\
[out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę, aby utworzyć obiekt, który reprezentuje pierwotny obiekt, który jest parametr do funkcji, która jest reprezentowana przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu. Na przykład jeśli ciąg wyrażenia "myString(5)", ta metoda może służyć do tworzenia obiekt reprezentujący liczbę całkowitą 5.

## <a name="see-also"></a>Zobacz także
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)