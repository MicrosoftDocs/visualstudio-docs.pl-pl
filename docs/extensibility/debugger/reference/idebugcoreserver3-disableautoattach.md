---
title: IDebugCoreServer3::DisableAutoAttach | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52d92cdfbbf076a733cacba307d30fe2006a4fc6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317748"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
Wyłącza automatyczne dołączanie do wszystkich aparatów debugowania skojarzone z tym serwerem.

## <a name="syntax"></a>Składnia

```cpp
HRESULT DisableAutoAttach(
   void
);
```

```csharp
int DisableAutoAttach();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)