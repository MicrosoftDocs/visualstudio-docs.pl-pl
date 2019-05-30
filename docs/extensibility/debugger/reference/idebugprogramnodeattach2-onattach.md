---
title: IDebugProgramNodeAttach2::OnAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01958b26b5b381bdbe51c2648d2751e822002e6b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325054"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Dołącza do skojarzonego programu lub procesu dołączania do odracza [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parametry
`guidProgramId`\
[in] `GUID` można przypisać do skojarzonego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) nie powinna być wywoływana metoda. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana podczas procesu dołączania przed [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana. `OnAttach` Metodę można wykonać sam proces attach (w którym to przypadku ta metoda zwraca `S_FALSE`) lub Odrocz procesu dołączania do `IDebugEngine2::Attach` — metoda ( `OnAttach` metoda zwraca `S_OK`). W obu przypadkach `OnAttach` metody można ustawić `GUID` programu debugowania do danego `GUID`.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)