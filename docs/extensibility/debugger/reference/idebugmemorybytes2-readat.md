---
title: IDebugMemoryBytes2::ReadAt | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42b159ebf70da6c00e649f1aee139df6aa1283ce
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894171"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Odczytuje sekwencji bajtów, zaczynając od danej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie należy rozpocząć odczyt bajtów.  
  
 `dwCount`  
 [in] Liczba bajtów do odczytania. Również określa długość `rgbMemory` tablicy.  
  
 `rgbMemory`  
 [out w] Tablica wypełniona Bajty odczytane.  
  
 `pdwRead`  
 [out] Zwraca liczbę bajtów ciągłych odczytane.  
  
 `pdwUnreadable`  
 [out w] Zwraca liczbę bajtów nie można go odczytać. Może być wartością null, jeśli klient jest zainteresowany liczbę bajtów nie można go odczytać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wymagane są 100 bajtów i 50 pierwszych można odczytać, następnych 20 są nieczytelne i pozostałe 30 do odczytu, Metoda ta zwraca:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 W tym przypadku ponieważ `*pdwRead + *pdwUnreadable < dwCount`, obiekt wywołujący musi wywoływania dodatkowych odczytu pozostałe bajty 30 oryginalnego 100, żądane i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt przekazany w `pStartContext` parametru musi być zaawansowane za 70.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)