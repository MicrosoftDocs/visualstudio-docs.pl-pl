---
title: IDebugReference2::GetMemoryBytes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryBytes
helpviewer_keywords:
- IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fa57614dfa7a27c38750d6162f3a224d5f86e2f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212942"
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
Pobiera bajty pamięci, które fizycznie zawierają wartość odwołania. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parametry
`ppMemoryBytes`\
[out] Zwraca [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiekt, który może służyć do pobierania pamięci, który zawiera wartości odwołania.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)