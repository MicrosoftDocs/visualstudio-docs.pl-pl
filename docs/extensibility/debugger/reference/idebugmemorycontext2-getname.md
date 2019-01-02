---
title: IDebugMemoryContext2::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 708402de28b7385d33c014e3b7c216cddc124d96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907936"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Pobiera użytkownika zawiera nazwę dla tego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrName`  
 [out] Zwraca nazwę kontekstu pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa kontekstu pamięci nie jest zwykle używana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)