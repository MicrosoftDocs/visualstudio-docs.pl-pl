---
description: Ta metoda szacuje przeanalizowane wyrażenie i opcjonalnie rzutuje wynik na inny typ danych.
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99760fb35975834186beddf2962ea8402543d088
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143107"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Ta metoda szacuje przeanalizowane wyrażenie i opcjonalnie rzutuje wynik na inny typ danych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametry
`dwEvalFlags`\
podczas Kombinacja stałych [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) kontrolujących sposób oceniania wyrażenia.

`dwTimeout`\
podczas Określa maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.

`pSymbolProvider`\
podczas Dostawca symboli wyrażony jako interfejs [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
podczas Bieżąca lokalizacja wykonywania w ramach metody wyrażona jako interfejs [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
podczas Spinacz, wyrażony jako interfejs [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`bstrResultType`\
podczas Typ, do którego ma być rzutowany wynik. Ten argument może być wartością null.

`ppResult`\
określoną Zwraca interfejs [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje wyniki oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst oceny wyrażenia jest określany przez `pAddress` , co umożliwia określenie metody zawierającej, a następnie użycie reguł określania zakresu języka w celu określenia wartości symboli w wyrażeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
