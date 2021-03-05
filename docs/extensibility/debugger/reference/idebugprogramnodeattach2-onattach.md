---
description: Dołącza do skojarzonego programu lub przypisuje proces Attach do metody Attach.
title: 'IDebugProgramNodeAttach2:: OnAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d1fdb6f0e2fe41555dbbc3b1bcfd16a1a2b4240
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167051"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Dołącza do skojarzonego programu lub przypisuje proces Attach do metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

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
[w] `GUID` Aby przypisać do skojarzonego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` czy metoda [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) nie powinna być wywoływana. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana podczas procesu dołączania przed wywołaniem metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . `OnAttach`Metoda może wykonać sam proces dołączania (w tym przypadku Metoda ta zwraca `S_FALSE` ) lub Odłóż proces dołączania do `IDebugEngine2::Attach` metody ( `OnAttach` Metoda zwraca `S_OK` ). W każdym z tych zdarzeń `OnAttach` Metoda może ustawić w `GUID` debugowanym programie program do danego elementu `GUID` .

## <a name="see-also"></a>Zobacz też
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
