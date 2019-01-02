---
title: IDebugMemoryBytes2::WriteAt | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c7d9cbd621b24db26316cc7fca48352a7d97df6e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873187"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapisuje określoną liczbę bajtów pamięci, zaczynając od określonego adresu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie rozpoczyna zapis bajtów.  
  
 `dwCount`  
 [in] Liczba bajtów do zapisania.  
  
 `rgbMemory`  
 [in] Bajty do zapisania. Ta tablica zakłada, że co najmniej `dwCount` bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie wszystkie wartości bajtowe mogłyby być zapisywane lub zwraca kod błędu (zwykle `E_FAIL`).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli adres początkowy nie jest w obrębie okna pamięci, reprezentowane przez ten [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiektu występuje nie zapisywania i kod błędu `E_FAIL` zwróceniem — nawet wtedy, gdy kwota do zapisania nakłada się do obszaru pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)