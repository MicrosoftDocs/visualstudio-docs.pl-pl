---
description: Ta metoda ustawia katalog główny rejestru.
title: 'IDebugExpressionEvaluator:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14ce5d00dcfec9da4c6193398f62edbe4e1988d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092049"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Ta metoda ustawia katalog główny rejestru. Używany do debugowania równoczesnego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

## <a name="parameters"></a>Parametry
`ustrRegistryRoot`\
podczas Nowy katalog główny rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Określony katalog główny rejestru jest zazwyczaj ustawiany podczas pierwszego tworzenia wystąpienia ewaluatora wyrażeń i wskazuje na klucz rejestru dla określonej wersji programu Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y*, gdzie *X. y* jest numerem wersji).

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
