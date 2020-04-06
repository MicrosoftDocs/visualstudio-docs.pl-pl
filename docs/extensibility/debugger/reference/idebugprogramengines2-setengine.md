---
title: IDebugProgramEngines2::SetEngine | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226f5bbf11627a3171641806a673eaa15b614572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722408"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Informuje o węźle programu lub programu, który aparat debugowania (DE) ma być używany do debugowania tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Parametry
`guidEngine`\
[w] Identyfikator GUID DE.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
