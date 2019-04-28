---
title: IDebugProgramEngines2::SetEngine | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78755a75582ed3e61784b8e7762f7f9f6390a34c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917180"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Informuje program lub węzeł program który aparat debugowania (DE) do użycia, aby debugować ten program.

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

#### <a name="parameters"></a>Parametry
 `guidEngine`

 [in] Identyfikator GUID DE.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)