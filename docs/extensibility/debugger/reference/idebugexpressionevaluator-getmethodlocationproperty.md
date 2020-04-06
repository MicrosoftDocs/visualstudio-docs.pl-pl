---
title: IDebugExpressionAwartuator::GetMethodLocationProperty | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729519"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Ta metoda konwertuje lokalizację metody i przesunięcie na adres pamięci.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametry
`upstrFullyQualifiedMethodPlusOffset`\
[w] Lokalizacja metody i przesunięcie, wyrażone jako ciąg.

`pSymbolProvider`\
[w] Dostawca symbolu wyrażony jako obiekt [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[w] Adres w ramach metody, wyrażone jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.

`pBinder`\
[w] Spinacz wyrażony jako obiekt [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
[na zewnątrz] Zwraca interfejs [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje adres pamięci.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zwracany adres może służyć do ustawiania punktu przerwania, na przykład.

 Pomimo nazwy, `upstrFullyQualifiedMethodPlusOffset`ten parametr może być przekazywany częściowo kwalifikowaną nazwą metody. W takim przypadku wybrana metoda jest tą, która obejmuje `pAddress`. Sposób interpretacji tego parametru zależy od implementacji oceniającego wyrażenie i języka, który obsługuje.

## <a name="see-also"></a>Zobacz też
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
