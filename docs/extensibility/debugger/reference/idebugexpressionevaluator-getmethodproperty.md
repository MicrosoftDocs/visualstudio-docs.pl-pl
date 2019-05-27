---
title: IDebugExpressionEvaluator::GetMethodProperty | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3fd0adf7d990c133b29dac724b863bc5608ac433
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200894"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Ta metoda pobiera obiekt właściwości, który zawiera zmienne, argumenty i inne właściwości, metody.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametry
`pSymbolProvider`\
[in] Dostawca symboli, które ma być używany, wyrażone jako [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) obiektu.

`pAddress`\
[in] Adres w kodzie, wyrażone jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu, które powinny zostać rozwiązane do najbliższej zawierającego funkcję.

`pBinder`\
[in] Obiekt wiążący, który ma być używany, wyrażone jako [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiektu.

`fIncludeHiddenLocals`\
[in] Wartość różną od zera (`TRUE`) oznacza, że zawierają ukryte elementy lokalne; wartość zero (`FALSE`) oznacza, że Opuść ukryte elementy lokalne

`ppProperty`\
[out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje metodę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ukryte elementy lokalne są zwykle zmienne, które są generowane przez kompilator.

## <a name="see-also"></a>Zobacz także
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)