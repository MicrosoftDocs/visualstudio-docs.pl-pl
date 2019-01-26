---
title: IDebugMemoryContext2::Add | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9625bcdc69d4df157f4309ae24d4baafcda1264a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974347"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Dodaje określoną wartość do bieżącego kontekstu i zwraca nowy kontekst.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCount`  
 [in] Wartość do dodania do bieżącego kontekstu.  
  
 `ppMemCxt`  
 [out] Zwraca nowy [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kontekst pamięci nie jest adresem, dlatego dodanie wartości do adresu tworzy nowy adres, który wymaga nowy interfejs kontekstu.  
  
 Ta metoda zawsze musi mieć nowy kontekst, nawet jeśli otrzymany adres znajduje się poza obszar pamięci skojarzone z tym kontekstem. Jedynym wyjątkiem jest, jeśli nie pamięć może być przydzielenia w nowym kontekście lub `ppMemCxt` jest wartością null (jest to błąd).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)