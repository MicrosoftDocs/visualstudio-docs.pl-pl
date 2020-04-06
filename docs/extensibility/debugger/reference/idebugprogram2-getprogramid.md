---
title: IDebugProgram2::GetProgramId | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb172f48b63ef2ec182f1a83d599a91eff1e2ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722771"
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
[na zewnątrz] Zwraca `GUID` dla tego programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aparat debugowania (DE) musi zwracać identyfikator programu pierwotnie przekazany do [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) lub [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Umożliwia to identyfikację programu w składnikach debugera.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
