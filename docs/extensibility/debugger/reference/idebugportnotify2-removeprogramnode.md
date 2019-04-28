---
title: IDebugPortNotify2::RemoveProgramNode | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords:
- IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09c7ccfcfee13f667091e96a638c17be2c9616d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871660"
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
Wyrejestrowuje program, który może być debugowany z portu, na którym jest uruchomiona na.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RemoveProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int RemoveProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

#### <a name="parameters"></a>Parametry
 `pProgramNode`

 [in] [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objecy, który reprezentuje program do wyrejestrowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda usuwa węzła program, który został dodany z wywołaniem [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)