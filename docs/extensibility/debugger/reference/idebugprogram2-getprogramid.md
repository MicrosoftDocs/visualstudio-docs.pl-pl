---
title: IDebugProgram2::GetProgramId | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca86175d34cc1bfd54882adda7e1f7cb464fb22f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212647"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Pobiera identyfikator GUID dla tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Parametry
`pguidProgramId`\
[out] Zwraca `GUID` dla tego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aparat debugowania (DE) musi zwrócić identyfikatora programu pierwotnie przekazana do [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) lub [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Dzięki temu identyfikacji programu przez debuger składników.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)