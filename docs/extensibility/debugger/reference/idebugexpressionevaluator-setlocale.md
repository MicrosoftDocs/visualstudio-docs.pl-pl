---
description: Ta metoda ustawia język, który ma być używany do tworzenia wyników drukowalnych.
title: 'IDebugExpressionEvaluator:: setlocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f833311fe9029931c0d56cbe828bd027c45c26a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092062"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Ta metoda ustawia język, który ma być używany do tworzenia wyników drukowalnych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametry
`wLangID`\
podczas Identyfikator języka.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda może być wywoływana wiele razy podczas ładowania ewaluatora wyrażeń (EE), więc w przypadku wersji EE musi być możliwe przełączenie języków na bieżąco. Na stronie EE są stosowane te ustawienia regionalne, które zwracają komunikaty o błędach i ciągi w odpowiednim języku.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
