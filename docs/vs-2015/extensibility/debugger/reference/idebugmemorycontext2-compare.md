---
title: IDebugMemoryContext2::Compare | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163430"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porównuje kontekstu pamięci dla każdego kontekstu w podanej tablicy w sposób wskazany przez porównanie flag, zwraca indeks pierwszego kontekst, który jest zgodny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
