---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d3af0affa1c6d98a8209a6a72913f9c2bccf1fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729569"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Pobiera wynik oceny wyrażenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>Parametry
`ppResult`[na zewnątrz] Zwraca obiekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje wynik oceny wyrażenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwrócony [obiekt IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) zawiera wartość obliczonego wyrażenia. Należy zauważyć, że ta wartość może być złożoną wartością, taką jak tablica, ale wynik końcowy musi być wartością numeryczną lub ciągiem, która jest wyświetlana użytkownikowi.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
