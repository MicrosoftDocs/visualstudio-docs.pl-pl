---
description: Ta metoda pobiera obiekt właściwości, który zawiera wartości lokalne, argumenty i inne właściwości metody.
title: 'IDebugExpressionEvaluator:: GetMethodProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4a82ce250b47f2f199d9e8e8fcf3a2ca7ec5777
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092179"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Ta metoda pobiera obiekt właściwości, który zawiera wartości lokalne, argumenty i inne właściwości metody.

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
podczas Dostawca symboli, który ma być używany, wyrażony jako obiekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
podczas Adres w kodzie, wyrażony jako obiekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , który powinien zostać rozpoznany do najbliższej funkcji zawierającej.

`pBinder`\
podczas Spinacz, który ma być używany, wyrażony jako obiekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
podczas Wartość niezerowa ( `TRUE` ) oznacza uwzględnienie ukrytych elementów lokalnych; zero ( `FALSE` ) oznacza pozostawienie ukrytych elementów lokalnych.

`ppProperty`\
określoną Zwraca obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje metodę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ukryte elementy lokalne są zwykle zmiennymi, które są generowane przez kompilator.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
