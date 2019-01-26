---
title: IDebugMemoryContext2::Compare | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d2e29cb65fb94ac5e244b7cb0536b6ac7be1901
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946571"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Porównuje kontekstu pamięci dla każdego kontekstu w podanej tablicy w sposób wskazany przez porównanie flag, zwraca indeks pierwszego kontekst, który jest zgodny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `compare`  
 [in] Wartość z zakresu od [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) wyliczenie, który określa typ porównania.  
  
 `rgpMemoryContextSet`  
 [in] Tablica odniesień do [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiektów, które ma zostać wykonane porównanie.  
  
 `dwMemoryContextSetLen`  
 [in] Liczbę kontekstów w `rgpMemoryContextSet` tablicy.  
  
 `pdwMemoryContext`  
 [out] Zwraca indeks pierwszego kontekst pamięci, który spełnia porównanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_COMPARE_CANNOT_COMPARE` Jeśli nie można porównać dwóch kontekstów.  
  
## <a name="remarks"></a>Uwagi  
 Aparat debugowania (DE) nie ma do obsługi wszystkich rodzajów porównań, ale musi obsługiwać co najmniej `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` i `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)