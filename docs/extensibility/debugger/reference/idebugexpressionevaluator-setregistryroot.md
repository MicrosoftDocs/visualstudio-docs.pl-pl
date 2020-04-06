---
title: IDebugExpression Wartośćwacja::SetRegistryRoot | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729414"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Ta metoda ustawia katalog główny rejestru. Służy do debugowania obok siebie.

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
[w] Nowy katalog główny rejestru.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Określony katalog główny rejestru jest zazwyczaj ustawiany, gdy oceniający wyrażenie jest najpierw wystąpienia i wskazuje klucz rejestru dla określonej wersji programu\\Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, gdzie *X.Y* jest numerem wersji).

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
