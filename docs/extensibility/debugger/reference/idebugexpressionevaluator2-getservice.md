---
description: Pobiera obiekt usługi z uwzględnieniem jego unikatowego identyfikatora.
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092010"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Pobiera obiekt usługi z uwzględnieniem jego unikatowego identyfikatora.

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
podczas Unikatowy identyfikator usługi do pobrania.

`ppService`\
określoną Zwraca obiekt, który reprezentuje usługę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Może to być wykorzystane przez ewaluatora wyrażeń innych firm do uzyskiwania usług z innej ewaluatora wyrażeń. Na przykład ta metoda może służyć do uzyskania interfejsu dla usługi wizualizatora z domyślnej ewaluatora wyrażeń. Ocenianie wyrażeń innych firm jest mało prawdopodobne, aby zaimplementować ten interfejs.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
