---
title: IDebugProcess2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 83cb927d86604096eac89da1d0efdf7e64e209be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353225"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Określa, jeżeli Menedżer debugowania sesji (SDM) można odłączyć procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK.` zwraca `S_FALSE` Jeśli debuger nie można odłączyć od procesu. W przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)