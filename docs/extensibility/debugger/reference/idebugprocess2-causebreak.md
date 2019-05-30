---
title: IDebugProcess2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbe4f3cac40306467e6efc7d87ca860a6d6f3f0e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353241"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Żądania następnego program jest uruchomiony kod w ramach tego procesu, Zatrzymaj i wysłać [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) obiektem zdarzenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CauseBreak( 
   void
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)