---
title: IDebugExpressionEvaluator2::GetService | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac6f73e31e7e15a2ffd86e2d969f98a686fbd004
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842935"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Pobiera obiekt usługi, na podstawie jego unikatowy identyfikator.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

#### <a name="parameters"></a>Parametry
 `uid`

 [in] Unikatowy identyfikator usługi do pobrania.

 `ppService`

 [out] Zwraca obiekt, który reprezentuje usługę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 To mogą być używane przez ewaluatora wyrażeń innych firm, można uzyskać usługi z innego Ewaluator wyrażeń. Na przykład tej metody może służyć do uzyskiwania interfejsu usługi Wizualizator z domyślną Ewaluator wyrażeń. Ewaluatory wyrażeń firm prawdopodobnie nie trzeba implementować ten interfejs.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)