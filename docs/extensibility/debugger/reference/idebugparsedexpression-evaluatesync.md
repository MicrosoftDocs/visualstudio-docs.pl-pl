---
title: IDebugParsedExpression::EvaluateSync | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726008"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Ta metoda ocenia analizowane wyrażenie i opcjonalnie rzutuje wynik do innego typu danych.

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
[w] Kombinacja stałych [EVALFLAGS,](../../../extensibility/debugger/reference/evalflags.md) które kontrolują sposób oceny wyrażenia.

`dwTimeout`\
[w] Określa maksymalny czas oczekiwania w milisekundach przed zwróceniem z tej metody. Służy `INFINITE` do oczekiwania przez czas nieokreślony.

`pSymbolProvider`\
[w] Dostawca symbolu, wyrażony jako interfejs [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[w] Bieżąca lokalizacja wykonywania w ramach metody, wyrażona jako interfejs [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[w] Spinacz, wyrażony jako interfejs [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
[w] Typ wynik powinien być rzutowy do. Ten argument może być wartością null.

`ppResult`\
[na zewnątrz] Zwraca interfejs [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje wyniki oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst oceny wyrażenia jest `pAddress`podany przez , co umożliwia określenie metody zawierającej, a następnie użycie reguł zakresu języka do określenia wartości symboli w wyrażeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
