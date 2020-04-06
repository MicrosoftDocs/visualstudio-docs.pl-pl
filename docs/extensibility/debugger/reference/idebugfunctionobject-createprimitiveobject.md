---
title: IDebugFunctionObject::CreatePrimitiveObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728535"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Tworzy prymitywny obiekt danych, taki jak prosta liczna.

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
[w] Wartość z [wyliczenia OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) reprezentujący typ pierwotnego do utworzenia.

`ppObject`\
[na zewnątrz] Zwraca [obiekt IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący nowo utworzony obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody, aby utworzyć obiekt, który reprezentuje obiekt pierwotny, który jest parametrem funkcji, która jest reprezentowana przez interfejs [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Na przykład jeśli ciąg wyrażenia jest "myString(5)", ta metoda będzie używana do tworzenia obiektu reprezentującego całkowitą 5.

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
