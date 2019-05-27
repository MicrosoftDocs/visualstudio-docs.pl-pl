---
title: IDebugProgramNodeAttach2::OnAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce1b5635685971b3a9390533589975ff0f323021
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203791"
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