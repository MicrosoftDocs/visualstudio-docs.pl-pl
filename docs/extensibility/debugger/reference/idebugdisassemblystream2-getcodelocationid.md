---
title: IDebugDisassemblyStream2::GetCodeLocationId | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b92bb6dbb25dc70032c04041c49164fc8f963bc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988537"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Zwraca identyfikator lokalizacji kodu dla kontekstu określonego kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt ma zostać przekonwertowany na identyfikator.  
  
 `puCodeLocationId`  
 [out] Zwraca identyfikator lokalizacji kodu. Zobacz uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_CODE_CONTEXT_OUT_OF_SCOPE` jeśli kontekst kodu jest prawidłowy, ale poza zakresem.  
  
## <a name="remarks"></a>Uwagi  
 Aparat debugowania (DE), obsługa demontaż dotyczy identyfikator lokalizacji kodu. Ten identyfikator lokalizacji jest używana wewnętrznie przez DE śledzenie pozycji w kodzie i jest zwykle adres lub przesunięcie pewnego rodzaju. Jedynym wymaganiem jest to, że jeśli kontekst kodu z jednej lokalizacji jest mniejsza niż kontekst kodu z innej lokalizacji, a następnie odpowiedni identyfikator kodu w lokalizacji, pierwszy kontekstu kodu również musi być mniejsza niż identyfikator lokalizacji kodu drugi kontekst kodu.  
  
 Aby uzyskać kontekst kodu identyfikatora lokalizacji kodu, należy wywołać [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)