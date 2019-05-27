---
title: IDebugParsedExpression::EvaluateSync | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1161b97c642b7dc28f2b27037ef3253adf9f6eda
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209732"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Ta metoda oblicza wyrażenie przeanalizowany i opcjonalnie rzutuje wynik, który ma inny typ danych.

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
[in] Kombinacji [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) stałe, które kontrolują sposób ma zostać obliczone wyrażenie.

`dwTimeout`\
[in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

`pSymbolProvider`\
[in] Dostawca symboli, wyrażone jako [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfejsu.

`pAddress`\
[in] Bieżąca lokalizacja wykonywania w metodzie, wyrażone jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

`pBinder`\
[in] Obiekt wiążący wyrażonej w postaci [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfejsu.

`bstrResultType`\
[in] Typ wyniku powinna być rzutowany. Ten argument może być wartością null.

`ppResult`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wyniki oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Kontekst oceny wyrażeń jest nadawana przez `pAddress`, która sprawia, że można określić zawierającego metodę, i następnie zakresu języka Użyj reguły do określenia wartości symboli w wyrażeniu.

## <a name="see-also"></a>Zobacz także
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)