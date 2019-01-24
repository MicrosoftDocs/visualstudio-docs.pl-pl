---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760553"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda konwertuje metody lokalizacji i Przesunięcie adresu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] Metoda lokalizacji i przesunięcie, wyrażone jako ciąg.  
  
 `pSymbolProvider`  
 [in] Dostawca symboli wyrażonej w postaci [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) obiektu.  
  
 `pAddress`  
 [in] Adres znajdujący się w metodzie, wyrażone jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
 `pBinder`  
 [in] Obiekt wiążący wyrażonej w postaci [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) obiektu.  
  
 `ppProperty`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje adres pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw punkt przerwania, na przykład można zwróconego adresu.  
  
 Niezależnie od nazwy `upstrFullyQualifiedMethodPlusOffset`, ten parametr może być przekazywany nazwę metody częściowo kwalifikowane. W takim przypadku wybranej metody jest tą, która otacza `pAddress`. Jak ten parametr jest interpretowany zależy od implementacji ewaluatora wyrażeń i język, który ją obsługuje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
