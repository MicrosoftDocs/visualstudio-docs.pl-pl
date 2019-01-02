---
title: IDebugProperty2::SetValueAsReference | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 079a80ddae42c68eb9b57b42183fa639c7b76241
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887162"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Ustawia wartość tej właściwości wartość danego odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rgpArgs`  
 [in] Tablica argumentów do przekazania do metody ustawiającej właściwość kodu zarządzanego. Jeśli metoda ustawiająca właściwości nie przyjmuje argumentów, lub jeśli [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu nie odwołuje się do takich właściwości metody ustawiającej, `rgpArgs` powinien mieć wartość null. Ten parametr jest zazwyczaj wartość null.  
  
 `dwArgCount`  
 [in] Liczba argumentów w `rgpArgs` tablicy.  
  
 `pValue`  
 [in] Odwołanie w formie [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu wartości do użycia, aby ustawić tę właściwość.  
  
 `dwTimeout`  
 [in] Jak długo konieczne w celu ustawienia wartości, w milisekundach. To typowa wartość `INFINITE`. Ma to wpływ na długość czasu, przez jaki wszystkie możliwe oceny może potrwać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca błąd kodu, zazwyczaj jedną z następujących czynności:  
  
|Błąd|Opis|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Ustawienie wartości z odwołania nie jest obsługiwana.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Nie można ustawić wartość, ponieważ ta właściwość odwołuje się do metody.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Wartość jest tylko do odczytu i nie można ustawić.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)