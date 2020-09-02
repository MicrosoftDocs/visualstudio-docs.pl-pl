---
title: 'IDebugExpressionEvaluator:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11e7cd69ed3f1e1b23cc0f2f03f3fd2cf912d308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729414"
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
 Określony katalog główny rejestru jest zazwyczaj ustawiany podczas pierwszego tworzenia wystąpienia ewaluatora wyrażeń i wskazuje na klucz rejestru dla określonej wersji programu Visual Studio (HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. y*, gdzie *X. y* jest numerem wersji).

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
