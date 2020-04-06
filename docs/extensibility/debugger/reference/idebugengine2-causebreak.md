---
title: IDebugEngine2::CauseBreak | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731157"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Żąda, aby wszystkie programy są debugowane przez ten aparat debugowania (DE), aby zatrzymać wykonanie następnym razem, gdy jeden z ich wątków próbuje uruchomić.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest asynchroniczne: [zdarzenie IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) jest wysyłane, gdy program próbuje wykonać po wywołaniu tej metody.

## <a name="see-also"></a>Zobacz też
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
