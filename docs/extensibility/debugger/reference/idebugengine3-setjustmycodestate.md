---
title: IDebugEngine3::SetJustMyCodeState | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9dafc7a98b511c9d7b8367e96621faee9e2cbc22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914426"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Ta metoda informuje aparat debugowania o stan JustMyCode.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fUpdate`  
 [in] Wartość różną od zera (`TRUE`) aby zaktualizować bieżące informacje, od zera (`FALSE`) można zresetować wszystkie informacje (bez uwzględnienia niczego ustawione wcześniej).  
  
 `dwModules`  
 [in] Liczba struktur informacji w `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Tablica [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) struktury do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 JustMyCode to pojęcie debugowania tylko kodu, który należy do użytkownika i ignoruje wszelkie kodu pośredniego, takich jak systemu kodu — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)