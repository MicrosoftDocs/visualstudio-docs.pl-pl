---
title: IDebugExpressionEvaluator2::GetService | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729347"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Pobiera obiekt usługi, biorąc pod uwagę jego unikatowy identyfikator.

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

## <a name="parameters"></a>Parametry
`uid`\
[w] Unikatowy identyfikator usługi do pobrania.

`ppService`\
[na zewnątrz] Zwraca obiekt, który reprezentuje usługę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Może to być używane przez oceniającego wyrażenie innej firmy w celu uzyskania usług od innego oceniającego wyrażenie. Na przykład ta metoda może służyć do uzyskania interfejsu dla usługi wizualizatora z domyślnego oceniającego wyrażenie. Oceniający wyrażenia innych firm prawdopodobnie nie będą musieli zaimplementować tego interfejsu.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
