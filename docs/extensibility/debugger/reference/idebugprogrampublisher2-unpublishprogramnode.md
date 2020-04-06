---
title: IDebugProgramPublisher2::UnpublishProgramNode | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae2c3d9f3c9f6c500b10f580035312b2d045689a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721580"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
Usuwa określony węzeł programu z dostępności do aparatów debugowania (DEs) i menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```cpp
HRESULT UnpublishProgramNode(
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int UnpublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parametry
`pProgramNode`\
[w] [Obiekt IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujący usunięty węzeł programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po usunięciu węzeł programu nie jest już dostępny do kwerendy w celu uzyskania informacji o programie.

 Aby udostępnić węzeł programu, należy [wywołać metodę PublishProgramNode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

## <a name="see-also"></a>Zobacz też
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
