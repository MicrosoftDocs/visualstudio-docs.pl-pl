---
title: IDebugProgramPublisher2::PublishProgramNode | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df68e72ee8597805bf02cb9c6e1c3a0bcaf8a449
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721666"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Udostępnia węzeł programu do użytku przez aparaty debugowania (DEs) i menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parametry
`pProgramNode`\
[w] [Obiekt IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujący węzeł programu do udostępnienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda umożliwia programy, które mają być poszukiwane w poszukiwaniu informacji przed wybraniem i uruchomieniem ich do debugowania.

 Aby usunąć węzeł programu z dostępności, należy wywołać [metodę UnpublishProgramNode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)

## <a name="see-also"></a>Zobacz też
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
