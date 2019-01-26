---
title: IDebugEngine2::GetEngineID | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 398e4f11702afc3184fb7d081f65a99cccad0bcf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924006"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Pobiera identyfikator GUID aparat debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEngineID(   
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineID(   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidEngine`  
 [out] Zwraca identyfikator GUID DE.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Oto kilka przykładów typowych identyfikatorów GUID `guidScriptEng`, `guidNativeEng`, lub `guidSQLEng`. Nowe aparaty debugowania spowoduje utworzenie własnych identyfikator GUID do identyfikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CEngine` obiekt, który implementuje [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejsu.  
  
```cpp  
HRESULT CEngine::GetEngineId(GUID *pguidEngine){    
   if (pguidEngine) {    
      // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.    
      // Other languages would require their own guidDifferentEngine to be  
      //defined in the Batdbg.idl file.    
      *pguidEngine = guidBatEng;    
      return NOERROR; // This is typically S_OK.    
   } else {  
      return E_INVALIDARG;    
   }    
}    
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)